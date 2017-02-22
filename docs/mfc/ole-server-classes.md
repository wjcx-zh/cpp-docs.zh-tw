---
title: "OLE 伺服器類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.classes.ole"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COM 元件, 類別"
  - "元件類別"
  - "OLE 伺服器應用程式, 伺服器類別"
  - "OLE 伺服器文件"
ms.assetid: 8e9b67a2-c0ff-479c-a8d6-19b36c5e6fc6
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# OLE 伺服器類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

伺服器應用程式使用這些類別。  伺服器資料衍生自 `COleServerDoc` 而不是從 **CDocument**。  請注意，因為 `COleServerDoc` 衍生自 `COleLinkingDoc`，伺服器資料也可以是支援連結的容器。  
  
 `COleServerItem` 類別表示包含在另一個文件可以被嵌入或連結到文件的文件或部分。  
  
 `COleIPFrameWnd` 和 `COleResizeBar` 可支援就地編譯，當物件在容器時，，且 `COleTemplateServer` 支援文件\/檢視產生配對，因此從其他應用程式的 OLE 物件則可以編輯。  
  
 [COleServerDoc](../mfc/reference/coleserverdoc-class.md)  
 使用做為基底類別為伺服器應用程式資料分類。  `COleServerDoc` 物件的互動的大部分伺服器支援以 `COleServerItem` 物件。  使用類別庫的文件\/檢視架構，視覺化編輯功能提供。  
  
 [CDocItem](../mfc/reference/cdocitem-class.md)  
 `COleClientItem` 和`COleServerItem` 的基底類別。  衍生自 `CDocItem` 的類別物件代表文件的部分。  
  
 [COleServerItem](../mfc/reference/coleserveritem-class.md)  
 用來表示 OLE 介面至 `COleServerDoc` 項目。  通常有一個 `COleServerDoc` 物件，表示文件中的內嵌部分。  在文件的支援連結，仍可以在許多 `COleServerItem` 物件，其中每個物件都代表連結至文件中的伺服器。  
  
 [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)  
 當伺服器資料時，就地編輯提供檢視框架視窗。  
  
 [COleResizeBar](../mfc/reference/coleresizebar-class.md)  
 就地調整提供標準的使用者介面。  這個類別的物件與 `COleIPFrameWnd` 物件一起使用。  
  
 [COleTemplateServer](../mfc/reference/coletemplateserver-class.md)  
 使用架構的文件\/檢視架構，用來建立文件。  `COleTemplateServer` 物件的委派物件最其關聯的 `CDocTemplate` 物件的工作。  
  
 [COleException](../mfc/reference/coleexception-class.md)  
 例外狀況造成 OLE 處理失敗。  容器和伺服器會使用這個類別。  
  
## 請參閱  
 [類別概觀](../mfc/class-library-overview.md)