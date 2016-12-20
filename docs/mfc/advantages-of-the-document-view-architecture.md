---
title: "文件/檢視架構的優點 | Microsoft Docs"
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
  - "文件/檢視架構, 的優點"
  - "檢視, 優點"
ms.assetid: 0bc27071-e120-4889-939c-ce1e61fb9cb3
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 文件/檢視架構的優點
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

對使用 MFC 文件\/檢視架構的主要優點是結構特殊完善支援相同文件的多個檢視。\(如果您不需要多個檢視，而低額外負荷文件\/檢視過高的在應用程式中，您可以避免結構。  [文件\/檢視架構的替代方案](../mfc/alternatives-to-the-document-view-architecture.md)\)  
  
 假設您的應用程式可以讓使用者檢視數值資料以報告格式或以圖表形式。  使用者可以同時查看未經處理資料，以報告格式和之圖形資料的結果。  您可使用這些不同檢視在個別的框架視窗或在單一視窗內的分割窗格。  現在假設使用者可以編輯報表中的資料並查看立即反映的變更在圖表上。  
  
 在 MFC 中，報告檢視和圖形檢視根據 CView 衍生的類別。  兩個檢視會與單一文件物件。  文件儲存資料或啟用 \(或衍生自它從資料庫\)。  它們是從它擷取的兩種檢視存取文件並顯示資料。  
  
 當使用者更新其中一個檢視，該檢視物件呼叫 `CDocument::UpdateAllViews`。  該函數通知所有的文件的檢視，並且每個檢視利用文件的最新資料來更新自身。  對 `UpdateAllViews` 的唯一呼叫同步處理不同的檢視。  
  
 特別是在檢視中的資料，而不是資料分離的檢視，這個案例中是錯誤程式碼。  文件\/檢視，非常容易。  架構完成大部分的協調工作。  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [替代方案文件\/檢視](../mfc/alternatives-to-the-document-view-architecture.md)  
  
-   [CDocument](../mfc/reference/cdocument-class.md)  
  
-   [CView](../mfc/reference/cview-class.md)  
  
-   [CDocument::UpdateAllViews](../Topic/CDocument::UpdateAllViews.md)  
  
-   [CView::GetDocument](../Topic/CView::GetDocument.md)  
  
## 請參閱  
 [文件\/檢視架構](../mfc/document-view-architecture.md)