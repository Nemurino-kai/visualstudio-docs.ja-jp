---
title: XML ドキュメント プロパティと [プロパティ] ウィンドウ
ms.date: 03/05/2019
ms.topic: reference
ms.assetid: 9dbb34d9-02ea-4201-b445-c98a0eb0d6db
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1b21f4435737597136e1ac4a4dd8651decaf4c65
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592426"
---
# <a name="xml-document-properties-properties-window"></a>XML ドキュメントのプロパティ、プロパティウィンドウ

**[プロパティ]** ウィンドウには、XML エディターでアクティブになっているドキュメントに関する基本的な情報が表示されます。 使用可能なプロパティは、現在アクティブになっている XML ドキュメントの種類によって異なります。

> [!NOTE]
> XML ドキュメントのプロパティは、すべてソリューション内に保存されます。 このため、ソリューションを次に開いたときにプロパティの値を再入力する必要はありません。

**エンコード**

ファイルの文字エンコードです。 このプロパティを変更すると、XML 宣言の encoding 属性も変更されます。逆に、encoding 属性を変更すれば、このプロパティも変更されます。 ファイルを保存するときに、ファイルをエンコードするために新しいエンコーディングが使用されます。

**入力**

XSLT スタイル シートに関連付けられた入力ドキュメントです。 **Xslt の開始**コマンドによって使用されます。たとえば、 **XML** > **デバッグなしで xslt を開始**します。 ドキュメントは、参照ボタン ([. **..** ]) を使用して選択できます。

このプロパティは、XSLT ファイルがエディターで開かれている場合にのみ表示されます。

**出力**

XML ドキュメントを変換するときに生成されるファイルです。

ファイルが指定されていない場合、`xsl:output` 要素の `method` 属性に基づいて、既定のファイル名が生成されます。これにより、ファイル拡張子が決まります。 既定のファイルは、現在のユーザーの一時ディレクトリに置かれます。

**スキーマ**

検証に使用するスキーマです。 このボタンをクリックすると、 **[XSD スキーマ]** ダイアログボックスが開き、使用するスキーマを選択できます。

スキーマへのパスを入力することもできます。 複数のスキーマを指定する場合は、スキーマのパスをそれぞれ二重引用符で囲む必要があります。

**スタイル**

**Xslt デバッグの開始**と、デバッグコマンドを使用**せずに xslt を開始**するときに、ドキュメントの変換に使用される xslt ファイルが使用されます。 このフィールドが空白の場合、エディターはドキュメントの `xml-stylesheet` 処理命令で指定された値を使用するか、ファイル名の入力を求めます。

XSLT ファイルを編集するときに、このプロパティを使用して、 **[Xslt デバッグの開始]** または **[デバッグなしで xslt を開始]** コマンドを選択したときに別のスタイルシートを使用するように指定できます。 たとえば、親スタイルシートに含まれているスタイルシートを編集しているときに、この操作を行うことができます。

## <a name="see-also"></a>関連項目

- [XML エディター](../xml-tools/xml-editor.md)
