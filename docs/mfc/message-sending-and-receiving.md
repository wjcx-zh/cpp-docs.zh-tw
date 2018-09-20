---
title: 訊息傳送和接收 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Windows messages [MFC], handling in MFC
- control-notification messages [MFC]
- messages [MFC], receiving
- messages [MFC], MFC
- MFC, messages
- messages [MFC], sending
ms.assetid: 9ce189cb-b259-4c3b-b6f2-9cfbed18b98b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e28f35fc87b78ac4e04df0f8147d76571c51320e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46438817"
---
# <a name="message-sending-and-receiving"></a>訊息傳送和接收

思考處理序中傳送的部分，以及架構如何回應。

大部分的訊息都是使用者與程式互動的結果。 命令是透過按一下功能表項目或工具列按鈕或快速鍵產生。 使用者也可透過諸如移動或調整視窗大小來產生 Windows 訊息。 當發生程式啟動或終止 (例如視窗取得或失去焦點) 等事件時，就會傳送其他 Windows 訊息。 控制項通知訊息是透過滑鼠點選或其他使用者與控制項 (例如對話方塊中的按鈕或清單方塊控制向) 的互動而產生。

`Run`類別成員函式`CWinApp`擷取訊息，並將其分派到適當的視窗。 大部分的命令訊息都會傳送到應用程式的主框架視窗。 由類別庫預先定義的 `WindowProc` 會收到訊息並視所接收訊息的分類，以不同的方式進行路由。

現在請考慮處理序的接收部分。

訊息的初始接收者必須是視窗物件。 Windows 訊息通常直接由該視窗物件處理。 命令訊息，通常來自應用程式的主框架視窗中，會路由至命令目標鏈結中所述[命令路由](../mfc/command-routing.md)。

每個可以接收訊息或命令的物件都有自己的訊息對應，該對應會將訊息或命令與其處理常式的名稱配對。

當命令目標物件接收訊息或命令時，會搜尋其訊息對應的符合項目。 如果它找到訊息的處理常式，便會呼叫處理常式。 如需有關如何搜尋訊息對應的詳細資訊，請參閱 < [Framework 搜尋訊息對應方式](../mfc/how-the-framework-searches-message-maps.md)。 再次參閱圖[架構中的命令](../mfc/user-interface-objects-and-command-ids.md)。

## <a name="see-also"></a>另請參閱

[架構如何呼叫處理常式](../mfc/how-the-framework-calls-a-handler.md)

