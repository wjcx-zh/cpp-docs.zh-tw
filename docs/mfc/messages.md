---
title: 訊息 |Microsoft 文件
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
ms.openlocfilehash: abd49410f9982788e9403f0cb83ca8656473417d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="messages"></a>訊息
中的訊息迴圈**執行**類別成員函式`CWinApp`擷取佇列的各種事件所產生的訊息。 例如，當使用者按一下滑鼠時，Windows 會傳送數個滑鼠相關訊息，例如當按下滑鼠左鍵時會傳送 `WM_LBUTTONDOWN`，當放開滑鼠左鍵時會傳送 `WM_LBUTTONUP`。 架構的應用程式訊息迴圈實作會將訊息分派至適當視窗。  
  
 重要的訊息分類如下所述[訊息分類](../mfc/message-categories.md)。  
  
## <a name="see-also"></a>另請參閱  
 [架構中的訊息和命令](../mfc/messages-and-commands-in-the-framework.md)

