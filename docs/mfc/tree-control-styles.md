---
title: "樹狀目錄控制項樣式 | Microsoft Docs"
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
  - "TVS_SINGLEEXPAND"
  - "TVS_LINESATROOT"
  - "TVS_HASBUTTONS"
  - "TVS_NOTOOLTIPS"
  - "TVS_HASLINES"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTreeCtrl 類別, 樣式"
  - "樣式, CTreeCtrl"
  - "樣式, 樹狀結構控制項"
  - "樹狀目錄控制項, 樣式"
  - "TVS_EDITLABELS"
  - "TVS_HASBUTTONS"
  - "TVS_HASLINES"
  - "TVS_LINESATROOT"
  - "TVS_NOTOOLTIPS"
  - "TVS_SINGLEEXPAND"
ms.assetid: f43faebd-a355-479e-888a-bf0673d5e1b4
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 樹狀目錄控制項樣式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

樹狀目錄控制項 \([CTreeCtrl](../mfc/reference/ctreectrl-class.md)\) 樣式控制樹狀目錄控制項的外觀。  將初始樣式時建立樹狀目錄控制項。  使用 [GetWindowLong](http://msdn.microsoft.com/library/windows/desktop/ms633584) 和 [SetWindowLong](http://msdn.microsoft.com/library/windows/desktop/ms633591) Windows 函式，您可以在建立樹狀目錄控制項之後擷取和變更樣式，指定 **GWL\_STYLE** 為 `nIndex` 參數。  如需樣式的完整清單，請參閱 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]的 [樹狀檢視控制項的視窗樣式。](http://msdn.microsoft.com/library/windows/desktop/bb760013) 。  
  
 **TVS\_HASLINES** 樣式會繪製與其對應的父項目連結子項目的行提高樹狀目錄控制項分級的圖形表示。  這個樣式不連結項目在階層架構的根。  若要這麼做，您需要合併 **TVS\_HASLINES** 和 **TVS\_LINESATROOT** 樣式。  
  
 使用者可以按兩下父項目已展開或摺疊子項目父項目的清單。  有 **TVS\_SINGLEEXPAND** 樣式的樹狀目錄控制項就會在已選取項目的展開和是項目未選取的損毀。  如果是使用滑鼠按一下選取的項目，且該項目已關閉，它將會展開。  如果選取的項目按一下，當是開啟的，則會摺疊。  
  
 有 **TVS\_HASBUTTONS** 樣式的樹狀目錄控制項將按鈕加入至每個父項目的左邊。  使用者可以按一下按鈕展開或摺疊子項目做為替代按兩下父項目。  **TVS\_HASBUTTONS** 不將按鈕加入至項目在階層架構的根。  若要這麼做，就必須將 **TVS\_HASLINES**和 **TVS\_LINESATROOT**和 **TVS\_HASBUTTONS**。  
  
 **TVS\_EDITLABELS** 模式可讓使用者編輯樹狀 Label 控制項項目。  如需編輯標籤的詳細資訊，請參閱本主題稍後的 [樹狀目錄控制項編輯標籤。](../mfc/tree-control-label-editing.md) 。  
  
 **TVS\_NOTOOLTIPS** 樣式停用樹狀檢視控制項自動工具提示功能。  如果整個標題中目前不可見的，則這個功能會自動顯示工具提示，其中包含項目的標題在滑鼠游標下。  
  
## 請參閱  
 [使用 CTreeCtrl](../mfc/using-ctreectrl.md)   
 [控制項](../mfc/controls-mfc.md)