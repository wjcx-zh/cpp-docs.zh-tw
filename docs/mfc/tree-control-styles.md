---
title: 樹狀目錄控制項樣式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- TVS_SINGLEEXPAND
- TVS_LINESATROOT
- TVS_HASBUTTONS
- TVS_NOTOOLTIPS
- TVS_HASLINES
dev_langs:
- C++
helpviewer_keywords:
- TVS_LINESATROOT [MFC]
- styles [MFC], CTreeCtrl
- styles [MFC], tree control
- TVS_HASLINES
- TVS_SINGLEEXPAND
- CTreeCtrl class [MFC], styles
- TVS_EDITLABELS [MFC]
- TVS_NOTOOLTIPS [MFC]
- TVS_HASBUTTONS [MFC]
- tree controls [MFC], styles
ms.assetid: f43faebd-a355-479e-888a-bf0673d5e1b4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b6f3f28bbc2a69a5ad5c4fe9910d8312b236c34f
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43686494"
---
# <a name="tree-control-styles"></a>樹狀目錄控制項樣式
樹狀目錄控制項 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) 樣式管理樹狀目錄控制項的外觀的層面。 當您建立的樹狀結構控制項時，您可以設定初始的樣式。 您可以擷取，並在建立樹狀結構控制項中使用之後變更樣式[GetWindowLong](/windows/desktop/api/winuser/nf-winuser-getwindowlonga)並[SetWindowLong](/windows/desktop/api/winuser/nf-winuser-setwindowlonga) Windows 函式，指定**GWL_STYLE**的*nIndex*參數。 如需完整的樣式清單，請參閱[樹狀檢視控制項的視窗樣式](/windows/desktop/Controls/tree-view-control-window-styles)Windows SDK 中。  
  
 **TVS_HASLINES**樣式繪製線條的子系項目連結至其對應的父項目以增強樹狀目錄控制項的階層架構的圖形表示法。 這個樣式不會連結階層的根目錄中的項目。 若要這樣做，您需要結合**TVS_HASLINES**並**TVS_LINESATROOT**樣式。  
  
 使用者可以展開或摺疊子項目的父項目的清單，方法是按兩下父項目。 樹狀目錄控制項具有**TVS_SINGLEEXPAND**樣式會導致正在以展開選取的項目] 和 [摺疊正在取消選取項目。 如果滑鼠來按一下選取的項目，且該項目已關閉，它將會展開。 如果選取的項目是按一下開啟時，它將會摺疊。  
  
 樹狀目錄控制項具有**TVS_HASBUTTONS**樣式會將按鈕新增至每個父項目的左邊。 使用者可以按一下 [展開或摺疊子項目，做為替代按兩下父項目] 按鈕。 **TVS_HASBUTTONS**不會將按鈕新增至階層的根目錄中的項目。 若要這樣做，您必須結合**TVS_HASLINES**， **TVS_LINESATROOT**，並**TVS_HASBUTTONS**。  
  
 **CTREECTRL**樣式可讓使用者編輯樹狀目錄控制項目標籤。 如需有關如何編輯標籤的詳細資訊，請參閱 <<c0> [ 樹狀目錄控制項標籤編輯](../mfc/tree-control-label-editing.md)本主題稍後的。  
  
 **TVS_NOTOOLTIPS**樣式會停用樹狀檢視控制項的自動工具提示功能。 這項功能會自動顯示工具提示，如果目前看不到完整的標題，其中包含滑鼠資料指標下項目的標題。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CTreeCtrl](../mfc/using-ctreectrl.md)   
 [控制項](../mfc/controls-mfc.md)

