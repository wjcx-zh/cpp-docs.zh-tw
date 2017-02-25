---
title: "CDaoQueryDefInfo 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDaoQueryDefInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDaoQueryDefInfo 結構"
  - "DAO (資料存取物件), QueryDefs 集合"
ms.assetid: e20837dc-e78d-4171-a195-1b4075fb5d2a
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# CDaoQueryDefInfo 結構
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

如需資料存取定義的 querydef 物件的 `CDaoQueryDefInfo` 結構中的物件 \(DAO\)。  
  
## 語法  
  
```  
  
      struct CDaoQueryDefInfo  
{  
   CString m_strName;               // Primary  
   short m_nType;                   // Primary  
   COleDateTime m_dateCreated;      // Secondary  
   COleDateTime m_dateLastUpdated;  // Secondary  
   BOOL m_bUpdatable;               // Secondary  
   BOOL m_bReturnsRecords;          // Secondary  
   CString m_strSQL;                // All  
   CString m_strConnect;            // All  
   short m_nODBCTimeout;            // All  
};  
```  
  
#### 參數  
 `m_strName`  
 唯一命名 querydef 物件。  如需詳細資訊，請參閱主題「Name 屬性 DAO 說明。  呼叫直接擷取這個屬性的 [CDaoQueryDef::GetName](../Topic/CDaoQueryDef::GetName.md) 。  
  
 `m_nType`  
 表示 querydef 物件之作業類型的值。  值可以是下列其中一項:  
  
-   選取**dbQSelect** —查詢選取資料錄。  
  
-   **dbQAction** 動作—查詢移動或變更資料，但不會傳回資料錄。  
  
-   **dbQCrosstab** Crosstab —查詢傳回在類似報表之格式的資料。  
  
-   **dbQDelete** 刪除—查詢刪除一組指定的行。  
  
-   **dbQUpdate** 更新—查詢變更一組資料錄。  
  
-   **dbQAppend** 附加—查詢加入新資料錄加入至資料表或查詢的結尾。  
  
-   **dbQMakeTable** Make Table —查詢會從資料錄集的新資料表。  
  
-   **dbQDDL** 資料定義—查詢影響資料表或其部分結構。  
  
-   **dbQSQLPassThrough** 傳遞— SQL 陳述式會直接傳遞至的資料庫後端，，而不會處理。  
  
-   **dbQSetOperation** —整合式查詢建立包含來自所有指定的資料錄的快照型資料錄集物件資料以移除任何重複記錄的兩個或多個資料表中。  若要包含迴圈，請在 querydef 的 SQL 陳述式的關鍵字 **ALL** 。  
  
-   **dbQSPTBulk** 和 **dbQSQLPassThrough** 使用指定不傳回資料錄的查詢。  
  
> [!NOTE]
>  若要建立 SQL 傳遞查詢，任何未設定 **dbQSQLPassThrough** 常數。  當您建立 querydef 物件並設定連接屬性時，這就是 Microsoft Jet 資料庫引擎自動設定。  
  
 如需詳細資訊，請參閱主題 DAO 說明的型別屬性。  
  
 `m_dateCreated`  
 querydef 的建立日期和時間。  直接擷取 querydef 建立的日期，呼叫 `CDaoTableDef` 物件的 [GetDateCreated](../Topic/CDaoTableDef::GetDateCreated.md) 成員函式與資料表。  請參閱底下的註解以取得詳細資訊。  請參閱本主題 DateCreated 「， LastUpdated 屬性 DAO 說明。  
  
 `m_dateLastUpdated`  
 所做的最新變更的日期和時間轉換為 querydef。  直接擷取資料表的上次更新的日期，請呼叫 querydef 的 [GetDateLastUpdated](../Topic/CDaoQueryDef::GetDateLastUpdated.md) 成員函式。  請參閱底下的註解以取得詳細資訊。  並請參閱本主題 DateCreated 「， LastUpdated 屬性 DAO 說明。  
  
 `m_bUpdatable`  
 指出變更是否可以對 querydef 物件。  如果這個屬性是 **TRUE**， querydef 可更新;否則，它不是。  可更新可以變更表示 querydef 物件的查詢定義。  querydef 物件之可更新的屬性設定為 **TRUE** ，如果查詢定義可以更新，即使，產生的資料錄集不可更新。  若要直接擷取這個屬性，請呼叫 querydef 的 [CanUpdate](../Topic/CDaoQueryDef::CanUpdate.md) 成員函式。  如需詳細資訊，請參閱主題可更新的屬性 DAO 說明。  
  
 *m\_bReturnsRecords*  
 表示外部資料庫的 SQL 傳遞查詢是否傳回資料錄。  如果這個屬性是 **TRUE**，查詢傳回資料錄。  直接擷取這個屬性，請呼叫 [CDaoQueryDef::GetReturnsRecords](../Topic/CDaoQueryDef::GetReturnsRecords.md)。  不是外部資料庫傳回資料錄的 SQL 傳遞查詢。  例如， SQL **UPDATE** 陳述式來更新資料錄，而不會傳回資料錄，而 **SELECT** ， SQL 陳述式會傳回資料錄。  如需詳細資訊，請參閱主題「ReturnsRecords 屬性 DAO 說明。  
  
 *m\_strSQL*  
 定義 querydef 物件執行查詢的 SQL 陳述式。  SQL 屬性包含所識別的 SQL 陳述式資料錄如何選取，群組，以及已排序時執行查詢。  您在 dynaset\-或快照型資料錄集物件可以使用查詢來選取資料錄中。  您也可以定義大量查詢修改資料，而不會傳回資料錄。  您可以直接呼叫 querydef 的 [GetSQL](../Topic/CDaoQueryDef::GetSQL.md) 成員函式來擷取這個屬性的值。  
  
 `m_strConnect`  
 提供用來傳遞查詢的資料庫來源的相關資訊。  這項資訊以連接字串的表單。  如需連接字串的詳細資訊以及有關直接擷取這個屬性值的詳細資訊，請參閱 [CDaoDatabase::GetConnect](../Topic/CDaoDatabase::GetConnect.md) 成員函式。  
  
 *m\_nODBCTimeout*  
 Microsoft Jet 資料庫引擎在逾時錯誤發生前等候的秒數，當查詢在 ODBC 資料庫執行。  當您使用 ODBC 資料庫，例如 Microsoft SQL Server 時，由於網路流量或對 ODBC 伺服器的大量使用，可能會有延遲。  而不是無限期等候，可以指定 Microsoft Jet 機引擎等候，並產生錯誤之前。  預設逾時值為 60 秒。  您可以直接呼叫 querydef 的 [GetODBCTimeout](../Topic/CDaoQueryDef::GetODBCTimeout.md) 成員函式來擷取這個屬性的值。  如需詳細資訊，請參閱主題「ODBCTimeout 屬性 DAO 說明。  
  
## 備註  
 querydef 是類別 [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)物件。  對主要，次要參考和所有在指令的資訊如何由類別 `CDaoDatabase`的 [GetQueryDefInfo](../Topic/CDaoDatabase::GetQueryDefInfo.md) 成員函式傳回。  
  
 [CDaoDatabase::GetQueryDefInfo](../Topic/CDaoDatabase::GetQueryDefInfo.md) 成員函式來擷取的資訊在 `CDaoQueryDefInfo` 結構中。  呼叫 QueryDefs 集合 querydef 物件中儲存的資料庫物件的 `GetQueryDefInfo` 。  `CDaoQueryDefInfo` 也會定義函式偵錯組建中一個 `Dump` 成員。  您可以使用 `Dump` 來傾印 `CDaoQueryDefInfo` 物件的內容。  `CDaoDatabase` 類別也提供直接存取 `CDaoQueryDefInfo` 物件中傳回的所有成員函式的屬性，因此，您可能不需要呼叫 `GetQueryDefInfo`。  
  
 當您附加至 querydef 物件的欄位或參數集合的新欄位或參數物件，就會擲回例外狀況，如果基礎資料庫不支援為新的物件所指定的資料型別。  
  
 日期和時間設定從 querydef 最近建立或更新電腦上取得。  在多使用者環境中，使用者應該直接從檔案伺服器取得這些設定使用 **net time** 命令避免在 DateCreated 和 LastUpdated 屬性的情形設定。  
  
## 需求  
 **Header:** afxdao.h  
  
## 請參閱  
 [結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoQueryDef Class](../../mfc/reference/cdaoquerydef-class.md)   
 [CDaoDatabase Class](../../mfc/reference/cdaodatabase-class.md)