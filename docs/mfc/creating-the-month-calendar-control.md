---
title: "建立月曆控制項 |Microsoft 文件"
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
- CMonthCalCtrl class [MFC], creating
- month calendar controls [MFC], creating
- month calendar controls [MFC]
ms.assetid: 185cc642-85e9-4365-8a4c-d90b75b010f7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f55960177fa8bc9a31ebfd16b4dbc6aeaba3ee38
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="creating-the-month-calendar-control"></a>建立月曆控制項
月曆控制項的建立方式，取決於您是在對話方塊中使用控制項，或在非對話方塊視窗建立控制項。  
  
### <a name="to-use-cmonthcalctrl-directly-in-a-dialog-box"></a>直接在對話方塊使用 CMonthCalCtrl  
  
1.  在對話方塊編輯器中，將月曆控制項加入至對話方塊範本資源。 指定其控制項 ID.  
  
2.  使用月曆控制項的 [屬性] 對話方塊，指定需要的樣式。  
  
3.  使用[加入成員變數精靈](../ide/adding-a-member-variable-visual-cpp.md)新增類型的成員變數[CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md)與控制項屬性。 您可以使用這個成員呼叫 `CMonthCalCtrl` 成員函式。  
  
4.  使用 [屬性] 視窗的任何月曆控制項告知訊息對應對話方塊類別中的處理常式函式需要將處理 (請參閱[訊息對應到函式](../mfc/reference/mapping-messages-to-functions.md))。  
  
5.  在[OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)，設定的任何其他樣式`CMonthCalCtrl`物件。  
  
### <a name="to-use-cmonthcalctrl-in-a-nondialog-window"></a>在非對話方塊視窗使用 CMonthCalCtrl  
  
1.  在檢視或視窗類別中定義控制項。  
  
2.  呼叫控制項的[建立](../mfc/reference/cmonthcalctrl-class.md#create)成員函式，可能在[OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate)，方式與父視窗[OnCreate](../mfc/reference/cwnd-class.md#oncreate) （如果您目前的處理常式函式子類別化控制項）。 設定控制項的樣式。  
  
## <a name="see-also"></a>請參閱  
 [使用 CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)   
 [控制項](../mfc/controls-mfc.md)

