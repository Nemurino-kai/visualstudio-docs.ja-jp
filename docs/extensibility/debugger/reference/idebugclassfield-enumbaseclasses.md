---
title: IDebugClassField::EnumBaseClasses |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumBaseClasses
helpviewer_keywords:
- IDebugClassField::EnumBaseClasses method
ms.assetid: 78749674-ef75-46d3-a1f4-ff33afd90e32
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f5735ac6f0ecdf9d3f2a0e3bb868be092b8fdb7e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/29/2019
ms.locfileid: "66349650"
---
# <a name="idebugclassfieldenumbaseclasses"></a>IDebugClassField::EnumBaseClasses
このクラスの基底クラスの列挙子を作成します。

## <a name="syntax"></a>構文

```cpp
HRESULT EnumBaseClasses( 
   IEnumDebugFields** ppEnum
);
```

```csharp
int EnumBaseClasses(
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>パラメーター
`ppEnum`\

[out]返します、 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)基底クラスの一覧を表すオブジェクト。 基底クラスがない場合は、null 値を返します。

## <a name="return-value"></a>戻り値
 成功した場合は S_OK を返します、基底クラスがない場合に、S_SH_NO_BASE_CLASSES を返します (および`ppEnum`パラメーターが null 値に設定されている)、それ以外のエラー コードを返します。

## <a name="remarks"></a>Remarks
 列挙子オブジェクトの基底クラスは、ほとんどのリモートの基本クラスに最も直接的な (または最も派生) の基本クラスの順序で指定されます。 たとえば、C++ クラスを考えてみます。

```
class Root { }
class Level1 : Root { }
class Level2 : Level1 { }
class MyClass : Level2 { }
```

 列挙は順で基底クラスを返す`Level2`、 `Level1`、`Root`します。

## <a name="see-also"></a>関連項目
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)