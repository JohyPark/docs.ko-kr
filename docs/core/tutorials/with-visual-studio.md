---
title: Visual Studio를 사용하여 .NET Core 콘솔 애플리케이션 만들기
description: Visual Studio를 사용하여 C# 또는 Visual Basic으로 .NET Core 콘솔 애플리케이션을 만드는 방법을 알아봅니다.
ms.date: 06/08/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: fbe0b3491260e787c08b98b320b19408f2c897eb
ms.sourcegitcommit: 09bad6ec0cbf18be7cd7f62e77286d305a18b607
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87795387"
---
# <a name="tutorial-create-a-net-core-console-application-using-visual-studio"></a>자습서: Visual Studio를 사용하여 .NET Core 콘솔 애플리케이션 만들기

이 자습서에서는 Visual Studio 2019에서 .NET Core 콘솔 애플리케이션을 만들고 실행하는 방법을 보여 줍니다.

## <a name="prerequisites"></a>사전 요구 사항

- **.NET Core 플랫폼 간 개발** 워크로드가 설치된 [Visual Studio 2019 버전 16.6 이상](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019). 이 워크로드를 선택하면 .NET Core 3.1 SDK가 자동으로 설치됩니다.

  자세한 내용은 [Visual Studio로 .NET Core SDK 설치](../install/sdk.md?pivots=os-windows#install-with-visual-studio)를 참조하세요.

## <a name="create-the-app"></a>앱 만들기

"HelloWorld"라는 .NET Core 콘솔 앱 프로젝트를 만듭니다.

1. Visual Studio 2019를 시작합니다.

1. 시작 페이지에서 **새 프로젝트 만들기**를 선택합니다.

   ![Visual Studio 시작 페이지에서 새 프로젝트 만들기 단추 선택](./media/with-visual-studio/start-window.png)

1. **새 프로젝트 만들기** 페이지의 검색 상자에 **console**(또는 **콘솔**)을 입력합니다. 다음으로 언어 목록에서 **C#** 또는 **Visual Basic**을 선택한 다음 플랫폼 목록에서 **모든 플랫폼**을 선택합니다. **콘솔 앱(.NET Core)** 템플릿을 선택하고 **다음**을 선택합니다.

   ![필터가 선택된 새 프로젝트 만들기 창](./media/with-visual-studio/create-new-project.png)

   > [!TIP]
   > .NET Core 템플릿이 표시되지 않으면 필요한 워크로드가 없을 수 있습니다. **원하는 항목을 찾지 못하셨나요?** 메시지에서 **추가 도구 및 기능 설치** 링크를 선택합니다. Visual Studio 설치 관리자가 열립니다. **.NET Core 플랫폼 간 개발** 워크로드가 설치되어 있어야 합니다.

1. **새 프로젝트 구성** 대화 상자에서 **프로젝트 이름** 상자에 **HelloWorld**를 입력합니다. 그런 다음, **만들기**를 선택합니다.

   ![프로젝트 이름, 위치 및 솔루션 이름 필드를 사용하여 새 프로젝트 창을 구성합니다.](./media/with-visual-studio/configure-new-project.png)

템플릿은 간단한 "Hello World" 애플리케이션을 만듭니다. <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> 메서드를 호출하여 "Hello World!"를 콘솔 창에 표시합니다.

템플릿 코드는 <xref:System.String> 배열을 인수로 사용하는 단일 메서드 `Main`으로 `Program` 클래스를 정의합니다.

```csharp
using System;

namespace HelloWorld
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

```vb
Imports System

Module Program
    Sub Main(args As String())
        Console.WriteLine("Hello World!")
    End Sub
End Module
```

`Main`은 애플리케이션 진입점으로, 애플리케이션을 시작할 때 런타임에 의해 자동으로 호출되는 메서드입니다. 애플리케이션이 시작될 때 제공되는 모든 명령줄 인수는 *args* 배열에서 사용할 수 있습니다.

사용하려는 언어가 표시되지 않으면 페이지 맨 위에 있는 언어 선택기를 변경합니다.

## <a name="run-the-app"></a>앱 실행

1. <kbd>Ctrl</kbd>+<kbd>F5</kbd>를 눌러 디버깅 없이 프로그램을 실행합니다.

   콘솔 창이 열리고 "Hello World!"라는 텍스트가 화면에 표시되며 일부 Visual Studio 디버그 정보도 표시됩니다.

   ![“Hello World 계속하려면 아무 키나 누르세요.”를 표시하는 콘솔 창](./media/with-visual-studio/hello-world-console.png)

1. 콘솔 창을 닫으려면 아무 키나 누릅니다.

## <a name="enhance-the-app"></a>앱 향상

사용자에게 이름을 입력하라는 메시지를 표시한 다음 사용자 이름을 날짜 및 시간과 함께 표시하도록 애플리케이션을 개선합니다.

1. *Program.cs* 또는 *Program.vb*에서 다음 코드로 `Console.WriteLine`를 호출하는 줄인 `Main` 메서드의 내용을 바꿉니다.

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="MainMethod":::
   :::code language="vb" source="./snippets/with-visual-studio/vb/Program.vb" id="MainMethod":::

   이 코드는 "What is your name?"을 콘솔 창에 표시하고 사용자가 문자열을 입력한 후 <kbd>Enter</kbd> 키를 누를 때까지 기다립니다. 이 문자열을 `name`이라는 변수에 저장합니다. 또한 현재 현지 시간을 포함하는 <xref:System.DateTime.Now?displayProperty=nameWithType> 속성 값을 검색한 후 `date`라는 변수(Visual Basic에서는 `currentDate`)에 할당합니다. 마지막으로 콘솔 창에 이러한 값을 표시합니다.

   `\n`(Visual Basic에서는 `vbCrLf`)은 줄 바꿈 문자를 나타냅니다.

   문자열 앞의 달러 기호(`$`)를 사용하면 변수 이름과 같은 식을 문자열의 중괄호 안에 넣을 수 있습니다. 식 값은 식 대신 문자열에 삽입됩니다. 이 구문을 [보간된 문자열](../../csharp/language-reference/tokens/interpolated.md)이라고 합니다.

1. <kbd>Ctrl</kbd>+<kbd>F5</kbd>를 눌러 디버깅 없이 프로그램을 실행합니다.

1. 이름을 입력하고 <kbd>Enter</kbd> 키를 눌러 프롬프트에 응답합니다.

   ![수정된 프로그램 출력이 표시된 콘솔 창](./media/with-visual-studio/hello-world-update.png)

1. 콘솔 창을 닫으려면 아무 키나 누릅니다.

## <a name="next-steps"></a>다음 단계

이 자습서에서는 .NET Core 콘솔 애플리케이션을 만들었습니다. 다음 자습서에서는 앱을 디버그합니다.

> [!div class="nextstepaction"]
> [Visual Studio에서 .NET Core 콘솔 애플리케이션 디버그](debugging-with-visual-studio.md)
