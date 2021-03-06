---
ms.openlocfilehash: e4d9efe7d2a06a1e501b070c23184dcd913dba71
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621285"
---
### <a name="persian-calendar-now-uses-the-hijri-solar-algorithm"></a>이제 페르시아력이 회교식 양력 알고리즘을 사용합니다.

#### <a name="details"></a>세부 정보

.NET Framework 4.6부터는 <xref:System.Globalization.PersianCalendar?displayProperty=fullName> 클래스에서 회교식 양력 알고리즘을 사용합니다. .NET Framework 4.6부터 <xref:System.Globalization.PersianCalendar?displayProperty=fullName>와 다른 달력 간의 날짜 변환은 1800년 전 또는 2023년 후에 대한 날짜에 대해(그레고리오력) 약간 다른 결과를 생성할 수 있습니다. 또한 <xref:System.Globalization.PersianCalendar.MinSupportedDateTime?displayProperty=nameWithType>은 이제 <code>March 21, 0622</code> 대신 <code>March 22, 0622</code>입니다.

#### <a name="suggestion"></a>제안 해결 방법

.NET Framework 4.6에서 PersianCalendar를 사용할 때 일부 이전 또는 늦은 날짜는 약간 다를 수 있습니다. 또한 다른 .NET Framework 버전에서 실행될 수 있는 프로세스 사이의 날짜를 직렬화할 때 PersianCalendar 날짜 문자열로 저장하지 마십시오(해당 값이 다를 수 있음).

| 이름    | 값       |
|:--------|:------------|
| Scope   |부|
|버전|4.6|
|형식|런타임

#### <a name="affected-apis"></a>영향을 받는 API

-<xref:System.Globalization.PersianCalendar?displayProperty=nameWithType></li></ul>|
