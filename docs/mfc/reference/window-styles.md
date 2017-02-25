---
title: "視窗樣式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "WS_MINIMIZEBOX"
  - "WS_SIZEBOX"
  - "WS_CLIPCHILDREN"
  - "WS_TILED"
  - "WS_GROUP"
  - "WS_VSCROLL"
  - "WS_CHILD"
  - "WS_TABSTOP"
  - "WS_HSCROLL"
  - "WS_THICKFRAME"
  - "WS_DISABLED"
  - "WS_POPUP"
  - "WS_ICONIC"
  - "WS_MAXIMIZE"
  - "WS_VISIBLE"
  - "WS_POPUPWINDOW"
  - "WS_TILEDWINDOW"
  - "WS_DLGFRAME"
  - "WS_MINIMIZE"
  - "WS_CAPTION"
  - "WS_OVERLAPPED"
  - "WS_BORDER"
  - "WS_MAXIMIZEBOX"
  - "WS_OVERLAPPEDWINDOW"
  - "WS_SYSMENU"
  - "WS_CHILDWINDOW"
  - "WS_CLIPSIBLINGS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "樣式, 視窗"
  - "視窗樣式"
  - "視窗樣式, 在 MFC 中"
  - "WS_BORDER 常數"
  - "WS_CAPTION 常數"
  - "WS_CHILD 常數"
  - "WS_CHILDWINDOW 常數"
  - "WS_CLIPCHILDREN 常數"
  - "WS_CLIPSIBLINGS 常數"
  - "WS_DISABLED 常數"
  - "WS_DLGFRAME 常數"
  - "WS_GROUP 常數"
  - "WS_HSCROLL 常數"
  - "WS_ICONIC 常數"
  - "WS_MAXIMIZE 常數"
  - "WS_MAXIMIZEBOX 常數"
  - "WS_MINIMIZE 常數"
  - "WS_MINIMIZEBOX 常數"
  - "WS_OVERLAPPED 常數"
  - "WS_OVERLAPPEDWINDOW 常數"
  - "WS_POPUP 常數"
  - "WS_POPUPWINDOW 常數"
  - "WS_SIZEBOX 常數"
  - "WS_SYSMENU 常數"
  - "WS_TABSTOP 常數"
  - "WS_THICKFRAME 常數"
  - "WS_TILED 常數"
  - "WS_TILEDWINDOW 常數"
  - "WS_VISIBLE 常數"
  - "WS_VSCROLL 常數"
ms.assetid: c85ffbe4-f4ff-4227-917a-48ec4a411842
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# 視窗樣式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

-   `WS_BORDER`：建立具有邊框的視窗。  
  
-   **WS\_CAPTION** 建立具有標題列的視窗 \(隱含 `WS_BORDER` 樣式\)。  不可與 **WS\_DLGFRAME** 樣式一起使用。  
  
-   **WS\_CHILD** 建立子視窗。  不可與 `WS_POPUP` 樣式一起使用。  
  
-   **WS\_CHILDWINDOW** 和 **WS\_CHILD** 樣式相同。  
  
-   **WS\_CLIPCHILDREN** 在您於父視窗內繪圖時，排除子視窗佔用的區域。  在建立父視窗時使用。  
  
-   **WS\_CLIPSIBLINGS** 相對於彼此裁剪子視窗；也就是說，當特定子視窗收到繪製訊息時，**WS\_CLIPSIBLINGS** 樣式會將所有其他重疊的子視窗，從要更新的子視窗區域中裁剪掉。\(如果未指定 **WS\_CLIPSIBLINGS**，而且子視窗重疊，當您在子視窗工作區中繪製時，可能會在鄰近子視窗的工作區中繪製\)。只用於 **WS\_CHILD** 樣式。  
  
-   **WS\_DISABLED** 建立一開始即停用的視窗。  
  
-   **WS\_DLGFRAME** 建立有雙框線，但沒有標題的視窗。  
  
-   **WS\_GROUP** 指定控制項群組的第一個控制項，可讓使用者使用方向鍵從一個控制項移至下一個。  在第一個控制項之後，以 **WS\_GROUP** 樣式 **FALSE** 定義的所有控制項屬於相同群組。  包含 **WS\_GROUP** 樣式的下一個控制項會開始下一個群組 \(也就是，一個群組會在下一個群組開始之處結束\)。  
  
-   **WS\_HSCROLL** 建立有水平捲軸的視窗。  
  
-   **WS\_ICONIC** 建立一開始即最小化的視窗。  與 **WS\_MINIMIZE** 樣式相同。  
  
-   **WS\_MAXIMIZE** 建立最大大小的視窗。  
  
-   **WS\_MAXIMIZEBOX** 建立有最大化按鈕的視窗。  
  
-   **WS\_MINIMIZE** 建立一開始即最小化的視窗。  只用於 **WS\_OVERLAPPED** 樣式。  
  
-   **WS\_MINIMIZEBOX** 建立有最小化按鈕的視窗。  
  
-   **WS\_OVERLAPPED** 建立重疊的視窗。  重疊視窗通常具有標題和框線。  
  
-   **WS\_OVERLAPPEDWINDOW** 建立有 **WS\_OVERLAPPED**、**WS\_CAPTION**、**WS\_SYSMENU**、**WS\_THICKFRAME**、**WS\_MINIMIZEBOX** 和 **WS\_MAXIMIZEBOX** 樣式的重疊的視窗。  
  
-   `WS_POPUP`：建立快顯視窗。  不可與 **WS\_CHILD** 樣式一起使用。  
  
-   **WS\_POPUPWINDOW** 建立有 `WS_BORDER`、`WS_POPUP` 和 **WS\_SYSMENU** 樣式的快顯視窗。  **WS\_CAPTION** 樣式必須與 **WS\_POPUPWINDOW** 樣式結合，才能讓控制功能表顯示。  
  
-   **WS\_SIZEBOX**：建立具有縮放邊框 \(Sizing Border\) 的視窗。  與 **WS\_THICKFRAME** 樣式相同。  
  
-   **WS\_SYSMENU**：建立在標題列中擁有控制功能表方塊的視窗。  只用於具有標題列的視窗。  
  
-   **WS\_TABSTOP** 在任何數目的控制項中指定一個使用者可以使用 TAB 鍵移動的控制項。  TAB 鍵會將使用者移至 **WS\_TABSTOP** 樣式指定的下一個控制項。  
  
-   **WS\_THICKFRAME**：建立擁有可以調整視窗大小粗框架的視窗。  
  
-   **WS\_TILED** 建立重疊的視窗。  重疊視窗具有標題列和框線。  與 **WS\_OVERLAPPED** 樣式相同。  
  
-   **WS\_TILEDWINDOW** 建立有 **WS\_OVERLAPPED**、**WS\_CAPTION**、**WS\_SYSMENU**、**WS\_THICKFRAME**、**WS\_MINIMIZEBOX** 和 **WS\_MAXIMIZEBOX** 樣式的重疊的視窗。  與 **WS\_OVERLAPPEDWINDOW** 樣式相同。  
  
-   **WS\_VISIBLE** 建立一開始即可見的視窗。  
  
-   **WS\_VSCROLL** 建立有垂直捲軸的視窗。  
  
## 請參閱  
 [MFC 使用的樣式](../../mfc/reference/styles-used-by-mfc.md)   
 [CWnd::Create](../Topic/CWnd::Create.md)   
 [CWnd::CreateEx](../Topic/CWnd::CreateEx.md)   
 [CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679)