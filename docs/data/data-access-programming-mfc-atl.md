---
title: "Data Access Programming (MFC/ATL) | Microsoft Docs"
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
  - "資料 [C++], 資料存取技術"
  - "資料存取 [C++], 資料庫的類別庫"
  - "資料庫 [C++], MFC"
  - "MFC [C++], 資料存取應用程式"
  - "OLE DB [C++], 資料存取技術"
ms.assetid: def97b2c-b5a6-445f-afeb-308050fd4852
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# Data Access Programming (MFC/ATL)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ 提供數種使用資料庫的方式。  慣用方法是使用其中一種類別庫，例如 Active Template Class Library \(ATL\) 或 Microsoft Foundation Class \(MFC\) 程式庫，簡化使用資料庫 API。  
  
> [!NOTE]
>  本主題內容涵蓋可用於 Visual C\+\+ 資料庫程式設計的舊技術。  如需使用 Visual C\+\+ 和 SQL Server 2005 的資料存取程式設計資訊，請參閱[資料存取](../dotnet/data-access-using-adonet-cpp-cli.md)、[存取 Visual Studio 中的資料](../Topic/Accessing%20data%20in%20Visual%20Studio.md) 和[Creating SQL Server 2005 Objects In Managed Code](http://msdn.microsoft.com/zh-tw/5358a825-e19b-49aa-8214-674ce5fed1da)。  
  
 程式庫類別支援下列幾種資料存取：  
  
-   ATL 提供 OLE DB 範本和資料庫屬性。  
  
-   MFC 提供開放式資料庫連接 \(ODBC\) 和 ODBC 驅動程式。  
  
 這些程式庫提供抽象概念，以簡化使用資料庫，完整獲得 C\+\+ 的速度、強大功能及彈性。  它們會將您的資料存取工作與程式庫的應用程式架構加以整合。  
  
 或者，您可以從 COM、ODBC 或 DAO 軟體開發套件 \(SDK\)，直接呼叫資料庫 API 函式。  如需直接以 COM、DAO 或 ODBC API 函式進行程式設計的相關資訊，請參閱 COM SDK、DAO SDK 或 ODBC SDK。  
  
 如果您需要存取資料，請使用 ATL OLE DB，不論它是以何種形式儲存。  當您不使用 Microsoft Jet \(.mdb\) 資料庫，並且想要針對完整且獨立的資料來源使用 ODBC API，則請使用 MFC ODBC 類別。  當您想要使用 Microsoft Jet \(.mdb\) 資料庫，或使用 ODBC 資料來源之類的外部資料庫，請使用 MFC DAO 類別。  
  
> [!NOTE]
>  Microsoft 建議為新專案使用 OLE DB 或 ODBC。  DAO 應僅用於維護現有應用程式。  
  
 除了撰寫獨立的資料庫應用程式，您通常還可以在其他種類的程式中有效地使用資料庫，當做方便的儲存體和擷取媒體。  
  
|若要深入了解|請參閱|  
|------------|---------|  
|**選取資料庫技術**||  
|ODBC 與  DAO|[我應該使用 DAO 或是 ODBC？](../data/should-i-use-dao-or-odbc-q.md)|  
|使用「Microsoft 知識庫」找到由產品支援工程師所撰寫的其他資料庫主題文章。|[Microsoft 知識庫](../data/where-can-i-find-microsoft-knowledge-base-articles-on-database-topics-q.md)|  
|**ATL 資料庫支援 \(OLE DB\)**||  
|OLE DB 程式設計 \(概念性主題\)|[OLE DB 程式設計概觀](../data/oledb/ole-db-programming-overview.md)|  
|使用 OLE DB 取用者範本 \(概念性主題\)|[OLE DB 消費者樣板](../data/oledb/ole-db-consumer-templates-cpp.md)|  
|OLE DB 取用者屬性|[OLE DB 消費者屬性](../windows/ole-db-consumer-attributes.md)|  
|使用 OLE DB 提供者範本 \(概念性主題\)|[OLE DB 提供者樣板](../data/oledb/ole-db-provider-templates-cpp.md)|  
|將 OLE DB 取用者加入至 MFC 專案|[建立 OLE DB 消費者](../data/oledb/creating-an-ole-db-consumer.md)|  
|**MFC 資料庫支援 \(ODBC 和 DAO\)**||  
|什麼是 DAO 和 ODBC|[什麼是 DAO 和 ODBC？](../data/what-are-dao-and-odbc-q.md)|  
|何時使用 MFC 資料庫類別|[我何時應該使用資料庫類別？](../data/when-should-i-use-the-database-classes-q.md)|  
|深入了解 MFC 資料庫程式設計模型|[MFC 資料庫程式撰寫模型是什麼？](../data/what-is-the-mfc-database-programming-model-q.md)|  
|MFC DAO 類別和 MFC ODBC 類別間的選擇|[我應該使用 DAO 或是 ODBC？](../data/should-i-use-dao-or-odbc-q.md)|  
|您可以使用 DAO 和 ODBC 存取的資料來源|[我可以使用 DAO 和 ODBC 存取何種資料來源？](../data/what-data-sources-can-i-access-with-dao-and-odbc-q.md)|  
|開放式資料庫連接 \(ODBC\)|[ODBC 和 MFC](../data/odbc/odbc-and-mfc.md)|  
|使用類別時是否可以直接呼叫 DAO 或 ODBC API|[我可以直接呼叫 DAO 或 ODBC 嗎？](../data/can-i-call-dao-or-odbc-directly-q.md)|  
|提供哪些 ODBC 驅動程式|[ODBC 驅動程式清單](../data/odbc/odbc-driver-list.md)|  
|資料庫類別搭配 MFC 的文件\/檢視架構的運作方式|[MFC：使用具有文件和檢視的資料庫類別](../data/mfc-using-database-classes-with-documents-and-views.md)|  
|安裝 MFC 資料庫支援；預設會在 Visual C\+\+ 中安裝哪些 ODBC 驅動程式；會安裝哪些 ODBC 和 DAO SDK 元件|[安裝 MFC 資料庫支援](../data/installing-mfc-database-support.md)|  
|**資料繫結控制項 \(ADO 和 RDO\)**||  
|撰寫使用資料繫結控制項的程式|[資料繫結控制項 \(ADO 和 RDO\)](../data/ado-rdo/data-bound-controls-ado-and-rdo.md)|  
|使用 ActiveX 控制項的資料繫結|[MFC ActiveX 控制項：在 ActiveX 控制項中使用資料繫結](../mfc/mfc-activex-controls-using-data-binding-in-an-activex-control.md)|  
|散發 ActiveX 控制項|[MFC ActiveX 控制項：散發 ActiveX 控制項](../mfc/mfc-activex-controls-distributing-activex-controls.md)|  
  
## 請參閱  
 [資料存取](../Topic/Data%20Access%20in%20Visual%20C++.md)