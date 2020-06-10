---
title: 訊息處理和對應
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, messages
- message handling [MFC]
- message maps [MFC]
ms.assetid: 62fe2a1b-944c-449d-a0f0-63c11ee0a3cb
ms.openlocfilehash: a27f8220055630873b02dd7ff975c04744ad9e8e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622411"
---
# <a name="message-handling-and-mapping"></a>訊息處理和對應

此系列的文章描述 MFC 架構如何處理訊息和命令以及如何連接至其處理函式。

在傳統的 Windows 程式中，Windows 訊息是由視窗程序的大型 switch 陳述式來處理。 MFC 會改為使用[訊息對應](message-categories.md)，將直接訊息對應至不同的類別成員函式。 訊息對應在這種用途下較虛擬函式更有效率，而且其允許訊息由最適當的 C++ 物件 (應用程式、文件、檢視等等) 進行處理。 您可以對應單一訊息或一個範圍的訊息、命令 ID 或控制項 ID。

WM_COMMAND 訊息 (通常由功能表、工具列按鈕或快速鍵產生) 也使用訊息對應機制。 MFC 會在應用程式、框架視窗、視圖和程式中的活動文檔之間，定義命令訊息的標準[路由](command-routing.md)。 如果需要，您可以覆寫這個路由。

訊息對應也提供了更新使用者介面物件 (例如功能表和工具列按鈕)、啟用或停用它們以符合目前內容的方法。

如需 Windows 中訊息和訊息佇列的一般資訊，請參閱 Windows SDK 中的[訊息和訊息佇列](/windows/win32/winmsg/messages-and-message-queues)。

## <a name="what-do-you-want-to-know-more-about"></a>您想要深入瞭解的內容

- [架構中的訊息和命令](messages-and-commands-in-the-framework.md)

- [架構如何呼叫訊息處理常式](how-the-framework-calls-a-handler.md)

- [架構如何搜尋訊息對應](how-the-framework-searches-message-maps.md)

- [宣告訊息處理函式](declaring-message-handler-functions.md)

- [將訊息對應到函式](reference/mapping-messages-to-functions.md)

- [如何在狀態列中顯示命令資訊](how-to-display-command-information-in-the-status-bar.md)

- [使用者介面物件的動態更新](how-to-update-user-interface-objects.md)

- [如何：建立樣板類別的訊息對應](how-to-create-a-message-map-for-a-template-class.md)

## <a name="see-also"></a>另請參閱

[概念](mfc-concepts.md)<br/>
[一般 MFC 主題](general-mfc-topics.md)<br/>
[CWnd 類別](reference/cwnd-class.md)<br/>
[CCmdTarget 類別](reference/ccmdtarget-class.md)
