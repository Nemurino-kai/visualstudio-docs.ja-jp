---
title: '方法: Office ドキュメントに Windows フォームコントロールを追加する'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], adding
- controls [Office development in Visual Studio], Windows Forms controls
- documents [Office development in Visual Studio], Windows Forms controls
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c4484d07c5cfb77a5fa17460859972bc58b219fc
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/28/2019
ms.locfileid: "72986006"
---
# <a name="how-to-add-windows-forms-controls-to-office-documents"></a>方法: Office ドキュメントに Windows フォームコントロールを追加する
  Windows フォーム コントロールは、デザイン時にドキュメント レベルのプロジェクトの Microsoft Office Excel および Microsoft Office Word のドキュメントに追加できます。 実行時には、ドキュメントレベルのカスタマイズと VSTO アドインにコントロールを追加できます。たとえば、<xref:Microsoft.Office.Tools.Excel.Controls.ComboBox> コントロールをワークシートに追加して、ユーザーがオプションの一覧から選択できるようにすることができます。

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

 このトピックでは、次のタスクについて説明します。

- [デザイン時にコントロールを追加する](#designtime)

- [実行時にドキュメントレベルのプロジェクトにコントロールを追加する](#runtimedoclevel)

- [実行時の VSTO アドインでのコントロールの追加](#runtimeaddin)

## <a name="designtime"></a>デザイン時にコントロールを追加する
 デザイン時にドキュメント レベルのプロジェクトの文書に Windows フォーム コントロールを追加する方法はいくつかあります。

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-drag-a-windows-forms-control-to-the-document"></a>Windows フォーム コントロールをドキュメントにドラッグするには

1. Visual Studio で Excel ブック プロジェクトまたは Word 文書プロジェクトを作成するかまたは開き、ドキュメントがデザイナーに表示されるようにします。 プロジェクトの作成の詳細については、「[方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)」を参照してください。

2. **ツールボックス**の **[コモンコントロール]** タブで、追加するコントロールをクリックし、ドキュメントにドラッグします。

    > [!NOTE]
    > Excel 内でコントロールを選択すると、 **数式バー** に  " **=EMBED("WinForms.Control.Host","")** " と表示されます。 このテキストは必要なので、削除しないでください。

### <a name="to-draw-a-windows-forms-control-on-the-document"></a>Windows フォーム コントロールをドキュメントに描画するには

1. Visual Studio で Excel ブック プロジェクトまたは Word 文書プロジェクトを作成するかまたは開き、ドキュメントがデザイナーに表示されるようにします。 プロジェクトの作成の詳細については、「[方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)」を参照してください。

2. **ツールボックス**の **[コモンコントロール]** タブで、追加するコントロールをクリックします。

3. ドキュメント上で、コントロールの左上隅となる位置をクリックし、コントロールの右下隅となる位置までドラッグします。

     指定したドキュメントの位置に、指定したサイズのコントロールが追加されます。

    > [!NOTE]
    > Excel でコントロールを選択すると、**数式バー**に " **= EMBED (" WinForms "," ")** " と表示されます。 このテキストは必要なので、削除しないでください。

### <a name="to-add-a-windows-forms-control-to-the-document-by-single-clicking-the-control"></a>シングルクリックで Windows フォーム コントロールをドキュメントに追加するには

1. Visual Studio で Excel ブック プロジェクトまたは Word 文書プロジェクトを作成するかまたは開き、ドキュメントがデザイナーに表示されるようにします。 プロジェクトの作成の詳細については、「[方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)」を参照してください。

2. **ツールボックス**の **[コモンコントロール]** タブで、追加するコントロールをクリックします。

3. ドキュメント上で、コントロールを追加する位置をクリックします。

     コントロールが既定のサイズでドキュメントに追加されます。

    > [!NOTE]
    > Excel 内でコントロールを選択すると、 **数式バー** に  " **=EMBED("WinForms.Control.Host","")** " と表示されます。 このテキストは必要なので、削除しないでください。

### <a name="to-add-a-windows-forms-control-to-the-document-by-double-clicking-the-control"></a>ダブルクリックで Windows フォーム コントロールをドキュメントに追加するには

1. Visual Studio で Excel ブック プロジェクトまたは Word 文書プロジェクトを作成するかまたは開き、ドキュメントがデザイナーに表示されるようにします。 プロジェクトの作成の詳細については、「[方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)」を参照してください。

2. **ツールボックス**の **[コモンコントロール]** タブで、追加するコントロールをダブルクリックします。

     コントロールは、ドキュメントまたはアクティブなペインの中央に追加されます。

    > [!NOTE]
    > Excel 内でコントロールを選択すると、 **数式バー** に  " **=EMBED("WinForms.Control.Host","")** " と表示されます。 このテキストは必要なので、削除しないでください。

### <a name="to-add-a-windows-forms-control-to-the-document-by-pressing-the-enter-key"></a>Enter キーを押して Windows フォームコントロールを文書に追加するには

1. Visual Studio で Excel ブック プロジェクトまたは Word 文書プロジェクトを作成するかまたは開き、ドキュメントがデザイナーに表示されるようにします。 プロジェクトの作成の詳細については、「[方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)」を参照してください。

2. **ツールボックス**の **[コモンコントロール]** タブで、追加するコントロールをクリック**し、enter キーを**押します。

     コントロールは、ドキュメントまたはアクティブなペインの中央に追加されます。

    > [!NOTE]
    > Excel 内でコントロールを選択すると、 **数式バー** に  " **=EMBED("WinForms.Control.Host","")** " と表示されます。 このテキストは必要なので、削除しないでください。

## <a name="runtimedoclevel"></a>実行時にドキュメントレベルのプロジェクトにコントロールを追加する
 Windows フォーム コントロールは、実行時にプログラムを使用してドキュメントに追加できます。 Word では、`ThisDocument` クラスの <xref:Microsoft.Office.Tools.Word.DocumentBase.Controls%2A> プロパティのメソッドを使用します。 Excel では、`Sheet`*n*クラスの <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Controls%2A> プロパティのメソッドを使用します。 各メソッドにはいくつかのオーバーロードがあり、それらを使用してさまざまな方法でコントロールの場所を指定できます。

 実行時にドキュメントに Windows フォーム コントロールを追加した場合、ドキュメントが閉じられると、コントロールはドキュメント内に保持されません。 次にドキュメントを開くときに、コントロールを再作成できます。 詳細については、「[実行時に Office ドキュメントにコントロールを追加する](../vsto/adding-controls-to-office-documents-at-run-time.md)」を参照してください。

### <a name="to-add-a-windows-forms-control-at-run-time"></a>実行時に Windows フォーム コントロールを追加するには

1. \<*コントロールクラス*> を追加するメソッドを使用します (ここで、 *control class*は、追加する Windows フォームコントロールのクラス名です (<xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A>など)。

     次のコード例は、Excel のドキュメントレベルのプロジェクトで `Sheet1` のセル**C5**に <xref:Microsoft.Office.Tools.Excel.Controls.Button> を追加する方法を示しています。

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#4](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#4)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#4)]

## <a name="runtimeaddin"></a>実行時の VSTO アドインでのコントロールの追加
 Windows フォーム コントロールは、実行時にプログラムを使用して任意の開いているドキュメントに追加できます。 まず、開いているドキュメントかワークシートに基づいたホスト項目を生成します。 次に、Word では、新しいホスト項目の <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> プロパティのメソッドを使用します。 Excel では、新しいホスト項目の <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> プロパティのメソッドを使用します。 各メソッドにはいくつかのオーバーロードがあり、それらを使用してさまざまな方法でコントロールの場所を指定できます。

 実行時にドキュメントに Windows フォーム コントロールを追加した場合、ドキュメントが閉じられると、コントロールはドキュメント内に保持されません。 次にドキュメントを開くときに、コントロールを再作成できます。 詳細については、「[実行時に Office ドキュメントにコントロールを追加する](../vsto/adding-controls-to-office-documents-at-run-time.md)」を参照してください。

 VSTO アドインプロジェクトでのホスト項目の生成の詳細については、「[実行時の Vsto アドインでの Word 文書と Excel ブックの拡張](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)」を参照してください。

### <a name="to-add-a-windows-forms-control-at-run-time"></a>実行時に Windows フォーム コントロールを追加するには

1. \<*コントロールクラス*> を追加するメソッドを使用します (ここで、 *control class*は、追加する Windows フォームコントロールのクラス名です (<xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A>など)。

    > [!NOTE]
    > [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降を対象とする VSTO アドインプロジェクトでは、Add @no__ にアクセスする前に、そのアセンブリへの参照を追加する必要があります。そのためには、「」と*いう*形式の *.dll または*「」を参照してください。t_3_ *control クラス*> メソッド。

     次のコード例で、Word VSTO アドインを使用して作業中のドキュメントの最初の段落に <xref:Microsoft.Office.Tools.Word.Controls.Button> を追加する方法を示します。

     [!code-vb[Trin_WordAddInDynamicControls#7](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#7)]
     [!code-csharp[Trin_WordAddInDynamicControls#7](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#7)]

## <a name="see-also"></a>関連項目
- [Office ドキュメントのコントロールの Windows フォームの概要](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [実行時に Office ドキュメントにコントロールを追加する](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [方法: ワークシートのセル内のコントロールのサイズを変更する](../vsto/how-to-resize-controls-within-worksheet-cells.md)
- [ホスト項目とホストコントロールの概要](../vsto/host-items-and-host-controls-overview.md)
- [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)
