---
title: "主動式文件伺服程式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "主動式文件伺服程式 [C++]"
  - "主動式文件 [C++], 伺服器"
  - "伺服器 [C++], 主動式文件"
ms.assetid: 131fec1e-02a0-4305-a7ab-903b911232a7
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 主動式文件伺服程式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

主動式文件伺服程式，例如 Word、Excel、PowerPoint 其他應用程式類型的主應用程式呼叫文件中的文件。  不同於其他資料的網頁顯示的 OLE 內嵌物件，主動式文件提供建立它們的伺服器應用程式的完整介面和完成原生功能。  使用者建立文件使用它們最愛的應用程式的完整功能 \(如果有啟用主動式文件\)，可以將產生的專案作為單一實體。  
  
 現用文件可能有多個網頁而且永遠就地啟動。  使用者介面的現用文件控制項區段，結合其功能表與容器的 **File** 和 **Help** 功能表。  它們佔用容器的整個編輯區域和控制項檢視和印表機頁面 \(框線，頁尾的配置，依此類推\)。  
  
 MFC 實作具有文件\/檢視介面、命令分派對應、列印、功能表和管理登錄的管理主動式文件伺服程式。  特定程式設計需要在 [現用文件](../mfc/active-documents.md)中討論。  
  
 MFC 支援使用 [CDocObjectServer](../mfc/reference/cdocobjectserver-class.md) 類別的現用文件，衍生自 [CCmdTarget](../mfc/reference/ccmdtarget-class.md)和 [CDocObjectServerItem](../mfc/reference/cdocobjectserveritem-class.md)，衍生自 [COleServerItem](../mfc/reference/coleserveritem-class.md)。  MFC 支援 [COleDocObjectItem](../mfc/reference/coledocobjectitem-class.md) 類別的主動式文件容器，衍生自 [COleClientItem](../mfc/reference/coleclientitem-class.md)。  
  
 `CDocObjectServer` 將現用文件介面和初始化並啟動現用文件。  MFC 也提供巨集來處理現用文件上的命令路由。  若要使用現用文件中的應用程式，請包含 AfxDocOb.h StdAfx.h 檔。  
  
 一般 MFC 伺服器連接其 `COleServerItem`衍生類別。  如果您選取 **Mini\-server** 和 **Full\-server** 核取方塊可讓您的應用程式伺服器複合文件支援，則是 MFC 應用程式精靈所產生的類別。  如果您同時選取 **Active document server** 核取方塊， MFC 應用程式精靈產生衍生自 `CDocObjectServerItem` 的類別。  
  
 `COleDocObjectItem` 類別允許 OLE 容器變成主動式文件容器。  您可以使用 MFC 應用程式精靈可選取 MFC 應用程式精靈的複合文件支援網頁的 **Active document container** 核取方塊建立主動式文件容器。  如需詳細資訊，請參閱 [建立主動式文件容器應用程式](../mfc/creating-an-active-document-container-application.md)。  
  
## 請參閱  
 [主動式文件內含項目](../mfc/active-document-containment.md)