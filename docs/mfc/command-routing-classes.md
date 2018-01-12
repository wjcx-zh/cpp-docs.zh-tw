---
title: "命令路由類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.classes.command
dev_langs: C++
helpviewer_keywords:
- MFC, command routing
- command routing [MFC], classes
ms.assetid: 4b50e689-2c54-4e6c-90f0-37333e22b2a1
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c7e49c92b909abb01f3daec9e16f0e08b2a31c89
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="command-routing-classes"></a>命令路由類別
當使用者透過使用滑鼠選擇功能表或控制列按鈕來與應用程式互動時，應用程式會從受影響的使用者介面物件傳送訊息至適當的命令目標物件。 命令目標類別衍生自`CCmdTarget`包含[CWinApp](../mfc/reference/cwinapp-class.md)， [CWnd](../mfc/reference/cwnd-class.md)， [CDocTemplate](../mfc/reference/cdoctemplate-class.md)， [CDocument](../mfc/reference/cdocument-class.md)， [CView](../mfc/reference/cview-class.md)，並從它們衍生的類別。 架構支援自動的命令路由，以便可以由目前在應用程式中作用中的最適當物件來處理命令。  
  
 類別的物件`CCmdUI`傳遞至命令目標的更新命令 UI ([ON_UPDATE_COMMAND_UI](reference/message-map-macros-mfc.md#on_update_command_ui)) 處理常式，讓您更新特定命令的使用者介面的狀態 （例如，用來檢查或移除從功能表項目檢查）。 您呼叫 `CCmdUI` 物件的成員函式來更新 UI 物件的狀態。 這個程序與 UI 物件與特定命令關聯的是功能表項目或按鈕 (或者二者都關聯) 相同。  
  
 [CCmdTarget](../mfc/reference/ccmdtarget-class.md)  
 做為可以接收和回應訊息之物件的所有類別的基底類別。  
  
 [CCmdUI](../mfc/reference/ccmdui-class.md)  
 提供程式設計介面，以更新使用者介面物件 (例如功能表項目或控制列按鈕)。 命令目標物件會使用此物件啟用、停用、檢查和/或清除使用者介面物件。  
  
## <a name="see-also"></a>請參閱  
 [類別概觀](../mfc/class-library-overview.md)

