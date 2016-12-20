---
title: "靜態樣式 | Microsoft Docs"
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
  - "SS_SUNKEN"
  - "SS_CENTER"
  - "SS_ENHMETAFILE"
  - "SS_RIGHT"
  - "SS_BLACKRECT"
  - "SS_LEFTNOWORDWRAP"
  - "SS_GRAYFRAME"
  - "SS_USERITEM"
  - "SS_GRAYRECT"
  - "SS_WHITEFRAME"
  - "SS_ETCHEDFRAME"
  - "SS_ETCHEDVERT"
  - "SS_WHITERECT"
  - "SS_PATHELLIPSIS"
  - "SS_WORDELLIPSIS"
  - "SS_NOPREFIX"
  - "SS_BITMAP"
  - "SS_SIMPLE"
  - "SS_CENTERIMAGE"
  - "SS_BLACKFRAME"
  - "SS_OWNERDRAW"
  - "SS_REALSIZEIMAGE"
  - "SS_RIGHTJUST"
  - "SS_ICON"
  - "SS_NOTIFY"
  - "SS_ETCHEDHORZ"
  - "SS_LEFT"
  - "SS_ENDELLIPSIS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SS_BITMAP 常數"
  - "SS_BLACKFRAME 常數"
  - "SS_BLACKRECT 常數"
  - "SS_CENTER 常數"
  - "SS_CENTERIMAGE 常數"
  - "SS_ENDELLIPSIS 常數"
  - "SS_ENHMETAFILE 常數"
  - "SS_ETCHEDFRAME 常數"
  - "SS_ETCHEDHORZ 常數"
  - "SS_ETCHEDVERT 常數"
  - "SS_GRAYFRAME 常數"
  - "SS_GRAYRECT 常數"
  - "SS_ICON 常數"
  - "SS_LEFT 常數"
  - "SS_LEFTNOWORDWRAP 常數"
  - "SS_NOPREFIX 常數"
  - "SS_NOTIFY 常數"
  - "SS_OWNERDRAW 常數"
  - "SS_PATHELLIPSIS 常數"
  - "SS_REALSIZEIMAGE 常數"
  - "SS_RIGHT 常數"
  - "SS_RIGHTJUST 常數"
  - "SS_SIMPLE 常數"
  - "SS_SUNKEN 常數"
  - "SS_USERITEM 常數"
  - "SS_WHITEFRAME 常數"
  - "SS_WHITERECT 常數"
  - "SS_WORDELLIPSIS 常數"
  - "靜態樣式"
ms.assetid: a1114548-fc6d-491d-8c46-21d11b8574f5
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 靜態樣式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

-   **SS\_BITMAP** 在靜態控制項指定點陣圖中顯示。  指定文字是資源檔 \(不是檔名\) 定義於其他地方的點陣圖名稱。  這個樣式忽略 nWidth 和 nHeight 參數;控制項會自動調整大小以容納點陣圖。  
  
-   **SS\_BLACKFRAME** 指定以方塊繪製色彩的框架和視窗框架相同。  預設為黑色。  
  
-   **SS\_BLACKRECT** 指定矩形則會以用來繪製視窗框架的色彩。  預設為黑色。  
  
-   **SS\_CENTER** 所設定簡單的矩形並顯示矩形中心的特定文字。  在顯示之前，文字格式化。  將延伸超過行尾的文字自動換行至下置行的開頭。  
  
-   **SS\_CENTERIMAGE** 指定，否則，如果點陣圖或圖示小於靜態控制項的工作區，工作區的其餘部分填滿像素的色彩點陣圖或圖示的左上角。  如果靜態控制項包含單行文字，文字垂直顯示在控制項工作區的中央。  
  
-   **SS\_ENDELLIPSIS** 和 **SS\_PATHELLIPSIS** 用橢圓形在必要時，取代一部分的特定字串，因此，結果符合指定的矩形。  
  
     您可以指定 **SS\_END\_ELLIPSIS** 取代字元在字串結尾或 **SS\_PATHELLIPSIS** 在字串中的字元取代。  如果字串包含反斜線 \(\\\) 字元， **SS\_PATHELLIPSIS** 盡可能保留相同的許多在最後一個反斜線之後的文字。  
  
-   **SS\_ENHMETAFILE** 在靜態控制項指定顯示加強圖元文件。  指定文字是中圖元文件的名稱。  加強型圖元文件靜態控制項有固定的大小;圖元文件將縮放至適合靜態控制項的工作區。  
  
-   使用 **EDGE\_ETCHED** 框線樣式，**SS\_ETCHEDFRAME** 繪製靜態控制項的框架。  
  
-   **SS\_ETCHEDHORZ** 繪製框線，以及靜態控制項的下邊緣使用 **EDGE\_ETCHED** 的邊緣樣式。  
  
-   使用 EDGE\_ETCHED 框線樣式，**SS\_ETCHEDVERT** 繪製靜態控制項的左右邊緣。  
  
-   **SS\_GRAYFRAME** 指定有框架以方塊繪製色彩和螢幕背景 \(桌上型電腦\) 相同。  預設為灰色。  
  
-   **SS\_GRAYRECT** 指定矩形則會以用來的色彩填滿螢幕背景。  預設為灰色。  
  
-   **SS\_ICON** 將對話方塊所顯示的圖示。  指定文字是資源檔 \(不是檔名\) 定義於其他地方圖標的名稱。  `nWidth` 和 `nHeight` 參數已忽略;圖示自動調整大小。  
  
-   **SS\_LEFT** 所設定簡單的矩形並在矩形的特定文字清除左邊。  在顯示之前，文字格式化。  將延伸超過行尾的文字自動換行至下個左對齊線的開頭。  
  
-   **SS\_LEFTNOWORDWRAP** 所設定簡單的矩形並在矩形的特定文字清除左邊。  選項展開，不過，文字不換行。  文字超出行尾之延伸裁剪。  
  
-   **SS\_NOPREFIX**，除非樣式指定， Windows 會說明在控制項中的所有連字號 \(&\) 字元為快速鍵前置字元。  在這個案例中，移除連字號，並在字串中的下一個字元會加上底線。  如果靜態控制項是含有這個功能不會想要的文字， **SS\_NOPREFIX** 可能會增加。  這個靜態控制項樣式可能包含有任何已定義的靜態控制項。  使用位元 OR 運算子，您可以結合 **SS\_NOPREFIX** 與其他樣式。  這是最常用的，當在對話方塊中的靜態控制項可能包含連字號需要顯示的檔名或其他字串。  
  
-   當使用者按一下或按兩下控制項時，**SS\_NOTIFY** 傳送父視窗 **STN\_CLICKED**， **STN\_DBLCLK**和 **STN\_DISABLE**和 **STN\_ENABLE** 通知訊息。  
  
-   **SS\_OWNERDRAW** 指定靜態控制項的擁有者負責繪製控制項。  主控視窗收到 `WM_DRAWITEM` 訊息，每當控制項需要繪製。  
  
-   **SS\_REALSIZEIMAGE** 防止有 **SS\_ICON** 或 **SS\_BITMAP** 樣式\) 的靜態圖示或點陣圖控制項 \(即靜態控制項調整大小時，載入或繪製。  如果圖示或點陣圖大於目的區域，影像會裁剪。  
  
-   **SS\_LEFTNOWORDWRAP** 所設定簡單的矩形並在矩形的特定文字清除右邊。  在顯示之前，文字格式化。  將延伸超過行尾的文字自動換行至下個右對齊線的開頭。  
  
-   **SS\_RIGHTJUST** 指定靜態控制項的右下角有 **SS\_BITMAP** 或 **SS\_ICON** 樣式的是，保持在控制項調整大小時。  只調整上方和左邊容納新的點陣圖或圖示。  
  
-   **SS\_SIMPLE** 所設定簡單的矩形並顯示單行文字在矩形中清除的。  文字行不能有任何縮短或修改。\(控制項的父視窗或對話方塊無法處理 `WM_CTLCOLOR` 訊息\)。  
  
-   **SS\_SUNKEN** 在靜態控制項周圍繪製一個半下凹框線。  
  
-   **SS\_USERITEM** 指定使用者定義的項目。  
  
-   **SS\_WHITEFRAME** 指定有框架以方塊繪製色彩和視窗背景相同。  預設值是白色。  
  
-   **SS\_WHITERECT** 指定矩形則會以用來的色彩填滿視窗背景。  預設值是白色。  
  
-   **SS\_WORDELLIPSIS** 截斷不符合的文字並將橢圓形。  
  
## 請參閱  
 [MFC 使用的樣式](../../mfc/reference/styles-used-by-mfc.md)   
 [CStatic::Create](../Topic/CStatic::Create.md)   
 [DrawEdge](http://msdn.microsoft.com/library/windows/desktop/dd162477)   
 [Static Control Styles](http://msdn.microsoft.com/library/windows/desktop/bb760773)