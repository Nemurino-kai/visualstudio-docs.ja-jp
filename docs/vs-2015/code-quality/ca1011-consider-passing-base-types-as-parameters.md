---
title: 'CA1011: 基本型をパラメーターとして渡すことを検討してください |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ConsiderPassingBaseTypesAsParameters
- CA1011
helpviewer_keywords:
- CA1011
- ConsiderPassingBaseTypesAsParameters
ms.assetid: ce1e1241-dcf4-419b-9363-1d5bc4989279
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 3968d81e8ee18b4b0a56bed50f7aa1f121e1c074
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663249"
---
# <a name="ca1011-consider-passing-base-types-as-parameters"></a>CA1011: 基本型をパラメーターとして渡すことを考慮します
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ConsiderPassingBaseTypesAsParameters|
|CheckId|CA1011|
|カテゴリ|Microsoft Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 メソッドの宣言には、派生型の仮パラメーターが含まれています。このメソッドは、パラメーターの基本型のメンバーのみを呼び出します。

## <a name="rule-description"></a>規則の説明
 メソッドの宣言で基本型をパラメーターとして指定すると、その基本型から派生した型は、メソッドに対応する引数として渡すことができます。 引数がメソッド本体の内部で使用されている場合、実行される特定のメソッドは引数の型によって異なります。 派生型によって提供される追加機能が不要な場合は、基本型を使用することで、メソッドを広範囲に使用できます。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、パラメーターの型をその基本型に変更します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 このルールからの警告を抑制するのは安全です。

- メソッドに、派生型によって提供される特定の機能が必要な場合

   \- または

- 派生型のみ、またはそれ以上の派生型のみがメソッドに渡されるようにするには、を適用します。

  このような場合は、コンパイラとランタイムによって提供される厳密な型チェックにより、コードがより堅牢になります。

## <a name="example"></a>例
 次の例は、この規則に違反する <xref:System.IO.FileStream> オブジェクトでのみ使用できるメソッド `ManipulateFileStream` を示しています。 2番目のメソッドである `ManipulateAnyStream` は、<xref:System.IO.Stream> を使用して <xref:System.IO.FileStream> パラメーターを置き換えることでルールを満たします。

 [!code-cpp[FxCop.Design.ConsiderPassingBaseTypes#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ConsiderPassingBaseTypes/cpp/FxCop.Design.ConsiderPassingBaseTypes.cpp#1)]
 [!code-csharp[FxCop.Design.ConsiderPassingBaseTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ConsiderPassingBaseTypes/cs/FxCop.Design.ConsiderPassingBaseTypes.cs#1)]
 [!code-vb[FxCop.Design.ConsiderPassingBaseTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ConsiderPassingBaseTypes/vb/FxCop.Design.ConsiderPassingBaseTypes.vb#1)]

## <a name="related-rules"></a>関連規則
 [CA1059: メンバーは特定の具象型を公開できません](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)
