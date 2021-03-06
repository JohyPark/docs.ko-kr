---
ms.openlocfilehash: 9dada93c3330331064b7a944d97d61edb4dea299
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620249"
---
### <a name="listsort-algorithm-changed"></a>List.Sort 알고리즘 변경

#### <a name="details"></a>설명

.NET Framework 4.5부터 <xref:System.Collections.Generic.List%601?displayProperty=fullName>의 정렬 알고리즘이 변경되었습니다(빠른 정렬 대신 내면적인 정렬). <xref:System.Collections.Generic.List%601?displayProperty=fullName>의 정렬은 안정적이지 않았지만 이 변경으로 인해 다양한 시나리오가 불안정하게 정렬될 수 있습니다. 즉, API의 후속 호출에서 동일한 항목이 다른 순서로 정렬될 수 있습니다.

#### <a name="suggestion"></a>제안 해결 방법

이전 정렬 알고리즘은 불안정했기 때문에(약간 다른 방식이지만) 항상 특정 순서로 정렬하는 해당 항목에 종속된 코드가 없어야 합니다. 이에 종속된 코드의 인스턴스가 있고 이전 동작에 운이 따른다면 원하는 순서로 항목을 명확하게 정렬하는 비교자를 사용하도록 해당 코드를 업데이트해야 합니다.

| 이름    | 값       |
|:--------|:------------|
| Scope   |투명|
|버전|4.5|
|형식|런타임

#### <a name="affected-apis"></a>영향을 받는 API

-<xref:System.Collections.Generic.List%601.Sort?displayProperty=nameWithType></li><li><xref:System.Collections.Generic.List%601.Sort(System.Collections.Generic.IComparer{%600})?displayProperty=nameWithType></li><li><xref:System.Collections.Generic.List%601.Sort(System.Comparison{%600})?displayProperty=nameWithType></li><li><xref:System.Collections.Generic.List%601.Sort(System.Int32,System.Int32,System.Collections.Generic.IComparer{%600})?displayProperty=nameWithType></li></ul>|
