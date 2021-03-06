---
title: '방법: StackPanel에서 콘텐츠 가로 또는 세로 맞춤'
description: Windows Presentation Foundation StackPanel의 콘텐츠 방향과 자식 콘텐츠의 HorizontalAlignment 및 VerticalAlignment를 조정 하는 방법에 대해 알아봅니다.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- StackPanel control [WPF], content alignment [WPF]
- content alignment [WPF]
- aligning [WPF], content
ms.assetid: c1e8f962-72c8-4e7a-8670-7a2d7e021791
ms.openlocfilehash: d3c7215d8193d1d8a72597c44cf265f5bd400ea1
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167625"
---
# <a name="how-to-horizontally-or-vertically-align-content-in-a-stackpanel"></a>방법: StackPanel에서 콘텐츠 가로 또는 세로 맞춤
이 예제에서는 요소 내에서 콘텐츠의를 조정 하는 방법과 <xref:System.Windows.Controls.StackPanel.Orientation%2A> <xref:System.Windows.Controls.StackPanel> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> 자식 콘텐츠의 및를 조정 하는 방법을 보여 줍니다 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> .  
  
## <a name="example"></a>예제  
 다음 예에서는에서 3 개의 요소를 만듭니다 <xref:System.Windows.Controls.ListBox> [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] . 각은 <xref:System.Windows.Controls.ListBox> <xref:System.Windows.Controls.StackPanel.Orientation%2A> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> 의, 및 속성에 사용할 수 있는 값을 나타냅니다 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> <xref:System.Windows.Controls.StackPanel> . 사용자가 임의의 요소에서 값을 선택 하면 <xref:System.Windows.Controls.ListBox> <xref:System.Windows.Controls.StackPanel> 및 해당 자식 요소의 연결 된 속성이 <xref:System.Windows.Controls.Button> 변경 됩니다.  
  
 [!code-xaml[StackPanelIntroSamp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelIntroSamp/CSharp/Window1.xaml#1)]  
  
 다음 코드를 사용 하는 파일은 선택 변경 내용과 연결 된 이벤트에 대 한 변경 내용을 정의 합니다 <xref:System.Windows.Controls.ListBox> . <xref:System.Windows.Controls.StackPanel>는로 식별 됩니다 <xref:System.Windows.FrameworkElement.Name%2A> `sp1` .  
  
 [!code-csharp[StackPanelIntroSamp#2](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelIntroSamp/CSharp/Window1.xaml.cs#2)]
 [!code-vb[StackPanelIntroSamp#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelIntroSamp/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>참고 항목

- <xref:System.Windows.Controls.StackPanel>
- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>
- <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>
- [Panel 개요](panels-overview.md)
