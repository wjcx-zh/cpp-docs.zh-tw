---
title: "頁首和頁尾 | Microsoft Docs"
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
  - "頁尾, 列印"
  - "頁首, 列印"
  - "頁尾"
  - "頁尾, 列印"
  - "頁首"
  - "頁首, 列印"
  - "列印 [MFC], 頁首和頁尾"
  - "列印 [MFC], 多頁文件"
ms.assetid: b0be9c53-5773-4955-a777-3c15da745128
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 頁首和頁尾
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文說明如何將頁首和頁尾加入至列印的文件。  
  
 當您在螢幕看到一個文件，文件名稱和您的文件中目前的位置在標題列和狀態列通常會顯示。  當檢視文件的列印的複本時，在頁首或頁尾和頁碼顯示名稱會很有用。  這是即使 WYSIWYG 程式執行列印和螢幕顯示的方式有所不同時的一個常見方法。  
  
 [OnPrint](../Topic/CView::OnPrint.md) 成員函式是列印頁首或頁尾的適當位置，因為它會為每個頁面被呼叫，且因為它只為列印呼叫，而非針對螢幕顯示。  您可以定義不同的函式列印頁首或頁尾，並傳給它 `OnPrint` 的印表機內容。  您可能需要在呼叫 [OnDraw](../Topic/CView::OnDraw.md) 之前調整視窗原點或範圍以避免排列頁面主體重疊頁首或頁尾。  您可能也需要修改 `OnDraw` ，因為在頁面相容的數量文件會降低。  
  
 一種補償頁首或頁尾佔據的區域是使用 [CPrintInfo](../mfc/reference/cprintinfo-structure.md)的 **m\_rectDraw** 成員。  每次列印頁面，這個成員以使用的頁面的可以使用區域初始化。  如果您在列印頁面主體前先列印頁首或頁尾，可以減少在 **m\_rectDraw** 存放的矩形大小佔頁首或頁尾採取的區域。  然後 `OnPrint` 可以參考 **m\_rectDraw** 以尋找為列印頁面主體會保持多少區域。  
  
 從 [OnPrepareDC](../Topic/CView::OnPrepareDC.md)，您無法列印標題或任何其他東西，因為它在 [CDC](../mfc/reference/cdc-class.md) 的 `StartPage` 成員函式呼叫之前被呼叫。  此時，印表機內容視為在頁面界限。  您只可以從 `OnPrint` 成員函式執行列印。  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [列印多頁文件](../mfc/multipage-documents.md)  
  
-   [配置列印的 GDI 資源](../mfc/allocating-gdi-resources.md)  
  
## 請參閱  
 [列印](../mfc/printing.md)