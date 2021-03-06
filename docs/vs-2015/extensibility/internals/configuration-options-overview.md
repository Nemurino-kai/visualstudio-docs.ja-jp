---
title: 構成オプションの概要 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project configurations
- configuration options, about configuration options
ms.assetid: f4ad4dd3-b39e-42df-ad89-d403cdf24a2b
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0b37d93adbd2accb7a12fb176ab15aafc6914190
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441521"
---
# <a name="configuration-options-overview"></a>構成オプションの概要
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

プロジェクトで[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]構築できますが、デバッグ、実行、および配置された複数の構成をサポートすることができます。 構成とは、ビルドの種類のコンパイラ スイッチおよびファイルの場所では通常、プロパティの名前付きセットを使用して記述します。 既定では、新しいソリューションには、2 つの構成、デバッグとリリースが含まれます。 既定の設定を使用するか、特定のソリューションやプロジェクトの要件を満たすように変更は、これらの構成を適用できます。 一部のパッケージは、2 つの方法でビルドできます。 またはインプレース コンポーネントとして ActiveX エディターとして。 ただし、複数の構成をサポートするためには、プロジェクトは必要はありません。 1 つのみの構成が使用可能な場合、その構成は、すべてのソリューション構成にマップされます。  
  
 通常の構成は 2 つの部分で構成されている、プラットフォームの設定と構成の名前 (デバッグやリリースなど)。 プラットフォーム名の構成の設定の構成対象の API など、環境またはオペレーティング システム プラットフォームを識別します。 ユーザーの[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]プラットフォーム; を作成することはできませんにより、VSPackage プロジェクト選択項目が選択する必要があります。 ユーザー インストール、VSPackage のパッケージ開発中に作成された配信プラットフォームが必要な任意のプラットフォーム名を表示する場合は、パッケージ作成者によって設定のいずれかの条件に基づいています。 ユーザーは、プロパティ ページがインスタンス化されるときに VSPackage を使用できるプラットフォームの一覧から選択できます。  
  
 すべてのプロジェクトのプラットフォームの概念をサポートするため、プラットフォーム名は省略できます。 構成では、プラットフォーム名がない、UI の"N/A"という文字列が表示されます。  
  
 各ソリューションには、独自のセットのうちの 1 つのみを有効にする時間を構成します。 ソリューション構成には、各プロジェクトから複数の構成のセットです。 「以下」規定では、ソリューション構成からプロジェクトを除外するオプションが原因です。 ユーザーは、独自のカスタム ソリューション構成を作成できます。  
  
 次の表は、プロジェクトの一般的な構成設定を示しています。 行には、構成名とプラットフォームの名前の列が付きます。  
  
|構成名|プラットフォーム、Win32|プラットフォーム: Win64|  
|------------------------|----------------------|----------------------|  
|デバッグ|\<デバッグの Win32 設定 >|\<デバッグ Win64 設定 >|  
|Release|\<リリース Win32 設定 >|\<リリース Win64 設定 >|  
|MyConfig|N/A|\<MyConfig Win64 設定 >|  
  
> [!NOTE]
> 対象とするプロジェクトは Win32 をサポートしていない場合を除き、"Win32"プラットフォームを除外する"MyConfig"ソリューション構成を作成することはできません。  
  
 ソリューションのアクティブな構成の変更は、そのソリューションにビルド、実行、デバッグまたは配置するプロジェクト構成のセットを選択します。 たとえば、リリースからデバッグするアクティブなソリューション構成を変更する場合、ソリューションのデバッグ構成に示されているプロジェクトの構成ではそのソリューション内のすべてのプロジェクトはビルド自動的に。 プロジェクトの構成は、します通常はも名前付きのデバッグ、ユーザーが手動で変更を環境の Configuration Manager で行った場合を除き。  
  
 格納されている各プロジェクトのソリューション構成のプロパティには、プロジェクト名、プロジェクト構成名、フラグを示すかどうかを構築するかを展開してプラットフォーム名が含まれます。 詳細については、次を参照してください。[ソリューション構成](../../extensibility/internals/solution-configuration.md)します。  
  
 ユーザーは、表示し、階層 (ソリューション エクスプ ローラー) で、ソリューションを選択し、プロパティ ページを開くソリューションの構成パラメーターを設定できます。 同様に、表示し、ソリューション エクスプ ローラーでプロジェクトを選択し、そのプロジェクトのプロパティ ページを開くプロジェクトの構成パラメーターを設定することができます。  
  
 ユーザーは、必要な場合に、デバッグ構成の設定でリリースの構成設定とすべての rest を使用する 1 つのプロジェクトをビルドもできます。 詳細については、次を参照してください。[構築するためのプロジェクト構成](../../extensibility/internals/project-configuration-for-building.md)します。  
  
 次の図は、ソリューションとプロジェクト構成をサポートするインターフェイスを実装する方法を示しています。  
  
 ![構成インターフェイス グラフィック](../../extensibility/internals/media/vsconfiginterfaces.gif "vsConfigInterfaces")  
構成インターフェイス  
  
 前の図に関連するいくつかの注意:  
  
- `IDispatch` 構成オブジェクトでは省略可能としてマークされます。 具体的には、参照オブジェクトの構成インターフェイスを実装する省略可能です。  
  
- `IVsDebuggableProjectCfg` 省略可能で、構成オブジェクトに設定されていますのデバッグのサポートが必要です。  
  
- `IVsProjectCfg2` 省略可能で、構成オブジェクトに設定されていますが、出力のサポートをグループ化が必要です。  
  
- `Config Provider`オブジェクトが、省略可能なオブジェクトとしてマークされていますが、オプションは、それを実装する場所。 プロジェクト オブジェクトまたは別のオブジェクトは、オブジェクトを実装することができます。  
  
- `IVsCfgProvider2` プラットフォームのサポートと構成の編集が必要です。 `IVsCfgProvider` その機能を実装していない場合は十分です。  
  
- いくつかのように個別のオブジェクトは、可能であれば、同じクラスに結合できます、図に示したこれらのオブジェクトの特定の設計要件に基づいています。 このセクションの他のトピックでは、ただし、オブジェクトとそれらのオブジェクトに関連付けられているインターフェイスについては説明に従って、ダイアグラムのシナリオでします。  
  
- 特定のオブジェクトは、個別に実装されます。 たとえば、プロジェクトとソリューションの構築とビルドの構成を記述するオブジェクトからビルド生活がどれほどを個別に管理するオブジェクトの個別のスレッドの発生します。  
  
  構成オブジェクトのインターフェイスと、前の図での構成プロバイダー オブジェクトのインターフェイスについては、次を参照してください。[プロジェクト構成オブジェクト](../../extensibility/internals/project-configuration-object.md)します。 さらに、[構築するためのプロジェクト構成](../../extensibility/internals/project-configuration-for-building.md)構成ビルダーとビルドの依存関係オブジェクトのインターフェイスについて詳しく説明しますと[展開を管理するためのプロジェクト構成](../../extensibility/internals/project-configuration-for-managing-deployment.md)さらに、構成を配置するユーザーと展開の依存関係オブジェクトにアタッチされているインターフェイスについて説明します。 最後に、[出力用のプロジェクト構成](../../extensibility/internals/project-configuration-for-output.md)出力グループと出力オブジェクトのインターフェイスと、表示し、構成に依存するプロパティを設定するプロパティ ページの使用について説明します。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>   
 [ビルドするためのプロジェクト構成](../../extensibility/internals/project-configuration-for-building.md)   
 [ソリューション構成](../../extensibility/internals/solution-configuration.md)
