---
title: 處理標題控制項告知 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CHeaderCtrl class [MFC], processing notifications
- controls [MFC], header
- notifications [MFC], processing for CHeaderCtrl
- header controls [MFC], processing notifications
- header control notifications
ms.assetid: e6c6af7c-d458-4d33-85aa-48014ccde5f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 539e7411dcc47be17bb10a5322e30a524679ca8c
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43194207"
---
# <a name="processing-header-control-notifications"></a>處理標題控制項告知
在檢視或對話方塊類別中，使用 [屬性] 視窗來建立[OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify) switch 陳述式的任何標頭控制項使用的處理常式函式 ([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) 您想要的通知訊息處理 (請參閱[將訊息對應至函式](../mfc/reference/mapping-messages-to-functions.md))。 通知會傳送至父視窗中，當使用者按一下或按兩下標頭項目，拖曳分割線之間的項目，依此類推。  
  
 標頭控制項相關聯的通知訊息所述[標頭控制項參考](https://msdn.microsoft.com/library/windows/desktop/bb775239)Windows SDK 中。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)   
 [控制項](../mfc/controls-mfc.md)

