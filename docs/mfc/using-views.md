---
title: "使用檢視 | Microsoft Docs"
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
  - "CView 類別, 檢視架構"
  - "繪製, 資料"
  - "與使用者互動，以及檢視類別的角色"
  - "MFC, 檢視"
  - "繪製資料"
  - "呈現資料"
  - "使用者輸入, 透過檢視類別解譯"
  - "檢視類別, 在顯示應用程式資料中扮演的角色"
  - "檢視類別, 在管理使用者互動中扮演的角色"
  - "檢視, 使用"
ms.assetid: dc3de6ad-5c64-4317-8f10-8bdcc38cdbd5
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用檢視
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

檢視的責任是以圖形顯示文件的資料給使用者和接受和解譯為文件的作業中的使用者輸入。  您在撰寫自己的檢視類別的工作包括:  
  
-   撰寫自己的檢視類別的 [OnDraw](../Topic/CView::OnDraw.md) 成員函式，呈現文件的資料。  
  
-   連接到適當的 Windows 訊息和使用者介面物件 \(例如功能表項目的訊息處理常式成員函式在檢視類別。  
  
-   實作這些處理常式會解譯使用者輸入。  
  
 此外，您可能需要覆寫您的衍生類別檢視的其他 `CView` 成員函式。  特別是，在這種情況下，檢視重繪之前，您可能想要覆寫 [OnInitialUpdate](../Topic/CView::OnInitialUpdate.md) 執行檢視和 [OnUpdate](../Topic/CView::OnUpdate.md) 的特殊初始設定可以進行任何需要的特殊處理。  對於多頁文件，您也必須覆寫 [OnPreparePrinting](../Topic/CView::OnPreparePrinting.md) 初始化具有的頁數的列印對話方塊加入至列印和其他資訊。  如需覆寫 `CView` 成員函式的詳細資訊，請參閱《 *MFC 參考》中的*[CView](../mfc/reference/cview-class.md) 類別。  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [取得檢視在 MFC 的可用分類](../mfc/derived-view-classes-available-in-mfc.md)  
  
-   [繪製在檢視](../mfc/drawing-in-a-view.md)  
  
-   [您可以檢視輸入的解譯使用者](../mfc/interpreting-user-input-through-a-view.md)  
  
-   [檢視的作用在列印](../mfc/role-of-the-view-in-printing.md)  
  
-   [捲動和縮放檢視](../mfc/scrolling-and-scaling-views.md)  
  
-   [初始化和清除文件和檢視](../mfc/initializing-and-cleaning-up-documents-and-views.md)  
  
## 請參閱  
 [文件\/檢視架構](../mfc/document-view-architecture.md)   
 [CFormView Class](../mfc/reference/cformview-class.md)   
 [記錄檢視 \(MFC 資料存取\)](../data/record-views-mfc-data-access.md)   
 [略過序列化機制](../mfc/bypassing-the-serialization-mechanism.md)