---
title: "文件類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.classes.document
dev_langs:
- C++
helpviewer_keywords:
- document classes [MFC]
ms.assetid: 4bf19b02-0a4f-4319-b68e-cddcba2705cb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5a2436b46b7486bd30398dffc530d2adea3d2e48
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="document-classes"></a>文件類別
建立的文件範本物件的文件類別物件來管理應用程式的資料。 您將會從這些類別的其中一個，您的文件衍生類別。  
  
 檢視物件的文件類別物件互動。 檢視物件表示視窗工作區、 顯示文件的資料，並允許使用者與它互動。 文件範本物件會建立文件和檢視。  
  
 [CDocument](../mfc/reference/cdocument-class.md)  
 應用程式特定文件的基底類別。 衍生您的文件類別或類別從**CDocument**。  
  
 [COleDocument](../mfc/reference/coledocument-class.md)  
 用於複合文件的實作，以及基本的容器支援。 做為容器類別，衍生自[CDocItem](../mfc/reference/cdocitem-class.md)。 這個類別可用來當作基底類別的文件容器中，是基底類別`COleServerDoc`。  
  
 [COleLinkingDoc](../mfc/reference/colelinkingdoc-class.md)  
 類別衍生自`COleDocument`所提供的基礎結構連結。 您應該為容器應用程式而不是從這個類別衍生的文件類別`COleDocument`如果您想要支援內嵌物件連結。  
  
 [CRichEditDoc](../mfc/reference/cricheditdoc-class.md)  
 維護 rich edit 控制項中的 OLE 用戶端項目的清單。 搭配[CRichEditView](../mfc/reference/cricheditview-class.md)和[CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)。  
  
 [COleServerDoc](../mfc/reference/coleserverdoc-class.md)  
 做為伺服器應用程式文件類別的基底類別。 `COleServerDoc`物件提供的伺服器支援，透過與互動大量[COleServerItem](../mfc/reference/coleserveritem-class.md)物件。 使用類別庫的文件/檢視架構來提供視覺化編輯的功能。  
  
 [CHtmlEditDoc](../mfc/reference/chtmleditdoc-class.md)  
 提供與[CHtmlEditView](../mfc/reference/chtmleditview-class.md)，HTML WebBrowser 編輯平台的 MFC 文件檢視架構內容中的功能。  
  
## <a name="related-classes"></a>相關的類別  
 文件類別物件可以是持續性 — 亦即，它們可以儲存媒體寫入其狀態和讀回。 MFC 提供`CArchive`以便將文件的資料傳輸到儲存體中的類別。  
  
 [CArchive](../mfc/reference/carchive-class.md)  
 與 cooperates [CFile](../mfc/reference/cfile-class.md)實作永續性儲存體透過序列化物件的物件 (請參閱[cobject:: Serialize](../mfc/reference/cobject-class.md#serialize))。  
  
 文件也可以包含 OLE 物件。 `CDocItem`是伺服器和用戶端項目的基底類別。  
  
 [CDocItem](../mfc/reference/cdocitem-class.md)  
 抽象基底類別的[COleClientItem](../mfc/reference/coleclientitem-class.md)和[COleServerItem](../mfc/reference/coleserveritem-class.md)。 物件的類別衍生自`CDocItem`代表文件的部分。  
  
## <a name="see-also"></a>請參閱  
 [類別概觀](../mfc/class-library-overview.md)

