---
title: "WINDOWPLACEMENT 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "WINDOWPLACEMENT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "WINDOWPLACEMENT 結構"
ms.assetid: ea7d61f6-eb57-478e-9b08-7c1d07091aa8
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# WINDOWPLACEMENT 結構
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`WINDOWPLACEMENT` 結構包含視窗位置資訊在螢幕**.**的  
  
## 語法  
  
```  
  
      typedef struct tagWINDOWPLACEMENT {     /* wndpl */  
   UINT length;  
   UINT flags;  
   UINT showCmd;  
   POINT ptMinPosition;  
   POINT ptMaxPosition;  
   RECT rcNormalPosition;  
} WINDOWPLACEMENT;  
```  
  
#### 參數  
 *length*  
 以位元組為單位\)，指定這個結構的長度，**.**  
  
 `flags`  
 指定控制項最小化的視窗位置和方法視窗還原的旗標。  這個成員可以是下列旗標之一或兩個:  
  
-   **WPF\_SETMINPOSITION** 指定最小化視窗的 X 和 Y 位置可以是指定的**.**必須指定這個旗標座標是否在 **ptMinPosition** 成員設定。  
  
-   **WPF\_RESTORETOMAXIMIZED** 指定還原的視窗會最大化，不論它是否為最大化，在最小化之前。  只有在下次視窗還原，這個設定是否有效。  它不會變更預設復原行為。  只有在 **SW\_SHOWMINIMIZED** 值為 **showCmd** 成員時，指定這個旗標才有效。  
  
 *showCmd*  
 指定視窗目前的顯示狀態。  這個成員可以是下列其中一個值:  
  
-   **SW\_HIDE** 隱藏視窗並將啟動到另一個視窗。  
  
-   指定**SW\_MINIMIZE** 最小化的視窗並啟動系統中清單的最上層視窗。  
  
-   **SW\_RESTORE** 啟動並顯示視窗。  如果視窗最小化或最大化，視窗還原成其原始大小和位置 \(和 **SW\_SHOWNORMAL**相同\)。  
  
-   **SW\_SHOW** 啟動視窗並顯示其目前的大小和位置。  
  
-   **SW\_SHOWMAXIMIZED** 啟動視窗並將它顯示為最大化的視窗。  
  
-   **SW\_SHOWMINIMIZED** 啟動視窗並將它顯示為圖示。  
  
-   **SW\_SHOWMINNOACTIVE** 視窗顯示為圖示。  作用中目前作用中的視窗。  
  
-   **SW\_SHOWNA** 處於目前狀態的顯示視窗。  作用中目前作用中的視窗。  
  
-   **SW\_SHOWNOACTIVATE** 顯示其重新調整大小和位置的視窗。  作用中目前作用中的視窗。  
  
-   **SW\_SHOWNORMAL** 啟動並顯示視窗。  如果視窗最小化或最大化，視窗還原成其原始大小和位置 \(和 **SW\_RESTORE**相同\)。  
  
 *ptMinPosition*  
 當視窗最小化時，指定視窗左上角的位置。  
  
 `ptMaxPosition`  
 當視窗最大化時，指定視窗左上角的位置。  
  
 *rcNormalPosition*  
 指定視窗的座標，則視窗在 Normal \(已還原\) 位置。  
  
## 需求  
 **Header:** 中  
  
## 請參閱  
 [結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::SetWindowPlacement](../Topic/CWnd::SetWindowPlacement.md)