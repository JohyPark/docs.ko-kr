---
title: <type1>'<typename>'은 '<interfacename>' 인터페이스에 대한 '<membername>'을 구현해야 합니다.
ms.date: 07/20/2015
f1_keywords:
- vbc30154
- bc30154
helpviewer_keywords:
- BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
ms.openlocfilehash: 4ffe18e11c388a8c69ef0592bde1b78f5b219680
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84386856"
---
# <a name="type1typename-must-implement-membername-for-interface-interfacename"></a>\<type1>'\<typename>'은 '\<interfacename>' 인터페이스에 대한 '\<membername>'을 구현해야 합니다.
' ' \<typename> 은 ' ' \<membername> 인터페이스에 대해 ' '을 (를) 구현 해야 합니다 \<interfacename> . 구현 속성에 일치 하는 ' ReadOnly '/' WriteOnly ' 지정 자가 있어야 합니다.  
  
 클래스 또는 구조체는 인터페이스를 구현 하지만 인터페이스에 의해 정의 된 프로시저, 속성 또는 이벤트를 구현 하지는 않습니다. 인터페이스의 모든 멤버를 구현 해야 합니다.  
  
 **오류 ID:** BC30154  
  
## <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
1. 인터페이스에 정의 된 것과 동일한 이름 및 서명을 사용 하 여 멤버를 선언 합니다. 적어도, `End Function` `End Sub` 또는 문을 포함 해야 `End Property` 합니다.  
  
2. ,, `Implements` 또는 문의 끝에 절을 `Function` 추가 `Sub` `Property` `Event` 합니다. 예를 들면 다음과 같습니다.  
  
    ```vb  
    Public Event ItHappened() Implements IBaseInterface.ItHappened  
    ```  
  
3. 속성을 구현할 때 `ReadOnly` 또는 `WriteOnly` 가 인터페이스 정의에서와 동일한 방식으로 사용 되는지 확인 합니다.  
  
4. 속성을 구현 하는 경우 `Get` 및 `Set` 프로시저를 적절 하 게 선언 합니다.  
  
## <a name="see-also"></a>참고 항목

- [Implements 문](../statements/implements-statement.md)
- [인터페이스](../../programming-guide/language-features/interfaces/index.md)
