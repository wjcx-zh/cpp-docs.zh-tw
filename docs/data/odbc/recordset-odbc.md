---
title: "資料錄集 (ODBC) | Microsoft Docs"
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
  - "動態資料錄集"
  - "動態集"
  - "順向類型資料錄集"
  - "ODBC 資料錄集"
  - "ODBC 資料錄集, CRecordset 物件"
  - "資料錄集, 關於資料錄集"
  - "資料錄集, 建立"
  - "資料錄集, 動態集"
  - "資料錄集, 快照"
  - "快照, ODBC 資料錄集"
ms.assetid: 333337c5-575e-4d26-b5f6-47166ad7874d
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 資料錄集 (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本文件適用於 MFC ODBC 類別。  
  
 [CRecordset](../../mfc/reference/crecordset-class.md) 物件代表選取自資料來源的資料錄集。  資料錄可以來自：  
  
-   資料表。  
  
-   查詢。  
  
-   存取一個或多個資料表的預存程序 \(Stored Procedure\)。  
  
 「所有的顧客」是根據資料表所建立的資料錄集範例，其將存取「顧客」資料表。  「Joe Smith 的所有發票」是一個查詢範例。「所有違法的帳戶」是根據預存程序 \(有時稱作預先定義查詢 \(Predefined Query\)\) 所建立的資料錄集範例，其會叫用 \(Invoke\) 後端資料庫內的預存程序。  資料錄集可聯結 \(Join\) 兩個以上來自相同資料來源的資料表，但卻不能聯結不同資料來源的資料表。  
  
> [!NOTE]
>  如需使用精靈來衍生資料錄集類別的詳細資訊，請參閱[加入 MFC ODBC 消費者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)和 [MFC 應用程式精靈、資料庫支援](../../mfc/reference/database-support-mfc-application-wizard.md)。  
  
> [!NOTE]
>  某些 ODBC 驅動程式支援資料庫檢視。  此處的檢視意指使用 SQL `CREATE VIEW` 陳述式 \(Statement\) 來建立查詢。  目前精靈並不支援檢視，但您仍可以自行編寫程式完成此項支援。  
  
##  <a name="_core_recordset_capabilities"></a> 資料錄集功能  
 所有的資料錄集物件 \(Recordset Object\) 共用下列功能：  
  
-   如果資料來源不是唯讀，您可將資料錄集指定為[可更新](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)、[可附加](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)或唯讀。  如果資料錄集可更新，您可選擇封閉式 \(Pessimistic\) 鎖定或開放式 \(Optimistic\) 的[鎖定](../../data/odbc/recordset-locking-records-odbc.md)方法，驅動程式會提供適用的鎖定支援。  資料來源若是唯讀，資料錄集將會是唯讀。  
  
-   您可呼叫成員 \(Member\) 函式以[捲動](../../data/odbc/recordset-scrolling-odbc.md)選取的資料錄。  
  
-   您可[篩選](../../data/odbc/recordset-filtering-records-odbc.md)資料錄以便從可用的資料錄中條件約束要選取的資料錄。  
  
-   您可根據一或多個資料行，依照遞增或遞減順序來[排序](../../data/odbc/recordset-sorting-records-odbc.md)資料錄。  
  
-   您可以[參數化](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)資料錄集以便在執行階段中限定資料錄集選取範圍。  
  
##  <a name="_core_snapshots_and_dynasets"></a> 快照集和動態集  
 有兩個主要的資料錄集類型：[快照集](../../data/odbc/snapshot.md)和[動態集](../../data/odbc/dynaset.md)。  `CRecordset` 類別支援這兩種資料錄集。  每種資料錄集會共用所有資料錄集的一般特性，但每種資料錄集也會以自身的特殊方法來擴充通用功能。  快照集 \(Snapshot\) 提供資料的靜態檢視，它可用於報表和其他您想要檢視特定時間內存在資料時。  當您希望不需重新查詢或重新整理資料錄集，就可在資料錄集內看見其他使用者所做的更新時，便可以使用動態集 \(Dynaset\)。  快照集和動態集可以是可更新的或唯讀的。  若要反映其他使用者所加入或刪除的資料錄，請呼叫 [CRecordset::Requery](../Topic/CRecordset::Requery.md)。  
  
 `CRecordset` 也允許其他兩個資料錄集類型：動態 \(Dynamic\) 資料錄集和順向 \(Forward\-only\) 資料錄集。  動態資料錄集與動態集相似；然而，動態資料錄集並不需要呼叫 `CRecordset::Requery` 便可反映所有加入或刪除的資料錄。  基於這個理由，動態資料錄集通常會耗上較多的 DBMS 處理時間，而許多 ODBC 驅動程式也不支援這種資料錄集。  反之，順向資料錄集提供不需更新或向後捲動的資料錄集，最有效率的資料存取方法。  例如，您可使用順向資料錄集將資料由一個資料來源遷移到另一個來源，此時您只要順向移動資料即可。  若要使用順向資料錄集，您必須完成以下兩個步驟：  
  
-   將 **CRecordset::forwardOnly** 選項當成 [Open](../Topic/CRecordset::Open.md) 成員函式的 `nOpenType` 參數傳遞。  
  
-   指定在 **Open** 的 `dwOptions` 參數中的 **CRecordset::readOnly**。  
  
    > [!NOTE]
    >  如需動態集支援的 ODBC 驅動程式需求的詳細資訊，請參閱 [ODBC](../../data/odbc/odbc-basics.md)。  如需本版 Visual C\+\+ 中所包含 ODBC 驅動程式的清單，以及取得其他驅動程式的詳細資訊，請參閱 [ODBC 驅動程式清單](../../data/odbc/odbc-driver-list.md)。  
  
##  <a name="_core_your_recordsets"></a> 您的資料錄集  
 對於想要存取的每個不同資料表、檢視或預存程序，通常會需要定義衍生自 `CRecordset` 的類別 \(資料庫聯結是一個例外，聯結中的一個資料錄集代表來自兩個或更多個資料表的資料行\)。當您在衍生資料錄集類別時，您會啟用類似於對話資料交換 \(DDX\) 機制的資料錄欄位交換 \(RFX\) 機制或大量資料錄欄位交換 \(Bulk RFX\) 機制。  RFX 和 Bulk RFX 可以簡化從資料來源傳輸資料至您的資料錄集的動作；另外 RFX 還可將資料由您的資料錄集傳送至資料來源。  如需詳細資訊，請參閱[資料錄欄位交換 \(RFX\)](../../data/odbc/record-field-exchange-rfx.md) 和[資料錄集：擷取大量資料錄 \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 資料錄集物件讓您可存取所有選取的資料錄。  您可使用例如 `MoveNext` 和 `MovePrev` 的 `CRecordset` 成員函式，在多筆選取的資料錄間捲動。  資料錄集物件在相同時間內只能表示一筆選取的資料錄，即目前資料錄。  您可藉由宣告與資料庫查詢所得到的資料表或資料錄資料行的相對應資料錄集類別成員變數，檢查目前資料錄的欄位。  如需資料錄集資料成員的詳細資訊，請參閱[資料錄集：架構 \(ODBC\)](../../data/odbc/recordset-architecture-odbc.md)。  
  
 下列主題說明使用資料錄集物件的詳細資料：  這些主題會依照功能分類和容許循序讀取的自然瀏覽順序列出。  
  
### 開啟、讀取和關閉資料錄集機制的主題  
  
-   [資料錄集：架構 \(ODBC\)](../../data/odbc/recordset-architecture-odbc.md)  
  
-   [資料錄集：宣告資料表的類別 \(ODBC\)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)  
  
-   [資料錄集：建立和關閉資料錄集 \(ODBC\)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)  
  
-   [資料錄集：捲動 \(ODBC\)](../../data/odbc/recordset-scrolling-odbc.md)  
  
-   [資料錄集：書籤和絕對位置 \(ODBC\)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)  
  
-   [資料錄集：篩選資料錄 \(ODBC\)](../../data/odbc/recordset-filtering-records-odbc.md)  
  
-   [資料錄集：排序資料錄 \(ODBC\)](../../data/odbc/recordset-sorting-records-odbc.md)  
  
-   [資料錄集：參數化資料錄集 \(ODBC\)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)  
  
### 修改資料錄集機制的主題  
  
-   [資料錄集：加入、更新和刪除資料錄 \(ODBC\)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)  
  
-   [資料錄集：鎖定資料錄 \(ODBC\)](../../data/odbc/recordset-locking-records-odbc.md)  
  
-   [資料錄集：重新查詢資料錄集 \(ODBC\)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)  
  
### 進階技術的主題  
  
-   [資料錄集：執行聯結 \(ODBC\)](../../data/odbc/recordset-performing-a-join-odbc.md)  
  
-   [資料錄集：宣告預先定義查詢的類別 \(ODBC\)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)  
  
-   [資料錄集：動態地繫結資料行 \(ODBC\)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)  
  
-   [資料錄集：擷取大量資料錄 \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)  
  
-   [資料錄集：使用大型的資料項目 \(ODBC\)](../../data/odbc/recordset-working-with-large-data-items-odbc.md)  
  
-   [資料錄集：取得 SUM 和其他彙總結果 \(ODBC\)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)  
  
### 資料錄集運作的主題  
  
-   [資料錄集：資料錄集選取資料錄的方式 \(ODBC\)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)  
  
-   [資料錄集：資料錄集更新資料錄的方式 \(ODBC\)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)  
  
## 請參閱  
 [開放式資料庫連接 \(ODBC\)](../../data/odbc/open-database-connectivity-odbc.md)   
 [MFC ODBC 消費者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)   
 [異動 \(ODBC\)](../../data/odbc/transaction-odbc.md)