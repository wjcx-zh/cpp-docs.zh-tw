---
title: "使用文件 | Microsoft Docs"
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
  - "資料 [MFC], 文件"
  - "資料 [MFC], 讀取"
  - "文件/檢視架構 [C++], 文件"
  - "文件 [C++]"
  - "文件 [C++], C++ 應用程式"
  - "檔案 [C++]"
  - "檔案 [C++], 寫入至"
  - "列印 [MFC], 文件"
  - "讀取資料 [C++], 文件和檢視"
  - "檢視 [C++], C++ 應用程式"
  - "寫入檔案 [C++]"
ms.assetid: f390d6d8-d0e1-4497-9b6a-435f7ce0776c
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用文件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

文件和檢視:  
  
-   包含處理，並顯示您應用程式特定的 [資料](../mfc/managing-data-with-document-data-variables.md)。  
  
-   提供管理資料提供介面中的 [文件資料變數](../mfc/managing-data-with-document-data-variables.md) 。  
  
-   參與 [寫入和讀取檔案](../mfc/serializing-data-to-and-from-files.md)。  
  
-   參與 [列印](../mfc/role-of-the-view-in-printing.md)。  
  
-   大部分[控制代碼](../mfc/handling-commands-in-the-document.md) 應用程式的命令和訊息。  
  
 文件在處理資料特殊介入。  儲存您的資料，通常，文件類別成員變數。  檢視使用這些變數可存取資料以便顯示和更新。  文件的預設序列化機制來回檔案處理讀取和寫入資料。  文件也處理命令 \(，但是除了 **WM\_COMMAND**之外的不是 Windows 訊息\)。  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [取得文件類別從 CDocument](../mfc/deriving-a-document-class-from-cdocument.md)  
  
-   [與文件資料變數中管理資料。](../mfc/managing-data-with-document-data-variables.md)  
  
-   [序列化至檔案中的資料。](../mfc/serializing-data-to-and-from-files.md)  
  
-   [略過序列化機制](../mfc/bypassing-the-serialization-mechanism.md)  
  
-   [在文件的處理命令](../mfc/handling-commands-in-the-document.md)  
  
-   [OnNewDocument 成員函式](../Topic/CDocument::OnNewDocument.md)  
  
-   [DeleteContents 成員函式](../Topic/CDocument::DeleteContents.md)  
  
## 請參閱  
 [文件\/檢視架構](../mfc/document-view-architecture.md)