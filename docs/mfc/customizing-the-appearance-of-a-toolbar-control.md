---
title: 自訂工具列控制項的外觀 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- TBSTYLE_
dev_langs:
- C++
helpviewer_keywords:
- flat toolbars
- CToolBar class [MFC], styles
- transparent toolbars
- TBSTYLE_ styles [MFC]
- CToolBarCtrl class [MFC], object styles
- toolbar controls [MFC], style
ms.assetid: fd0a73db-7ad1-4fe4-889b-02c3980f49e8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 96ec459e1c956c805991f2e37d22b8260f0ffdf2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="customizing-the-appearance-of-a-toolbar-control"></a>自訂工具列控制項的外觀
類別`CToolBarCtrl`提供許多會影響外觀 （甚至是偶爾行為） 的工具列物件的樣式。 藉由設定修改工具列物件`dwCtrlStyle`參數`CToolBarCtrl::Create`(或`CToolBar::CreateEx`) 成員函式，當您第一次建立工具列控制項時。  
  
 「 3D"層面的工具列按鈕和按鈕文字的位置，會影響下列樣式：  
  
-   **TBSTYLE_FLAT**建立一般工具列，其中的工具列和按鈕皆為透明的。 按鈕文字會出現在按鈕點陣圖之下。 使用此樣式時，會自動反白顯示游標下的按鈕。  
  
-   **TBSTYLE_TRANSPARENT**建立透明工具列。 在透明的工具列中，工具列是透明，但按鈕不會。 按鈕文字會出現在按鈕點陣圖之下。  
  
-   **TBSTYLE_LIST**數位按鈕右邊的點陣圖按鈕的文字。  
  
> [!NOTE]
>  若要防止重新繪製問題**TBSTYLE_FLAT**和**TBSTYLE_TRANSPARENT**應該先設定樣式，工具列物件為可見。  
  
 下列樣式會判斷工具列是否允許使用者重新調整位置拖曳工具列物件內的個別按鈕，並卸除：  
  
-   **TBSTYLE_ALTDRAG**可讓使用者在拖曳時按住 alt 鍵來變更工具列按鈕的位置。 如果未指定此樣式，使用者必須按住 SHIFT 同時拖曳的按鈕。  
  
    > [!NOTE]
    >  `CCS_ADJUSTABLE`樣式必須指定要啟用拖曳工具列按鈕。  
  
-   **TBSTYLE_REGISTERDROP**產生**TBN_GETOBJECT**通知要求的訊息卸除目標物件，當滑鼠指標移至工具列按鈕。  
  
 其餘的樣式會影響工具列物件的視覺與非視覺層面：  
  
-   `TBSTYLE_WRAPABLE` 建立可以有多行按鈕的工具列。 工具列按鈕可以 「 包裝 」 至下一行工具列太窄，無法包含在同一行上的所有按鈕時。 文繞圖就會發生在分隔及行會界限。  
  
-   **TBSTYLE_CUSTOMERASE**產生**NM_CUSTOMDRAW**通知訊息處理時`WM_ERASEBKGND`訊息。  
  
-   `TBSTYLE_TOOLTIPS` 建立應用程式可以使用工具列中顯示按鈕的描述性文字的工具提示控制項。  
  
 Toolbar 樣式和擴充的樣式的完整清單，請參閱[工具列控制項和按鈕樣式](http://msdn.microsoft.com/library/windows/desktop/bb760439)和[工具列延伸樣式](http://msdn.microsoft.com/library/windows/desktop/bb760430)Windows SDK 中。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [控制項](../mfc/controls-mfc.md)

