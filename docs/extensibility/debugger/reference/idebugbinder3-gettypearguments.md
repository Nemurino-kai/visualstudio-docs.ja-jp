---
title: IDebugBinder3::GetTypeArguments |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetTypeArguments
helpviewer_keywords:
- IDebugBinder3::GetTypeArguments method
ms.assetid: fa0c37a7-327f-463e-9a9d-bb3f534584cb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a9d301dbb99e88ba4552ad59d9116f64dc032371
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/29/2019
ms.locfileid: "66330742"
---
# <a name="idebugbinder3gettypearguments"></a>IDebugBinder3::GetTypeArguments
このメソッドは、このオブジェクトに関連付けられている引数の型の一覧を取得します。

## <a name="syntax"></a>構文

```cpp
HRESULT GetTypeArguments(
   UINT          skip,
   UINT          count,
   IDebugField** ppFields,
   UINT*         pFetched
);
```

```csharp
int GetTypeArguments(
   uint          skip,
   uint          count,
   IDebugField[] ppFields,
   out uint      pFetched
);
```

## <a name="parameters"></a>パラメーター
`skip`\
[in]引数の型を取得する前にスキップするフィールドの数。

`count`\
[in]返される引数のフィールドの数 (ものサイズを指定します、`ppFields`配列)。

`ppFields`\
[入力、出力]このメソッドの戻り値の入力フィールドの配列。

`pFetched`\
[out]\(省略可能)引数の数は、実際に返されるフィールドを入力します。

## <a name="return-value"></a>戻り値
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。

## <a name="remarks"></a>Remarks
 引数の型の数を事前に取得できる[GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)します。

## <a name="see-also"></a>関連項目
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)