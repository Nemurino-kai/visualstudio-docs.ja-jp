---
title: '手順 10: その他のボタンおよびチェック ボックスに対するコードの記述'
ms.date: 08/30/2019
ms.assetid: 185cf370-ab39-4ac0-b6bc-601d5b95a4a2
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 414e477dcc2e7b3bd4fcde6c82fe6c0ef77f1df0
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2020
ms.locfileid: "76113369"
---
# <a name="step-10-write-code-for-additional-buttons-and-a-check-box"></a>手順 10: その他のボタンおよびチェック ボックスに対するコードの記述

ここまでで、他の 4 つのメソッドを実行する準備が整いました。 このコードをコピーして貼り付けることもできますが、コードを入力し、IntelliSense を使用すると、このチュートリアルの学習の効果を最大限に高めることができます。

このコードは、以前に追加したボタンに機能を追加します。 このコードがないと、ボタンは何も実行しません。 コントロールをアクティブにすると、ボタンは <xref:System.Windows.Forms.Control.Click> イベントのコードを使用して (およびチェック ボックスは <xref:System.Windows.Forms.CheckBox.CheckedChanged> イベントを使用して)、異なる内容を実行します。 たとえば、 **[Clear the picture]** ボタンをクリックするとアクティブになる `clearButton_Click` (または `ClearButton_Click`) イベントでは、**Image** プロパティが **null** (または **nothing**) に設定されることによって、現在のイメージが消去されます。 コードの各イベントには、コードが実行する内容を説明するコメントが含まれています。

> [!TIP]
> ベスト プラクティスとして、コードには常にコメントを付けることをお勧めします。 コメントは人が読むための情報であり、時間をかけてでも記述しておけばコードがわかりやすくなります。 コメント行の内容は、アプリではすべて無視されます。 行をコメント行にするには、C# の場合は先頭に 2 つのスラッシュ (//) を入力し、Visual Basic の場合は先頭に単一引用符 (') を入力します。

## <a name="how-to-write-code-for-additional-buttons-and-a-check-box"></a>その他のボタンとチェック ボックスのコードを記述する方法

次のコードを **Form1** コード ファイル (*Form1.cs* または *Form1.vb*) に追加します。

  [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

  [!code-csharp[VbExpressTutorial1Step9_10#2](../ide/codesnippet/CSharp/step-10-write-code-for-additional-buttons-and-a-check-box_1.cs)]

  [!code-vb[VbExpressTutorial1Step9_10#2](../ide/codesnippet/VisualBasic/step-10-write-code-for-additional-buttons-and-a-check-box_1.vb)]

> [!NOTE]
> ご利用のコードでは、"camelCase" という文字が表示されない場合があります。

## <a name="next-steps"></a>次の手順

* チュートリアルの次の手順に進むには、 **[手順 11: アプリの実行とその他の機能の使用](../ide/step-11-run-your-program-and-try-other-features.md)** に関するページを参照してください。

* チュートリアルの前の手順に戻るには、「[手順 9:レビュー、コメントの追加、およびコードのテスト](../ide/step-9-review-comment-and-test-your-code.md)」をご覧ください。

## <a name="see-also"></a>関連項目

* [チュートリアル 2: 制限時間ありの計算クイズの作成](tutorial-2-create-a-timed-math-quiz.md)
* [チュートリアル 3: 絵合わせゲームの作成](tutorial-3-create-a-matching-game.md)
