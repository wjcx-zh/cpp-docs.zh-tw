---
title: 工具列控制項中使用下拉按鈕 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- TBN_DROPDOWN
- TBSTYLE_EX_DRAWDDARROWS
dev_langs:
- C++
helpviewer_keywords:
- CToolBarCtrl class [MFC], drop-down buttons
- toolbars [MFC], drop-down buttons
- drop-down buttons in toolbars
- TBSTYLE_EX_DRAWDDARROWS
- TBN_DROPDOWN notification [MFC]
ms.assetid: b859f758-d2f6-40d9-9c26-0ff61993b9b2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1e76db0bacd7984c97fd8e2696b3543f6e9bf66b
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2018
ms.locfileid: "36953239"
---
# <a name="using-drop-down-buttons-in-a-toolbar-control"></a>在工具列控制項中使用下拉按鈕
除了標準按鈕，工具列也可以具有下拉式按鈕。 下拉式按鈕通常會以附加向下箭號的目前狀態。  
  
> [!NOTE]
>  只有當已設定延伸樣式 TBSTYLE_EX_DRAWDDARROWS，會出現附加向下箭號。  
  
 當使用者按一下此箭頭 （或按鈕本身，如果沒有出現箭頭時） 時，TBN_DROPDOWN 告知訊息會傳送至工具列控制項的父代。 您可以處理此通知並顯示快顯功能表。Internet Explorer 的行為類似。  
  
 下列程序說明如何實作快顯功能表的下拉式工具列按鈕：  
  
### <a name="to-implement-a-drop-down-button"></a>若要實作下拉式按鈕  
  
1.  一次您`CToolBarCtrl`物件已建立、 設定 TBSTYLE_EX_DRAWDDARROWS 樣式，使用下列程式碼：  
  
     [!code-cpp[NVC_MFCControlLadenDialog#36](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_1.cpp)]  
  
2.  讓新設定 TBSTYLE_DROPDOWN 樣式 ([InsertButton](../mfc/reference/ctoolbarctrl-class.md#insertbutton)或[AddButtons](../mfc/reference/ctoolbarctrl-class.md#addbuttons)) 或現有的 ([SetButtonInfo](../mfc/reference/ctoolbarctrl-class.md#setbuttoninfo)) 將會下拉按鈕的按鈕。 下列範例示範如何修改現有按鈕中的`CToolBarCtrl`物件：  
  
     [!code-cpp[NVC_MFCControlLadenDialog#37](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_2.cpp)]  
  
3.  TBN_DROPDOWN 處理常式加入工具列物件的父類別。  
  
     [!code-cpp[NVC_MFCControlLadenDialog#38](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_3.cpp)]  
  
4.  在新的處理常式，會顯示適當的快顯功能表。 下列程式碼示範一種方法：  
  
     [!code-cpp[NVC_MFCControlLadenDialog#39](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_4.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [使用 CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [控制項](../mfc/controls-mfc.md)

