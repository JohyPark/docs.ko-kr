---
title: '방법: 바인딩된 항목 목록을 기반으로 값 산출'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], MultiBinding
- Multibinding [WPF]
ms.assetid: b3d06378-b511-4181-95aa-316d60c9229b
ms.openlocfilehash: da183a34eb85de54b1e3f54f8d14c09e25640165
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459699"
---
# <a name="how-to-produce-a-value-based-on-a-list-of-bound-items"></a>방법: 바인딩된 항목 목록을 기반으로 값 산출
<xref:System.Windows.Data.MultiBinding>를 사용 하 여 바인딩 대상 속성을 소스 속성 목록에 바인딩한 다음 지정 된 입력을 사용 하 여 값을 생성 하는 논리를 적용할 수 있습니다. 이 예제에서는 <xref:System.Windows.Data.MultiBinding>를 사용 하는 방법을 보여 줍니다.  
  
## <a name="example"></a>예제  
 다음 예제에서 `NameListData`은 `firstName`과 `lastName` 두 개의 속성을 포함하는 `PersonName` 개체의 컬렉션을 참조합니다. 다음 예에서는 성을 가진 사람의 성과 이름을 먼저 표시 하는 <xref:System.Windows.Controls.TextBlock>를 생성 합니다.  
  
 [!code-xaml[MultiBinding#Resources1](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources1)]  
[!code-xaml[MultiBinding#Resources2](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources2)]  
[!code-xaml[MultiBinding#MultiBindingTextBox2](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#multibindingtextbox2)]  
[!code-xaml[MultiBinding#Window](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#window)]  
  
 성이 먼저 표시되는 형식이 생성되는 방법을 이해하기 위해 `NameConverter`의 구현을 살펴보겠습니다.  
  
 [!code-csharp[MultiBinding#3](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/NameConverter.cs#3)]
 [!code-vb[MultiBinding#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MultiBinding/VisualBasic/NameConverter.vb#3)]  
  
 `NameConverter`는 <xref:System.Windows.Data.IMultiValueConverter> 인터페이스를 구현합니다. `NameConverter`은 개별 바인딩에서 값을 가져오고 값 개체 배열에 저장합니다. <xref:System.Windows.Data.Binding> 요소가 <xref:System.Windows.Data.MultiBinding> 요소 아래에 표시 되는 순서는 배열에 해당 값이 저장 되는 순서입니다. <xref:System.Windows.Data.MultiBinding.ConverterParameter%2A> 특성의 값은 매개 변수에 대 한 스위치를 수행 하 여 이름의 형식을 지정 하는 방법을 결정 하는 <xref:System.Windows.Data.MultiBinding.Converter%2A> 메서드의 매개 변수 인수에서 참조 됩니다.  
  
## <a name="see-also"></a>참조

- [바인딩된 데이터 변환](how-to-convert-bound-data.md)
- [데이터 바인딩 개요](../../../desktop-wpf/data/data-binding-overview.md)
- [방법 항목](data-binding-how-to-topics.md)
