---
title: "CDaoTableDefInfo 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDaoTableDefInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDaoTableDefInfo 結構"
  - "DAO (資料存取物件), TableDefs 集合"
ms.assetid: c01ccebb-5615-434e-883c-4f60eac943dd
caps.latest.revision: 13
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDaoTableDefInfo 結構
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

如需資料存取定義的 tabledef 物件的 `CDaoTableDefInfo` 結構中的物件 \(DAO\)。  
  
## 語法  
  
```  
  
      struct CDaoTableDefInfo  
{  
   CString m_strName;               // Primary  
   BOOL m_bUpdatable;               // Primary  
   long m_lAttributes;              // Primary  
   COleDateTime m_dateCreated;      // Secondary  
   COleDateTime m_dateLastUpdated;  // Secondary  
   CString m_strSrcTableName;       // Secondary  
   CString m_strConnect;            // Secondary  
   CString m_strValidationRule;     // All  
   CString m_strValidationText;     // All  
   long m_lRecordCount;             // All  
};  
```  
  
#### 參數  
 `m_strName`  
 唯一命名 tabledef 物件。  若要直接擷取這個屬性的值，請呼叫 tabledef 物件的 [GetName](../Topic/CDaoTableDef::GetName.md) 成員函式。  如需詳細資訊，請參閱主題「Name 屬性 DAO 說明。  
  
 `m_bUpdatable`  
 指出變更是否可對資料表。  這個快速判斷資料表是否可更新會開啟資料表的 `CDaoTableDef` 物件和呼叫物件的 [CanUpdate](../Topic/CDaoTableDef::CanUpdate.md) 成員函式。  `CanUpdate` 永遠傳回非零 \(**TRUE**\) 新建立物件 tabledef 和 0 \(**FALSE**\) 中附加的 tabledef 物件的。  新的 tabledef 只可將物件附加至目前使用者沒有寫入權限的資料庫。  如果資料表只包含不可更新的欄位，則 `CanUpdate` 會傳回 0。  當一個或多個欄位可更新時， `CanUpdate` 會傳回非零。  您可以編輯只可更新的欄位。  如需詳細資訊，請參閱主題可更新的屬性 DAO 說明。  
  
 `m_lAttributes`  
 指定 tabledef 物件表示的資料表的特性。  若要擷取 tabledef 的目前屬性，呼叫它的 [GetAttributes](../Topic/CDaoTableDef::GetAttributes.md) 成員函式。  傳回的值可以是下列的常數的組合 \(使用位元 OR \(  **&#124;**\) 運算子\):  
  
-   使用 Microsoft Jet 資料庫引擎的資料庫中，資料表是另一個資料表的指示**dbAttachExclusive** 開啟為獨佔使用。  
  
-   使用 Microsoft Jet 資料庫引擎的資料庫的**dbAttachSavePWD**，表示使用者 ID 和密碼附加資料表中儲存的連接資訊。  
  
-   **dbSystemObject** 表示表格是 Microsoft Jet 資料庫引擎提供的系統資料表。\(唯讀\)。  
  
-   **dbHiddenObject** 表示表格是 Microsoft Jet 資料庫引擎提供的隱藏資料表 \(暫時使用\)。\(唯讀\)。  
  
-   **dbAttachedTable** 表示資料表是從非 ODBC 資料庫的附加資料表，例如衝突資料庫。  
  
-   **dbAttachedODBC** 表示資料表是從一個 ODBC 資料庫的附加資料表，例如 Microsoft SQL Server。  
  
 `m_dateCreated`  
 資料表的建立日期和時間。  直接擷取資料表的建立日期，呼叫 `CDaoTableDef` 物件的 [GetDateCreated](../Topic/CDaoTableDef::GetDateCreated.md) 成員函式與資料表。  請參閱底下的註解以取得詳細資訊。  如需相關資訊，請參閱本主題 DateCreated 「， LastUpdated 屬性 DAO 說明。  
  
 `m_dateLastUpdated`  
 所做的最新變更的日期和時間轉換為資料表的設計。  直接擷取資料表的上次更新的日期，請呼叫 `CDaoTableDef` 物件的 [GetDateLastUpdated](../Topic/CDaoTableDef::GetDateLastUpdated.md) 成員函式與資料表。  請參閱底下的註解以取得詳細資訊。  如需相關資訊，請參閱本主題 DateCreated 「， LastUpdated 屬性 DAO 說明。  
  
 *m\_strSrcTableName*  
 指定另一個資料表的名稱，如果有的話。  直接擷取來源資料表名稱，請呼叫 `CDaoTableDef` 物件的 [GetSourceTableName](../Topic/CDaoTableDef::GetSourceTableName.md) 成員函式與資料表。  
  
 `m_strConnect`  
 提供關於開放式資料庫來源的相關資訊。  您可以呼叫您的 `CDaoTableDef` 物件的 [GetConnect](../Topic/CDaoTableDef::GetConnect.md) 成員函式來檢查這個屬性。  如需連接字串的詳細資訊，請參閱 `GetConnect`。  
  
 `m_strValidationRule`  
 驗證在 tabledef 的資料值欄位，會變更或加入至資料表。  驗證為使用 Microsoft Jet 資料庫引擎的資料庫才支援。  直接擷取驗證規則，請呼叫 `CDaoTableDef` 物件的 [GetValidationRule](../Topic/CDaoTableDef::GetValidationRule.md) 成員函式與資料表。  如需相關資訊，請參閱本主題 \< ValidationRule 屬性 DAO 說明。  
  
 `m_strValidationText`  
 指定訊息文字應用程式應顯示的值，如果 ValidationRule 屬性所指定的驗證規則不滿足。  如需相關資訊，請參閱本主題 \< ValidationText 屬性 DAO 說明。  
  
 *m\_lRecordCount*  
 在 tabledef 物件存取資料錄數目。  這個屬性設定為唯讀。  直接擷取記錄計數，請呼叫 `CDaoTableDef` 物件的 [GetRecordCount](../Topic/CDaoTableDef::GetRecordCount.md) 成員函式。  `GetRecordCount` 的文件進一步描述記錄計數。  如果資料表包含許多資料錄，請注意擷取這個計數的，可以是耗時的作業。  
  
## 備註  
 tabledef 是類別 [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)物件。  對主要，次要參考和所有在指令的資訊如何由類別 `CDaoDatabase`的 [GetTableDefInfo](../Topic/CDaoDatabase::GetTableDefInfo.md) 成員函式傳回。  
  
 [CDaoDatabase::GetTableDefInfo](../Topic/CDaoDatabase::GetTableDefInfo.md) 成員函式來擷取的資訊在 `CDaoTableDefInfo` 結構中。  呼叫 TableDefs 集合 tabledef 物件儲存 `CDaoDatabase` 物件的 `GetTableDefInfo` 成員函式中。  `CDaoTableDefInfo` 也會定義函式偵錯組建中一個 `Dump` 成員。  您可以使用 `Dump` 來傾印 `CDaoTableDefInfo` 物件的內容。  
  
 日期和時間設定從基底資料表建立或最近更新的電腦上取得。  在多使用者環境中，使用者應該直接從檔案伺服器取得這些設定避免在 DateCreated 和 LastUpdated 屬性的情形設定。  
  
## 需求  
 **Header:** afxdao.h  
  
## 請參閱  
 [結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoTableDef Class](../../mfc/reference/cdaotabledef-class.md)   
 [CDaoDatabase Class](../../mfc/reference/cdaodatabase-class.md)   
 [CDaoTableDef::CanUpdate](../Topic/CDaoTableDef::CanUpdate.md)   
 [CDaoTableDef::GetAttributes](../Topic/CDaoTableDef::GetAttributes.md)   
 [CDaoTableDef::GetDateCreated](../Topic/CDaoTableDef::GetDateCreated.md)   
 [CDaoTableDef::GetDateLastUpdated](../Topic/CDaoTableDef::GetDateLastUpdated.md)   
 [CDaoTableDef::GetRecordCount](../Topic/CDaoTableDef::GetRecordCount.md)   
 [CDaoTableDef::GetSourceTableName](../Topic/CDaoTableDef::GetSourceTableName.md)   
 [CDaoTableDef::GetValidationRule](../Topic/CDaoTableDef::GetValidationRule.md)   
 [CDaoTableDef::GetValidationText](../Topic/CDaoTableDef::GetValidationText.md)