---
title: "OLE 相關類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
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
  - "ActiveX 類別 [C++]"
  - "OLE [C++], 類別"
  - "OLE 類別 [C++]"
ms.assetid: 2135cf54-1d9d-4e0e-91b4-943b3440effa
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# OLE 相關類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這些類別提供檔案輸入和輸出提供許多不同的服務，範圍從例外狀況。  
  
 [COleObjectFactory](../mfc/reference/coleobjectfactory-class.md)  
 用來建立項目，當要求其他容器。  這個類別可做為類別的基底類別的特定型別，包括 `COleTemplateServer`。  
  
 [COleMessageFilter](../mfc/reference/colemessagefilter-class.md)  
 用來處理與 OLE 輕量型遠端程序呼叫 \(LRPC\) 的並行。  
  
 [COleStreamFile](../mfc/reference/colestreamfile-class.md)  
 使用 COM `IStream` 介面提供 `CFile` 對複合檔案。  這個類別 \(衍生自 `CFile`\) 可讓序列化使用 MFC OLE 結構化儲存體。  
  
 [CRectTracker](../mfc/reference/crecttracker-class.md)  
 用來允許移動，就地項目的調整大小和重新定位。  
  
## 請參閱  
 [類別概觀](../mfc/class-library-overview.md)