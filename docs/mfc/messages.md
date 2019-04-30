---
title: 訊息
ms.date: 11/04/2016
helpviewer_keywords:
- messages, MFC
- messages [MFC]
ms.assetid: b1476310-a135-42ca-817c-444fb3675491
ms.openlocfilehash: 8e1bfd1baa8ffef76ba31912fc619c4217696683
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384123"
---
# <a name="messages"></a>訊息

中的訊息迴圈`Run`類別成員函式`CWinApp`擷取佇列的各種事件所產生的訊息。 比方說，當使用者按一下滑鼠時，Windows 會傳送數個滑鼠相關的訊息，例如 WM_LBUTTONDOWN 時按下滑鼠左鍵和 WM_LBUTTONUP 當使用者放開滑鼠左的按鈕。 架構的應用程式訊息迴圈實作會將訊息分派至適當視窗。

重要的訊息分類所述[訊息分類](../mfc/message-categories.md)。

## <a name="see-also"></a>另請參閱

[架構中的訊息和命令](../mfc/messages-and-commands-in-the-framework.md)
