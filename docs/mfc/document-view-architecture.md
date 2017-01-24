---
title: "文件/檢視架構 | Microsoft Docs"
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
  - "CDocument 類別"
  - "CView 類別, 檢視架構"
  - "文件物件"
  - "文件物件, 文件/檢視架構"
  - "文件物件, MFC 文件/檢視模型"
  - "文件, MFC 文件/檢視模型"
  - "MFC, 文件"
  - "MFC, 檢視"
  - "檢視, MFC 文件/檢視模型"
ms.assetid: 6127768a-553f-462a-b01b-a5ee6068c81e
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 文件/檢視架構
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

根據預設，MFC 應用程式精靈建立具有文件類別和檢視類別的應用程式基本架構。  MFC 將資料管理到這兩個類別。  文件儲存資料和處理列印資料並協調更新資料的多個檢視。  這個檢視會顯示資料、處理使用者的互動，包括選取和編輯。  
  
 在這個模型， MFC 文件物件在持續性儲存體中讀取和寫入資料。  文件可能也提供介面給資料位置，無論它位於何處 \(例如資料庫\)。  一個檢視物件處理資料顯示，從呈現在視窗中的資料到使用者選取和編輯資料。  這個檢視從文件得到顯示資料並將任何資料變更傳回給文件。  
  
 當您可以輕易地覆寫或忽略文件\/檢視中斷連接時，有強制性的理由在大部分的情況下遵循此模型。  其中一個最好的是當您需要相同文件的多個檢視時，例如報表和圖形檢視。  文件\/檢視模型讓另一個檢視物件表示資料的每一個檢視，而對所有檢視共用的程式碼 \(例如計算引擎\) 可能位於文件。  每當資料變更文件也負責更新所有檢視工作。  
  
 MFC 文件\/檢視架構可支援多個檢視、多個資料型別、分隔視窗和其他重要的使用者介面功能。  
  
 MFC 架構最能讓使用者、您和程式設計人員看見的部分，是文件和檢視。  大部分使用 framework 開發應用程式進入撰寫文件和檢視類別。  本文章系列描述：  
  
-   文件和檢視的目的，以及如何在 framework 互動。  
  
-   說明您實作必須做什麼。  
  
 在文件\/檢視的核心是四個重要類別：  
  
 [CDocument](../mfc/reference/cdocument-class.md) \(或 [COleDocument](../mfc/reference/coledocument-class.md)\) 類別支援儲存或控制您程式的資料並提供為程式設計人員定義的文件類別的基本功能的物件。  代表使用者通常會使用檔案功能表上的開啟命令開啟並使用檔案功能表上的儲存命令儲存的單位資料的文件。  
  
 [CView](../mfc/reference/cview-class.md) \(或其中一個衍生類別\) 為程式設計人員定義的檢視類別提供基本功能。  檢視連結至文件，並作為文件和使用者之間的媒介：這個檢視呈現文件的影像在螢幕上將使用者輸入轉譯成對文件的作業。  此檢視也會呈現列印和預覽列印的影像。  
  
 其[CFrameWnd](../mfc/reference/cframewnd-class.md) \(或其中一個變化\) 支援文件的一或多個檢視周圍提供架構的物件。  
  
 [CDocTemplate](../mfc/reference/cdoctemplate-class.md) \(或 [CSingleDocTemplate](../mfc/reference/csingledoctemplate-class.md) 或 [CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md)\) 支援協調特定類型的一個或多個現有文件並處理建立正確的文件、檢視和框架視窗物件那個型別的物件。  
  
 下圖顯示了一個文件和它的檢視之間的關係。  
  
 ![檢視是所顯示文件的一部分](../mfc/media/vc379n1.png "vc379N1")  
文件和檢視  
  
 在類別庫中的文件\/檢視實作將資料從其顯示與使用者操作分開。  對資料所做的變更都透過文件類別管理。  這個檢視呼叫這個介面存取及更新資料。  
  
 文件、其相關聯的檢視和建構檢視的框架檢視由文件樣板建立。  文件樣板負責建立和管理一個資料型別的所有文件。  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [文件\/檢視架構的簡介](../mfc/a-portrait-of-the-document-view-architecture.md)  
  
-   [文件\/檢視架構的優點](../mfc/advantages-of-the-document-view-architecture.md)  
  
-   [文件和檢視類別由應用程式精靈建立。](../mfc/document-and-view-classes-created-by-the-mfc-application-wizard.md)  
  
-   [文件\/檢視架構的替代方案](../mfc/alternatives-to-the-document-view-architecture.md)  
  
-   [將多個檢視加入至單一文件](../mfc/adding-multiple-views-to-a-single-document.md)  
  
-   [使用文件](../mfc/using-documents.md)  
  
-   [使用檢視](../mfc/using-views.md)  
  
-   [多重文件類型、檢視和框架視窗](../mfc/multiple-document-types-views-and-frame-windows.md)  
  
-   [初始化及清除文件和檢視](../mfc/initializing-and-cleaning-up-documents-and-views.md)  
  
-   [初始化您加入至文件 & 檢視類別。](../mfc/creating-new-documents-windows-and-views.md)  
  
-   [使用具有文件和檢視的資料庫類別](../data/mfc-using-database-classes-with-documents-and-views.md)  
  
-   [使用不具文件和檢視的資料庫類別](../data/mfc-using-database-classes-without-documents-and-views.md)  
  
-   [範例](../top/visual-cpp-samples.md)  
  
## 請參閱  
 [使用者介面項目](../mfc/user-interface-elements-mfc.md)   
 [Windows](../mfc/windows.md)   
 [框架視窗](../mfc/frame-windows.md)   
 [文件範本和文件\/檢視建立流程](../mfc/document-templates-and-the-document-view-creation-process.md)   
 [文件\/檢視建立](../mfc/document-view-creation.md)   
 [建立新文件、視窗和檢視](../mfc/creating-new-documents-windows-and-views.md)