---
title: "OLE 容器類別 | Microsoft Docs"
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
  - "ActiveX 類別 [C++]"
  - "容器類別 [C++]"
  - "容器 [C++], OLE 容器應用程式"
  - "OLE [C++], 類別"
  - "OLE 類別 [C++]"
  - "視覺化編輯 [C++], 類別"
ms.assetid: 1e27e1ab-4c22-41eb-8547-6915c72668ae
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# OLE 容器類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

伺服器容器使用這些類別。  `COleLinkingDoc` 和 `COleDocument` 管理 `COleClientItem` 物件的集合。  您自己的文件類別而非從 **CDocument**衍生，從 `COleLinkingDoc` 或 `COleDocument`是衍生，取決於您是否想要支援連結至您的文件中內嵌的物件。  
  
 使用 `COleClientItem` 物件表示從另一份文件中內嵌或連結至另一個文件的文件的每個 OLE 項目。  
  
 [COleDocObjectItem](../mfc/reference/coledocobjectitem-class.md)  
 支援主動式文件內含項目。  
  
 [COleDocument](../mfc/reference/coledocument-class.md)  
 使用為複合檔案實作，以及基礎容器支援。  以容器階層架構的根類別衍生自 `CDocItem`。  這個類別可以當做基底類別為容器文件且為 `COleServerDoc`的基底類別。  
  
 [COleLinkingDoc](../mfc/reference/colelinkingdoc-class.md)  
 用於連接的基礎結構的類別衍生自 `COleDocument` 。  如果您想要對支援連接至內嵌物件，您應該從這個類別衍生您的容器應用程式的文件類別而不是 `COleDocument` 。  
  
 [CRichEditDoc](../mfc/reference/cricheditdoc-class.md)  
 維護在 Rich 編輯控制項中 OLE 用戶端項目的清單。  使用 [CRichEditView](../mfc/reference/cricheditview-class.md) 和 [CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)。  
  
 [CDocItem](../mfc/reference/cdocitem-class.md)  
 `COleClientItem` 和`COleServerItem` 的基底類別。  衍生自 `CDocItem` 的類別物件代表文件的部分。  
  
 [COleClientItem](../mfc/reference/coleclientitem-class.md)  
 表示連接的用戶端框具有內嵌或連結的 OLE 項目的用戶端項目類別。  從這個類別衍生您的用戶端項目。  
  
 [CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)  
 提供用戶端存取在 Rich 編輯控制項儲存的 OLE 項目，同時使用 `CRichEditView` 和 `CRichEditDoc`。  
  
 [COleException](../mfc/reference/coleexception-class.md)  
 例外狀況造成 OLE 處理失敗。  容器和伺服器會使用這個類別。  
  
## 請參閱  
 [類別概觀](../mfc/class-library-overview.md)