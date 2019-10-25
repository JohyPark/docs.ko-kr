---
ms.openlocfilehash: e0d0a680915f14c2d33f1864ad5ad05aff3dde5f
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394329"
---
### <a name="http-headernames-constants-changed-to-static-readonly"></a><span data-ttu-id="39e77-101">HTTP: HeaderNames 상수가 정적 readonly로 변경됨</span><span class="sxs-lookup"><span data-stu-id="39e77-101">HTTP: HeaderNames constants changed to static readonly</span></span>

<span data-ttu-id="39e77-102">ASP.NET Core 3.0 Preview 5부터 <xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName>의 필드가 `const`에서 `static readonly`로 변경되었습니다.</span><span class="sxs-lookup"><span data-stu-id="39e77-102">Starting in ASP.NET Core 3.0 Preview 5, the fields in <xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName> changed from `const` to `static readonly`.</span></span>

<span data-ttu-id="39e77-103">자세한 내용은 [aspnet/AspNetCore#9514](https://github.com/aspnet/AspNetCore/issues/9514)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="39e77-103">For discussion, see [aspnet/AspNetCore#9514](https://github.com/aspnet/AspNetCore/issues/9514).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="39e77-104">도입된 버전</span><span class="sxs-lookup"><span data-stu-id="39e77-104">Version introduced</span></span>

<span data-ttu-id="39e77-105">3.0</span><span class="sxs-lookup"><span data-stu-id="39e77-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="39e77-106">이전 동작</span><span class="sxs-lookup"><span data-stu-id="39e77-106">Old behavior</span></span>

<span data-ttu-id="39e77-107">이러한 필드는 `const`가 되는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="39e77-107">These fields used to be `const`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="39e77-108">새 동작</span><span class="sxs-lookup"><span data-stu-id="39e77-108">New behavior</span></span>

<span data-ttu-id="39e77-109">이러한 필드는 이제 `static readonly`입니다.</span><span class="sxs-lookup"><span data-stu-id="39e77-109">These fields are now `static readonly`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="39e77-110">변경 이유</span><span class="sxs-lookup"><span data-stu-id="39e77-110">Reason for change</span></span>

<span data-ttu-id="39e77-111">변경 내용:</span><span class="sxs-lookup"><span data-stu-id="39e77-111">The change:</span></span>

* <span data-ttu-id="39e77-112">값이 어셈블리 경계를 넘어 포함되지 않도록 하여 필요에 따라 값을 수정할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="39e77-112">Prevents the values from being embedded across assembly boundaries, allowing for value corrections as needed.</span></span>
* <span data-ttu-id="39e77-113">참조 같음 검사를 더 빠르게 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39e77-113">Enables faster reference equality checks.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="39e77-114">권장 작업</span><span class="sxs-lookup"><span data-stu-id="39e77-114">Recommended action</span></span>

<span data-ttu-id="39e77-115">3\.0에 대해 다시 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="39e77-115">Recompile against 3.0.</span></span> <span data-ttu-id="39e77-116">다음 방법으로 이러한 필드를 사용하는 소스 코드는 더 이상 이렇게 할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="39e77-116">Source code using these fields in the following ways can no longer do so:</span></span>

* <span data-ttu-id="39e77-117">특성 인수로 사용</span><span class="sxs-lookup"><span data-stu-id="39e77-117">As an attribute argument</span></span>
* <span data-ttu-id="39e77-118">`switch` 문의 `case`로 사용</span><span class="sxs-lookup"><span data-stu-id="39e77-118">As a `case` in a `switch` statement</span></span>
* <span data-ttu-id="39e77-119">다른 `const`를 정의하는 경우</span><span class="sxs-lookup"><span data-stu-id="39e77-119">When defining another `const`</span></span>

<span data-ttu-id="39e77-120">호환성이 손상되는 변경을 해결하려면 자체 정의된 헤더 이름 상수 또는 문자열 리터럴을 사용하도록 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="39e77-120">To work around the breaking change, switch to using self-defined header name constants or string literals.</span></span>

#### <a name="category"></a><span data-ttu-id="39e77-121">범주</span><span class="sxs-lookup"><span data-stu-id="39e77-121">Category</span></span>

<span data-ttu-id="39e77-122">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="39e77-122">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="39e77-123">영향을 받는 API</span><span class="sxs-lookup"><span data-stu-id="39e77-123">Affected APIs</span></span>

<xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.Net.Http.Headers.HeaderNames`

-->