---
title: IDebugObject |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject
helpviewer_keywords:
- IDebugObject interface
ms.assetid: 05cd8bf4-c9ee-4b49-b782-2263c33067d6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 97fd6c328b15c8e41dbbc2b4e45bfc4285b4273f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/29/2019
ms.locfileid: "66319027"
---
# <a name="idebugobject"></a>IDebugObject
> [!IMPORTANT]
> Visual Studio 2015 での式エバリュエーターの実装には、この方法は非推奨とされます。 CLR 式エバリュエーターの実装方法の詳細についてを参照してください[CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)と[マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)します。

 このインターフェイスは、記号と式の値をカプセル化するバインダーを作成するオブジェクトを表します。

## <a name="syntax"></a>構文

```
IDebugObject : IUnknown
```

## <a name="notes-for-implementers"></a>実装についてのメモ
 式エバリュエーターでは、オブジェクトを表すためには、このインターフェイスを実装します。

## <a name="notes-for-callers"></a>呼び出し元のノート
 このインターフェイスは、式エバリュエーターが解析された式で使用するすべてのオブジェクトの基本クラスです。 呼び出しによって返される、[バインド](../../../extensibility/debugger/reference/idebugbinder-bind.md)メソッド。 [QueryInterface](/cpp/atl/queryinterface)はこのインターフェイスより専門的なインターフェイスを取得します。

## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド
 次の表は、メソッドの`IDebugObject`します。

|メソッド|説明|
|------------|-----------------|
|[GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md)|オブジェクトのサイズを取得します。|
|[GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)|連続した一連のバイトとしてオブジェクトの値を取得します。|
|[SetValue](../../../extensibility/debugger/reference/idebugobject-setvalue.md)|連続した一連のバイトから、オブジェクトの値を設定します。|
|[SetReferenceValue](../../../extensibility/debugger/reference/idebugobject-setreferencevalue.md)|このオブジェクトの参照値を設定します。|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugobject-getmemorycontext.md)|オブジェクトの値のアドレスを表すメモリ コンテキストを取得します。|
|[GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md)|デバッグ エンジンのアドレス空間には、管理対象のオブジェクトのコピーを作成します。|
|[IsNullReference](../../../extensibility/debugger/reference/idebugobject-isnullreference.md)|このオブジェクトが null 参照であるかどうかをテストします。|
|[IsEqual](../../../extensibility/debugger/reference/idebugobject-isequal.md)|このオブジェクトを比較します。|
|[IsReadOnly](../../../extensibility/debugger/reference/idebugobject-isreadonly.md)|このオブジェクトは読み取り専用のかどうかを決定します。|
|[IsProxy](../../../extensibility/debugger/reference/idebugobject-isproxy.md)|オブジェクトが透過プロキシであるかどうかを判断します。|

## <a name="remarks"></a>Remarks
 式エバリュエーターでは、基底クラスとしてのこのインターフェイスを使用して、解析ツリー内のオブジェクトを表します。

## <a name="requirements"></a>必要条件
 ヘッダー: ee.h

 名前空間: Microsoft.VisualStudio.Debugger.Interop

 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>関連項目
- [式の評価のインターフェイス](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)
- [Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md)