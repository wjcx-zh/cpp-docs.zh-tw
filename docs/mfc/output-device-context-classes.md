---
title: "輸出(裝置內容) 類別 | Microsoft Docs"
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
  - "vc.classes.output"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "裝置內容, 類別"
  - "輸出類別"
  - "繪製類別"
  - "列印類別"
  - "螢幕輸出類別"
  - "視窗繪圖類別"
ms.assetid: 35fd6435-a38e-42c6-a3fa-cd6f39370fc3
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 輸出(裝置內容) 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這些類別會封裝視窗內可用的不同類型的裝置內容。  
  
 大部分下列類別會封裝對視窗裝置內容的控制代碼。  裝置內容是一個視窗物件，其包含繪製裝置 \(例如顯示或印表機\) 的屬性之相關資訊。  所有繪製呼叫都是透過裝置內容物件進行。  從 `CDC` 封裝衍生的其他類別會封裝特製化的裝置內容功能，包括 Windows 中繼檔。  
  
 [CDC](../mfc/reference/cdc-class.md)  
 裝置內容的基底類別。  用來直接存取整體顯示與存取不顯示的內容 \(例如印表機\)。  
  
 [CPaintDC](../mfc/reference/cpaintdc-class.md)  
 用於 `OnPaint` 視窗中的成員函式的顯示內容。  自動在建構時呼叫 `BeginPaint` ，以及在解構時呼叫 `EndPaint` 。  
  
 [CClientDC](../mfc/reference/cclientdc-class.md)  
 視窗工作區的顯示內容。  例如，用來繪製對滑鼠事件的直接回應。  
  
 [CWindowDC](../mfc/reference/cwindowdc-class.md)  
 整個視窗之顯示內容，包括用戶端和非工作區。  
  
 [CMetaFileDC](../mfc/reference/cmetafiledc-class.md)  
 Windows 中繼檔的裝置內容。  Windows 中繼檔包含可以重新執行建立影像的繪圖裝置介面 \(GDI\) 命令之序列。  對 `CMetaFileDC` 的成員函式的呼叫記錄在中繼檔中。  
  
## 相關類別  
 [CPoint](../atl-mfc-shared/reference/cpoint-class.md)  
 保持座標 \(x, y\)。  
  
 [CSize](../atl-mfc-shared/reference/csize-class.md)  
 保持距離、相對位置或配對的值。  
  
 [CRect](../atl-mfc-shared/reference/crect-class.md)  
 保持矩形區域的座標。  
  
 [CRgn](../mfc/reference/crgn-class.md)  
 封裝一個 GDI 區域，在視窗內進行縮寫、多邊形或不規則區域的作業。  與類別 `CDC` 中的裁剪成員函式一起使用。  
  
 [CRectTracker](../mfc/reference/crecttracker-class.md)  
 在使用者介面顯示及處理調整大小和移動矩形物件。  
  
 [CColorDialog](../mfc/reference/ccolordialog-class.md)  
 提供選取色彩的標準對話方塊。  
  
 [CFontDialog](../mfc/reference/cfontdialog-class.md)  
 提供選取字體的標準對話方塊。  
  
 [CPrintDialog](../mfc/reference/cprintdialog-class.md)  
 提供列印檔案的標準對話方塊。  
  
## 請參閱  
 [類別概觀](../mfc/class-library-overview.md)