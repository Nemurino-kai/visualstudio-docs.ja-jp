---
title: '方法: プログラムによってブックを閉じる'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, closing
- Excel [Office development in Visual Studio], closing workbooks
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ea2ec3162ae7ffdee20f65452f67b0ddf4cc2dd1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62575404"
---
# <a name="how-to-programmatically-close-workbooks"></a>方法: プログラムによってブックを閉じる
  作業中のブックを閉じたり、ブックを指定して閉じたりすることができます。

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="close-the-active-workbook"></a>アクティブなブックを閉じる
 作業中のブックを閉じる手順には、ドキュメント レベルのカスタマイズでの手順と VSTO アドインでの手順の 2 つがあります。

### <a name="to-close-the-active-workbook-in-a-document-level-customization"></a>ドキュメント レベルのカスタマイズで作業中のブックを閉じるには

1. <xref:Microsoft.Office.Tools.Excel.Workbook.Close%2A> メソッドを呼び出して、カスタマイズに関連付けられているブックを閉じます。 次のコード例を使用するには、Excel のドキュメント レベルのプロジェクトの `Sheet1` クラスから実行します。

     [!code-csharp[Trin_VstcoreExcelAutomation#3](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#3)]
     [!code-vb[Trin_VstcoreExcelAutomation#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#3)]

### <a name="to-close-the-active-workbook-in-a-vsto-add-in"></a>VSTO アドインで作業中のブックを閉じるには

1. <xref:Microsoft.Office.Interop.Excel._Workbook.Close%2A> メソッドを呼び出して、作業中のブックを閉じます。 次のコード例を使用するには、Excel 用 VSTO アドイン プロジェクトの `ThisAddIn` クラスから実行します。

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#1](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#1)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#1](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#1)]

## <a name="close-a-workbook-that-you-specify-by-name"></a>名前を指定してブックを閉じる
 名前を指定してブックを閉じる方法は、VSTO アドインとドキュメント レベルのカスタマイズで同じです。

### <a name="to-close-a-workbook-that-you-specify-by-name"></a>名前を指定してブックを閉じるには

1. <xref:Microsoft.Office.Interop.Excel.Workbooks> コレクションの引数にブック名を指定します。 次のコード例では、Excel で **NewWorkbook** というブックが開いていることを前提としています。

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#2](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#2)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#2](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#2)]

## <a name="see-also"></a>関連項目
- [ブックを操作します。](../vsto/working-with-workbooks.md)
- [方法: プログラムによってブックを保存します。](../vsto/how-to-programmatically-save-workbooks.md)
- [方法: プログラムによってブックを開く](../vsto/how-to-programmatically-open-workbooks.md)
- [ホスト項目とホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)
- [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)
