---
title: "WINDOWPOS 結構&amp;1; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "WINDOWPOS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "WINDOWPOS 結構"
ms.assetid: a4ea7cd9-c4c2-4480-9c55-cbbff72195e1
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# WINDOWPOS 結構
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`WINDOWPOS` 結構包含視窗的大小和位置的資訊。  
  
## 語法  
  
```  
  
      typedef struct tagWINDOWPOS { /* wp */  
   HWND hwnd;  
   HWND hwndInsertAfter;  
   int x;  
   int y;  
   int cx;  
   int cy;  
   UINT flags;  
} WINDOWPOS;  
```  
  
#### 參數  
 *hwnd*  
 識別視窗。  
  
 *hwndInsertAfter*  
 識別這個視窗之後的視窗。  
  
 *x*  
 指定視窗左邊緣的位置。  
  
 *y*  
 指定視窗右邊緣的位置。  
  
 `cx`  
 指定視窗的寬度 \(以像素為單位\)。  
  
 `cy`  
 指定視窗的高度 \(以像素為單位\)。  
  
 `flags`  
 指定視窗位置選項。  這個成員可以是下列其中一個值：  
  
-   **SWP\_DRAWFRAME** 在視窗周圍繪製框架 \(定義於視窗的類別描述\)。  視窗收到 `WM_NCCALCSIZE` 訊息。  
  
-   **SWP\_FRAMECHANGED** 傳送 `WM_NCCALCSIZE` 訊息至視窗，即使未變更視窗的大小。  如果未指定這個旗標，只有在變更時視窗的大小 `WM_NCCALCSIZE` 傳送。  
  
-   **SWP\_HIDEWINDOW** 隱藏視窗。  
  
-   `SWP_NOACTIVATE` 不會啟動視窗。  
  
-   **SWP\_NOCOPYBITS** 捨棄工作區的整個內容。  如果未指定這個旗標，工作區的有效內容會儲存並複製回工作區，在視窗調整大小或重新調整位置之後。  
  
-   `SWP_NOMOVE` 保留目前位置 \(忽略 **x** 和 **y** 成員\)。  
  
-   **SWP\_NOOWNERZORDER** 不變更 Z 圖層的主控視窗的位置。  
  
-   `SWP_NOSIZE` 保留目前大小 \(忽略 **cx** 和 **cy** 成員\)。  
  
-   **SWP\_NOREDRAW** 不重繪變更。  
  
-   **SWP\_NOREPOSITION** 和 **SWP\_NOOWNERZORDER** 相同。  
  
-   **SWP\_NOSENDCHANGING** 防止視窗接收 `WM_WINDOWPOSCHANGING` 訊息。  
  
-   `SWP_NOZORDER` 保留目前定序 \(忽略 **hwndInsertAfter** 成員\)。  
  
-   **SWP\_SHOWWINDOW** 顯示視窗。  
  
## 需求  
 **Header:** winuser.h  
  
## 請參閱  
 [結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnWindowPosChanging](../Topic/CWnd::OnWindowPosChanging.md)