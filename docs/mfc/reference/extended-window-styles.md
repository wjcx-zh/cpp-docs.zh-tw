---
title: "延伸的視窗樣式 | Microsoft Docs"
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
  - "WS_EX_TOOLWINDOW"
  - "WS_EX_LEFTSCROLLBAR"
  - "WS_EX_RTLREADING"
  - "WS_EX_WINDOWEDGE"
  - "WS_EX_CLIENTEDGE"
  - "WS_EX_STATICEDGE"
  - "WS_EX_LTRREADING"
  - "WS_EX_DLGMODALFRAME"
  - "WS_EX_RIGHTSCROLLBAR"
  - "WS_EX_CONTROLPARENT"
  - "WS_EX_ACCEPTFILES"
  - "WS_EX_TRANSPARENT"
  - "WS_EX_RIGHT"
  - "WS_EX_APPWINDOW"
  - "WS_EX_TOPMOST"
  - "WS_EX_CONTEXTHELP"
  - "WS_EX_MDICHILD"
  - "WS_EX_LEFT"
  - "WS_EX_OVERLAPPEDWINDOW"
  - "WS_EX_PALETTEWINDOW"
  - "WS_EX_NOPARENTNOTIFY"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "延伸的視窗樣式"
  - "樣式, 視窗"
  - "WS_EX_ACCEPTFILES 常數"
  - "WS_EX_APPWINDOW 常數"
  - "WS_EX_CLIENTEDGE 常數"
  - "WS_EX_CONTEXTHELP 常數"
  - "WS_EX_CONTROLPARENT 常數"
  - "WS_EX_DLGMODALFRAME 常數"
  - "WS_EX_LEFT 常數"
  - "WS_EX_LEFTSCROLLBAR 常數"
  - "WS_EX_LTRREADING 常數"
  - "WS_EX_MDICHILD 常數"
  - "WS_EX_NOPARENTNOTIFY 常數"
  - "WS_EX_OVERLAPPEDWINDOW 常數"
  - "WS_EX_PALETTEWINDOW 常數"
  - "WS_EX_RIGHT 常數"
  - "WS_EX_RIGHTSCROLLBAR 常數"
  - "WS_EX_RTLREADING 常數"
  - "WS_EX_STATICEDGE 常數"
  - "WS_EX_TOOLWINDOW 常數"
  - "WS_EX_TOPMOST 常數"
  - "WS_EX_TRANSPARENT 常數"
  - "WS_EX_WINDOWEDGE 常數"
ms.assetid: d18e6c69-0a01-49ed-b58a-55b3802b47c1
caps.latest.revision: 14
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 延伸的視窗樣式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

-   **WS\_EX\_ACCEPTFILES** 指定視窗建立接受拖放檔案的樣式。  
  
-   當視窗為可見時，**WS\_EX\_APPWINDOW** 強制在工作列上的最上層視窗。  
  
-   **WS\_EX\_CLIENTEDGE** 指定視窗有 3D樣子 —意即有凹陷邊緣的框線。  
  
-   **WS\_EX\_CONTEXTHELP** 在視窗的標題列包含問號。  當使用者按一下問號，游標會變為有指標的問號。  如果使用者再按一下子視窗，子視窗會收到  **WM\_HELP**訊息。  
  
-   使用 TAB 鍵，**WS\_EX\_CONTROLPARENT** 允許使用者在視窗的子視窗中巡覽。  
  
-   **WS\_EX\_DLGMODALFRAME** 指定具備可以的雙框線的視窗 \(選擇性\) 建立與標題列，當您在 `dwStyle` 參數中指定 **WS\_CAPTION** 樣式旗標。  
  
-   **WS\_EX\_LAYERED** 視窗為 [層次視窗](http://msdn.microsoft.com/library/ms632599\(v=vs.85\).aspx#layered") 如果視窗有 **CS\_OWNDC** 或 **CS\_CLASSDC**， [類別樣式。](http://msdn.microsoft.com/library/ms633574\(v=vs.85\).aspx#class_styles") 則不能使用這個樣式。  不過， [!INCLUDE[win8_first](../../mfc/reference/includes/win8_first_md.md)] 支援子視窗的 **WS\_EX\_LAYERED** 樣式，之前的 Windows 版本只支援其最上層視窗的。  
  
-   **WS\_EX\_LEFT** 給視窗泛型靠左對齊屬性。  這是預設值。  
  
-   **WS\_EX\_LEFTSCROLLBAR** 在工作區左邊放置垂直捲軸。  
  
-   使用由左向右讀取 Order 屬性，**WS\_EX\_LTRREADING** 顯示視窗文字。  這是預設值。  
  
-   **WS\_EX\_MDICHILD** 建立 MDI 子視窗。  
  
-   **WS\_EX\_NOPARENTNOTIFY** 當子視窗建立或終結時，指定子視窗建立樣式不會傳送 `WM_PARENTNOTIFY` 資訊給其父視窗。  
  
-   **WS\_EX\_OVERLAPPEDWINDOW** 合併 **WS\_EX\_CLIENTEDGE** 和 **WS\_EX\_WINDOWEDGE** 樣式  
  
-   **WS\_EX\_PALETTEWINDOW** 合併 **WS\_EX\_WINDOWEDGE** 和 **WS\_EX\_TOPMOST** 樣式  
  
-   **WS\_EX\_RIGHT** 給視窗泛型靠右對齊的屬性。  這取決於視窗類別。  
  
-   **WS\_EX\_RIGHTSCROLLBAR** 在工作區右側放置垂直捲軸 \(如果有的話\)。  這是預設值。  
  
-   使用由右向左讀取 Order 屬性，**WS\_EX\_RTLREADING** 顯示視窗文字。  
  
-   **WS\_EX\_STATICEDGE** 建立有 3D 框線樣式用以項目的視窗為不接受使用者輸入。  
  
-   **WS\_EX\_TOOLWINDOW** 建立要當做浮動工具列的工具視窗。  工具視窗的標題列較一般標題列短，而且適用小字型繪製視窗標題。  當使用者按下 ALT\+TAB 時，在工作列或出現的視窗中不會顯示工具視窗。  
  
-   **WS\_EX\_TOPMOST** 指定以這種樣式產生的視窗應該被放置在最上層，即使視窗沒有活動，也要保持在最上層。  應用程式可以使用 `SetWindowPos` 成員函式來加入或移除此屬性。  
  
-   **WS\_EX\_TRANSPARENT** 指定以這種樣式產生的視窗會為透明。  也就是說，任何在這種視窗下的視窗不會被遮蔽。  只有在所有同層級視窗更新之後，使用這個樣式建立視窗會收到 `WM_PAINT` 訊息。  
  
-   **WS\_EX\_WINDOWEDGE** 指定視窗具有凸起邊緣的框線。  
  
## 請參閱  
 [MFC 使用的樣式](../../mfc/reference/styles-used-by-mfc.md)   
 [CWnd::CreateEx](../Topic/CWnd::CreateEx.md)   
 [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680)