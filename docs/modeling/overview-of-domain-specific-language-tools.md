---
title: ドメイン固有言語ツールの概要
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7af9aa8ce8719fe08e16e244a2f7009ddf67f533
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591698"
---
# <a name="overview-of-domain-specific-language-tools"></a>ドメイン固有言語ツールの概要
Visual Studio でホストされているドメイン固有言語ツール (DSL ツール) を使用すると、ドメイン固有言語を設計し、その言語に基づくモデルを作成するためにユーザーが必要とするすべてのものを生成することができます。

 DSL ツールには次のツールが含まれています。

- さまざまなソリューション テンプレートを使用してドメイン固有言語の開発を始めるのに役立つ、プロジェクト ウィザード。

- ドメイン固有言語の定義を作成、編集するためのグラフィカル デザイナー。

- ドメイン固有言語の定義が適切な形式であることを確認し、問題がある場合はエラーや警告を表示する検証エンジン。

- ドメイン固有言語の定義を入力として受け取り、ソース コードを出力として生成するコード ジェネレーター。

## <a name="the-dsl-tools-solution"></a>DSL ツール ソリューション
 ドメイン固有デザイナー ウィザードには、次のソリューション テンプレートが用意されています。

- タスク フロー

- クラス ダイアグラム

- 最小言語

- コンポーネント モデル

- 最小限の WPF

- 最小 Windows.Forms

- DSL ライブラリ

  詳細については、「[ドメイン固有言語ソリューション テンプレートの選択](../modeling/choosing-a-domain-specific-language-solution-template.md)」を参照してください。

  ウィザードによって、次のプロジェクトを含む Visual Studio ソリューションが作成されます。

- Dsl

   Dsl プロジェクトでは、ドメイン固有言語と、その言語の編集および処理ツールを定義します。

- **DslPackage**

   DslPackage プロジェクトは、言語ツールを Visual Studio と統合する方法を決定します。

## <a name="the-dsl-tools-graphical-interface"></a>DSL ツールのグラフィカル インターフェイス
 DSL ツールのグラフィカル インターフェイスを使用して、ドメイン固有言語に要素とリレーションシップを追加することができます。 要素を追加後、要素をシェイプにマッピングし、色をカスタマイズして、デコレーターを追加することによって、要素の外観を定義できます。 要素をツールボックスに追加することもできます。

## <a name="validation-in-dsl-tools"></a>DSL ツールでの検証
 DSL には、ドメイン モデルがコード生成のための基本的な要件を満たしていることを確認する、1 つの検証レベルが用意されています。 通常、ご自分のドメイン固有言語を作成するときは、ご自分のビジネス ロジック ルールを表す独自の検証を追加します。 カスタム検証の詳細については、「[ドメイン固有言語における検証](../modeling/validation-in-a-domain-specific-language.md)」を参照してください。

 ドメイン固有言語を設計する際は、頻繁に検証することをお勧めします。 ドメイン固有言語に検証エラーがあると、ソース コードを生成できません。 テンプレートからソース コードを生成するプロセスは、ソリューション エクスプローラーのツール バーで **[すべてのテンプレートの変換]** をクリックすることによって実行します。 言語の定義を変更したときは、必ず**すべてのテンプレートの変換**も実行してください。 詳細については、「[方法: ドメイン固有言語ソリューションを作成](../modeling/how-to-create-a-domain-specific-language-solution.md)する」を参照してください。

## <a name="customization-of-dsl-tools"></a>DSL ツールのカスタマイズ
 モデルの動作を改善するために、また使用する言語に制約を定義するために、追加のコードを記述できます。 必要な場合は、テキスト テンプレートを変更することによって、大幅な変更を行うことができます。

## <a name="distributing-your-dsl-solution"></a>DSL ソリューションの配布
 DSL ツールは、Visual Studio でホストされているパッケージを生成します。 パッケージにはツールボックス、DSL エクスプローラー、およびその他の UI 要素が表示され、ユーザーは、ドメイン固有言語を使用してモデルを作成できます。

 Visual Studio で DSL ツールソリューションをビルドして実行すると、Visual Studio の2番目のインスタンスによって、ドメイン固有言語がその言語のユーザーにどのように表示されるかがわかります。 すべてが正常に動作することを確認した後、DslPackage プロジェクトのビルド フォルダーにある `.vsix` ファイルを配布できます。 このファイルは、他のコンピューターに Visual Studio 拡張機能として DSL をインストールするために使用できます。  詳細については、「[ドメイン固有言語ソリューションの配置](msi-and-vsix-deployment-of-a-dsl.md)」を参照してください。

## <a name="see-also"></a>関連項目

- [実験用インスタンス](../extensibility/the-experimental-instance.md)
- [ドメイン固有言語ツールの用語集](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
