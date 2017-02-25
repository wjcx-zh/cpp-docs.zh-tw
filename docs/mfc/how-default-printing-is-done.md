---
title: "如何完成預設列印 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "預設列印"
  - "預設, 列印"
  - "列印 [MFC], 預設"
ms.assetid: 0f698459-0fc9-4d43-97da-29cf0f65daa2
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 如何完成預設列印
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文說明Windows的預設列印處理序是 MFC 架構。  
  
 在 MFC 應用程式，其檢視類別具有一個名稱為 `OnDraw`、包含任何繪圖程式碼的成員函式。  `OnDraw` 將指向 [CDC](../mfc/reference/cdc-class.md) 物件的指標做為參數。  `CDC` 物件表示裝置內容接收由 `OnDraw`所產生的影像。  當顯示文件的視窗收到 [WM\_PAINT](http://msdn.microsoft.com/library/windows/desktop/dd145213) 訊息時，架構會呼叫 `OnDraw` 並將它繪製至畫面 \( [CPaintDC](../mfc/reference/cpaintdc-class.md) 物件的裝置內容，是特定的\)。  因此， `OnDraw` 要輸出至螢幕。  
  
 在 Windows 程式設計中，將輸出傳送至印表機非常類似於傳送輸出至螢幕。  這是因為 Windows 繪圖裝置介面 \(Graphics Device \(GDI\) 無關硬體。  使用適當的裝置內容，可以使用相同的 GDI 函式為螢幕顯示和列印。  如果 `OnDraw` 所接收的 `CDC` 物件代表印表機， `OnDraw` 輸出到印表機。  
  
 這說明 MFC 應用程式如何執行簡單的列印，而不需要在您部分的額外工作。  架構負責顯示列印對話方塊並建立印表機的裝置內容。  當使用者從檔案功能表選取列印命令時，這個檢視會傳遞這個裝置內容至 `OnDraw`，其描製文件於印表機。  
  
 不過，在列印和螢幕顯示之間有一些重大差異。  您在列印時必須將文件分割成不同頁面並一次顯示一個，而不是在視窗中顯示任何可顯示的部分。  做為推算，您必須知道文件大小 \(不論是字母大小、法定規格或信封\)。  您可能需要不同的列印方向，例如橫向和縱向模式。  MFC 程式庫無法預測應用程式如何處理這些問題，因此，它提供了通訊協定來加強這些功能。  
  
 該通訊協定說明於文件 [多頁文件](../mfc/multipage-documents.md)中。  
  
## 請參閱  
 [列印](../mfc/printing.md)