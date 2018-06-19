---
title: 建立標題控制項 |Microsoft 文件
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
ms.openlocfilehash: 465c880c480f9ccd3a52f6319ee97ed203c3bd74
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33344509"
---
# <a name="creating-the-header-control"></a>建立標題控制項
標題控制項不是直接使用對話方塊編輯器中 （雖然您可以新增清單控制項，包括標頭控制項）。  
  
### <a name="to-put-a-header-control-in-a-dialog-box"></a>在對話方塊中放入標題控制項  
  
1.  以手動方式將內嵌類型的成員變數[CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)對話方塊類別中。  
  
2.  在[OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)、 建立及設定的樣式`CHeaderCtrl`、 位置，並顯示它。  
  
3.  將項目加入至標題控制項。  
  
4.  使用 [屬性] 視窗將在對話方塊類別中的處理常式函式對應任何標題控制項通知訊息，您需要將處理 (請參閱[訊息對應到函式](../mfc/reference/mapping-messages-to-functions.md))。  
  
### <a name="to-put-a-header-control-in-a-view-not-a-clistview"></a>將標題控制項中的檢視 (不 CListView)  
  
1.  內嵌[CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)檢視類別中的物件。  
  
2.  樣式、 位置，並顯示標頭控制項視窗中檢視的[OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate)成員函式。  
  
3.  將項目加入至標題控制項。  
  
4.  使用 [屬性] 視窗來檢視類別中的處理常式函式對應任何標題控制項通知訊息，您需要將處理 (請參閱[訊息對應到函式](../mfc/reference/mapping-messages-to-functions.md))。  
  
 在任一情況下，建立檢視或對話方塊物件時，會建立內嵌的控制項物件。 您必須呼叫[CHeaderCtrl::Create](../mfc/reference/cheaderctrl-class.md#create)來建立控制項視窗。 要放置控制項，請呼叫[CHeaderCtrl::Layout](../mfc/reference/cheaderctrl-class.md#layout)以判斷控制項的初始大小和位置和[SetWindowPos](../mfc/reference/cwnd-class.md#setwindowpos)設定想要的位置。 然後加入項目中所述[將項目加入至標題控制項](../mfc/adding-items-to-the-header-control.md)。  
  
 如需詳細資訊，請參閱[建立標題控制項](http://msdn.microsoft.com/library/windows/desktop/bb775238)Windows SDK 中。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)   
 [控制項](../mfc/controls-mfc.md)

