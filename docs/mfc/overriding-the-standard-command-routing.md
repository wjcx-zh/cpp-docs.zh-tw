---
title: 覆寫標準命令路由 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, command routing
- command routing [MFC], overriding
- command handling [MFC], routing commands
- overriding, standard command routing
ms.assetid: 872b698a-7432-40c4-9008-68721e8effa5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 13f6c8f262061477da95a4863965c04e9d75c49a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="overriding-the-standard-command-routing"></a>覆寫標準命令路由
偶爾當您必須實作一些標準架構路由變化時，您可以覆寫它。 這個概念是可以藉由在這些類別中覆寫 `OnCmdMsg` 來變更一個或多個類別的路由。 可以這麼做：  
  
-   在中斷命令以傳遞至非預設物件的類別。  
  
-   在新的非預設物件，或在可能接收依序傳遞之命令的命令目標。  
  
 如果您將一些新物件插入至路由，其類別必須是命令目標類別。 在您覆寫的 `OnCmdMsg` 版本中，務必呼叫您覆寫的版本。 請參閱[OnCmdMsg](../mfc/reference/ccmdtarget-class.md#oncmdmsg)類別成員函式`CCmdTarget`中*MFC 參考*與做為這類類別中的版本`CView`和**CDocument**中提供範例的原始程式碼。  
  
## <a name="see-also"></a>另請參閱  
 [架構如何呼叫處理常式](../mfc/how-the-framework-calls-a-handler.md)

