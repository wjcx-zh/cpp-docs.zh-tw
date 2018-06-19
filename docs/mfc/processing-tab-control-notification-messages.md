---
title: 處理索引標籤控制項通知訊息 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- notifications [MFC], tab controls
- CTabCtrl class [MFC], processing notifications
- notifications [MFC], processing in CTabCtrl
- processing notifications [MFC]
- tab controls [MFC], processing notifications
ms.assetid: 758ccb7a-9e73-48f8-9073-23f7cb09918c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6ce59bfe298798d4574bf158998e989c4a6af62c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33348357"
---
# <a name="processing-tab-control-notification-messages"></a>處理索引標籤控制項通知訊息
當使用者按一下索引標籤或按鈕，此索引標籤控制項 ([CTabCtrl](../mfc/reference/ctabctrl-class.md)) 會傳送通知訊息至其父視窗。 如果您想要執行動作以作為回應，請處理這些訊息。 例如，當使用者按一下索引標籤，您可以在預設之前顯示頁面上的控制項資料。  
  
 處理序**WM_NOTIFY**來自您檢視或對話方塊類別中的索引標籤控制項的訊息。 使用 [屬性] 視窗建立[OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify) switch 陳述式的處理常式函式會根據正在處理通知訊息。 如需索引標籤控制項可以傳送給其父視窗的通知，請參閱**通知**區段[ 索引標籤控制項參考](http://msdn.microsoft.com/library/windows/desktop/bb760548)Windows SDK 中。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CTabCtrl](../mfc/using-ctabctrl.md)   
 [控制項](../mfc/controls-mfc.md)

