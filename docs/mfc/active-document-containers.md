---
title: "主動式文件容器 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- active documents [MFC], containers
- active document containers [MFC]
- containers [MFC], active document
- MFC COM, active document containment
ms.assetid: ba20183a-8b4c-440f-9031-e5fcc41d391b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 87546f3c02025438b3e60cd2038fdc885dfedf9f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="active-document-containers"></a>主動式文件容器
主動式文件容器，例如 Microsoft Office Binder 或 Internet Explorer 中，可讓您能夠使用不同的應用程式類型 （而不是強迫您建立及使用多個應用程式框架每個在單一的範圍內的數個文件文件類型）。  
  
 MFC 提供完整支援主動式文件容器中`COleDocObjectItem`類別。 您可以使用 MFC 應用程式精靈來建立主動式文件容器選取**主動式文件容器** 核取方塊**複合文件支援**MFC 應用程式精靈頁面。 如需詳細資訊，請參閱[建立主動式文件容器應用程式](../mfc/creating-an-active-document-container-application.md)。  
  
 如需有關主動式文件容器的詳細資訊，請參閱：  
  
-   [容器需求](#container_requirements)  
  
-   [文件站台物件](#document_site_objects)  
  
-   [檢視站台物件](#view_site_objects)  
  
-   [框架物件](#frame_object)  
  
-   [說明功能表合併](../mfc/help-menu-merging.md)  
  
-   [以程式設計方式列印](../mfc/programmatic-printing.md)  
  
-   [命令目標](../mfc/message-handling-and-command-targets.md)  
  
##  <a name="container_requirements"></a>容器需求  
 主動式文件容器中的主動式文件支援意味著之外的其他介面實作： 也需要使用包含物件之介面的資訊。 相同適用於使用中文件的延伸模組，其中容器也必須了解如何在使用中的文件本身上使用這些延伸模組介面。  
  
 整合主動式文件的主動式文件容器必須：  
  
-   能夠處理物件的儲存體透過**IPersistStorage**介面，亦即它必須提供`IStorage`每個使用中文件的執行個體。  
  
-   支援 OLE 文件，並強迫 （文件或內嵌的每一個） 的 「 網站 」 物件的基礎內嵌功能，實作**IOleClientSite**和**IAdviseSink**。  
  
-   支援就地啟用的內嵌的物件或主動式文件。 容器的站台物件必須實作`IOleInPlaceSite`和容器的框架物件必須提供**IOleInPlaceFrame**。  
  
-   藉由實作支援主動式文件副檔名`IOleDocumentSite`提供與文件容器的機制。 容器可以選擇性地實作主動式文件介面`IOleCommandTarget`和`IContinueCallback`挑選簡單的命令，例如，列印或儲存。  
  
 框架物件、 檢視物件和容器物件可以選擇性地實作**IOleCommandTarget**中所述，支援的特定命令，分派[命令目標](../mfc/message-handling-and-command-targets.md)。 檢視和容器物件可以也可以選擇性地實作`IPrint`和`IContinueCallback`，來支援以程式設計方式列印，如下所述[以程式設計方式列印](../mfc/programmatic-printing.md)。  
  
 下圖顯示概念性的關聯性，容器和其元件 （左） 和主動式文件和它的檢視 （右邊） 之間。 主動式文件管理儲存體和資料，並檢視顯示，或選擇性的列印該資料。 以粗體顯示的介面是所需的使用中文件的參與。這些粗體和斜體是選擇性的。 需要的其他所有介面都。  
  
 ![主動式文件容器介面](../mfc/media/vc37gj1.gif "vc37gj1")  
  
 支援單一檢視的文件上單一實體類別可實作檢視 」 和 「 文件的元件 （亦即，其對應的介面）。 此外，只支援一次一個檢視的容器網站可以合併文件及檢視網站的單一實體站台的類別。 容器的框架物件，不過，仍然必須不同，和容器的文件元件只是本文提及來提供完整的架構。它不會受到現用文件內含項目結構。  
  
##  <a name="document_site_objects"></a>文件站台物件  
 在使用中文件內含項目架構中，文件網站等同於用戶端站台物件中 OLE 文件加上的`IOleDocument`介面：  
  
 `interface IOleDocumentSite : IUnknown`  
  
 `{`  
  
 `HRESULT ActivateMe(IOleDocumentView *pViewToActivate);`  
  
 `}`  
  
 文件網站的概念中一或多個 「 檢視網站 」 物件的容器。 每個檢視站台物件是由文件網站管理的文件的個別檢視物件與相關聯。 如果容器僅支援單一檢視每個文件網站，然後它可以實作在文件網站，檢視站台與單一具象類別。  
  
##  <a name="view_site_objects"></a>檢視站台物件  
 容器的檢視站台物件會管理文件的特定檢視的顯示空間。 除了支援標準`IOleInPlaceSite`介面，檢視站台通常也會實作`IContinueCallback`以程式設計方式列印控制項。 (請注意，永遠不會查詢檢視物件`IContinueCallback`讓它可以實際實作上容器成員的任何物件。)  
  
 支援多個檢視的容器必須能夠建立多個檢視的文件網站內的站台物件。 這會提供每個檢視與個別啟用和停用服務透過提供`IOleInPlaceSite`。  
  
##  <a name="frame_object"></a>框架物件  
 容器的框架物件時，大部分的情況下，相同的框架，也就是用於 OLE 文件，在就地啟用，它會處理功能表和工具列的交涉。 檢視物件具有存取此框架物件，透過**IOleInPlaceSite::GetWindowContext**，也可存取容器物件，表示容器文件 （它可以處理層級 窗格工具列交涉與包含的物件的列舉型別）。  
  
 主動式文件容器可以藉由新增擴充框架`IOleCommandTarget`。 這可讓它能夠接收肇因於使用中文件的使用者介面，這個介面可以讓容器傳送相同的命令的方式相同的命令 (例如**開新檔案**，**開啟**， **將儲存為**，**列印**;**編輯複本**，**貼上**，**復原**，等等) 目前的文件。 如需詳細資訊，請參閱[命令目標](../mfc/message-handling-and-command-targets.md)。  
  
## <a name="see-also"></a>請參閱  
 [主動式文件內含項目](../mfc/active-document-containment.md)

