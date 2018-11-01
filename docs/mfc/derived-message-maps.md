---
title: 衍生訊息對應
ms.date: 11/04/2016
helpviewer_keywords:
- message handling [MFC], derived message handlers
- messages, routing
- message maps [MFC], derived
- derived message maps
ms.assetid: 21829556-6e64-40c3-8279-fed85d99de77
ms.openlocfilehash: 1413290bc04af37a6d3204150dff5244e1dcb5c5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50662523"
---
# <a name="derived-message-maps"></a>衍生訊息對應

在處理訊息期間，檢查類別本身的訊息對應並不是訊息對應劇本的結束。 如果發生什麼事類別`CMyView`(衍生自`CView`) 沒有相符的項目訊息

請記住，`CView` 的基底類別 `CMyView` 會接著從`CWnd` 衍生。 因此`CMyView`*是*`CView`並*是* `CWnd`。 這些類別的每一種都有其訊息對應。 以下為「檢視階層架構」的圖例，顯示類別的階層關聯性，但請記住，`CMyView` 物件為具有所有三個類別特性的單一物件。

![檢視的階層](../mfc/media/vc38621.gif "vc38621")檢視階層架構

因此，如果訊息在類別 `CMyView` 的訊息對應中無法相符，架構也會搜尋其直接基底類別的訊息對應。 在訊息對應的開始 `BEGIN_MESSAGE_MAP` 巨集指定兩個類別名稱做為其引數:

[!code-cpp[NVC_MFCMessageHandling#2](../mfc/codesnippet/cpp/derived-message-maps_1.cpp)]

第一個引數會為訊息對應所屬的類別命名。 第二個引數會提供與直接基底類別 (例如 `CView`) 的連接，因此架構也可以搜尋其訊息對應。

基底類別中所提供的訊息處理常式會由衍生類別繼承。 這和一般虛擬成員函式非常類似，而不需要讓所有的處理常式成員函式虛擬化。

如果在任何基底類別訊息對應中找不到處理常式，便會執行預設的訊息處理。 如果訊息為命令，架構會將其路由到下一個命令目標。 如果是標準 Windows 訊息，則將訊息傳遞至適當的預設視窗程序。

為加速訊息對應的比對，架構會基於可能再次收到相同的訊息而快取近來最相符者。 這種處理方式的結果之一，是架構對於未處理訊息的處理會相當具有效率。 訊息對應的空間利用也比使用虛擬函式的實作更有效率。

## <a name="see-also"></a>另請參閱

[架構如何搜尋訊息對應](../mfc/how-the-framework-searches-message-maps.md)

