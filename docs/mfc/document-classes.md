---
title: "文件類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.classes.document"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "文件類別"
ms.assetid: 4bf19b02-0a4f-4319-b68e-cddcba2705cb
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 文件類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

文件類別物件，建立由文件樣板物件，管理應用程式資料。  您從其中一個類別中衍生自己的文件的類別。  
  
 文件類別物件與檢視物件互動。  檢視物件表示視窗的工作區，顯示文件中的資料，並允許使用者與其互動。  文件和檢視的文件樣板物件建立。  
  
 [CDocument](../mfc/reference/cdocument-class.md)  
 應用程式專屬資料的基底類別。  從 **CDocument**衍生您自己的文件類別或類別。  
  
 [COleDocument](../mfc/reference/coledocument-class.md)  
 使用為複合檔案實作，以及基礎容器支援。  以容器階層架構的根類別衍生自 [CDocItem](../mfc/reference/cdocitem-class.md)的。  這個類別可以當做基底類別為容器文件且為 `COleServerDoc`的基底類別。  
  
 [COleLinkingDoc](../mfc/reference/colelinkingdoc-class.md)  
 用於連接的基礎結構的類別衍生自 `COleDocument` 。  如果您想要對支援連接至內嵌物件，您應該從這個類別衍生您的容器應用程式的文件類別而不是 `COleDocument` 。  
  
 [CRichEditDoc](../mfc/reference/cricheditdoc-class.md)  
 維護在 Rich Edit 控制項中 OLE 用戶端項目的清單。  使用 [CRichEditView](../mfc/reference/cricheditview-class.md) 和 [CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)。  
  
 [COleServerDoc](../mfc/reference/coleserverdoc-class.md)  
 使用做為基底類別為伺服器應用程式資料分類。  `COleServerDoc` 物件的互動的大部分伺服器支援以 [COleServerItem](../mfc/reference/coleserveritem-class.md) 物件。  使用類別庫的文件\/檢視架構，視覺化編輯功能提供。  
  
 [CHtmlEditDoc](../mfc/reference/chtmleditdoc-class.md)  
 搭配 [CHtmlEditView](../mfc/reference/chtmleditview-class.md)，在 MFC 的文件檢視架構內容中提供 WebBrowser HTML 編輯平台的功能。  
  
## 相關類別  
 文件換句話說，物件可以是保留的\-\-的類別可以為存放媒體寫入其狀態和讀取它。  MFC 提供 `CArchive` 類別有助於將文件的資料到存放媒體。  
  
 [CArchive](../mfc/reference/carchive-class.md)  
 與實作持續性儲存體的 [C 檔案](../mfc/reference/cfile-class.md) 物件共同作業的物件可以還原序列化時 \(請參閱 [CObject::Serialize](../Topic/CObject::Serialize.md)\)。  
  
 文件也可以包含 OLE 物件。  `CDocItem` 是伺服器和用戶端項目的基底類別。  
  
 [CDocItem](../mfc/reference/cdocitem-class.md)  
 [COleClientItem](../mfc/reference/coleclientitem-class.md) 和 [COleServerItem](../mfc/reference/coleserveritem-class.md)抽象基底類別。  衍生自 `CDocItem` 的類別物件代表文件的部分。  
  
## 請參閱  
 [類別概觀](../mfc/class-library-overview.md)