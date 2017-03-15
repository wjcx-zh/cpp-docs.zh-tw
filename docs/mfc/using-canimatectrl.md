---
title: "使用 CAnimateCtrl | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CAnimateCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "動畫控制項 [C++], CAnimateCtrl 類別"
  - "CAnimateCtrl 類別, 關於 CAnimateCtrl 類別"
  - "控制項 [MFC], 動畫"
ms.assetid: 696c0805-bef0-4e2e-a9e7-b37b9215b7f0
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 使用 CAnimateCtrl
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

動畫控制項，以 [CAnimateCtrl](../mfc/reference/canimatectrl-class.md)類別顯示，為顯示在播放視訊的交錯 \(AVI\) 格式的裁剪—標準 Windows 視訊與音訊格式的視窗。  AVI 裁剪是一系列的點陣圖框架，像是影片。  
  
 因為您的執行緒繼續執行，則 AVI 裁剪顯示時，使用者通常為動畫控制項是表示系統活動在長時間作業時。  例如，當系統搜尋檔案，視窗搜尋對話方塊顯示一個移動的放大鏡。  
  
 動畫控制項只能播放簡單 AVI 裁剪，也不支援音效。如需限制的完整清單，請參閱 [CAnimateCtrl](../mfc/reference/canimatectrl-class.md)。因為動畫控制項的功能是嚴格限制和隨時變更，您應使用替代例如 MCIWnd 控制項，如果您需要控制項提供多媒體播放和記錄功能。  如需 MCIWnd 控制項的詳細資訊，請參閱多媒體檔案。  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [使用動畫控制項](../mfc/using-an-animation-control.md)  
  
-   [動畫控制項傳送的告知](../mfc/notifications-sent-by-animation-controls.md)  
  
## 請參閱  
 [控制項](../mfc/controls-mfc.md)