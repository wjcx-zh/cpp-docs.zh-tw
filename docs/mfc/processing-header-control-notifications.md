---
title: "處理標題控制項告知 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CHeaderCtrl class [MFC], processing notifications
- controls [MFC], header
- notifications [MFC], processing for CHeaderCtrl
- header controls [MFC], processing notifications
- header control notifications
ms.assetid: e6c6af7c-d458-4d33-85aa-48014ccde5f6
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a442e6aadf7c91918cd523c29330e79c753b115c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="processing-header-control-notifications"></a>處理標題控制項告知
在檢視或對話方塊類別中，使用 [屬性] 視窗建立[OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify) switch 陳述式的任何標頭控制項的處理常式函式 ([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) 您想要的通知訊息處理 (請參閱[訊息對應到函式](../mfc/reference/mapping-messages-to-functions.md))。 通知會傳送至父視窗中，當使用者按一下或按兩下標題項目，項目，以及其他的之間拖曳分割線。  
  
 標頭控制項相關聯的通知訊息會列在[標頭控制項參考](http://msdn.microsoft.com/library/windows/desktop/bb775239)Windows SDK 中。  
  
## <a name="see-also"></a>請參閱  
 [使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)   
 [控制項](../mfc/controls-mfc.md)

