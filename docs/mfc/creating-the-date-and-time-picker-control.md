---
title: "建立日期和時間選擇器控制項 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- DateTimePicker control [MFC], creating
- CDateTimeCtrl class [MFC], creating
ms.assetid: 764ec2fb-98cd-478b-a5f2-d63f0bb12279
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e9c0b99f42bef162ed3c571e19630f9227a8504e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="creating-the-date-and-time-picker-control"></a>建立日期時間選擇器控制項
建立日期和時間選擇器控制項的方式取決於您是使用控制項在對話方塊中還是非對話方塊視窗中建立。  
  
### <a name="to-use-cdatetimectrl-directly-in-a-dialog-box"></a>在對話方塊中直接使用 CDateTimeCtrl  
  
1.  在對話方塊編輯器中，將加入至您的對話方塊範本資源的日期和時間選擇器控制項。 指定其控制項 ID.  
  
2.  指定需要，使用 [屬性] 對話方塊的日期和時間選擇器控制項的樣式。  
  
3.  使用[加入成員變數精靈](../ide/adding-a-member-variable-visual-cpp.md)新增類型的成員變數[CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md)與控制項屬性。 您可以使用這個成員呼叫 `CDateTimeCtrl` 成員函式。  
  
4.  使用 [屬性] 視窗將在任何日期時間選擇器控制項的對話方塊類別中的處理常式函式對應[通知](../mfc/processing-notification-messages-in-date-and-time-picker-controls.md)您需要處理的訊息 (請參閱[訊息對應到函式](../mfc/reference/mapping-messages-to-functions.md))。  
  
5.  在[OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)，設定的任何其他樣式`CDateTimeCtrl`物件。  
  
### <a name="to-use-cdatetimectrl-in-a-nondialog-window"></a>若要在非對話方塊視窗中使用 CDateTimeCtrl  
  
1.  宣告中檢視或視窗類別的控制項。  
  
2.  呼叫控制項的[建立](../mfc/reference/ctabctrl-class.md#create)成員函式，可能在[OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate)，方式與父視窗[OnCreate](../mfc/reference/cwnd-class.md#oncreate) （如果您目前的處理常式函式子類別化控制項）。 設定控制項的樣式。  
  
## <a name="see-also"></a>請參閱  
 [使用 CDateTimeCtrl](../mfc/using-cdatetimectrl.md)   
 [控制項](../mfc/controls-mfc.md)

