---
title: 訊息傳送和接收
ms.date: 11/04/2016
helpviewer_keywords:
- Windows messages [MFC], handling in MFC
- control-notification messages [MFC]
- messages [MFC], receiving
- messages [MFC], MFC
- MFC, messages
- messages [MFC], sending
ms.assetid: 9ce189cb-b259-4c3b-b6f2-9cfbed18b98b
ms.openlocfilehash: 4da2fce68c1b6fd3827bc8b5d2a40dea5e5f117c
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626166"
---
# <a name="message-sending-and-receiving"></a>訊息傳送和接收

思考處理序中傳送的部分，以及架構如何回應。

大部分的訊息都是使用者與程式互動的結果。 命令是透過按一下功能表項目或工具列按鈕或快速鍵產生。 使用者也可透過諸如移動或調整視窗大小來產生 Windows 訊息。 當發生程式啟動或終止 (例如視窗取得或失去焦點) 等事件時，就會傳送其他 Windows 訊息。 控制項通知訊息是透過滑鼠點選或其他使用者與控制項 (例如對話方塊中的按鈕或清單方塊控制向) 的互動而產生。

類別的成員函式會抓取 `Run` `CWinApp` 訊息，並將它們分派至適當的視窗。 大部分的命令訊息都會傳送到應用程式的主框架視窗。 由類別庫預先定義的 `WindowProc` 會收到訊息並視所接收訊息的分類，以不同的方式進行路由。

現在請考慮處理序的接收部分。

訊息的初始接收者必須是視窗物件。 Windows 訊息通常直接由該視窗物件處理。 命令訊息通常源自于應用程式的主框架視窗，會路由傳送到命令[路由](command-routing.md)中所述的命令目標鏈。

每個可以接收訊息或命令的物件都有自己的訊息對應，該對應會將訊息或命令與其處理常式的名稱配對。

當命令目標物件接收訊息或命令時，會搜尋其訊息對應的符合項目。 如果它找到訊息的處理常式，便會呼叫處理常式。 如需有關如何搜尋訊息對應的詳細資訊，請參閱[架構如何搜尋訊息對應](how-the-framework-searches-message-maps.md)。 再次參閱[架構中](user-interface-objects-and-command-ids.md)的 [圖形] 命令。

## <a name="see-also"></a>另請參閱

[架構如何呼叫處理常式](how-the-framework-calls-a-handler.md)
