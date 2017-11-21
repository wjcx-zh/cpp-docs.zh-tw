---
title: "建立清單控制項 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CListCtrl class [MFC], creating control
- list controls [MFC]
ms.assetid: a4cb1729-31b6-4d2b-a44b-367474848a39
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: dd187bf945e2bcf018575db8d45e4d653c5b869b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="creating-the-list-control"></a>建立清單控制項
如何控制清單 ([CListCtrl](../mfc/reference/clistctrl-class.md)) 建立取決於您是直接使用控制項或是使用類別[CListView](../mfc/reference/clistview-class.md)改為。 如果您使用`CListView`，架構建構檢視其文件/檢視建立順序的一部分。 建立清單檢視中建立清單控制項 （這兩者是相同的動作）。 在檢視中建立控制項[OnCreate](../mfc/reference/cwnd-class.md#oncreate)處理常式函式。 在此情況下，此控制項是準備好要加入項目，透過呼叫[GetListCtrl](../mfc/reference/clistview-class.md#getlistctrl)。  
  
### <a name="to-use-clistctrl-directly-in-a-dialog-box"></a>在對話方塊中直接使用 CListCtrl  
  
1.  在對話方塊編輯器中，將清單控制項加入至對話方塊範本資源。 指定其控制項 ID.  
  
2.  使用[加入成員變數精靈](../ide/adding-a-member-variable-visual-cpp.md)新增類型的成員變數`CListCtrl`與控制項屬性。 您可以使用這個成員呼叫 `CListCtrl` 成員函式。  
  
3.  使用 [屬性] 視窗來對應處理常式函式，在對話方塊類別中的，所有清單控制項通知訊息，您需要將處理 (請參閱[訊息對應到函式](../mfc/reference/mapping-messages-to-functions.md))。  
  
4.  在[OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)，設定的樣式`CListCtrl`。 請參閱[變更清單控制項樣式](../mfc/changing-list-control-styles.md)。 雖然您可以稍後變更檢視，這會決定在控制項中，您收到 「 檢視 」 的類型。  
  
### <a name="to-use-clistctrl-in-a-nondialog-window"></a>若要在非對話方塊視窗中使用 CListCtrl  
  
1.  在檢視或視窗類別中定義控制項。  
  
2.  呼叫控制項的[建立](../mfc/reference/clistctrl-class.md#create)成員函式，可能在[OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate)，方式與父視窗[OnCreate](../mfc/reference/cwnd-class.md#oncreate) （如果您目前的處理常式函式子類別化控制項）。 設定控制項的樣式。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CListCtrl](../mfc/using-clistctrl.md)   
 [控制項](../mfc/controls-mfc.md)

