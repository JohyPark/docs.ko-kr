---
title: '방법: 사용자의 컴퓨터에 연결된 프린터 선택'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- printing [Windows Forms], choosing printers
- printers [Windows Forms], choosing
ms.assetid: 63c1172b-2931-4ac0-953f-37f629494bbf
ms.openlocfilehash: 2afbccd02ef42a78d5eac1a01841516fca27c92e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182607"
---
# <a name="how-to-choose-the-printers-attached-to-a-users-computer-in-windows-forms"></a>방법: Windows Forms에서 사용자의 컴퓨터에 연결된 프린터 선택
사용자는 기본 프린터 이외의 프린터를 선택하는 경우가 많습니다. <xref:System.Windows.Forms.PrintDialog> 구성 요소를 사용하면 현재 설치된 프린터 중에서 사용자가 원하는 프린터를 선택하도록 할 수 있습니다. <xref:System.Windows.Forms.PrintDialog> 구성 요소를 통해 <xref:System.Windows.Forms.DialogResult> 구성 요소의 <xref:System.Windows.Forms.PrintDialog> 가 캡처되고 프린터 선택에 사용됩니다.  
  
 다음 절차에서는 텍스트 파일이 기본 프린터로 인쇄되도록 선택되었습니다. 그런 다음 <xref:System.Windows.Forms.PrintDialog> 클래스가 인스턴스화됩니다.  
  
### <a name="to-choose-a-printer-and-then-print-a-file"></a>프린터를 선택한 다음 파일을 인쇄하려면  
  
1. 구성 요소를 사용하여 사용할 <xref:System.Windows.Forms.PrintDialog> 프린터를 선택합니다.  
  
     다음 코드 예제에서는 두 이벤트가 처리되고 있습니다. 첫 <xref:System.Windows.Forms.Button> 번째 컨트롤의 <xref:System.Windows.Forms.Control.Click> 이벤트에서 클래스가 <xref:System.Windows.Forms.PrintDialog> 인스턴스화되고 사용자가 선택한 프린터가 <xref:System.Windows.Forms.DialogResult> 속성에 캡처됩니다.  
  
     두 번째 이벤트에서는 <xref:System.Drawing.Printing.PrintDocument.PrintPage> <xref:System.Drawing.Printing.PrintDocument> 구성 요소의 경우 샘플 문서가 지정된 프린터에 인쇄됩니다.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As Object, ByVal e As System.EventArgs) Handles Button1.Click  
       Dim PrintDialog1 As New PrintDialog()  
       PrintDialog1.Document = PrintDocument1  
       Dim result As DialogResult = PrintDialog1.ShowDialog()  
  
       If (result = DialogResult.OK) Then  
         PrintDocument1.Print()  
       End If
  
    End Sub  
  
    Private Sub PrintDocument1_PrintPage(ByVal sender As Object, ByVal e As System.Drawing.Printing.PrintPageEventArgs) Handles PrintDocument1.PrintPage  
       e.Graphics.FillRectangle(Brushes.Red, New Rectangle(500, 500, 500, 500))
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       PrintDialog printDialog1 = new PrintDialog();  
       printDialog1.Document = printDocument1;  
       DialogResult result = printDialog1.ShowDialog();  
       if (result == DialogResult.OK)  
       {  
          printDocument1.Print();  
       }  
    }  
  
    private void printDocument1_PrintPage(object sender,
    System.Drawing.Printing.PrintPageEventArgs e)  
    {  
       e.Graphics.FillRectangle(Brushes.Red,
         new Rectangle(500, 500, 500, 500));  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          PrintDialog ^ printDialog1 = gcnew PrintDialog();  
          printDialog1->Document = printDocument1;  
          System::Windows::Forms::DialogResult result =
             printDialog1->ShowDialog();  
          if (result == DialogResult::OK)  
          {  
             printDocument1->Print();  
          }  
       }  
    private:  
       void printDocument1_PrintPage(System::Object ^ sender,  
          System::Drawing::Printing::PrintPageEventArgs ^ e)  
       {  
          e->Graphics->FillRectangle(Brushes::Red,  
             Rectangle(500, 500, 500, 500));  
       }  
    ```  
  
     (비주얼 C# 및 비주얼 C++) 양식의 생성자에서 다음 코드를 배치하여 이벤트 처리기를 등록합니다.  
  
    ```csharp  
    this.printDocument1.PrintPage += new  
       System.Drawing.Printing.PrintPageEventHandler  
       (this.printDocument1_PrintPage);  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->printDocument1->PrintPage += gcnew  
       System::Drawing::Printing::PrintPageEventHandler  
       (this, &Form1::printDocument1_PrintPage);  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>참고 항목

- [Windows Forms 인쇄 지원](windows-forms-print-support.md)
