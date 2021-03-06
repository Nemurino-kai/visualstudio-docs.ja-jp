---
title: ButtonText 要素 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ButtonText element (VSCT XML schema)
- VSCT XML schema elements, ButtonText
ms.assetid: 56aba884-0356-4894-ae4e-32d3938f6865
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fe2440258e95ad0d61998b24dae54b731a998c47
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/29/2019
ms.locfileid: "66321213"
---
# <a name="buttontext-element"></a>ButtonText 要素
このフィールドでは、さまざまなメニューに表示されるテキストを指定できます。 既定で、`ButtonText`要素は、メニュー コント ローラーに表示されます。 `ButtonText`他のテキスト フィールドが空白の場合に要素が既定値にもになります。 `ButtonText`場合でも、他のテキスト フィールドが指定された要素を空にすることはできません。

## <a name="syntax"></a>構文

```xml
<ButtonText>My Command</ButtonText>
```

## <a name="attributes-and-elements"></a>属性と要素
 以降のセクションでは、属性、子要素、および親要素について説明します。

### <a name="attributes"></a>属性
 なし。

### <a name="child-elements"></a>子要素
 なし。

### <a name="parent-elements"></a>親要素

|要素|説明|
|-------------|-----------------|
|[ 要素](../extensibility/strings-element.md)|など、テキスト要素をグループ化`ButtonText`と`CommandName`します。|

## <a name="text-value"></a>テキスト値
 テキスト値、`ButtonText`要素がメニュー項目、combos、およびテキストが表示されている他のユーザー インターフェイス (UI) 要素に表示されるテキストを提供します。

## <a name="see-also"></a>関連項目
- [Visual Studio コマンド テーブル (.vsct) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)