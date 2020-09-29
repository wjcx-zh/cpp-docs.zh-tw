---
title: 衍生訊息對應
description: 描述 MFC 訊息處理。
ms.date: 09/23/2020
helpviewer_keywords:
- message handling [MFC], derived message handlers
- messages, routing
- message maps [MFC], derived
- derived message maps
ms.assetid: 21829556-6e64-40c3-8279-fed85d99de77
ms.openlocfilehash: 44c2180e441c91d34350c65bc17a53d1b650607c
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414213"
---
# <a name="derived-message-maps"></a>衍生訊息對應

在處理訊息期間，檢查類別本身的訊息對應並不是訊息對應劇本的結束。 如果 `CMyView` 衍生自) 的類別 (`CView` 沒有符合訊息的專案，會發生什麼事？

請記住，`CView` 的基底類別 `CMyView` 會接著從`CWnd` 衍生。 因此 `CMyView` *，* 是 `CView` ， *is*而且是 `CWnd` 。 這些類別的每一種都有其訊息對應。 下圖顯示類別的階層式關聯性，但請記住， `CMyView` 物件是具有這三個類別特性的單一物件。

![檢視的階層架構](../mfc/media/vc38621.gif "檢視的階層架構") <br/>
檢視階層架構

如果訊息無法在類別 `CMyView` 的訊息對應中相符，架構也會搜尋其直屬基類的訊息對應。 在訊息對應的開始 `BEGIN_MESSAGE_MAP` 巨集指定兩個類別名稱做為其引數:

[!code-cpp[NVC_MFCMessageHandling#2](codesnippet/cpp/derived-message-maps_1.cpp)]

第一個引數會為訊息對應所屬的類別命名。 第二個引數會提供與直屬基類的連接（在此案例中為 `CView` ），讓架構也可以搜尋其訊息對應。

基底類別中所提供的訊息處理常式會由衍生類別繼承。 這和一般虛擬成員函式非常類似，而不需要讓所有的處理常式成員函式虛擬化。

如果在任何基底類別訊息對應中找不到處理常式，便會執行預設的訊息處理。 如果訊息為命令，架構會將其路由到下一個命令目標。 如果是標準 Windows 訊息，則將訊息傳遞至適當的預設視窗程序。

為加速訊息對應的比對，架構會基於可能再次收到相同的訊息而快取近來最相符者。 這種處理方式的結果之一，是架構對於未處理訊息的處理會相當具有效率。 訊息對應的空間利用也比使用虛擬函式的實作更有效率。

## <a name="see-also"></a>另請參閱

[架構如何搜尋訊息對應](how-the-framework-searches-message-maps.md)
