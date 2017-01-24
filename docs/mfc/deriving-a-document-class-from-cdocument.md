---
title: "從 CDocument 衍生文件類別 | Microsoft Docs"
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
  - "CDocument 類別, 衍生自"
  - "類別 [C++], 從 CDocument 衍生"
  - "衍生類別, 通常被覆寫的函式"
  - "文件類別, 通常被覆寫的函式"
  - "文件物件, 衍生"
ms.assetid: e6a198e0-9799-43c0-83c5-04174d8b532c
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 從 CDocument 衍生文件類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

文件包含和管理應用程式資料。  若要使用 MFC 應用程式精靈所提供的資料類別，您必須執行下列動作:  
  
-   從文件類型的 **CDocument** 衍生類別。  
  
-   加入成員變數儲存每個文件的資料。  
  
-   覆寫 **CDocument**`Serialize` 在文件類別的成員函式。  `Serialize` 來回磁碟寫入和讀取文件的資料。  
  
## 通常會覆寫的所有文件功能。  
 您也可以覆寫其他 **CDocument** 成員函式。  特別是，通常會需要覆寫 [OnNewDocument](../Topic/CDocument::OnNewDocument.md) ，並初始化文件資料成員和 [DeleteContents](../Topic/CDocument::DeleteContents.md) 的 [OnOpenDocument](../Topic/CDocument::OnOpenDocument.md) 動態地終結配置的資料。  如需可覆寫成員的詳細資訊，請參閱《 *MFC 參考》中的*[CDocument](../mfc/reference/cdocument-class.md) 類別。  
  
## 請參閱  
 [使用文件](../mfc/using-documents.md)