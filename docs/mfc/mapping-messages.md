---
title: "將訊息對應 |Microsoft 文件"
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
- message maps [MFC], about message maps
- mappings [MFC], commands
- commands [MFC], mapping
- command mapping [MFC]
- message handling [MFC], connecting to handler functions
- commands [MFC], connecting to handler functions
- mappings [MFC], messages
- messages [MFC], mapping
ms.assetid: 996f0652-0698-4b8c-b893-cdaa836d9d0f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c415b12b22c19a5e1f2d19fd9c808a98485eb7ae
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="mapping-messages"></a>對應訊息
每個可以接收訊息或命令的架構類別皆有其自己的「訊息對應」。 架構會使用訊息對應將訊息和命令連接到它們的處理函式。 任何衍生自類別 `CCmdTarget` 的類別皆可有訊息對應。 其他文件會詳細解釋訊息對應並說明用法。  
  
 即便名稱 「 訊息對應 」 訊息對應會處理訊息和命令，所有三個訊息中列出分類[訊息分類](../mfc/message-categories.md)。  
  
## <a name="see-also"></a>請參閱  
 [架構中的訊息和命令](../mfc/messages-and-commands-in-the-framework.md)

