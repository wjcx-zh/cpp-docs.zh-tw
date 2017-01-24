---
title: "初始化文件和檢視 | Microsoft Docs"
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
  - "文件, 初始化"
  - "初始化文件"
  - "初始化物件, 文件物件"
  - "初始化檢視"
  - "檢視, 初始化"
ms.assetid: 33cb8643-8a16-478c-bc26-eccc734e3661
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 初始化文件和檢視
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

資料會以兩種不同的方式產生，因此您的文件類別必須支援這兩個方式。  首先，使用者可用「建立檔案」命令產生新的空文件。  在這種情況下，請初始化 [CDocument](../mfc/reference/cdocument-class.md) 類別的 [OnNewDocument](../Topic/CDocument::OnNewDocument.md) 成員函式的覆寫中的文件。  再來，使用者可以使用檔案功能表的開啟命令建立內容從檔案讀取的新文件。  在這種情況下，請初始化 **CDocument** 類別的 [OnOpenDocument](../Topic/CDocument::OnOpenDocument.md) 成員函式的覆寫中的文件。  如果兩個初始化相同，您可以從兩個覆寫呼叫一個共同成員函式，或 `OnOpenDocument` 可以呼叫 `OnNewDocument` 以初始化乾淨文件後完成開啟作業。  
  
 檢視會在其資料建立後產生。  初始化檢視的最佳時機是在架構完成建立文件框架視窗和檢視之後。  您可以透過覆寫 [CView](../mfc/reference/cview-class.md) 的 [OnInitialUpdate](../Topic/CView::OnInitialUpdate.md) 成員函式來初始化您的檢視。  如果您需要重新初始化或調整文件每次的任何變更，您可以覆寫 [OnUpdate](../Topic/CView::OnUpdate.md)。  
  
## 請參閱  
 [初始化及清除文件和檢視](../mfc/initializing-and-cleaning-up-documents-and-views.md)