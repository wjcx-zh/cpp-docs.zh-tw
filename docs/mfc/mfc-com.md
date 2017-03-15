---
title: "MFC COM | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MFC COM (MFC)"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Active 技術 [C++]"
  - "ActiveX 控制項 [C++], COM 物件模型"
  - "COM [C++], MFC 支援"
  - "MFC [C++], COM 支援"
  - "MFC ActiveX 控制項 [C++], MFC 中的 COM 支援"
  - "MFC COM [C++]"
ms.assetid: 7646bdcb-3a06-4ed5-9386-9b00f3979dcb
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# MFC COM
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 的子集是設計為支援 COM，而大部分的 Active Template Library \(ATL\) 是專為 COM 程式設計而設計的。  主題的一節的 MFC 支援 COM。  
  
 Active 技術 \(例如 ActiveX 控制項，主動式文件內含項目， OLE 等等\)，在網路環境使用元件物件模型 \(COM\) \(COM\) 使軟體元件彼此互動，不論其建立的語言。  Active 技術可用來在桌面或網際網路執行的應用程式。  如需詳細資訊請參閱 [COM 簡介](../atl/introduction-to-com.md) 或 [元件物件模型](http://msdn.microsoft.com/library/windows/desktop/ms694363)。  
  
 Active 技術包括用戶端和伺服器技術，包括:  
  
-   [現用文件內含項目](../mfc/active-document-containment.md)，支援在 MFC 4.2 版和以後，可以讓使用者檢視 [現用文件](../mfc/active-documents.md) \(例如 Microsoft Excel 或 Word 檔案\) 和啟動文件的原生應用程式的整個介面在 [主動式文件容器](../mfc/active-document-containers.md) 的整個工作區 \(例如 Microsoft Office Binder 或 Microsoft Internet Explorer。  而 [主動式文件伺服程式](../mfc/active-document-servers.md)，提供文件容器做為用戶端。  如需使用主動式文件的詳細資訊可以在網際網路應用程式，請參閱: [在網際網路上的現用文件](../mfc/active-documents-on-the-internet.md)。  
  
-   ActiveX 控制項是可以用來容器 \(例如網站的互動式物件。  如需MFC ActiveX 控制項詳細資訊，請參閱:  
  
    -   [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)  
  
    -   [網際網路上的 ActiveX 控制項](../mfc/activex-controls-on-the-internet.md)  
  
    -   [概觀:網際網路](../mfc/mfc-internet-programming-basics.md)  
  
    -   [升級現有的網際網路使用 ActiveX 控制項](../mfc/upgrading-an-existing-activex-control.md)  
  
    -   [偵錯 ActiveX 控制項](../Topic/How%20to:%20Debug%20an%20ActiveX%20Control.md)  
  
-   Active Scripting 控制一個或多個 ActiveX 控制項整合式行為從瀏覽器或伺服器的。  如需 Active Scripting 的詳細資訊，請參閱 [在網際網路上 Active 技術](../mfc/active-technology-on-the-internet.md)。  
  
-   [Automation](../mfc/automation.md)\(先前稱為 OLE Automation\) 讓應用程式能操作在另一個應用程式實作的物件，或者公開物件讓它們可以被操作。  
  
     自動化物件可以是區域或 [遠端](../mfc/remote-automation.md) \(在網路上的其他電腦進行存取\)。  Aurotmation 在 OLE 和 COM 物件皆可取得。  
  
-   使用 MFC，本節也提供如何將 COM 元件，例如在 [連接點](../mfc/connection-points.md)。  
  
 如需何種討論仍會呼叫 OLE 對哪些現在稱為 Active 技術，請參閱 [OLE](../mfc/ole-in-mfc.md)主題。  
  
 此外，請參閱知識庫文件 Q248019:HOWTO:防止伺服器忙碌對話方塊隨即出現在冗長的 COM 作業時。  
  
## 本章節內容  
 [主動式文件內含項目](../mfc/active-document-containment.md)  
  
 [Automation](../mfc/automation.md)  
  
 [遠端 Automation](../mfc/remote-automation.md)  
  
 [連接點](../mfc/connection-points.md)  
  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)  
  
## 請參閱  
 [概念](../mfc/mfc-concepts.md)