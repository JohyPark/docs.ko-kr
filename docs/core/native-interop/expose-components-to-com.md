---
title: .NET Core 구성 요소를 COM에 노출
ms.date: 07/12/2019
helpviewer_keywords:
- exposing .NET Core components to COM
- interoperation with unmanaged code, exposing .NET Core components
- COM interop, exposing COM components
ms.assetid: 21271167-fe7f-46ba-a81f-a6812ea649d4
author: jkoritzinsky
ms.author: jekoritz
ms.openlocfilehash: 33574eeac5b1f7aa2067b1974f3f2e68fb22e8ff
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/30/2019
ms.locfileid: "69577175"
---
# <a name="exposing-net-core-components-to-com"></a><span data-ttu-id="5fd47-102">.NET Core 구성 요소를 COM에 노출</span><span class="sxs-lookup"><span data-stu-id="5fd47-102">Exposing .NET Core Components to COM</span></span>

<span data-ttu-id="5fd47-103">.NET Core에서는 COM에 .NET 개체를 공개하는 절차가 .NET Framework에 비해 크게 간소화되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5fd47-103">In .NET Core, the process for exposing your .NET objects to COM has been significantly streamlined in comparison to .NET Framework.</span></span> <span data-ttu-id="5fd47-104">다음 절차에서는 클래스를 COM에 공개하는 방법을 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd47-104">The following process will walk you through how to expose a class to COM.</span></span> <span data-ttu-id="5fd47-105">이 자습서에서는 다음을 수행하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5fd47-105">This tutorial shows you how to:</span></span>

- <span data-ttu-id="5fd47-106">.NET Core에서 COM에 클래스를 공개합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd47-106">Expose a class to COM from .NET Core.</span></span>
- <span data-ttu-id="5fd47-107">.NET Core 라이브러리를 빌드하는 동안 COM 서버를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd47-107">Generate a COM server as part of building your .NET Core library.</span></span>
- <span data-ttu-id="5fd47-108">레지스트리 없는 COM을 위한 병렬 서버 매니페스트를 자동으로 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd47-108">Automatically generate a side-by-side server manifest for Registry-Free COM.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5fd47-109">전제 조건</span><span class="sxs-lookup"><span data-stu-id="5fd47-109">Prerequisites</span></span>

- <span data-ttu-id="5fd47-110">[.NET Core 3.0 Preview 7 SDK](https://www.microsoft.com/net/core) 이상 버전을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd47-110">Install the [.NET Core 3.0 Preview 7 SDK](https://www.microsoft.com/net/core) or a newer version.</span></span>

## <a name="create-the-library"></a><span data-ttu-id="5fd47-111">라이브러리 만들기</span><span class="sxs-lookup"><span data-stu-id="5fd47-111">Create the library</span></span>

<span data-ttu-id="5fd47-112">첫 번째 단계는 라이브러리를 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="5fd47-112">The first step is to create the library.</span></span>

1. <span data-ttu-id="5fd47-113">새 폴더를 만들고 해당 폴더에서 `dotnet new classlib`을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd47-113">Create a new folder, and in that folder run `dotnet new classlib`.</span></span>
2. <span data-ttu-id="5fd47-114">`Class1.cs`를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="5fd47-114">Open `Class1.cs`.</span></span>
3. <span data-ttu-id="5fd47-115">`using System.Runtime.InteropServices;`를 파일의 맨 위에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd47-115">Add `using System.Runtime.InteropServices;` to the top of the file.</span></span>
4. <span data-ttu-id="5fd47-116">`IServer` 인터페이스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5fd47-116">Create an interface named `IServer`.</span></span> <span data-ttu-id="5fd47-117">예: [!code-csharp[The IServer interface](~/samples/core/extensions/COMServerDemo/COMContract/IServer.cs)]</span><span class="sxs-lookup"><span data-stu-id="5fd47-117">For example: [!code-csharp[The IServer interface](~/samples/core/extensions/COMServerDemo/COMContract/IServer.cs)]</span></span>
5. <span data-ttu-id="5fd47-118">구현 중인 COM 인터페이스의 인터페이스 GUID를 사용하여 `[Guid("<IID>")]` 특성을 인터페이스에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd47-118">Add the `[Guid("<IID>")]` attribute to the interface, with the interface GUID for the COM interface you're implementing.</span></span> <span data-ttu-id="5fd47-119">예를 들어, `[Guid("fe103d6e-e71b-414c-80bf-982f18f6c1c7")]`을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd47-119">For example, `[Guid("fe103d6e-e71b-414c-80bf-982f18f6c1c7")]`.</span></span> <span data-ttu-id="5fd47-120">이 GUID는 이 COM용 인터페이스의 유일한 식별자이므로 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd47-120">Note that this GUID needs to be unique since it is the only identifier of this interface for COM.</span></span> <span data-ttu-id="5fd47-121">Visual Studio에서 [도구] > [GUID 만들기]로 이동하여 GUID 만들기 도구를 열고 GUID를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5fd47-121">In Visual Studio, you can generate a GUID by going to Tools > Create GUID to open the Create GUID tool.</span></span>
6. <span data-ttu-id="5fd47-122">`[InterfaceType]` 특성을 인터페이스에 추가하고 이 인터페이스에서 구현해야 하는 기본 COM 인터페이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd47-122">Add the `[InterfaceType]` attribute to the interface and specify what base COM interfaces your interface should implement.</span></span>
7. <span data-ttu-id="5fd47-123">`IServer`를 구현하는 `Server`라는 클래스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5fd47-123">Create a class named `Server` that implements `IServer`.</span></span>
8. <span data-ttu-id="5fd47-124">구현 중인 COM 클래스의 클래스 식별자 GUID를 사용하여 `[Guid("<CLSID>")]` 특성을 클래스에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd47-124">Add the `[Guid("<CLSID>")]` attribute to the class, with the class identifier GUID for the COM class you're implementing.</span></span> <span data-ttu-id="5fd47-125">예를 들어, `[Guid("9f35b6f5-2c05-4e7f-93aa-ee087f6e7ab6")]`을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd47-125">For example, `[Guid("9f35b6f5-2c05-4e7f-93aa-ee087f6e7ab6")]`.</span></span> <span data-ttu-id="5fd47-126">인터페이스 GUID와 마찬가지로 이 GUID는 이 COM용 인터페이스의 유일한 식별자이므로 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd47-126">As with the interface GUID, this GUID must be unique since it is the only identifier of this interface to COM.</span></span>
9. <span data-ttu-id="5fd47-127">인터페이스 및 클래스에 모두 `[ComVisible(true)]` 특성을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd47-127">Add the `[ComVisible(true)]` attribute to both the interface and the class.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5fd47-128">.NET Framework와 달리 .NET Core에서는 COM을 통해 활성화하려는 클래스의 CLSID를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd47-128">Unlike in .NET Framework, .NET Core requires you to specify the CLSID of any class you want to be activatable via COM.</span></span>

## <a name="generate-the-com-host"></a><span data-ttu-id="5fd47-129">COM 호스트 생성</span><span class="sxs-lookup"><span data-stu-id="5fd47-129">Generate the COM host</span></span>

1. <span data-ttu-id="5fd47-130">`.csproj` 프로젝트 파일을 열고 `<PropertyGroup></PropertyGroup>` 태그 안에 `<EnableComHosting>true</EnableComHosting>`을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd47-130">Open the `.csproj` project file and add `<EnableComHosting>true</EnableComHosting>` inside a `<PropertyGroup></PropertyGroup>` tag.</span></span>
2. <span data-ttu-id="5fd47-131">프로젝트를 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd47-131">Build the project.</span></span>

<span data-ttu-id="5fd47-132">결과 출력에는 `ProjectName.dll`, `ProjectName.deps.json`, `ProjectName.runtimeconfig.json` 및 `ProjectName.comhost.dll` 파일이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="5fd47-132">The resulting output will have a `ProjectName.dll`, `ProjectName.deps.json`, `ProjectName.runtimeconfig.json` and `ProjectName.comhost.dll` file.</span></span>

## <a name="register-the-com-host-for-com"></a><span data-ttu-id="5fd47-133">COM용 COM 호스트 등록</span><span class="sxs-lookup"><span data-stu-id="5fd47-133">Register the COM host for COM</span></span>

<span data-ttu-id="5fd47-134">관리자 권한 명령 프롬프트를 열고 `regsvr32 ProjectName.comhost.dll`을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd47-134">Open an elevated command prompt and run `regsvr32 ProjectName.comhost.dll`.</span></span> <span data-ttu-id="5fd47-135">이렇게 하면 공개된 모든 .NET 개체가 COM에 등록됩니다.</span><span class="sxs-lookup"><span data-stu-id="5fd47-135">That will register all of your exposed .NET objects with COM.</span></span>

## <a name="enabling-regfree-com"></a><span data-ttu-id="5fd47-136">RegFree COM 사용</span><span class="sxs-lookup"><span data-stu-id="5fd47-136">Enabling RegFree COM</span></span>

1. <span data-ttu-id="5fd47-137">`.csproj` 프로젝트 파일을 열고 `<PropertyGroup></PropertyGroup>` 태그 안에 `<EnableRegFreeCom>true</EnableRegFreeCom>`을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd47-137">Open the `.csproj` project file and add `<EnableRegFreeCom>true</EnableRegFreeCom>` inside a `<PropertyGroup></PropertyGroup>` tag.</span></span>
2. <span data-ttu-id="5fd47-138">프로젝트를 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd47-138">Build the project.</span></span>

<span data-ttu-id="5fd47-139">이제 결과 출력에는 `ProjectName.X.manifest` 파일도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="5fd47-139">The resulting output will now also have a `ProjectName.X.manifest` file.</span></span> <span data-ttu-id="5fd47-140">이 파일은 레지스트리 없는 COM과 함께 사용할 병렬 매니페스트입니다.</span><span class="sxs-lookup"><span data-stu-id="5fd47-140">This file is the side-by-side manifest for use with Registry-Free COM.</span></span>

## <a name="sample"></a><span data-ttu-id="5fd47-141">샘플</span><span class="sxs-lookup"><span data-stu-id="5fd47-141">Sample</span></span>

<span data-ttu-id="5fd47-142">GitHub의 dotnet/samples 리포지토리에는 완벽하게 작동하는 [COM 서버 샘플](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo)이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5fd47-142">There is a fully functional [COM server sample](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo) in the dotnet/samples repository on GitHub.</span></span>

## <a name="additional-notes"></a><span data-ttu-id="5fd47-143">추가 참고 사항</span><span class="sxs-lookup"><span data-stu-id="5fd47-143">Additional Notes</span></span>

<span data-ttu-id="5fd47-144">.NET Framework와 달리 .NET Core에서는 .NET Core 어셈블리에서 COM 형식 라이브러리(TLB)를 생성하는 기능을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5fd47-144">Unlike in .NET Framework, there is no support in .NET Core for generating a COM Type Library (TLB) from a .NET Core assembly.</span></span> <span data-ttu-id="5fd47-145">인터페이스의 기본 선언을 위한 IDL 파일 또는 C++ 헤더를 수동으로 작성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5fd47-145">You will either have to manually write an IDL file or a C++ header for the native declarations of your interfaces.</span></span>

<span data-ttu-id="5fd47-146">또한 .NET Framework와 .NET Core를 동일한 프로세스에 로드하는 기능은 지원되지 않으므로, .NET Core COM 서버를 .NET Framework COM 클라이언트 프로세스에 로드하거나 그 반대로 로드할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5fd47-146">Additionally, loading both .NET Framework and .NET Core into the same process is unsupported, and as a result loading a .NET Core COM server into a .NET Framework COM client process or vice versa is not supported.</span></span>