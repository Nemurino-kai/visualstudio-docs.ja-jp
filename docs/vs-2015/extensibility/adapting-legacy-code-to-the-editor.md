---
title: エディターにレガシ コードを適合させる |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - adapters
ms.assetid: a208d38e-9bea-41c9-9fe2-38bd86a359cb
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0bb90723a72c10dbf6cfda5edd4aa68f71f1c6b9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "68184915"
---
# <a name="adapting-legacy-code-to-the-editor"></a>レガシ コードをエディターに適合させる
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio エディターには、既存のコード コンポーネントからアクセスできる多くの機能があります。 次の手順では、非 MEF コンポーネント、エディターの機能を使用する、VSPackage などを調整する方法を示します。 アダプターを使用して、マネージ コードとアンマネージの両方のコードで、エディターのサービスを取得する方法についても説明します。  
  
## <a name="editor-adapters"></a>エディターのアダプター  
 エディターのアダプター、または、shim もクラスとインターフェイスを公開するエディター オブジェクトのラッパーを<xref:Microsoft.VisualStudio.TextManager.Interop>API。 たとえばエディター以外のサービス間で移動するためにアダプタ、Visual Studio シェル コマンド、およびエディター サービスを使用することができます。 (これは Visual Studio で、エディターをホストする現在します。)また、アダプターには、Visual Studio で正しく動作するレガシ エディターと言語サービス拡張が有効にします。  
  
## <a name="using-editor-adapters"></a>アダプターのエディターを使用します。  
 <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>新しいエディター インターフェイスと従来のインターフェイスを切り替える方法ともアダプターを作成するメソッドを提供します。  
  
 MEF コンポーネント パーツをこのサービスを使用している場合は、次のようにサービスをインポートできます。  
  
```  
[Import(typeof(IVsEditorAdaptersFactoryService))]  
internal IVsEditorAdaptersFactoryService editorFactory;  
```  
  
 非 MEF コンポーネントでこのサービスを使用する場合はこのトピックの「「を使用して Visual Studio エディター サービスで、非 MEF コンポーネント」セクションの手順に従います。  
  
## <a name="switching-between-the-new-editor-api-and-the-legacy-api"></a>エディターの新しい API と、レガシ API 間の切り替え  
 エディター オブジェクトと従来のインターフェイス間を切り替えるには、次のメソッドを使用します。  
  
|メソッド|変換|  
|------------|----------------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetBufferAdapter%2A>|変換、<xref:Microsoft.VisualStudio.Text.ITextBuffer>を<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>します。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDataBuffer%2A>|変換、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>を<xref:Microsoft.VisualStudio.Text.ITextBuffer>します。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDocumentBuffer%2A>|変換、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>を<xref:Microsoft.VisualStudio.Text.ITextBuffer>します。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetViewAdapter%2A>|変換、<xref:Microsoft.VisualStudio.Text.Editor.ITextView>を<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>します。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetWpfTextView%2A>|変換、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>を<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>します。|  
  
## <a name="creating-adapters"></a>アダプターを作成します。  
 レガシー インターフェイスのアダプターを作成するのにには、次のメソッドを使用します。  
  
|メソッド|変換|  
|------------|----------------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsCodeWindowAdapter%2A>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> を作成します。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|作成、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>指定した<xref:Microsoft.VisualStudio.Utilities.IContentType>します。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> を作成します。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferCoordinatorAdapter%2A>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> を作成します。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|作成、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>の<xref:Microsoft.VisualStudio.Text.Editor.ITextViewRoleSet>します。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> を作成します。|  
  
## <a name="creating-adapters-in-unmanaged-code"></a>アンマネージ コードでアダプターを作成します。  
 ローカルですべてのアダプター クラスが登録されている、共同作成可能なを使用してインスタンス化することができます、`VsLocalCreateInstance()`関数。  
  
 すべてのアダプターで vsshlids.h ファイルで定義されている Guid を使用して作成します.Visual Studio SDK のインストールの \VisualStudioIntegration\Common\Inc\ フォルダーです。 VsTextBufferAdapter のインスタンスを作成するには、次のコードを使用します。  
  
```  
IVsTextBuffer *pBuf = NULL;  
VsLocalCreateInstance(CLSID_VsTextBuffer, NULL, CLSCTX_INPROC_SERVER, IID_IVsTextBuffer, (void**)&pBuf);  
```  
  
## <a name="creating-adapters-in-managed-code"></a>マネージ コードでアダプターを作成します。  
 マネージ コードでは、アンマネージ コードの記述されるのと同じ方法で併置アダプターを作成できます。 作成し、アダプターと対話できる MEF サービスを使用することもできます。 アダプターを取得するには、この方法は、共同作成するときよりも細かい制御を使用できます。  
  
#### <a name="to-create-an-adapter-for-ivstextview"></a>IVsTextView のアダプターを作成するには  
  
1. Microsoft.VisualStudio.Editor.dll への参照を追加します。 必ず`CopyLocal`に設定されている`false`します。  
  
2. インスタンスを作成、 <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>、次のようにします。  
  
    ```  
    using Microsoft.VisualStudio.Editor;  
    ...  
    IVsEditorAdaptersFactoryService adapterFactoryService = ComponentModel.GetService<IVsEditorAdaptersFactoryService>();  
    ```  
  
3. `CreateX()` メソッドを呼び出します。  
  
    ```  
    adapterFactoryService.CreateTextViewAdapter(textView);  
    ```  
  
## <a name="using-the-visual-studio-editor-directly-from-unmanaged-code"></a>アンマネージ コードから直接 Visual Studio エディターを使用してください。  
 Microsoft.VisualStudio.Platform.VSEditor 名前空間と Microsoft.VisualStudio.Platform.VSEditor.Interop 名前空間は、IVx * インターフェイスとして COM 呼び出し可能なインターフェイスを公開します。 たとえば、Microsoft.VisualStudio.Platform.VSEditor.Interop.IVxTextBuffer インターフェイスには、COM バージョンの<xref:Microsoft.VisualStudio.Text.ITextBuffer>インターフェイス。 `IVxTextBuffer`バッファーのスナップショットへのアクセスを取得、バッファーの変更、バッファーでテキスト変更イベントをリッスンおよび追跡ポイントとスパンを作成します。 次の手順にアクセスする方法を示して、`IVxTextBuffer`から、`IVsTextBuffer`します。  
  
#### <a name="to-get-an-ivxtextbuffer"></a>IVxTextBuffer を取得するには  
  
1. IVx* のインターフェイスの定義が VSEditor.h ファイルには.Visual Studio SDK のインストールの \VisualStudioIntegration\Common\Inc\ フォルダーです。  
  
2. 次のコードを使用してテキスト バッファーをインスタンス化、`IVsUserData->GetData()`メソッド。 次のコードで`pData`へのポインター、`IVsUserData`オブジェクト。  
  
    ```  
    #include <textmgr.h>  
    #include <VSEditor.h>  
    #include <vsshlids.h>  
  
    CComPtr<IVsTextBuffer> pVsTextBuffer;  
    CComPtr<IVsUserData> pData;  
    CComPtr<IVxTextBuffer> pVxBuffer;  
    ...  
    if (SUCCEEDED(pVsTextBuffer->QueryInterface(IID_IVsUserData, &pData))  
    {  
        CComVariant vt;  
        if (SUCCEEDED(pData->GetData(GUID_VxTextBuffer, &vt)) &&  
        (vt.Type == VT_UNKNOWN) && (vt.punkVal != NULL))  
        {  
            vt.punkVal->QueryInterface(IID_IVxTextBuffer, (void**)&pVxBuffer);  
        }  
    }  
    ```  
  
## <a name="using-visual-studio-editor-services-in-a-non-mef-component"></a>非 MEF コンポーネントで Visual Studio エディター サービスの使用  
 MEF を使用しない既存のマネージ コード コンポーネントがあり、Visual Studio エディターのサービスを使用する場合は、ComponentModelHost VSPackage を含むアセンブリへの参照を追加し、その SComponentModel サービスを取得する必要があります。  
  
#### <a name="to-consume-visual-studio-editor-components-from-a-non-mef-component"></a>非 MEF コンポーネントから Visual Studio エディターのコンポーネントを使用するには  
  
1. Microsoft.VisualStudio.ComponentModelHost.dll アセンブリへの参照を追加します.Visual Studio のインストールの \Common7\IDE\ フォルダーにあります。 必ず`CopyLocal`に設定されている`false`します。  
  
2. 追加のプライベート`IComponentModel`を次のように、Visual Studio エディター サービスを使用するクラスのメンバー。  
  
    ```  
    using Microsoft.VisualStudio.ComponentModelHost;  
    ....  
    private IComponentModel componentModel;  
    ```  
  
3. コンポーネントの初期化メソッドでコンポーネント モデルのインスタンスを作成します。  
  
    ```  
    componentModel =  
     (IComponentModel)Package.GetGlobalService(typeof(SComponentModel));  
    ```  
  
4. その後、呼び出すことによって、Visual Studio エディターのサービスのいずれかを取得できます、`IComponentModel.GetService<T>()`サービスのメソッド。  
  
    ```  
    textBufferFactoryService =  
         componentModel.GetService<ITextBufferFactoryService>();     
    ```
