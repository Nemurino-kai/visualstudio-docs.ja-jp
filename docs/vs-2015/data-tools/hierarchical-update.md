---
title: 階層更新 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- saving data, changed data
- data [Visual Basic], hierarchical update
- saving updated data
- datasets [Visual Basic], hierarchical update
- hierarchical update
- saving data, hierarchical update
- modified data saving
- updated data saving
- related tables, saving
ms.assetid: 68bae3f6-ec9b-45ee-a33a-69395029f54c
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 99e19bce34c2bc8578a062c87aaef10302589075
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670021"
---
# <a name="hierarchical-update"></a>階層更新
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

階層更新 * は、参照整合性ルールを維持したまま、更新されたデータを (2 つ以上の関連テーブルを含むデータセットから) データベースに保存するプロセスを指します。 *参照整合性*とは、関連レコードの挿入、更新、および削除の動作を制御する、データベース内の制約によって提供される整合性規則を指します。 たとえば、顧客レコードの作成を強制してから、その顧客の注文を作成できるようにする参照整合性です。  データセット内のリレーションシップの詳細については、「[データセット内のリレーションシップ](../data-tools/relationships-in-datasets.md)」を参照してください。

 階層更新機能では、`TableAdapterManager` を使用して、型指定されたデータセット内の `TableAdapter`s を管理します。 @No__t_0 コンポーネントは [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 生成されたクラスであるため、[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] の一部ではありません。 [データソース] ウィンドウから Windows フォームまたは WPF ページにテーブルをドラッグすると、Visual Studio によって TableAdapterManager 型の変数がフォームまたはページに追加され、コンポーネントトレイのデザイナーに表示されます。 @No__t_0 クラスの詳細については、「 [TableAdapterManager の概要](https://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650)」の「TableAdapterManager Reference」セクションを参照してください。

 既定では、データセットは関連テーブルを "リレーションのみ" として扱います。これは、外部キー制約が適用されないことを意味します。 この設定は、デザイン時にデータセットデザイナーを使用して変更できます。 2つのテーブル間のリレーション線を選択して、 **[リレーションシップ]** ダイアログボックスを表示します。 ここで行った変更によって、関連テーブルの変更をデータベースに送信するときの TableAdapterManager の動作が決まります。

## <a name="enablehierarchical-update-in-a-dataset"></a>データセット内の enablehierarchical 更新
 プロジェクトで追加または作成されたすべての新しいデータセットでは、階層更新が既定で有効になっています。 データセットデザイナーで、型指定されたデータセットの "**階層更新**" プロパティを**True**または**False**に設定して、階層更新をオンまたはオフにします。

 ![階層更新の設定](../data-tools/media/hierarchical-update-setting.png "階層更新の設定")

## <a name="create-a-new-relation-between-tables"></a>テーブル間に新しいリレーションシップを作成する
 2つのテーブル間の新しいリレーションシップを作成するには、データセットデザイナーで各テーブルのタイトルバーを選択し、右クリックして **[リレーションシップの追加]** を選択します。

 ![階層更新の [リレーションシップの追加] メニュー](../data-tools/media/hierarchical-update-add-relation-menu.png "階層更新の [リレーションシップの追加] メニュー")

## <a name="understand-foreign-key-constraints-cascading-updates-and-deletes"></a>外部キー制約、連鎖更新、および削除について
 生成されたデータセット コードで、データベースでの外部キー制約と連鎖動作がどのように作成されるかを理解することは重要です。

 既定では、データセットのデータ テーブルは、データベースでのリレーションシップと一致するリレーションシップ (<xref:System.Data.DataRelation>) が設定された状態で生成されます。 ただし、データセットでのリレーションシップは、外部キー制約としては生成されません。 @No__t_0 は、<xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> または <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> が有効になっていない場合に**のみ、リレーション**として構成されます。

 連鎖更新と連鎖削除は、データベースのリレーションシップで連鎖更新や連鎖削除が有効になっている場合でも、既定で無効になっています。 たとえば、新しい顧客と新しい注文を作成し、データを保存しようとすると、データベースで定義されている外部キー制約との競合が発生する可能性があります。 詳細については、「[方法: データセットの外部キー制約を構成する](https://msdn.microsoft.com/library/3954c388-e209-4a67-a34e-5ca106282f8e)」を参照してください。

## <a name="set-the-order-to-perform-updates"></a>更新を実行する順序を設定する
 更新を実行する順序を設定すると、データセットのすべてのテーブルのすべての変更されたデータを保存するために必要な個々の挿入、更新、および削除の順序が設定されます。 階層更新が有効な場合、まず挿入が実行され、次に更新、削除の順で実行されます。 `TableAdapterManager` には、更新、挿入、削除の順に実行できる `UpdateOrder` プロパティも用意されています。

> [!NOTE]
> 更新順序がすべて含まれていることを理解しておくことが重要です。 つまり、更新が実行されると、データセット内のすべてのテーブルに対して、挿入、および削除が実行されます。

 @No__t_0 プロパティを設定するには、[[データソース] ウィンドウ](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)からフォームに項目をドラッグした後、コンポーネントトレイで `TableAdapterManager` を選択し、 **[プロパティ]** ウィンドウで [`UpdateOrder`] プロパティを設定します。 詳細については、「[方法: 階層更新の実行順序を設定](https://msdn.microsoft.com/library/a0734935-78dd-4c0b-80d7-5e7925789c83)する」を参照してください。

## <a name="create-a-backup-copy-of-a-dataset-before-performing-a-hierarchical-update"></a>階層更新を実行する前にデータセットのバックアップコピーを作成する
 データを保存すると (`TableAdapterManager.UpdateAll()` メソッドを呼び出すことにより)、`TableAdapterManager` は単一のトランザクションで各テーブルのデータの更新を試みます。 任意のテーブルの更新時に、なんらかが失敗した場合、トランザクション全体がロールバックされます。 ほとんどの場合、ロールバックによってアプリケーションが元の状態に戻ります。

 ただし、バックアップ コピーからデータセットを復元することもできます。 この例の1つは、自動インクリメント値を使用している場合に発生する可能性があります。 たとえば、保存操作が失敗した場合、データセットの自動インクリメント値はリセットされず、データセットは自動インクリメント値を引き続き作成します。これにより、アプリケーションで受け入れられない可能性のある、番号付けのギャップが残ります。 これが問題となる状況では、`TableAdapterManager` に備わっている `BackupDataSetBeforeUpdate` プロパティを使用して、トランザクションが失敗した場合に既存のデータセットをバックアップ コピーと置き換えることができます。

> [!NOTE]
> バックアップコピーは、`TableAdapterManager.UpdateAll` メソッドの実行中にメモリ内にのみ存在します。 このため、このバックアップデータセットにプログラムでアクセスすることはできません。これは、`TableAdapterManager.UpdateAll` メソッドの実行が完了するとすぐに元のデータセットを置き換えるか、スコープ外に出るためです。

## <a name="modify-the-generated-save-code-to-perform-the-hierarchical-update"></a>階層更新を実行するために生成された保存コードを変更する
 データセットでの関連データ テーブルへの変更をデータベースに保存するには、`TableAdapterManager.UpdateAll` メソッドを呼び出し、関連テーブルが含まれるデータセットの名前を渡します。 たとえば、NorthwindDataset 内のすべてのテーブルの更新をバックエンドのデータベースに送信するには、`TableAdapterManager.UpdateAll(NorthwindDataset)` メソッドを実行します。

 **[データ ソース]** ウィンドウから項目をドロップすると、各テーブルにデータを読み込むコード (`TableAdapter.Fill` メソッド) が `Form_Load` イベントに自動的に追加されます。 <xref:System.Windows.Forms.BindingNavigator> の **[保存]** ボタン クリック イベントにも、データセットのデータをデータベースに保存するコード (`TableAdapterManager.UpdateAll` メソッド) が追加されます。

 生成された保存コードには、`CustomersBindingSource.EndEdit` メソッドを呼び出すコード行も含まれています。 具体的には、フォームに追加された最初の <xref:System.Windows.Forms.BindingSource>that の <xref:System.Windows.Forms.BindingSource.EndEdit%2A> メソッドを呼び出します。 言い換えると、このコードは **[データソース]** ウィンドウからフォームにドラッグされた最初のテーブルに対してのみ生成されます。 <xref:System.Windows.Forms.BindingSource.EndEdit%2A> 呼び出しは、現在編集中のデータ バインド コントロールで実行されている変更をコミットします。 したがって、あるデータ バインド コントロールにフォーカスがある状態で **[保存]** ボタンをクリックすると、実際の保存 (`TableAdapterManager.UpdateAll` メソッド) が実行される前に、そのコントロール内のすべての保留中の編集がコミットされます。

> [!NOTE]
> データセットデザイナーは、フォームにドロップされた最初のテーブルの `BindingSource.EndEdit` コードだけを追加します。 したがって、フォーム上の各関連テーブルに対して、`BindingSource.EndEdit` メソッドを呼び出すコード行を手動で追加する必要があります。 つまり、このチュートリアルでも、`OrdersBindingSource.EndEdit` メソッドの呼び出しを追加する必要があります。

#### <a name="to-update-the-code-to-commit-changes-to-the-related-tables-before-saving"></a>保存前に、関連テーブルへの変更をコミットするコードを更新するには

1. <xref:System.Windows.Forms.BindingNavigator> の **[保存]** ボタンをダブルクリックし、コード エディターで **Form1** を開きます。

2. `OrdersBindingSource.EndEdit` メソッドを呼び出す行の後に、`CustomersBindingSource.EndEdit` メソッドを呼び出すコード行を追加します。 **[保存]** ボタン クリック イベントのコードは、次のようになります。

    [!code-csharp[VSProDataOrcasHierarchicalUpdate#1](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasHierarchicalUpdate/CS/Form1.cs#1)]
    [!code-vb[VSProDataOrcasHierarchicalUpdate#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasHierarchicalUpdate/VB/Form1.vb#1)]

   データベースにデータを保存する前に関連子テーブルに対する変更をコミットするだけでなく、新しい子レコードをデータセットに追加する前に、新しく作成された親レコードをコミットすることが必要な場合もあります。 つまり、外部キー制約により、新しい子レコード (Orders) をデータセットに追加する前に、データセットに新しい親レコード (Customer) を追加することが必要な場合もあります。 この操作を行うには、子 `BindingSource.AddingNew` イベントを使用します。

> [!NOTE]
> 新しい親レコードをコミットする必要があるかどうかは、データソースへのバインドに使用されるコントロールの種類によって異なります。 このチュートリアルでは、個々のコントロールを使用して親テーブルにバインドします。 これには、新しい親レコードをコミットするための追加コードが必要です。 親レコードが <xref:System.Windows.Forms.DataGridView> のような複雑なバインドコントロールに表示された場合は、親レコードに対するこの追加の <xref:System.Windows.Forms.BindingSource.EndEdit%2A> 呼び出しは必要ありません。 これは、コントロールの基になるデータバインド機能によって、新しいレコードのコミットが行われるためです。

#### <a name="to-add-code-to-commit-parent-records-in-the-dataset-before-adding-new-child-records"></a>データセットで新しい子レコードを追加する前に親レコードをコミットするコードを追加するには

1. `OrdersBindingSource.AddingNew` イベントのイベント ハンドラーを作成します。

    - デザインビューで**Form1**を開き、コンポーネントトレイで **[OrdersBindingSource]** を選択します。次に、 **[プロパティ]** ウィンドウで **[イベント]** を選択し、 **[追加]** イベントをダブルクリックします。

2. @No__t_0 メソッドを呼び出すイベントハンドラーにコード行を追加します。 `OrdersBindingSource_AddingNew` イベント ハンドラー内のコードは、次のようになります。

     [!code-csharp[VSProDataOrcasHierarchicalUpdate#2](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasHierarchicalUpdate/CS/Form1.cs#2)]
     [!code-vb[VSProDataOrcasHierarchicalUpdate#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasHierarchicalUpdate/VB/Form1.vb#2)]

## <a name="tableadaptermanager-reference"></a>TableAdapterManager リファレンス
 既定では、関連テーブルを含むデータセットを作成すると、`TableAdapterManager` クラスが生成されます。 クラスが生成されないようにするには、データセットの `Hierarchical Update` プロパティの値を false に変更します。 Windows フォームまたは WPF ページのデザインサーフェイスにリレーションシップを持つテーブルをドラッグすると、Visual Studio はクラスのメンバー変数を宣言します。 データバインドを使用しない場合は、手動で変数を宣言する必要があります。

 @No__t_0 クラスは [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] の一部ではありません。 このため、ドキュメントでは確認できません。 これは、デザイン時にデータセット作成プロセスの一部として作成されます。

 @No__t_0 クラスの頻繁に使用されるメソッドとプロパティを次に示します。

|メンバー|説明|
|------------|-----------------|
|`UpdateAll` メソッド|すべてのデータテーブルのすべてのデータを保存します。|
|`BackUpDataSetBeforeUpdate` プロパティ|@No__t_0 メソッドを実行する前に、データセットのバックアップコピーを作成するかどうかを決定します。演算.|
|*tableName* `TableAdapter` プロパティ|@No__t_0 を表します。 生成される `TableAdapterManager` には、it が管理する各 `TableAdapter` のプロパティが含まれています。 たとえば、Customers テーブルと Orders テーブルを含むデータセットが生成され、`CustomersTableAdapter` と `OrdersTableAdapter` プロパティを含む `TableAdapterManager` が生成されます。|
|`UpdateOrder` プロパティ|個々の insert、update、および delete コマンドの順序を制御します。 @No__t_0 列挙体のいずれかの値に設定します。<br /><br /> 既定では、`UpdateOrder` は**Insertupdatedelete**に設定されています。 これは、データセット内のすべてのテーブルに対して、挿入、更新、および削除が実行されることを意味します。 詳細については、「[方法: 階層更新の実行順序を設定](https://msdn.microsoft.com/library/a0734935-78dd-4c0b-80d7-5e7925789c83)する」を参照してください。|

## <a name="see-also"></a>参照
 [データをデータベースに保存する](../data-tools/save-data-back-to-the-database.md)
