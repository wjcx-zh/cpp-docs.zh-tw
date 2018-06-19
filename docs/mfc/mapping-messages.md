---
title: 將訊息對應 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f521145599a3d734a22dd3b2707ad4dd16df8e80
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33345982"
---
# <a name="mapping-messages"></a>對應訊息
每個可以接收訊息或命令的架構類別皆有其自己的「訊息對應」。 架構會使用訊息對應將訊息和命令連接到它們的處理函式。 任何衍生自類別 `CCmdTarget` 的類別皆可有訊息對應。 其他文件會詳細解釋訊息對應並說明用法。  
  
 即便名稱 「 訊息對應 」 訊息對應會處理訊息和命令，所有三個訊息中列出分類[訊息分類](../mfc/message-categories.md)。  
  
## <a name="see-also"></a>另請參閱  
 [架構中的訊息和命令](../mfc/messages-and-commands-in-the-framework.md)

