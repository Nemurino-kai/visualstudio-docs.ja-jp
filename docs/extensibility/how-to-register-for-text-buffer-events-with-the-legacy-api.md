---
title: '方法: テキスト バッファー イベント、レガシ API の登録 |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - register for text buffer events
ms.assetid: 5fc00ced-882c-4b48-b46c-1fa5a2469f94
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 10f1dbbc50535c1b0fd297f99c359ea8b0511c68
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/29/2019
ms.locfileid: "66321455"
---
# <a name="how-to-register-for-text-buffer-events-with-the-legacy-api"></a>方法: 従来の API を使用したイベントのテキスト バッファーの登録します。
テキスト バッファーを従来の API を使用してアクセスする場合は、テキスト バッファー イベント、次の手順で示すように登録してください。

## <a name="to-advise-text-buffer-events"></a>テキスト バッファーのイベントを通知するには

1. 上のインターフェイスのいずれかへのポインターから<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>、呼び出す`QueryInterface`へのポインターの<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>します。

2. 呼び出す、<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer.FindConnectionPoint%2A>メソッド、および登録するイベントのインターフェイス ID を渡します。

     例では、登録する場合の<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>、インターフェイス ID の IID_IVsTextLinesEvents で渡します。

     テキスト バッファーへのポインターを返します、<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>適切な接続ポイント オブジェクトのインターフェイス。

3. このポインターを使用して、呼び出し、<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>を登録する、たとえば、イベント インターフェイスの実装にポインターを渡し、メソッド、`IVsTextLinesEvents`インターフェイス。

     環境が呼び出すことによってイベントのリッスンを中止し、使用できるクッキーを返します、<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Unadvise%2A>メソッド。

## <a name="see-also"></a>関連項目
- [従来の API でのテキスト バッファー イベント](../extensibility/text-buffer-events-in-the-legacy-api.md)