---
title: 訊息 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- messages, MFC
- messages [MFC]
ms.assetid: b1476310-a135-42ca-817c-444fb3675491
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f25c9cc70cec598f975bbd242af83597311bdc7c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392251"
---
# <a name="messages"></a>訊息

中的訊息迴圈`Run`類別成員函式`CWinApp`擷取佇列的各種事件所產生的訊息。 比方說，當使用者按一下滑鼠時，Windows 會傳送數個滑鼠相關的訊息，例如 WM_LBUTTONDOWN 時按下滑鼠左鍵和 WM_LBUTTONUP 當使用者放開滑鼠左的按鈕。 架構的應用程式訊息迴圈實作會將訊息分派至適當視窗。

重要的訊息分類所述[訊息分類](../mfc/message-categories.md)。

## <a name="see-also"></a>另請參閱

[架構中的訊息和命令](../mfc/messages-and-commands-in-the-framework.md)

