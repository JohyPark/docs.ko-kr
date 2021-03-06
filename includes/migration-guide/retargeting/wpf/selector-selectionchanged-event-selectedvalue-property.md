---
ms.openlocfilehash: 0ef39d67cd4335658658f5772b5bce49d827cad0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614935"
---
### <a name="selector-selectionchanged-event-and-selectedvalue-property"></a>선택기 SelectionChanged 이벤트 및 SelectedValue 속성

#### <a name="details"></a>세부 정보

.NET Framework 4.7.1부터 <xref:System.Windows.Controls.Primitives.Selector>는 해당 선택 항목이 변경될 때 <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> 이벤트를 발생시키기 전에 <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> 속성의 값을 항상 업데이트합니다. 이렇게 하면 SelectedValue 속성은 이벤트를 발생시키기 전에 업데이트되는 다른 선택 속성(<xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A> 및 <xref:System.Windows.Controls.Primitives.Selector.SelectedIndex%2A>)과 일치하게 됩니다.<p/>.NET Framework 4.7 및 이전 버전에서 대부분의 경우 이벤트 이전에 SelectedValue에 대한 업데이트가 발생했지만 선택 항목 변경이 <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> 속성 변경으로 인해 발생한 경우 이벤트 이후에 발생했습니다.

#### <a name="suggestion"></a>제안 해결 방법

.NET Framework 4.7.1 이상을 대상으로 하는 앱은 애플리케이션 구성 파일의 `<runtime>` 섹션에 다음을 추가하여 이 변경을 옵트아웃하고 레거시 동작을 사용할 수 있습니다.

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

.NET Framework 4.7 이하를 대상으로 하지만 .NET Framework 4.7.1 이상에서 실행되는 앱은 애플리케이션 .configuration 파일의 `<runtime>` 섹션에 다음 줄을 추가하여 새 동작을 사용할 수 있습니다.

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

| 이름    | 값       |
|:--------|:------------|
| Scope   | 부       |
| 버전 | 4.7.1       |
| 형식    | 대상 변경 |

#### <a name="affected-apis"></a>영향을 받는 API

- <xref:System.Windows.Controls.TabControl.SelectedContent?displayProperty=nameWithType>
- <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged?displayProperty=nameWithType>
