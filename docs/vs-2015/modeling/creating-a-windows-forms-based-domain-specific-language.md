---
title: Windows フォームベースのドメイン固有言語を作成する |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 452318ff-8ecf-46d0-8ca0-4013d0cdafaf
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cea3b76575e1da2e846e230580c6cfa50ef9b207
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651263"
---
# <a name="creating-a-windows-forms-based-domain-specific-language"></a>Windows フォームに基づくドメイン固有言語の作成
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows フォームを使用すると、DSL 図を使用する代わりに、ドメイン固有言語 (DSL) モデルの状態を表示できます。 このトピックでは、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] の視覚化およびモデリング SDK を使用して、Windows フォームを DSL にバインドする手順について説明します。

 ![DSL&#45;Wpf&#45;2](../modeling/media/dsl-wpf-2.png "DSL-Wpf-2")Windows フォーム UI とモデルエクスプローラーを表示する DSL インスタンス。

## <a name="creating-a-windows-forms-dsl"></a>Windows フォーム DSL の作成
 **最小限の WinForm デザイナー** DSL テンプレートでは、独自の要件に合わせて変更できる最小限の dsl が作成されます。

#### <a name="to-create-a-minimal-winforms-dsl"></a>最小 WinForms DSL を作成するには

1. **最小の WinForm デザイナー**テンプレートから DSL を作成します。

    このチュートリアルでは、次の名前を前提としています。

   |                       |                 |
   |-----------------------|-----------------|
   | ソリューションと DSL の名前 |     FarmApp     |
   |       Namespace       | FarmApp |

2. テンプレートに用意されている最初の例を試してみてください。

   1. すべてのテンプレートを変換します。

   2. サンプルをビルドして実行します (**CTRL + F5 キーを押し**ます)。

   3. Visual Studio の実験用インスタンスで、デバッグプロジェクトの `Sample` ファイルを開きます。

        Windows フォームコントロールに表示されることに注意してください。

        また、モデルの要素がエクスプローラーに表示されていることも確認できます。

        フォームまたはエクスプローラーでいくつかの要素を追加し、他の表示に表示されていることを確認します。

   @No__t_0 のメインインスタンスでは、DSL ソリューションに関する次の点に注意してください。

- `DslDefinition.dsl` には、図の要素が含まれていません。 これは、dsl の図を使用して DSL のインスタンスモデルを表示しないためです。 代わりに、Windows フォームをモデルにバインドすると、フォーム上の要素にモデルが表示されます。

- @No__t_0 と `DslPackage` のプロジェクトに加えて、ソリューションには、`UI.`**UI**プロジェクトという名前の3番目のプロジェクトが含まれています。このプロジェクトには、Windows フォームコントロールの定義が含まれています。 `DslPackage` は `UI` に依存し、`UI` は `Dsl` に依存します。

- @No__t_0 プロジェクトで `UI\DocView.cs` には、`UI` プロジェクトで定義されている Windows フォームコントロールを表示するコードが含まれています。

- @No__t_0 プロジェクトには、DSL にバインドされているフォームコントロールの実際のサンプルが含まれています。 ただし、DSL 定義を変更した場合は機能しません。 @No__t_0 プロジェクトには次のものが含まれます。

  - @No__t_0 という名前の Windows フォームクラス。

  - @No__t_1 の追加部分定義を含む `DataBinding.cs` という名前のファイル。 コンテンツを表示するには、**ソリューションエクスプローラー**で、ファイルのショートカットメニューを開き、 **[コードの表示]** をクリックします。

### <a name="about-the-ui-project"></a>UI プロジェクトについて
 Dsl 定義ファイルを更新して独自の DSL を定義する場合は、`UI` プロジェクトのコントロールを更新して DSL を表示する必要があります。 @No__t_0 プロジェクトと `DslPackage` プロジェクトとは異なり、サンプル `UI` プロジェクトは `DslDefinitionl.dsl` から生成されません。 必要に応じて、.tt ファイルを追加してコードを生成できます。ただし、このチュートリアルでは説明しません。

## <a name="updating-the-dsl-definition"></a>DSL 定義を更新しています
 このチュートリアルでは、次の DSL 定義を使用します。

 ![DSL&#45;Wpf&#45;1](../modeling/media/dsl-wpf-1.png "DSL-Wpf-1")

#### <a name="to-update-the-dsl-definition"></a>DSL 定義を更新するには

1. DSL デザイナーで DslDefinition. dsl を開きます。

2. **要素**の削除

3. **Examplemodel.store**ドメインクラスの名前を `Farm` に変更します。

     **Int32**型の `Size` という名前の追加のドメインプロパティと、**ブール**型の `IsOrganic` を指定します。

    > [!NOTE]
    > ルートドメインクラスを削除してから新しいルートを作成する場合は、エディターのルートクラスのプロパティをリセットする必要があります。 **DSL エクスプローラー**で、 **[エディター]** を選択します。 次に、プロパティウィンドウで、 **Root クラス**を `Farm` に設定します。

4. **名前付きドメインクラス**ツールを使用して、次のドメインクラスを作成します。

    - `Field` –これに `Size` という名前の追加のドメインプロパティを指定します。

    - `Animal` –プロパティウィンドウで、**継承修飾子**を**Abstract**に設定します。

5. **ドメインクラス**ツールを使用して、次のクラスを作成します。

    - `Sheep`

    - `Goat`

6. **継承**ツールを使用すると、`Goat` して `Animal` から継承 `Sheep` できます。

7. **埋め込み**ツールを使用して、`Field` と `Animal` を `Farm` の下に埋め込みます。

8. 図を整理することもできます。 重複する要素の数を減らすには、リーフ要素のショートカットメニューの **[サブツリーをここに移動]** を使用します。

9. ソリューションエクスプローラーのツールバーにある**すべてのテンプレートを変換**します。

10. **Dsl**プロジェクトをビルドします。

    > [!NOTE]
    > この段階では、他のプロジェクトはエラーなしでビルドされません。 ただし、データソースウィザードでそのアセンブリを使用できるように、Dsl プロジェクトをビルドする必要があります。

## <a name="updating-the-ui-project"></a>UI プロジェクトの更新
 DSL モデルに格納されている情報を表示する新しいユーザーコントロールを作成できるようになりました。 ユーザーコントロールをモデルに接続する最も簡単な方法は、データバインディングを使用することです。 **Modevdc bindingsource**という名前のデータバインディングアダプターの種類は、dsl を非 VMSDK インターフェイスに接続するように設計されています。

#### <a name="to-define-your-dsl-model-as-a-data-source"></a>DSL モデルをデータソースとして定義するには

1. **[データ]** メニューの **[データソースの表示]** をクリックします。

     **[データ ソース]** ウィンドウが開きます。

     **[新しいデータソースの追加]** を選択します。 **データ ソース構成ウィザード**が開きます。

2. **[オブジェクト]** 、 **[次へ]** の順に選択します。

     **[Dsl]** 、 **[FarmApp]** の順に展開し、モデルのルートクラスである **[ファーム]** を選択します。 **[完了]** を選択します。

     ソリューションエクスプローラーでは、 **UI**プロジェクトに**Properties\DataSources\Farm.datasource**が含まれるようになりました。

     [データソース] ウィンドウに、モデルクラスのプロパティとリレーションシップが表示されます。

     ![DslWpf&#45;3](../modeling/media/dslwpf-3.png "DslWpf-3")

#### <a name="to-connect-your-model-to-a-form"></a>モデルをフォームに接続するには

1. **UI**プロジェクトで、既存の .cs ファイルをすべて削除します。

2. @No__t_1 という名前の新しい**ユーザーコントロール**ファイルを**UI**プロジェクトに追加します。

3. **[データソース]** ウィンドウの **[ファーム]** のドロップダウンメニューで、 **[詳細]** を選択します。

    他のプロパティの既定の設定はそのままにします。

4. デザインビューで FarmControl.cs を開きます。

    [データソース] ウィンドウから FarmControl に**ファーム**をドラッグします。

    各プロパティに1つずつ、一連のコントロールが表示されます。 リレーションシップのプロパティでは、コントロールは生成されません。

5. **FarmBindingNavigator**を削除します。 これは、`FarmControl` デザイナーでも自動的に生成されますが、このアプリケーションには役立ちません。

6. ツールボックスを使用して、 **DataGridView**のインスタンスを2つ作成し、`AnimalGridView` と `FieldGridView` に名前を指定します。

   > [!NOTE]
   > 別の手順として、[データソース] ウィンドウからコントロールに [動物とフィールド] の項目をドラッグします。 この操作により、グリッドビューとデータソースの間にデータグリッドとバインドが自動的に作成されます。 ただし、このバインドは Dsl では正しく機能しません。 そのため、データグリッドとバインドを手動で作成することをお勧めします。

7. ツールボックスに**Modeの bindingsource**ツールが含まれていない場合は、ツールボックスを追加します。 **[データ]** タブのショートカットメニューで、 **[項目の選択]** を選択します。 **[ツールボックスアイテムの選択]** ダイアログで、[ **.NET Framework] タブ**の **[modeて bindingsource]** を選択します。

8. ツールボックスを使用して、 **modeの**2 つのインスタンスを作成し、その名前を `AnimalBinding` と `FieldBinding` にします。

9. 各**Modeの** **DataSource**プロパティを**farmBindingSource**に設定します。

     **DataMember**プロパティを **動物**または**フィールド**に設定します。

10. @No__t_1 の**DataSource**プロパティを `AnimalBinding` に設定し、`FieldGridView` を `FieldBinding` に設定します。

11. ファームコントロールのレイアウトを好みに合わせて調整します。

    **Modeare bindingsource**は、dsl に固有のいくつかの機能を実行するアダプターです。

- VMSDK ストアトランザクションで更新をラップします。

   たとえば、ユーザーがデータビューグリッドから行を削除すると、通常のバインドではトランザクションの例外が発生します。

- これにより、ユーザーが行を選択したときに、データグリッド行ではなく、対応するモデル要素のプロパティがプロパティウィンドウ表示されるようになります。

  ![DslWpf4](../modeling/media/dslwpf4.png "DslWpf4")データソースとビューの間のリンクのスキーマ。

#### <a name="to-complete-the-bindings-to-the-dsl"></a>DSL へのバインドを完了するには

1. **UI**プロジェクトの別のコードファイルに次のコードを追加します。

    ```csharp
    using System.ComponentModel;
    using Microsoft.VisualStudio.Modeling;
    using Microsoft.VisualStudio.Modeling.Design;

    namespace Company.FarmApp
    {
      partial class FarmControl
      {
        public IContainer Components { get { return components; } }

        /// <summary>Binds the WinForms data source to the DSL model.
        /// </summary>
        /// <param name="nodelRoot">The root element of the model.</param>
        public void DataBind(ModelElement modelRoot)
        {
          WinFormsDataBindingHelper.PreInitializeDataSources(this);
          this.farmBindingSource.DataSource = modelRoot;
          WinFormsDataBindingHelper.InitializeDataSources(this);
        }
      }
    }
    ```

2. **Dslpackage**プロジェクトで、次の変数定義を更新して、 **Dslpackage\ docview.tt**を編集します。

    ```csharp
    string viewControlTypeName = "FarmControl";
    ```

## <a name="testing-the-dsl"></a>DSL のテスト
 DSL ソリューションを構築して実行できるようになりました。ただし、後でさらに改良を加えることもできます。

#### <a name="to-test-the-dsl"></a>DSL をテストするには

1. ソリューションをビルドして実行します。

2. Visual Studio の実験用インスタンスで、**サンプル**ファイルを開きます。

3. **FarmApp エクスプローラー**で、**ファーム**のルートノードのショートカットメニューを開き、 **[新しい Goat の追加]** を選択します。

     **[動物]** ビューに `Goat1` が表示されます。

    > [!WARNING]
    > **[動物]** ノードではなく、 **[ファーム]** ノードのショートカットメニューを使用する必要があります。

4. **ファーム**のルートノードを選択し、そのプロパティを表示します。

     フォームビューで、ファームの**名前**または**サイズ**を変更します。

     フォームの各フィールドから移動すると、プロパティウィンドウの対応するプロパティが変更されます。

## <a name="enhancing-the-dsl"></a>DSL を強化する

#### <a name="to-make-the-properties-update-immediately"></a>プロパティを直ちに更新するには

1. FarmControl.cs のデザインビューで、名前、サイズ、IsOrganic などの単純なフィールドを選択します。

2. プロパティウィンドウで、 **[連結]** を展開して **[(詳細)]** を開きます。

     **[書式設定と詳細バインド]** ダイアログボックスの **[データソース更新モード]** で、 **[OnPropertyChanged]** を選択します。

3. ソリューションをビルドして実行します。

     フィールドの内容を変更すると、ファームモデルの対応するプロパティがすぐに変更されることを確認します。

#### <a name="to-provide-add-buttons"></a>[追加] ボタンを提供するには

1. FarmControl.cs のデザインビューで、ツールボックスを使用してフォーム上にボタンを作成します。

    ボタンの名前とテキストを編集します。たとえば、`New Sheep` します。

2. (たとえば、ダブルクリックして) ボタンの背後にあるコードを開きます。

    次のように編集します。

   ```csharp
   private void NewSheepButton_Click(object sender, EventArgs e)
   {
     using (Transaction t = farm.Store.TransactionManager.BeginTransaction("Add sheep"))
     {
       elementOperations.MergeElementGroup(farm,
         new ElementGroup(new Sheep(farm.Partition)));
       t.Commit();
     }
   }

   // The following code is shared with other add buttons:
   private ElementOperations operationsCache = null;
   private ElementOperations elementOperations
   {
     get
     {
       if (operationsCache == null)
       {
         operationsCache = new ElementOperations(farm.Store, farm.Partition);
       }
       return operationsCache;
     }
   }
   private Farm farm
   {
     get { return this.farmBindingSource.DataSource as Farm; }
   }

   ```

    また、次のディレクティブも挿入する必要があります。

   ```csharp

   using Microsoft.VisualStudio.Modeling;

   ```

3. Goats と Fields に似たボタンを追加します。

4. ソリューションをビルドして実行します。

5. [新規作成] ボタンによって項目が追加されていることを確認します。 FarmApp Explorer と適切なデータグリッドビューの両方に新しい項目が表示されます。

    データグリッドビューで要素の名前を編集できるようになります。 そこから削除することもできます。

   ![DSL&#45;Wpf&#45;2](../modeling/media/dsl-wpf-2.png "DSL-Wpf-2")

### <a name="about-the-code-to-add-an-element"></a>要素を追加するコードについて
 新しい要素のボタンについては、次の代替コードが少し単純になります。

```csharp
private void NewSheepButton_Click(object sender, EventArgs e)
{
  using (Transaction t = farm.Store.TransactionManager.BeginTransaction("Add sheep"))
  {
    farm.Animals.Add(new Sheep(farm.Partition)); ;
    t.Commit();
  }
}

```

 ただし、このコードでは、新しい項目の既定の名前は設定されません。 DSL の**要素マージディレクティブ**で定義したカスタマイズされたマージは実行されません。定義されている可能性があるカスタムマージコードは実行されません。

 そのため、<xref:Microsoft.VisualStudio.Modeling.ElementOperations> を使用して新しい要素を作成することをお勧めします。 詳細については、「[要素の作成および移動をカスタマイズ](../modeling/customizing-element-creation-and-movement.md)する」を参照してください。

## <a name="see-also"></a>参照
 ドメイン固有言語を[定義する方法](../modeling/how-to-define-a-domain-specific-language.md) [Visual Studio 用の](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)ドメイン固有言語モデリング SDK を[カスタマイズする](../modeling/writing-code-to-customise-a-domain-specific-language.md)ためのコードの作成-ドメイン固有言語
