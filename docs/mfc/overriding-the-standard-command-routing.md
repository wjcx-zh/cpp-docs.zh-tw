---
title: "覆寫標準命令路由 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC, command routing
- command routing [MFC], overriding
- command handling [MFC], routing commands
- overriding, standard command routing
ms.assetid: 872b698a-7432-40c4-9008-68721e8effa5
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6a8f926a2aa9ed48dac24f75850876bbd1e04ef4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="overriding-the-standard-command-routing"></a>覆寫標準命令路由
偶爾當您必須實作一些標準架構路由變化時，您可以覆寫它。 這個概念是可以藉由在這些類別中覆寫 `OnCmdMsg` 來變更一個或多個類別的路由。 可以這麼做：  
  
-   在中斷命令以傳遞至非預設物件的類別。  
  
-   在新的非預設物件，或在可能接收依序傳遞之命令的命令目標。  
  
 如果您將一些新物件插入至路由，其類別必須是命令目標類別。 在您覆寫的 `OnCmdMsg` 版本中，務必呼叫您覆寫的版本。 請參閱[OnCmdMsg](../mfc/reference/ccmdtarget-class.md#oncmdmsg)類別成員函式`CCmdTarget`中*MFC 參考*與做為這類類別中的版本`CView`和**CDocument**中提供範例的原始程式碼。  
  
## <a name="see-also"></a>請參閱  
 [架構如何呼叫處理常式](../mfc/how-the-framework-calls-a-handler.md)

