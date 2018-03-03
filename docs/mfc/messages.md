---
title: "訊息 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- messages, MFC
- messages [MFC]
ms.assetid: b1476310-a135-42ca-817c-444fb3675491
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d03eed129fd5a2a7c73f7c7948cb766813f63c34
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="messages"></a>訊息
中的訊息迴圈**執行**類別成員函式`CWinApp`擷取佇列的各種事件所產生的訊息。 例如，當使用者按一下滑鼠時，Windows 會傳送數個滑鼠相關訊息，例如當按下滑鼠左鍵時會傳送 `WM_LBUTTONDOWN`，當放開滑鼠左鍵時會傳送 `WM_LBUTTONUP`。 架構的應用程式訊息迴圈實作會將訊息分派至適當視窗。  
  
 重要的訊息分類如下所述[訊息分類](../mfc/message-categories.md)。  
  
## <a name="see-also"></a>請參閱  
 [架構中的訊息和命令](../mfc/messages-and-commands-in-the-framework.md)

