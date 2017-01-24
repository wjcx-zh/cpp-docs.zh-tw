---
title: "主動式文件容器 | Microsoft Docs"
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
  - "主動式文件容器 [C++]"
  - "主動式文件 [C++], 容器"
  - "容器 [C++], 主動式文件"
  - "MFC COM [C++], 主動式文件內含項目"
ms.assetid: ba20183a-8b4c-440f-9031-e5fcc41d391b
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 主動式文件容器
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用中文件容器，例如 Microsoft Office Binder 或 Internet Explorer，可讓您使用不同的應用程式類型的幾個資料一起使用單一框架內 \(而不是強制您為每個資料型別建立和使用多個應用程式框架\)。  
  
 MFC 會在 `COleDocObjectItem` 類別中的主動式文件容器提供完整的支援。  您可以使用 MFC 應用程式精靈可選取 MFC 應用程式精靈的頁面 **Compound Document Support** 的 **Active document container** 核取方塊建立主動式文件容器。  如需詳細資訊，請參閱 [建立主動式文件容器應用程式](../mfc/creating-an-active-document-container-application.md)。  
  
 如需主動式文件容器的詳細資訊，請參閱:  
  
-   [容器要求](#container_requirements)  
  
-   [文件的站台物件。](#document_site_objects)  
  
-   [檢視的站台物件。](#view_site_objects)  
  
-   [框架物件](#frame_object)  
  
-   [說明功能表合併](../mfc/help-menu-merging.md)  
  
-   [以程式設計方式列印](../mfc/programmatic-printing.md)  
  
-   [命令目標。](../mfc/message-handling-and-command-targets.md)  
  
##  <a name="container_requirements"></a> 容器要求  
 在主動式文件容器的主動式文件支援隱含多個介面實作:它也要求使用內含物件的介面知識。  同樣地套用至現用文件副檔名，容器必須也會使用中文件的那些擴充介面。  
  
 將現用文件的主動式文件容器必須:  
  
-   能夠處理物件儲存體上傳遞 **IPersistStorage** 介面，也就是說，它必須提供 `IStorage` 執行個體寫入每個現用文件。  
  
-   支援 OLE 文件基礎內嵌功能，需要「網站」物件 \(每個檔案或內嵌\) 實作 **IOleClientSite** 和 **IAdviseSink**。  
  
-   內嵌物件或現用文件的支援就地啟動。  容器的站台物件必須實作 `IOleInPlaceSite` ，且容器的框架物件必須提供 **IOleInPlaceFrame**。  
  
-   藉由實作 `IOleDocumentSite` 為容器提供這個機制支援主動式文件的副檔名與文件溝通。  或者，容器可以實作主動式文件介面 `IOleCommandTarget` 和 `IContinueCallback` 的簡單命令 \(如列印或儲存。  
  
 框架物件、檢視物件和容器物件可以選擇性地實作 **IOleCommandTarget** 支援某些命令分派，如 [命令目標。](../mfc/message-handling-and-command-targets.md)所述。  檢視和容器物件可以選擇性地也會實作 `IPrint` 和 `IContinueCallback`，支援以程式設計方式列印，如 [以程式設計方式列印](../mfc/programmatic-printing.md)所述。  
  
 下圖顯示容器及其元件之間的關聯性 \(左側\) 和現用文件及其檢視 \(在右邊\)。  現用文件處理儲存和資料，因此，這個檢視會顯示或選擇性資料的列印。  以粗體介面是針對現用文件參與所需的項目;這些粗體和斜體是選擇性的。  需要其他介面。  
  
 ![主動式文件容器介面](../mfc/media/vc37gj1.png "vc37gj1")  
  
 只支援一個檢視的資料可以實作檢視和文件組件 \(即其對應介面\) 在單一具象類別。  此外，一次只支援一個檢視的容器站台可以合併文件網站和檢視網站結合成單一特定網站類別。  容器的框架物件，不過，必須維持不同，因此，容器的文件組件只包含此處為結構的完整圖片;它不會影響現用文件內含項目的結構。  
  
##  <a name="document_site_objects"></a> 文件的站台物件。  
 在現用文件內含項目架構中，文件網站相同為 OLE 文件的用戶端站台物件加入 `IOleDocument` 介面:  
  
 `interface IOleDocumentSite : IUnknown`  
  
 `{`  
  
 `HRESULT ActivateMe(IOleDocumentView *pViewToActivate);`  
  
 `}`  
  
 文件網站概念上是一個或更多的容器檢視網站」物件。  每個檢視站台物件與 Managed 文件的個別檢視物件由文件網站。  如果容器只支援單一檢視每個文件網站，則它可以實作文件網站和檢視網站有單一特定類別的。  
  
##  <a name="view_site_objects"></a> 檢視的站台物件。  
 容器的檢視站台物件來處理資料的特定檢視的顯示空間。  除了支援標準 `IOleInPlaceSite` 介面之外，檢視網站通常也會實作以程式設計方式列印控制項的 `IContinueCallback` 。\(請注意 `IContinueCallback` ，因此它在未檢視物件查詢在所有物件會實際實作容器所需\)。  
  
 支援多個檢視的容器必須可以在文件網站內的多個檢視站台物件。  這提供每個檢視以個別啟動和停用服務所提供透過 `IOleInPlaceSite`。  
  
##  <a name="frame_object"></a> 框架物件  
 容器的框架物件是，至於大部分，就地啟動在 OLE 文件，也就是說，該使用處理功能表和工具列交涉的相同框架。  檢視物件存取這個物件的傳遞 **IOleInPlaceSite::GetWindowContext**，也提供對代表容器文件 \(的容器物件可以處理窗格層級工具列交涉和包含的物件列舉型別\)。  
  
 主動式文件容器可以將 `IOleCommandTarget`擴大框架。  這可讓它接收方式來自現用文件的使用者介面的命令這個介面可讓容器傳送相同的命令 \(例如 **File New**， **Open**， \[**儲存**\]， **Print**; **Edit Copy**和 **Paste**和 **Undo**， other\) 至現用文件。  如需詳細資訊，請參閱 [命令目標。](../mfc/message-handling-and-command-targets.md)。  
  
## 請參閱  
 [主動式文件內含項目](../mfc/active-document-containment.md)