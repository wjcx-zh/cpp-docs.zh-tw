---
title: Messages
ms.date: 11/04/2016
helpviewer_keywords:
- messages, MFC
- messages [MFC]
ms.assetid: b1476310-a135-42ca-817c-444fb3675491
ms.openlocfilehash: f36dab679a2e41910b2445a7dab36f5786081563
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624287"
---
# <a name="messages"></a>Messages

類別成員函式中的訊息迴圈會抓取 `Run` `CWinApp` 各種事件所產生的佇列訊息。 例如，當使用者按一下滑鼠時，Windows 會傳送數個滑鼠相關的訊息，例如，當按下滑鼠左鍵時 WM_LBUTTONDOWN，並在放開滑鼠左按鈕時 WM_LBUTTONUP。 架構的應用程式訊息迴圈實作會將訊息分派至適當視窗。

訊息[類別](message-categories.md)中會描述重要的訊息類別。

## <a name="see-also"></a>另請參閱

[架構中的訊息和命令](messages-and-commands-in-the-framework.md)
