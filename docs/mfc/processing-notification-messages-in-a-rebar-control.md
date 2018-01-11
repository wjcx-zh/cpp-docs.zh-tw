---
title: "處理 Rebar 控制項中的通知訊息 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- RBN_ notification messages, description of
- CReBarCtrl class [MFC], notification messages sent by
- RBN_ notification messages [MFC]
- notifications [MFC], CReBarCtrl
ms.assetid: 40f43a60-0c18-4d8d-8fab-213a095624f9
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 22a8b584c309cd6698ddd73449fcbba866111190
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="processing-notification-messages-in-a-rebar-control"></a>處理 Rebar 控制項中的通知訊息
在 Rebar 控制項的父類別中，請為任何一個您要處理的 Rebar 控制項 (`OnChildNotify`) 通知訊息建立一個 switch 陳述式的 `CReBarCtrl` 處理常式函式。 當使用者拖曳物件到 Rebar 控制項上方、變更 Rebar 群組列的配置、從 Rebar 控制項刪除群組列等等時，就會傳送通知給父視窗。  
  
 下列通知訊息可以由 Rebar 控制項物件傳送：  
  
-   **RBN_AUTOSIZE** ，由 rebar 控制項傳送 (使用建立**RBS_AUTOSIZE**樣式) 當 rebar 自動調整其大小。  
  
-   **RBN_BEGINDRAG**使用者開始拖曳群組列時，由 rebar 控制項傳送。  
  
-   **RBN_CHILDSIZE**調整寬線的子視窗的大小時，由 rebar 控制項傳送。  
  
-   **RBN_DELETEDBAND**被刪除後，由 rebar 控制項傳送。  
  
-   **RBN_DELETINGBAND**即將被刪除時，由 rebar 控制項傳送。  
  
-   **RBN_ENDDRAG**使用者停止拖曳群組列時，由 rebar 控制項傳送。  
  
-   **RBN_GETOBJECT** ，由 rebar 控制項傳送 (使用建立**RBS_REGISTERDROP**樣式) 當物件已拖曳至控制項中。  
  
-   **RBN_HEIGHTCHANGE**它的高度變更時，由 rebar 控制項傳送。  
  
-   **RBN_LAYOUTCHANGED**使用者變更控制項的寬線的版面配置時，由 rebar 控制項傳送。  
  
 如需有關這些通知的詳細資訊，請參閱[Rebar 控制項參考](http://msdn.microsoft.com/library/windows/desktop/bb774375)Windows SDK 中。  
  
## <a name="see-also"></a>請參閱  
 [使用 CReBarCtrl](../mfc/using-crebarctrl.md)   
 [控制項](../mfc/controls-mfc.md)

