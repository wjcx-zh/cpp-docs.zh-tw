---
title: 命令目標 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- command targets
- command mapping
- messages, command [MFC]
- command routing [MFC], command targets
ms.assetid: b0f784e5-c6dc-4391-9e71-aa7b7dcbe9f0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1cbcfa1042a8430c704bad93e4bc0ce5655b5921
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="command-targets"></a>命令目標
圖[架構中的命令](../mfc/user-interface-objects-and-command-ids.md)顯示使用者介面物件，例如功能表項目，以及在架構呼叫來執行產生的命令在按下的物件時的處理常式函式之間的連線。  
  
 Windows 會將不是命令訊息的訊息直接傳送至視窗，而其訊息處理常式則接著被呼叫。 不過，架構會將命令路由至多個候選物件 (稱為「命令目標」)，其中一個通常會叫用命令的處理常式。 處理常式函式的運作方式相同命令和標準 Windows 訊息，但所呼叫的機制則不同，如所述[架構如何呼叫處理常式](../mfc/how-the-framework-calls-a-handler.md)。  
  
## <a name="see-also"></a>另請參閱  
 [架構中的訊息和命令](../mfc/messages-and-commands-in-the-framework.md)

