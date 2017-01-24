---
title: "清除文件和檢視 | Microsoft Docs"
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
  - "文件, 清除"
  - "文件, 關閉"
  - "檢視, 清除"
ms.assetid: 0c454db2-3644-434d-9e53-8108a7aedfe1
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 清除文件和檢視
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當文件關閉時，框架會先呼叫它的 [DeleteContents](../Topic/CDocument::DeleteContents.md) 成員函式。  如果您在文件的作業期間配置任何記憶體在堆積上， `DeleteContents` 是解除配置它的最佳位置。  
  
> [!NOTE]
>  您不能在文件的解構函式解除配置文件資料。  在 SDI 應用程式案例中，可以重複使用文件物件。  
  
 您可以覆寫檢視的解構函式，取消配置任何記憶體中的堆積配置。  
  
## 請參閱  
 [初始化及清除文件和檢視](../mfc/initializing-and-cleaning-up-documents-and-views.md)