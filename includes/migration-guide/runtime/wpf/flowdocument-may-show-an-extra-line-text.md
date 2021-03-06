---
ms.openlocfilehash: 0470cefc05fb5da6a6195ee0a96f04feef01fd10
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620432"
---
### <a name="flowdocument-may-show-an-extra-line-of-text"></a>FlowDocument는 텍스트의 추가 줄을 표시할 수 있습니다.

#### <a name="details"></a>설명

일부 경우에는 <xref:System.Windows.Documents.FlowDocument> 요소가 .NET Framework 4.0에서 실행 중에 표시되는 방법과 비교하여 .NET Framework 4.5에서 실행 중에 텍스트의 추가 줄을 표시합니다. 변경 사항으로 인해 텍스트가 제대로 표시되지 않거나 불명확하게 표시되는 경우는 없지만 이전에 <xref:System.Windows.Documents.FlowDocument>의 보기에서 누락되었던 텍스트가 표시될 수 있습니다.

#### <a name="suggestion"></a>제안 해결 방법

일부 경우에는 디스플레이 요소의 PageHeight 속성을 하나씩 줄이면 이전에 표시된 줄 수를 복원할 수 있습니다.

| 이름    | 값       |
|:--------|:------------|
| Scope   |Microsoft Edge|
|버전|4.5|
|형식|런타임

#### <a name="affected-apis"></a>영향을 받는 API

-<xref:System.Windows.Documents.FlowDocument.%23ctor></li><li><xref:System.Windows.Documents.FlowDocument.%23ctor(System.Windows.Documents.Block)></li><li><xref:System.Windows.Controls.FlowDocumentReader.%23ctor></li><li><xref:System.Windows.Controls.FlowDocumentPageViewer.%23ctor></li><li><xref:System.Windows.Controls.Primitives.DocumentPageView.%23ctor></li></ul>|
