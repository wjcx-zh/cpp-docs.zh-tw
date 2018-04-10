---
title: 命令目標 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- command targets
- command mapping
- messages, command [MFC]
- command routing [MFC], command targets
ms.assetid: b0f784e5-c6dc-4391-9e71-aa7b7dcbe9f0
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bb8d2bff69e95a089827c85ade6dc4bcd67eb7ff
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="command-targets"></a>命令目標
圖[架構中的命令](../mfc/user-interface-objects-and-command-ids.md)顯示使用者介面物件，例如功能表項目，以及在架構呼叫來執行產生的命令在按下的物件時的處理常式函式之間的連線。  
  
 Windows 會將不是命令訊息的訊息直接傳送至視窗，而其訊息處理常式則接著被呼叫。 不過，架構會將命令路由至多個候選物件 (稱為「命令目標」)，其中一個通常會叫用命令的處理常式。 處理常式函式的運作方式相同命令和標準 Windows 訊息，但所呼叫的機制則不同，如所述[架構如何呼叫處理常式](../mfc/how-the-framework-calls-a-handler.md)。  
  
## <a name="see-also"></a>請參閱  
 [架構中的訊息和命令](../mfc/messages-and-commands-in-the-framework.md)

