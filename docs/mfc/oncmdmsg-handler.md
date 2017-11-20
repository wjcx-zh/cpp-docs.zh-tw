---
title: "OnCmdMsg 處理常式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: OnCmdMsg
dev_langs: C++
helpviewer_keywords:
- messages, routing
- handlers [MFC]
- command routing [MFC], OnCmdMsg handler
- handlers, OnCmdMessage [MFC]
- OnCmdMessage method [MFC]
ms.assetid: 8df07024-506f-47e7-bba9-1c3bc5ad8ab6
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 71913ede29f3a8e02c319b3c713d2c33bbcb5b8e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="oncmdmsg-handler"></a>OnCmdMsg 處理常式
若要完成命令路由，每個命令目標會呼叫序列中下一個命令目標的 `OnCmdMsg` 成員函式。 命令目標會使用 `OnCmdMsg` 判斷是否可以處理命令，如果無法處理便傳送至另一個命令目標。  
  
 每個命令目標類別可能會覆寫 `OnCmdMsg` 成員函式。 覆寫會讓每個類別將命令路由傳送到下一個特定目標。 框架視窗中，例如，一律將命令路由傳送至其目前子視窗或檢視表，如下表所示[標準命令路由](../mfc/command-routing.md)。  
  
 `CCmdTarget` 的預設 `OnCmdMsg` 實作會使用命令目標類別的訊息對應，搜尋每一個接收到的命令訊息的處理函式，其與搜尋標準訊息的方式相同。 如果找到符合的項目，便會呼叫處理常式。 搜尋訊息對應中會說明[如何架構搜尋訊息對應](../mfc/how-the-framework-searches-message-maps.md)。  
  
## <a name="see-also"></a>另請參閱  
 [架構如何呼叫處理常式](../mfc/how-the-framework-calls-a-handler.md)
