---
title: "對話方塊的生命週期 | Microsoft Docs"
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
  - "對話方塊, 生命週期"
  - "對話方塊的生命週期"
  - "MFC 對話方塊, 生命週期"
  - "強制回應對話方塊, 生命週期"
  - "非強制回應對話方塊, 生命週期"
ms.assetid: e16fd78e-238d-4f31-8c9d-8564f3953bd9
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 對話方塊的生命週期
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在對話方塊的生命週期，使用者叫用對話方塊，通常是在建立並初始化對話方塊物件的命令處理常式之內，使用者與對話方塊互動，，並關閉對話方塊。  
  
 對於強制回應對話方塊，，一旦對話方塊關閉，處理常式收集任何資料使用者輸入。  因為對話物件存在，在其對話視窗關閉之後，您可以使用自己的對話方塊類別的成員變數擷取資料。  
  
 對於非強制回應對話方塊，也就是說，當對話方塊為可見時，您可以從對話方塊物件通常擷取資料。  在某些情況下，終結對話物件;如果發生這種情況取決於您的程式碼。  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [建立和顯示對話方塊](../mfc/creating-and-displaying-dialog-boxes.md)  
  
-   [建立強制回應對話方塊](../mfc/creating-modal-dialog-boxes.md)  
  
-   [建立非強制回應對話方塊](../mfc/creating-modeless-dialog-boxes.md)  
  
-   [使用記憶體中的對話方塊範本](../mfc/using-a-dialog-template-in-memory.md)  
  
-   [設定對話方塊的背景色彩。](../mfc/setting-the-dialog-box’s-background-color.md)  
  
-   [初始化對話方塊](../mfc/initializing-the-dialog-box.md)  
  
-   [處理在對話方塊的視窗訊息。](../mfc/handling-windows-messages-in-your-dialog-box.md)  
  
-   [從資料物件擷取對話方塊物件](../mfc/retrieving-data-from-the-dialog-object.md)  
  
-   [關閉對話方塊。](../mfc/closing-the-dialog-box.md)  
  
-   [終結對話方塊](../mfc/destroying-the-dialog-box.md)  
  
-   [對話資料交換 \(Dialog Data Exchange，DDX\) 和驗證 \(DDV\)](../mfc/dialog-data-exchange-and-validation.md)  
  
-   [屬性工作表對話方塊](../mfc/property-sheets-and-property-pages-mfc.md)  
  
## 請參閱  
 [對話方塊](../mfc/dialog-boxes.md)