---
title: "文件/檢視建立 | Microsoft Docs"
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
  - "文件/檢視架構, 建立文件/檢視"
  - "文件, 建立"
  - "MFC, 文件"
  - "MFC, 檢視"
  - "物件建立者"
  - "資料表 [C++]"
  - "資料表 [C++], 每個 MFC 物件建立的物件"
  - "檢視, 和框架視窗"
  - "檢視, 建立"
ms.assetid: bda14f41-ed50-439d-af9e-591174e7dd64
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 文件/檢視建立
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

架構提供 `New` 和 **Open** 命令的實作 \(等等\) 在檔案功能表。  新的資料和其相關檢視和框架視窗的建立方式是在應用程式物件、文件樣板、這個新建立的檔案和新建立的框架視窗中的共同作業結果。  建立物件的動作下表摘要說明。  
  
### 物件建立者  
  
|建立者|建立|  
|---------|--------|  
|Application 物件|文件樣板|  
|文件樣板|Document|  
|文件樣板|框架視窗|  
|框架視窗|檢視|  
  
## 請參閱  
 [文件範本和文件\/檢視建立流程](../mfc/document-templates-and-the-document-view-creation-process.md)   
 [文件樣板建立](../mfc/document-template-creation.md)   
 [MFC 物件關聯性](../mfc/relationships-among-mfc-objects.md)   
 [建立新文件、視窗和檢視](../mfc/creating-new-documents-windows-and-views.md)