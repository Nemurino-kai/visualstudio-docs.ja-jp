---
title: IDebugProcessEx2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2
helpviewer_keywords:
- IDebugProcessEx2 interface
ms.assetid: 44e309ba-1d6f-499b-aa7e-9b34858a6d57
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5c27a03a09a6073ebab8d7a2dd5f60218066d474
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/29/2019
ms.locfileid: "66311600"
---
# <a name="idebugprocessex2"></a>IDebugProcessEx2
このインターフェイスには、セッション デバッグ マネージャー (SDM) へのアタッチまたはプロセスからデタッチしていますが、プロセスを通知することができます。

## <a name="syntax"></a>構文

```
IDebugProcessEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>実装についてのメモ
 カスタム ポート サプライヤーと同じオブジェクトでこのインターフェイスを実装する、 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)インターフェイスには。

- プロセスに接続されているセッションの追跡をサポート

- サポートのオート アタッチに複数のデバッグ エンジン

  カスタム ポート サプライヤーは、選択した場合、このインターフェイスを実装できます。

## <a name="notes-for-callers"></a>呼び出し元のノート

- SDM コール[QueryInterface](/cpp/atl/queryinterface)上、`IDebugProcess2`をこのインターフェイスを取得するインターフェイス。

## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド
 次の表は、メソッドの`IDebugProcessEx2`します。

|メソッド|説明|
|------------|-----------------|
|[Attach](../../../extensibility/debugger/reference/idebugprocessex2-attach.md)|セッションがプロセスをデバッグして今すぐ、プロセスに通知します。|
|[Detach](../../../extensibility/debugger/reference/idebugprocessex2-detach.md)|プロセスにセッションがプロセスのデバッグで不要になったことを通知します。|
|[AddImplicitProgramNodes](../../../extensibility/debugger/reference/idebugprocessex2-addimplicitprogramnodes.md)|デバッグ エンジンの一覧については、プログラムのノードを追加します。|

## <a name="remarks"></a>Remarks
 このインターフェイスは、SDM とプロセスの間にプライベートです。

## <a name="requirements"></a>必要条件
 ヘッダー:Portpriv.h

 名前空間: Microsoft.VisualStudio.Debugger.Interop

 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>関連項目
- [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)