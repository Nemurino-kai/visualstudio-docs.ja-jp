---
title: ビルドのプロジェクト構成 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], configuration for building
- project configurations, building
ms.assetid: 2c83615d-fa4d-4b9f-b315-7a69b3000da0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 956449d1207a9831f9dd04a707fffe4b9b5a4221
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726044"
---
# <a name="project-configuration-for-building"></a>ビルドのためのプロジェクト構成
特定のソリューションのソリューション構成の一覧は、[ソリューション構成] ダイアログボックスによって管理されます。

 ユーザーは、それぞれ独自の一意の名前を持つ追加のソリューション構成を作成できます。 ユーザーが新しいソリューション構成を作成すると、IDE では、プロジェクト内の対応する構成名が既定で設定されます。対応する名前が存在しない場合はデバッグが行われます。 ユーザーは、必要に応じて、特定の要件を満たすように選択を変更できます。 この動作の唯一の例外は、プロジェクトが新しいソリューション構成の名前と一致する構成をサポートしている場合です。 たとえば、Project1 と Project2 がソリューションに含まれているとします。 Project1 には、プロジェクト構成の Debug、Retail、および MyConfig1 があります。 Project2 には、プロジェクト構成の Debug、Retail、および MyConfig2 があります。

 ユーザーが MyConfig2 という名前の新しいソリューション構成を作成した場合、Project1 はそのデバッグ構成を既定でソリューション構成にバインドします。 また、Project2 では、MyConfig2 構成が既定でソリューション構成にバインドされます。

> [!NOTE]
> バインディングでは大文字と小文字が区別されません。

 ユーザーが [構成] ボックスの一覧で**複数の選択**項目を選択すると、使用可能な構成の一覧を示すダイアログボックスが表示されます。

 ![複数の構成](../../extensibility/internals/media/vsmultiplecfgs.gif "Vs乗算 Ecfgs")複数の構成

 このダイアログボックスでは、ユーザーは1つまたは複数の構成を選択できます。 選択すると、[プロパティページ] ダイアログボックスに表示されるプロパティ値に、選択した構成の値の積集合が反映されます。

 ソリューションとプロジェクトの構成の追加と名前変更に関する詳細については、「[ソリューションの構成](../../extensibility/internals/solution-configuration.md)」を参照してください。

 プロジェクトの依存関係とビルドの順序は、ソリューション構成に依存しません。つまり、ソリューション内のすべてのプロジェクトに対して1つの依存関係ツリーしか設定できません。 ソリューションまたはプロジェクトを右クリックし、 **[プロジェクトの依存関係]** または **[プロジェクトのビルド順序]** オプションを選択すると、 **[プロジェクトの依存関係]** ダイアログボックスが開きます。 また、 **[プロジェクト]** メニューから開くこともできます。

 ![プロジェクトの依存関係](../../extensibility/internals/media/vsprojdependencies.gif "vsProjDependencies")プロジェクトの依存関係

 プロジェクトの依存関係によって、プロジェクトのビルド順序が決まります。 ダイアログボックスの [ビルド順序] タブを使用すると、ソリューション内のプロジェクトがビルドされる正確な順序を表示し、[依存関係] タブを使用してビルド順序を変更できます。

> [!NOTE]
> リスト内のチェックボックスがオンになっているが淡色表示になっているプロジェクトは、<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> または <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> インターフェイスによって指定された明示的な依存関係があるため、環境によって追加されており、変更することはできません。 たとえば、[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] プロジェクトから別のプロジェクトにプロジェクト参照を追加すると、参照を削除することによってのみ削除できるビルド依存関係が自動的に追加されます。 チェックボックスが明確で淡色表示になっているプロジェクトは選択できません。これにより、依存関係ループ (Project1 は Project2 に依存し、Project2 は Project1 に依存します) が作成され、ビルドが停止します。

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] のビルドプロセスには、1つのビルドコマンドで呼び出される一般的なコンパイル操作とリンク操作が含まれます。 他にも2つのビルドプロセスがサポートされています。前のビルドからすべての出力項目を削除するためのクリーン操作と、構成内の出力項目が変更されたかどうかを確認するための最新のチェック。

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> オブジェクトは、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A> から返された対応する <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> を返して、ビルドプロセスを管理します。 ビルド操作の発生中に状態を報告するために、構成は、環境およびビルドステータスイベントに関係するその他のオブジェクトによって実装されたインターフェイスである <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildStatusCallback> を呼び出します。

 ビルドが完了すると、構成設定を使用して、デバッガーの制御下で実行できるかどうかを判断できます。 構成は、デバッグをサポートするために <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> を実装します。

 プロジェクトの依存関係を実装した後は、オートメーションモデルを使用して依存関係をプログラムで操作できます。 オートメーションモデルで <xref:EnvDTE.SolutionBuild.BuildDependencies%2A> を呼び出します。 ソリューションビルドマネージャーの構成とそのプロパティを直接操作できる、使用可能な VSIP API レベルのインターフェイスはありません。

 また、[プロジェクトの依存関係] ウィンドウにグリッドを指定することもできます。 詳細については、「 [Properties Display Grid](../../extensibility/internals/properties-display-grid.md)」を参照してください。

## <a name="see-also"></a>関連項目
- [構成オプションの管理](../../extensibility/internals/managing-configuration-options.md)
- [展開の管理のためのプロジェクト構成](../../extensibility/internals/project-configuration-for-managing-deployment.md)
- [出力のためのプロジェクト構成](../../extensibility/internals/project-configuration-for-output.md)