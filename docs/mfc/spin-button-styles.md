---
title: "微調按鈕樣式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSpinButtonCtrl 類別, 樣式"
  - "微調按鈕控制項, 樣式"
  - "樣式, CSpinButtonCtrl"
  - "樣式, 微調按鈕控制項"
ms.assetid: fb4a7f6f-9182-47be-bccf-0728fdc5332f
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 微調按鈕樣式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

許多微調按鈕 \([CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)\) 設定為由樣式控制項的。  使用在對話方塊編輯器時， \[**屬性**\] 視窗可以設定下列樣式。  
  
-   水平或垂直**Orientation**。  控制箭號按鈕的方向。  與 `UDS_HORZ` 相關聯的樣式。  
  
-   **Alignment** 獨立，左邊或右邊。  控制微調按鈕的位置。  左右位置協同視窗旁邊的微調按鈕。  協同視窗的寬度會縮小以配合微調按鈕。  與 `UDS_ALIGNLEFT` 和 `UDS_ALIGNRIGHT` 樣式。  
  
-   **Auto Buddy** 自動選取疊置順序中的上一個視窗，協同視窗為微調按鈕。  在對話方塊樣板，這是在定位順序中的微調按鈕之前的控制項。  與 `UDS_AUTOBUDDY` 相關聯的樣式。  
  
-   目前位置變更，**Set Buddy Integer** 造成微調控制項遞增和遞減協同視窗標題。  與 `UDS_SETBUDDYINT` 相關聯的樣式。  
  
-   **No Thousands** 不插入千位分隔符號按鈕在協同視窗標題的值。  與 `UDS_NOTHOUSANDS` 相關聯的樣式。  
  
    > [!NOTE]
    >  設定樣式，如果您要使用對話資料交換 \(Dialog Data Exchange，DDX\) 從協同控制項取得整數值。  `DDX_Text` 不接受內嵌的千位分隔符號。  
  
-   在控制項之外，範圍會遞增或遞減**Wrap** 造成位置包裝」。  與 `UDS_WRAP` 相關聯的樣式。  
  
-   表示向上鍵和向下鍵時，**Arrow Keys** 造成微調按鈕遞增或遞減位置。  與 `UDS_ARROWKEYS` 相關聯的樣式。  
  
## 請參閱  
 [使用 CSpinButtonCtrl](../mfc/using-cspinbuttonctrl.md)   
 [控制項](../mfc/controls-mfc.md)