---
title: "閒置迴圈處理 | Microsoft Docs"
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
  - "背景處理"
  - "閒置迴圈處理"
  - "閒置處理"
  - "訊息, 迴圈"
  - "MFC, 背景處理"
  - "MFC, 訊息"
  - "OnIdle 方法"
  - "PeekMessage 方法"
  - "PeekMessage 方法, elsewhere than 訊息迴圈"
  - "處理"
  - "處理, 背景"
  - "處理, 閒置迴圈期間"
  - "執行緒 [MFC], 多執行緒的替代項目"
ms.assetid: 5c7c46c1-6107-4304-895f-480983bb1e44
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 閒置迴圈處理
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

許多應用程式「在背景」執行長處理序。有時候效能考量指示使用多執行緒為這類工作。  執行緒包含額外的開發負荷，因此對於像是閒置時間工作這種 MFC 在 [OnIdle](../Topic/CWinThread::OnIdle.md) 函式中做的簡單工作並不推薦。  本文著重於閒置處理。  如需多執行續的詳細資訊，請參閱 [多執行緒主題](../parallel/multithreading-support-for-older-code-visual-cpp.md)。  
  
 一些背景處理的種類適當地在使用者與應用程式沒有互動的期間完成。  在為 Microsoft Windows 作業系統開發的應用程式中，應用程式可以藉由將長執行緒分割成許多小片段來執行閒置時間處理。  在處裡每個片段之後，應用程式使用 [PeekMessage](http://msdn.microsoft.com/library/windows/desktop/ms644943) 迴圈，產生執行控制項傳回到視窗。  
  
 本文說明這兩種對您的應用程式進行閒置處理的方式：  
  
-   在 MFC 的主要訊息迴圈使用 **PeekMessage** 。  
  
-   將另一個 **PeekMessage** 迴圈嵌入至應用程式的其他位置。  
  
##  <a name="_core_peekmessage_in_the_mfc_message_loop"></a> 在 MFC 訊息迴圈的 PeekMessage  
 在使用 MFC 開發的應用程式中，在 `CWinThread` 類別中的主要訊息迴圈包含呼叫 [PeekMessage](http://msdn.microsoft.com/library/windows/desktop/ms644943) Win32 API 的訊息迴圈。  這個迴圈也呼叫 `CWinThread` 的 `OnIdle` 成員函式在訊息之間。  應用程式可以藉由覆寫 `OnIdle` 函式處理這些閒置時間的訊息。  
  
> [!NOTE]
>  **Run**、 `OnIdle` 和其他成員函式現在是類別 `CWinThread` 的成員而不是 `CWinApp` 類別中的。  `CWinApp` 是衍生自 `CWinThread`。  
  
 如需執行閒置處理的詳細資訊，請參閱《 *MFC 參考*》中的[OnIdle](../Topic/CWinThread::OnIdle.md) 。  
  
##  <a name="_core_peekmessage_elsewhere_in_your_application"></a> 您應用程式中別處的 PeekMessage  
 在應用程式中執行閒置處理的其他方法包含內嵌訊息迴圈在自己的函式中。  這個訊息迴圈非常類似於 MFC 的主要訊息迴圈，可以在 [CWinThread::Run](../Topic/CWinThread::Run.md) 中找到。  這表示在使用 MFC 開發的應用程式中的這類迴圈必須執行許多和主要訊息迴圈相同的函式。  下列程式碼片段示範撰寫與 MFC 相容的訊息迴圈：  
  
 [!code-cpp[NVC_MFCDocView#8](../mfc/codesnippet/CPP/idle-loop-processing_1.cpp)]  
  
 這個嵌入在函式中的程式碼，只要有閒置處理要做就執行迴圈。  在該迴圈內，巢狀迴圈重複呼叫 **PeekMessage**。  只要呼叫傳回非零的值，則迴圈會呼叫 `CWinThread::PumpMessage` 執行一般訊息轉譯和分派。  雖然 `PumpMessage` 並未記載，您可以檢查 Visual C\+\+ 安裝的 \\atlmfc\\src\\mfc 目錄中的 ThrdCore.Cpp 檔案的原始程式碼。  
  
 一旦內部迴圈結束，外部迴圈便搭配一個或多個對 `OnIdle` 的呼叫執行閒置處理。  第一次呼叫是 MFC 的目的。  您可以開啟其他呼叫 `OnIdle` 完成您的背景工作。  
  
 如需執行閒置處理的詳細資訊，請參閱《 MFC 參考》中的[OnIdle](../Topic/CWinThread::OnIdle.md) 。  
  
## 請參閱  
 [一般 MFC 主題](../mfc/general-mfc-topics.md)