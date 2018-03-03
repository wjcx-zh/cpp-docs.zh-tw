---
title: "Run 成員函式 |Microsoft 文件"
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
- WinMain method [MFC]
ms.assetid: 24ab7597-2354-495b-9a20-2c8ccc7385b3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 90436e3b775cd547a67be49c120d1fb94b32a5dc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="run-member-function"></a>Run 成員函式
架構應用程式花費最多時間在[執行](../mfc/reference/cwinapp-class.md#run)類別成員函式[CWinApp](../mfc/reference/cwinapp-class.md)。 在初始化之後，`WinMain`呼叫**執行**處理訊息迴圈。  
  
 **執行**循環訊息迴圈，檢查訊息佇列中可用的訊息。 如果訊息可用**執行**分派它以進行動作。 如果沒有訊息可供使用，這是通常為 true，**執行**呼叫`OnIdle`執行任何閒置時間處理您或架構可能需要完成。 如果沒有想要的訊息和閒置處理，則應用程式會等候直到有動作發生。 當應用程式終止時，**執行**呼叫`ExitInstance`。 在圖[OnIdle 成員函式](../mfc/onidle-member-function.md)訊息迴圈中顯示的動作順序。  
  
 訊息分派取決於訊息的類型。 如需詳細資訊，請參閱[訊息和架構中的命令](../mfc/messages-and-commands-in-the-framework.md)。  
  
## <a name="see-also"></a>請參閱  
 [CWinApp：應用程式類別](../mfc/cwinapp-the-application-class.md)
