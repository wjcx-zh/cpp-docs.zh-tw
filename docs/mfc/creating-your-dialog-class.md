---
title: "建立您的對話方塊類別 | Microsoft Docs"
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
  - "對話方塊 [C++], 建立"
  - "對話方塊類別, 加入類別精靈"
  - "對話方塊類別, 建立"
  - "檔案 [C++], 建立"
  - "MFC 對話方塊, 建立"
ms.assetid: d5321741-da41-47a8-bb1c-6a0e8b28c4c1
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 建立您的對話方塊類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

對於在程式中的每個對話方塊，請建立新的對話方塊類別的對話方塊資源一起使用。  
  
 [加入類別](../ide/adding-a-class-visual-cpp.md) 說明如何建立新的對話方塊類別。  當您使用加入類別精靈中的對話方塊類別，它會寫入下列項目。您指定的 H 和 .CPP 檔案:  
  
 在。H 檔案:  
  
-   對話方塊類別的類別宣告。  類別衍生自 [CDialog](../mfc/reference/cdialog-class.md)。  
  
 在 .CPP 檔案:  
  
-   類別的訊息對應。  
  
-   對話方塊的標準建構函式。  
  
-   [DoDataExchange](../Topic/CWnd::DoDataExchange.md) 成員函式的覆寫。  編輯此函式。  它為對話資料交換和驗證功能在使用如 [對話資料交換和驗證](../mfc/dialog-data-exchange-and-validation.md)所述。  
  
## 請參閱  
 [使用程式碼精靈建立對話方塊類別](../mfc/creating-a-dialog-class-with-code-wizards.md)   
 [對話方塊的生命週期](../mfc/life-cycle-of-a-dialog-box.md)