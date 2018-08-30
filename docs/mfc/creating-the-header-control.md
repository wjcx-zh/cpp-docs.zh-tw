---
title: 建立標題控制項 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CHeaderCtrl class [MFC], creating
- header controls [MFC], creating
ms.assetid: 7864d9d2-4a2c-4622-b58b-7b110a1e28d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 18517f969dc64b0c1d9a51bcdc67a1655ec82d7c
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43214005"
---
# <a name="creating-the-header-control"></a>建立標題控制項
標題控制項無法直接使用。 在對話方塊編輯器中 （雖然您可以新增清單控制項，其中包含標頭控制項）  
  
### <a name="to-put-a-header-control-in-a-dialog-box"></a>在對話方塊中放入標題控制項  
  
1.  手動內嵌型別的成員變數[CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)對話方塊類別中。  
  
2.  在  [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)、 建立和設定的樣式`CHeaderCtrl`、 位置，並顯示它。  
  
3.  加入至標題控制項的項目。  
  
4.  使用 [屬性] 視窗來對應對話方塊類別中的處理常式函式，針對任何標題控制項通知訊息，您需要將處理 (請參閱[將訊息對應至函式](../mfc/reference/mapping-messages-to-functions.md))。  
  
### <a name="to-put-a-header-control-in-a-view-not-a-clistview"></a>若要將標題控制項放在一個檢視 (不 CListView)  
  
1.  內嵌[CHeaderCtrl](../mfc/reference/cheaderctrl-class.md) view 類別中的物件。  
  
2.  樣式、 定位，以及在檢視中顯示標頭的 [控制] 視窗[OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate)成員函式。  
  
3.  加入至標題控制項的項目。  
  
4.  使用 [屬性] 視窗，對應的 view 類別中的處理常式函式，針對任何標題控制項通知訊息，您需要將處理 (請參閱[將訊息對應至函式](../mfc/reference/mapping-messages-to-functions.md))。  
  
 在任一情況下，建立檢視或對話方塊物件時，會建立內嵌的控制項物件。 您必須呼叫[Dwstyle](../mfc/reference/cheaderctrl-class.md#create)來建立控制項的視窗。 要放置控制項，請呼叫[CHeaderCtrl::Layout](../mfc/reference/cheaderctrl-class.md#layout)來判斷控制項的初始大小和位置並[SetWindowPos](../mfc/reference/cwnd-class.md#setwindowpos)設定想要的位置。 然後加入項目中所述[將項目加入至標題控制項](../mfc/adding-items-to-the-header-control.md)。  
  
 如需詳細資訊，請參閱 <<c0> [ 建立標題控制項](/windows/desktop/Controls/header-controls)Windows SDK 中。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)   
 [控制項](../mfc/controls-mfc.md)

