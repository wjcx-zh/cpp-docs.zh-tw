---
title: "強制回應和非強制回應對話方塊 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MFC 對話方塊, 強制回應"
  - "MFC 對話方塊, 非強制回應"
  - "強制回應對話方塊"
  - "非強制回應對話方塊"
ms.assetid: e83df336-5994-4b8f-8233-7942f997315b
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 強制回應和非強制回應對話方塊
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以使用 [CDialog](../mfc/reference/cdialog-class.md) 類別處理兩種對話方塊:  
  
-   *強制回應對話方塊*，要求使用者在繼續執行程式前回應  
  
-   *非強制回應對話方塊*，在螢幕上暫停並隨時可供使用，但允許其他使用者活動  
  
 建立對話方塊樣板資源編輯和方法是相同的強制回應和非強制回應對話方塊的。  
  
 建立程式的對話方塊需要下列步驟:  
  
1.  使用 [對話方塊編輯器](../mfc/dialog-editor.md) 設計對話方塊並建立自己的對話方塊範本資源。  
  
2.  建立對話方塊類別。  
  
3.  連接至對話方塊類別的 [對話方塊的訊息處理常式的資源](../mfc/adding-event-handlers-for-dialog-box-controls.md) 。  
  
4.  加入資料成員與對話方塊的控制項以及控制項指定 [對話資料交換](../mfc/dialog-data-exchange.md) 和 [對話資料驗證](../mfc/dialog-data-validation.md) 。  
  
## 請參閱  
 [對話方塊](../mfc/dialog-boxes.md)   
 [對話方塊的生命週期](../mfc/life-cycle-of-a-dialog-box.md)