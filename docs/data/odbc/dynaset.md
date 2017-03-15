---
title: "動態集 | Microsoft Docs"
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
  - "資料指標程式庫 [ODBC], 動態集可用性"
  - "資料指標 [ODBC], 動態集中索引鍵集驅動型資料指標"
  - "動態集"
  - "動態集中索引鍵集驅動型資料指標"
  - "ODBC 資料指標程式庫 [ODBC], 動態集"
  - "ODBC 資料錄集, 動態集"
  - "資料錄集 [C++], 動態集"
ms.assetid: 2867e6be-208e-4fe7-8bbe-b8697cb1045c
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 動態集
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個主題會說明動態集 \(Dynaset\)，並討論它們的[可用性](#_core_availability_of_dynasets)。  
  
> [!NOTE]
>  本主題適用於 MFC ODBC 類別，包含 [CRecordset](../../mfc/reference/crecordset-class.md)。  如需 DAO 類別動態集的詳細資訊，請參閱 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)。  您可以使用 DAO 來開啟動態集類型的資料錄集。  
  
 動態集是指具有動態屬性的資料錄集。  動態集模式 \(通常稱為一個動態集\) 的資料錄集物件會在其存留期 \(Lifetime\) 期間，以下述方式與資料來源保持同步。  在多使用者環境下，其他使用者可能會編輯或刪除您動態集中的資料錄，或將資料錄加入至動態集呈現的資料表。  您的應用程式從資料錄集所加入或刪除的資料錄會反映在您的動態集中。  其他使用者在資料表上加入的資料錄，並不會反映在動態集，必須等到您呼叫動態集的 **Requery** 成員函式進行重建之後，才會反映。  當其他使用者刪除資料錄時，MFC 程式碼會略過資料錄集的刪除部分。  一旦您捲動至受到影響的資料錄時，其他使用者對現存資料錄的編輯就會反映在您的動態集中。  
  
 相同地，您在動態集中所做的編輯會反映在其他使用者正在使用的動態集中。  您所加入的資料錄將在其他使用者重新查詢其動態集時才會反映。  您所刪除的資料錄在其他使用者的資料錄集中將標記成「已刪除」。  若您擁有相同資料庫的多個連接 \(多個 `CDatabase` 物件\)，則這些連接的相關資料錄集的狀態就會與其他使用者資料錄集相同。  
  
 當資料必須是動態時，動態集會是最有價值的，例如在航空預訂系統中。  
  
> [!NOTE]
>  若要使用動態集，您的資料來源所使用的 ODBC 驅動程式必須能夠支援動態集，且不可以載入 ODBC 資料指標程式庫。  如需詳細資訊，請參閱[動態集的可用性](#_core_availability_of_dynasets)。  
  
 若要指定某一資料錄集成為動態集，請將 **CRecordset::dynaset** 當做第一個參數傳遞到您的資料錄集物件的 **Open** 成員函式。  
  
> [!NOTE]
>  針對可更新的動態集，您的 ODBC 驅動程式必須支援已定位的更新陳述式或 **::SQLSetPos** ODBC API 函式。  MFC 會在兩者都可支援情況下，使用效能較高的 **::SQLSetPos**。  
  
##  <a name="_core_availability_of_dynasets"></a> 動態集的可用性  
 MFC 資料庫類別會在符合下列需求時支援動態集：  
  
-   ODBC 資料指標程式庫 DLL 一定不能用在這個資料來源上。  
  
     若使用資料指標程式庫，其會遮罩動態集支援所需的某些 ODBC 驅動程式功能。  如果您希望使用動態集 \(且您的 ODBC 驅動程式就像本章節其他內容所述，具有動態集的所需功能\)，您就可以在建立 `CDatabase` 物件時使 MFC 不要載入資料指標程式庫。  如需詳細資訊，請參閱 [ODBC](../../data/odbc/odbc-basics.md) 和 [OpenEx](../Topic/CDatabase::OpenEx.md) 或 `CDatabase` 類別的 [Open](../Topic/CDatabase::Open.md) 成員函式。  
  
     在 ODBC 詞彙中，動態集和快照集都是指資料指標。  資料指標是一種可用於儲存其在資料錄集位置的機制。  
  
-   您的資料來源使用的 ODBC 驅動程式必須支援索引鍵集驅動 \(Keyset\-Driven\) 的資料指標。  
  
     索引鍵集驅動資料指標可以藉取得和儲存一組索引鍵來管理資料表的資料。  索引鍵可以在使用者捲動到特定資料錄時，用來取得來自資料表的目前資料。  若要決定您的驅動程式是否提供這項支援，請以 **SQL\_SCROLL\_OPTIONS** 參數呼叫 **::SQLGetInfo** ODBC API 函式。  
  
     若您嘗試在不具索引鍵集 \(Keyset\) 情況下開啟一個動態集，您將會得到一個帶有傳回碼值為 **AFX\_SQL\_ERROR\_DYNASET\_NOT\_SUPPORTED** 的 `CDBException`。  
  
-   您的資料來源的 ODBC 驅動程式必須能夠支援擴充擷取 \(Extended Fetch\)。  
  
     擴充擷取是可以在 SQL 查詢的結果資料錄上向後、向前捲動的功能。  若要決定您的驅動程式是否可支援這種功能，請以 **SQL\_API\_SQLEXTENDEDFETCH** 參數呼叫 **::SQLGetFunctions** ODBC API 函式。  
  
 若您希望使用可更新的動態集 \(或是在相同情況下的快照集\)，您的 ODBC 驅動程式必須也支援 **::SQLSetPos** ODBC API 函式或定位更新。  這個 **::SQLSetPos** 函式允許 MFC 在未傳送 SQL 陳述式情形下更新資料來源。  若可以使用這項支援，MFC 會優先使用它來以 SQL 製作更新。  若要決定您的驅動程式是否可支援 **::SQLSetPos**，請以 **SQL\_POS\_OPERATIONS** 參數呼叫 **::SQLGetInfo**。  
  
 定位更新會以 SQL 語法 \(形式為 **WHERE CURRENT OF** \<cursorname\>\) 來識別資料來源資料表的特定資料列。  若要決定您的驅動程式是否支援定位更新，請以 **SQL\_POSITIONED\_STATEMENTS** 參數呼叫 **::SQLGetInfo**。  
  
 一般說來，MFC 動態集 \(不適用順向 \(Forward\-only\) 資料錄集\) 需要一個具有層級 2 一致性的 ODBC 驅動程式。  如果您的資料來源的驅動程式符合層級 1 API 集，您仍然可以使用同時為可更新和唯讀的快照集和順向的資料錄集，但不可使用動態集。  但是一個層級 1 驅動程式若是可以支援擴充擷取和索引鍵集驅動資料指標，就可支援動態集。  如需 ODBC 一致性層級的詳細資訊，請參閱 [ODBC](../../data/odbc/odbc-basics.md)。  
  
> [!NOTE]
>  如果您想要使用快照集和動態集，就必須將它們建立在兩個不同的 `CDatabase` 物件上 \(兩種不同的連接\)。  
  
 與使用 ODBC 資料指標程式庫所維持的中繼儲存體之快照集不同，動態集會在您一捲動到一資料錄時，就直接從資料來源擷取該筆資料錄。  這樣便可為原本由動態集選取的資料錄與資料來源保持同步。  
  
 如需本版 Visual C\+\+ 中所包含 ODBC 驅動程式的清單，以及取得其他驅動程式的詳細資訊，請參閱 [ODBC 驅動程式清單](../../data/odbc/odbc-driver-list.md)。  
  
## 請參閱  
 [開放式資料庫連接 \(ODBC\)](../../data/odbc/open-database-connectivity-odbc.md)