---
title: "工具列控制項中使用下拉按鈕 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TBN_DROPDOWN
- TBSTYLE_EX_DRAWDDARROWS
dev_langs: C++
helpviewer_keywords:
- CToolBarCtrl class [MFC], drop-down buttons
- toolbars [MFC], drop-down buttons
- drop-down buttons in toolbars
- TBSTYLE_EX_DRAWDDARROWS
- TBN_DROPDOWN notification [MFC]
ms.assetid: b859f758-d2f6-40d9-9c26-0ff61993b9b2
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 01c09cb2bec4b466928557434767ce49948f46ae
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="using-drop-down-buttons-in-a-toolbar-control"></a>在工具列控制項中使用下拉按鈕
除了標準按鈕，工具列也可以具有下拉式按鈕。 下拉式按鈕通常會以附加向下箭號的目前狀態。  
  
> [!NOTE]
>  才會出現的附加向下箭號`TBSTYLE_EX_DRAWDDARROWS`已設定延伸的樣式。  
  
 當使用者按一下此箭頭 （或按鈕本身，如果沒有出現箭頭時），`TBN_DROPDOWN`工具列控制項的父代傳送通知訊息。 您可以處理此通知並顯示快顯功能表。Internet Explorer 的行為類似。  
  
 下列程序說明如何實作快顯功能表的下拉式工具列按鈕：  
  
### <a name="to-implement-a-drop-down-button"></a>若要實作下拉式按鈕  
  
1.  一次您`CToolBarCtrl`物件已建立、 設定`TBSTYLE_EX_DRAWDDARROWS`樣式，使用下列程式碼：  
  
     [!code-cpp[NVC_MFCControlLadenDialog#36](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_1.cpp)]  
  
2.  設定`TBSTYLE_DROPDOWN`新增任何樣式 ([InsertButton](../mfc/reference/ctoolbarctrl-class.md#insertbutton)或[AddButtons](../mfc/reference/ctoolbarctrl-class.md#addbuttons)) 或現有的 ([SetButtonInfo](../mfc/reference/ctoolbarctrl-class.md#setbuttoninfo)) 將會下拉按鈕的按鈕。 下列範例示範如何修改現有按鈕中的`CToolBarCtrl`物件：  
  
     [!code-cpp[NVC_MFCControlLadenDialog#37](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_2.cpp)]  
  
3.  新增`TBN_DROPDOWN`工具列物件的父類別處理常式。  
  
     [!code-cpp[NVC_MFCControlLadenDialog#38](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_3.cpp)]  
  
4.  在新的處理常式，會顯示適當的快顯功能表。 下列程式碼示範一種方法：  
  
     [!code-cpp[NVC_MFCControlLadenDialog#39](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_4.cpp)]  
  
## <a name="see-also"></a>請參閱  
 [使用 CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [控制項](../mfc/controls-mfc.md)

