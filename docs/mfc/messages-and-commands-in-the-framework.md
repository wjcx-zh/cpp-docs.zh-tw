---
title: 架構中的訊息和命令
ms.date: 11/04/2016
helpviewer_keywords:
- events [MFC], command routing in MFC
- event-driven programming [MFC]
- events [MFC], event-driven programming
- message-driven programming [MFC]
ms.assetid: d799ed8c-6a9f-4f05-be5d-29cb5bc6d185
ms.openlocfilehash: db529e2a22b45de3c6f6a659874bbaa941187217
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624296"
---
# <a name="messages-and-commands-in-the-framework"></a>架構中的訊息和命令

針對 Microsoft Windows 撰寫的應用程式是「訊息驅動」。 為了回應事件（例如滑鼠點按、按鍵、視窗移動等等），Windows 會將訊息傳送至適當的視窗。 架構應用程式會處理 Windows 訊息，就像 Windows 的任何其他應用程式一樣。 但是，此架構也提供一些增強功能，讓處理訊息更容易、更易於維護，以及更有效率地封裝。

下列主題將介紹文章系列其餘部分所使用的主要詞彙，以討論訊息和命令：

- [Messages](messages.md)

- [訊息處理常式](message-handlers.md)

- [訊息類別](message-categories.md)

- [Windows 訊息和控制項通知訊息](message-categories.md)

- [命令訊息](message-categories.md)

- [訊息對應](mapping-messages.md)

- [使用者介面物件和命令識別碼](user-interface-objects-and-command-ids.md)

- [命令目標](command-targets.md)

## <a name="see-also"></a>另請參閱

[訊息處理和對應](message-handling-and-mapping.md)
