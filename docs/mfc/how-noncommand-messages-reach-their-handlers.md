---
title: 非命令訊息如何連接其處理常式
ms.date: 11/04/2016
helpviewer_keywords:
- messages [MFC], routing
- noncommand messages
- Windows messages [MFC], routing
- message handling [MFC], noncommand messages
ms.assetid: e7df8aef-9fae-41f4-9c11-881d8465f602
ms.openlocfilehash: f64eb97315b41a314c791e1a4c5bc7721b329fca
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50545453"
---
# <a name="how-noncommand-messages-reach-their-handlers"></a>非命令訊息如何連接其處理常式

與命令不同，標準 Windows 訊息不會透過鏈結的命令目標路由，但通常都由 Windows 會傳送訊息的視窗。 視窗可能是主框架視窗、 的 MDI 子視窗，為標準控制項、 對話方塊、 檢視或某種其他類型的子視窗。

在執行階段，每個 Windows 視窗附加至視窗物件 (直接或間接衍生自`CWnd`) 具有自己的相關聯的訊息對應和處理常式函式。 架構會使用訊息對應，與命令，將內送訊息對應至處理常式。

## <a name="see-also"></a>另請參閱

[架構如何呼叫處理常式](../mfc/how-the-framework-calls-a-handler.md)

