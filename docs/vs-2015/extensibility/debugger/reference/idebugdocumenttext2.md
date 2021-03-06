---
title: IDebugDocumentText2 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDocumentText2
helpviewer_keywords:
- IDebugDocumentText2 interface
ms.assetid: e85f50a3-211c-4220-a9f4-789950ba2782
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2e81aaccd3af692f4a7e0f708685dbea4a44d5c6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200168"
---
# <a name="idebugdocumenttext2"></a>IDebugDocumentText2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このインターフェイスは、テキスト ドキュメントを表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugDocumentText2 : IDebugDocument2  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デバッグ エンジン (DE) は、指定する必要があるソース コードがテキスト形式の場合、このインターフェイスを実装します。 以降、DE が実装されている場合は、最も一般的なケースで、これは、 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)インターフェイスが実装する必要も、`IDebugDocumentText2`インターフェイス。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 使用して、`QueryInterface`からこのインターフェイスを取得するメソッド、`IDebugDocument2`インターフェイス。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 メソッドだけでなく、`IDebugDocument2`インターフェイスでは、このインターフェイスは、次のメソッドを実装します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetSize](../../../extensibility/debugger/reference/idebugdocumenttext2-getsize.md)|ドキュメントのこの位置でテキストのサイズを取得します。|  
|[GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)|ドキュメント内の指定した位置からテキストを取得します。|  
  
## <a name="remarks"></a>Remarks  
 このインターフェイスを実装するオブジェクトを実装する必要がありますも、<xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer>インターフェイスを提供する、<xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint>のためのインターフェイス、 [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)オブジェクト。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 名前空間: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)   
 [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)
