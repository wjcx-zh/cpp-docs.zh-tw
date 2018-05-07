---
title: 樹狀目錄控制項樣式 |Microsoft 文件
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
ms.openlocfilehash: 3c0158bfc24eb86f88695b58943989fbb7cac435
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="tree-control-styles"></a>樹狀目錄控制項樣式
樹狀目錄控制項 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) 樣式管理樹狀目錄控制項的外觀。 當您建立的樹狀結構控制項時，您可以設定初始的樣式。 您可以擷取和變更之後建立的樹狀目錄控制項使用的樣式[GetWindowLong](http://msdn.microsoft.com/library/windows/desktop/ms633584)和[SetWindowLong](http://msdn.microsoft.com/library/windows/desktop/ms633591) Windows 函式，指定**GWL_STYLE**的`nIndex`參數。 如需完整的樣式清單，請參閱[樹狀檢視控制項的視窗樣式](http://msdn.microsoft.com/library/windows/desktop/bb760013)Windows SDK 中。  
  
 **TVS_HASLINES**樣式，以增強樹狀目錄控制項階層架構的圖形表示法繪製線條的子系項目連結至其對應的父項目。 這個樣式不連結階層的根目錄中的項目。 若要這樣做，您需要結合**TVS_HASLINES**和**TVS_LINESATROOT**樣式。  
  
 使用者可以展開或摺疊子項目的父項目清單，只要按兩下父項目。 樹狀目錄控制項具有**TVS_SINGLEEXPAND**樣式使展開選取的項目，而被取消選取 摺疊的項目。 如果用滑鼠按一下選取的項目，該項目已關閉，將會展開。 如果選取的項目是按一下開啟時，它會摺疊。  
  
 樹狀目錄控制項具有**TVS_HASBUTTONS**樣式將按鈕加入至每個父項的左半部。 使用者可以按一下按鈕來展開或摺疊子項目，或者按兩下父項目。 **TVS_HASBUTTONS**不將按鈕加入至階層的根目錄中的項目。 若要這樣做，您必須結合**TVS_HASLINES**， **TVS_LINESATROOT**，和**TVS_HASBUTTONS**。  
  
 **CTREECTRL**樣式可讓使用者編輯樹狀目錄控制項目標籤。 如需有關編輯標籤的詳細資訊，請參閱[樹狀目錄控制項標籤編輯](../mfc/tree-control-label-editing.md)本主題稍後。  
  
 **TVS_NOTOOLTIPS**樣式會停用的樹狀檢視控制項的自動工具提示功能。 這項功能會自動顯示工具提示，如果目前看不到完整的標題，其中包含滑鼠游標，底下項目的標題。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CTreeCtrl](../mfc/using-ctreectrl.md)   
 [控制項](../mfc/controls-mfc.md)

