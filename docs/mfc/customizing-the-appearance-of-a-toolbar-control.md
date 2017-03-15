---
title: "自訂工具列控制項的外觀 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TBSTYLE_"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CToolBar 類別, 樣式"
  - "CToolBarCtrl 類別, 物件樣式"
  - "平面工具列"
  - "TBSTYLE_ 樣式"
  - "工具列控制項 [MFC], 樣式"
  - "透明工具列"
ms.assetid: fd0a73db-7ad1-4fe4-889b-02c3980f49e8
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 自訂工具列控制項的外觀
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`CToolBarCtrl` 類別提供會影響外觀的許多樣式 \(而且，偶爾，行為\) 工具列物件。  藉由將 `CToolBarCtrl::Create` \(或 `CToolBar::CreateEx`\) 成員函式的 `dwCtrlStyle` 參數修改工具列物件，也就是說，當您先建立工具列控制項時。  
  
 下列樣式會影響工具列按鈕的「3D」方面和按鈕文字的位置:  
  
-   **TBSTYLE\_FLAT** 建立工具列和按鈕透明平面工具列。  按鈕文字顯示在按鈕點陣圖下。  當使用這個樣式，游標下方的按鈕自動反白顯示。  
  
-   **TBSTYLE\_TRANSPARENT** 建立透明的工具列。  在透明工具列，工具列透明，但按鈕不是。  按鈕文字顯示在按鈕點陣圖下。  
  
-   **TBSTYLE\_LIST** 位在按鈕點陣圖右邊的文字。  
  
> [!NOTE]
>  若要防止請重新繪製問題， **TBSTYLE\_FLAT** ，應該設定 **TBSTYLE\_TRANSPARENT** 樣式，工具列物件為可見的。  
  
 下列樣式決定工具列使用拖放方式，是否允許使用者重新調整在工具列物件內的個別按鈕:  
  
-   **TBSTYLE\_ALTDRAG** 允許使用者將它變更工具列按鈕的位置時，按住 ALT 鍵時。  如果樣式未指定，則使用者必須按住 Shift 鍵，同時拖曳按鈕時。  
  
    > [!NOTE]
    >  必須指定 `CCS_ADJUSTABLE` 樣式讓工具列按鈕拖曳。  
  
-   表示當滑鼠指標經過工具列按鈕時，會產生**TBSTYLE\_REGISTERDROP TBN\_GETOBJECT** 通知訊息要求置放目標物件。  
  
 其餘的樣式會影響視覺物件，而工具列的隱藏式方面物件:  
  
-   `TBSTYLE_WRAPABLE` 建立可能有按鈕多行的工具列。  當工具列變得太小而無法包含在同一行時，所有按鈕的工具列按鈕所公開的可」到下一行。  包裝在分隔和 nongroup 界限時發生。  
  
-   **TBSTYLE\_CUSTOMERASE** 產生 **NM\_CUSTOMDRAW** 通知訊息，在處理 `WM_ERASEBKGND` 訊息。  
  
-   建立`TBSTYLE_TOOLTIPS` 的應用程式可以使用顯示按鈕的描述性文字在工具列上的工具提示控制項。  
  
 如需工具列樣式和延伸樣式完整清單，請參閱 [工具列控制項和按鈕樣式](http://msdn.microsoft.com/library/windows/desktop/bb760439) 和 [工具列的延伸樣式。](http://msdn.microsoft.com/library/windows/desktop/bb760430) 在 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]。  
  
## 請參閱  
 [使用 CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [控制項](../mfc/controls-mfc.md)