---
title: 樹狀目錄控制項標籤編輯 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- editing tree control labels
- CTreeCtrl class [MFC], editing labels
- label editing in CTreeCtrl class [MFC]
- tree controls [MFC], label editing
ms.assetid: 6cde2ac3-43ee-468f-bac2-cf1a228ad32d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7f9ba5360ddce81061bf73839e1700fed57c9fa7
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43210399"
---
# <a name="tree-control-label-editing"></a>樹狀目錄控制項標籤編輯
使用者可以直接編輯之標籤的樹狀結構控制項中的項目 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md))，其**CTREECTRL**樣式。 按一下具有焦點的項目標籤，使用者就可以開始進行編輯。 應用程式會開始藉由編輯[EditLabel](../mfc/reference/ctreectrl-class.md#editlabel)成員函式。 當編輯開始和取消或完成時，樹狀目錄控制項會傳送通知。 當編輯完成時，您可以視狀況負責更新項目的標籤。  
  
 開始編輯標籤時，樹狀目錄控制項會傳送[TVN_BEGINLABELEDIT](/windows/desktop/Controls/tvn-beginlabeledit)通知訊息。 藉由處理這個通知，您可以允許編輯某些標籤並防止編輯其他標籤。 傳回 0 表示允許編輯，傳回非零值表示無法編輯。  
  
 樹狀目錄控制項標籤編輯取消或完成，當傳送[TVN_ENDLABELEDIT](/windows/desktop/Controls/tvn-endlabeledit)通知訊息。 *LParam*參數是位址[2&AMP;GT;NMTVDISPINFO&AMP;LT;2](/windows/desktop/api/commctrl/ns-commctrl-tagtvdispinfoa)結構。 **項目**成員[TVITEM](/windows/desktop/api/commctrl/ns-commctrl-tagtvitema)結構，以識別項目，並包含編輯的文字。 在驗證編輯字串後，您可以視狀況負責更新項目的標籤。 *PszText*隸屬`TV_ITEM`如果取消編輯，則為 0。  
  
 在標籤編輯期間，通常以回應[TVN_BEGINLABELEDIT](/windows/desktop/Controls/tvn-beginlabeledit)通知訊息，您可以編輯控制項標籤編輯方法是使用用來取得指標[GetEditControl](../mfc/reference/ctreectrl-class.md#geteditcontrol)成員函式。 您可以呼叫編輯控制項的[SetLimitText](../mfc/reference/cedit-class.md#setlimittext)成員函式，以限制使用者可以輸入的文字或子類別化編輯控制項，以攔截並捨棄無效的字元。 不過請注意，編輯控制項，只顯示*之後* **TVN_BEGINLABELEDIT**傳送。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CTreeCtrl](../mfc/using-ctreectrl.md)   
 [控制項](../mfc/controls-mfc.md)

