---
title: 處理清單控制項中的通知訊息 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- processing notifications [MFC]
- CListCtrl class [MFC], processing notifications
ms.assetid: 1f0e296e-d2a3-48fc-ae38-51d7fb096f51
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: af648a0bf4ae78c5c5e8bcceeac12c5dbc87307a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33347672"
---
# <a name="processing-notification-messages-in-list-controls"></a>處理清單控制項中的通知訊息
當使用者按一下資料行標頭、 拖曳圖示、 編輯標籤等等，清單控制項 ([CListCtrl](../mfc/reference/clistctrl-class.md)) 會傳送通知訊息至其父視窗。 如果您想要執行動作以作為回應，請處理這些訊息。 例如，當使用者按一下資料行標頭時，您可能會想要根據所按資料行的內容 (例如在 Microsoft Outlook 中) 來為項目排序。  
  
 處理序**WM_NOTIFY**從清單中的控制項檢視或對話方塊類別的訊息。 使用 [屬性] 視窗建立[OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify) switch 陳述式的處理常式函式會根據正在處理通知訊息。  
  
 如需清單控制項可以傳送給其父視窗的通知，請參閱[清單檢視控制項參考](http://msdn.microsoft.com/library/windows/desktop/bb774737)Windows SDK 中。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CListCtrl](../mfc/using-clistctrl.md)   
 [控制項](../mfc/controls-mfc.md)

