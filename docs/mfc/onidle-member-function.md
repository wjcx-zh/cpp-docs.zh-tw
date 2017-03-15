---
title: "OnIdle 成員函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "OnIdle"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CWinApp 類別, OnIdle 方法"
  - "閒置迴圈處理"
  - "訊息處理, OnIdle 方法"
  - "OnIdle 方法"
  - "處理訊息"
ms.assetid: 51adc874-0075-4f76-be1c-79283f46c10b
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# OnIdle 成員函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當視窗訊息未處理時，架構會呼叫 [CWinApp](../mfc/reference/cwinapp-class.md) 成員函式 [OnIdle](../Topic/CWinApp::OnIdle.md) \(說明 MFC 程式庫參考\)。  
  
 覆寫會執行背景工作的 `OnIdle` 。  預設版本更新使用者介面物件狀態 \(例如工具列按鈕並執行架構建立的暫存物件清除其作業期間。  下圖說明訊息迴圈如何呼叫 `OnIdle` ，而不在佇列中的訊息。  
  
 ![訊息迴圈處理序](../mfc/media/vc387c1.png "vc387C1")  
訊息迴圈  
  
 如需功能的詳細資訊可以在閒置迴圈可以這麼做，請參閱 [閒置迴圈處理。](../mfc/idle-loop-processing.md)。  
  
## 請參閱  
 [CWinApp：應用程式類別](../mfc/cwinapp-the-application-class.md)