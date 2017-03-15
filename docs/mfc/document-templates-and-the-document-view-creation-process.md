---
title: "文件範本和文件/檢視建立流程 | Microsoft Docs"
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
  - "CDocTemplate 類別"
  - "文件樣板, 和檢視"
  - "文件/檢視架構, 建立文件/檢視"
  - "圖示, 多個文件範本的"
  - "MFC, 文件樣板"
  - "多個文件範本"
  - "單一文件範本"
  - "範本, 文件樣板"
ms.assetid: 311ce4cd-fbdf-4ea1-a51b-5bb043abbcee
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 文件範本和文件/檢視建立流程
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若要處理文件建立複雜處理序有關聯的檢視和框架視窗，架構會使用兩個文件範本類別:SDI 應用程式的 [CSingleDocTemplate](../mfc/reference/csingledoctemplate-class.md) 和 [CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md) 至 MDI 應用程式。  `CSingleDocTemplate` 可以同時建立和儲存一個型別的文件。  `CMultiDocTemplate` 保留一個型別的多個開啟的文件清單。  
  
 某些應用程式支援多個資料型別。  例如，應用程式可能支援 Word 文件和檢視的。  在這種應用程式，也就是說，當使用者選取檔案功能表的新命令，對話方塊會顯示可能的新資料型別清單開啟。  對於每個支援的資料型別，應用程式會使用不同的文件樣板物件。  下圖說明支援兩種文件類型和顯示多個開啟的 MDI 應用程式的組態。  
  
 ![具有兩個文件類型的 MDI 應用程式](../mfc/media/vc387h1.png "vc387H1")  
具有兩個文件類型的 MDI 應用程式  
  
 文件樣板由應用程式物件建立和維護。  在應用程式中使用 `InitInstance` 函式時要執行的其中一個主要工作是建構一個或多個資料範本適當的型別。  這個功能在 [資料範本建立](../mfc/document-template-creation.md)中說明。  應用程式物件儲存指標到每個文件範本在它的範本清單並將文件範本提供介面。  
  
 如果您需要支援兩個以上的資料型別，您必須將額外的 [AddDocTemplate](../Topic/CWinApp::AddDocTemplate.md) 的呼叫每個資料型別的。  
  
 圖示註冊根據其在文件範本應用程式清單中的每個文件範本。  它們會將與呼叫 `AddDocTemplate`的順序來決定文件範本的順序。  MFC 假設，在應用程式的第一個圖示資源是應用程式圖示，下圖顯示資源是第一個文件圖示，依此類推。  
  
 例如，文件樣板是三個應用程式的。  如果在應用程式的圖示資源位於索引 3，該圖示為文件樣板使用。  否則，會在索引 0 做為預設值。  
  
## 請參閱  
 [一般 MFC 主題](../mfc/general-mfc-topics.md)   
 [文件樣板建立](../mfc/document-template-creation.md)   
 [文件\/檢視建立](../mfc/document-view-creation.md)   
 [MFC 物件關聯性](../mfc/relationships-among-mfc-objects.md)   
 [建立新文件、視窗和檢視](../mfc/creating-new-documents-windows-and-views.md)