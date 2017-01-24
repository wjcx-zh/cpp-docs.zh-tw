---
title: "容器：用戶端項目 | Microsoft Docs"
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
  - "用戶端項目與 OLE 容器"
  - "OLE 容器, 用戶端項目"
ms.assetid: 231528b5-0744-4f83-8897-083bf55ed087
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 容器：用戶端項目
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文說明哪些用戶端項目，並從哪些類別應用程式應該衍生它的用戶端項目。  
  
 用戶端項目是為所包含或參考由一個 OLE 容器應用程式的文件屬於另一個應用程式的資料項目。  資料儲存在文件中內嵌的用戶端項目;資料在容器文件參考的其他位置中的連結。  
  
 在 OLE 應用程式的文件類別從 **CDocument**的類別衍生自 [，而不是COleDocument](../mfc/reference/coledocument-class.md) 。  `COleDocument` 類別是 **CDocument** 繼承所有功能也會使用 MFC 應用程式的文件\/檢視架構。  `COleDocument` 也會定義將資料當做 `CDocItem` 物件集合的介面。  數個 `COleDocument` 成員函式來加入，擷取和刪除該集合的項目。  
  
 每個容器應用程式應該衍生至少一個類別自 `COleClientItem`。  這個類別表示物件項目，內嵌或連結，在這個 OLE 文件。  除非從文件刪除，這些物件存在於包含其文件的存留期。  
  
 `CDocItem` 是 `COleClientItem` 和 `COleServerItem` 的基底類別。  分別從這兩個衍生類別的物件為 OLE 項目以及用戶端和伺服器應用程式之間的媒介。  每次新的 OLE 項目加入至文件， MFC 架構將用戶端應用程式的 `COleClientItem`新物件\-對 `CDocItem` 物件之文件的集合中的衍生類別。  
  
## 請參閱  
 [容器](../mfc/containers.md)   
 [容器：複合檔案](../mfc/containers-compound-files.md)   
 [容器：使用者介面問題](../mfc/containers-user-interface-issues.md)   
 [容器：進階功能](../mfc/containers-advanced-features.md)   
 [COleClientItem Class](../mfc/reference/coleclientitem-class.md)   
 [COleServerItem Class](../mfc/reference/coleserveritem-class.md)