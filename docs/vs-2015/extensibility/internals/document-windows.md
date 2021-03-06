---
title: Windows のドキュメント |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, document windows
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5e62be456422b7ee5e9f2828a44a6be05e1211d9
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436347"
---
# <a name="document-windows"></a>ドキュメント ウィンドウ
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio で、*ドキュメント ウィンドウ*はマルチ ドキュメント インターフェイス (MDI) ウィンドウに関連付けられている子フレーム ウィンドウです。 ドキュメント ウィンドウは、通常、表示やソース コードまたはテキストの変更を使用しますが、その他の機能の種類をホストすることもできます。 ドキュメント ウィンドウ:  
  
- 同時に複数のファイルを表示できるように、MDI 親内の別の水平または垂直タブ グループに整理できます。  
  
- 任意の順序で MDI 親にドッキングできます。  
  
- 自由にフロートすることができます。  
  
- その他の MDI ウィンドウのタブ オーダー内でリンクされています。  
  
  グループ化のためのコマンドをドッキングとフローティング見つかりますドキュメント ウィンドウ タブのショートカット メニュー上。  
  
  Visual Studio でウィンドウの動作の詳細については、次を参照してください。[ウィンドウ レイアウトをカスタマイズ](../../ide/customizing-window-layouts-in-visual-studio.md)します。  
  
## <a name="document-window-implementation"></a>ドキュメント ウィンドウの実装  
 ドキュメント ウィンドウは、エディターの実装によって作成されます。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>インターフェイス エディターをインスタンス化の一部としてドキュメント ウィンドウを作成します。 詳細については、次を参照してください。[エディターでのレガシー インターフェイス](../../extensibility/legacy-interfaces-in-the-editor.md)します。  
  
> [!NOTE]
> 後方の提供をウィンドウ内のナビゲーションのポイントに転送は、実装、<xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation>インターフェイス。 テキスト エディターでは、ドキュメント内のナビゲーションのポイントを識別するためにテキスト マーカーが使用されます。  
  
## <a name="the-running-document-table"></a>実行中の Document テーブル  
 IDE では、すべてのドキュメント ウィンドウの状態を追跡するために実行中のドキュメント テーブル (RDT) を使用します。 RDT は、どのドキュメントを windows にソリューションを閉じたときなど、または、ファイルが編集されているときに、イベントの通知メカニズムです。 詳細については、次を参照してください。[を実行しているドキュメント テーブル](../../extensibility/internals/running-document-table.md)します。  
  
## <a name="see-also"></a>関連項目  
 [ドキュメントの読み込みの遅延](../../extensibility/internals/delayed-document-loading.md)
