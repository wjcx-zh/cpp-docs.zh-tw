---
title: "CDaoQueryDefInfo 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDaoQueryDefInfo
dev_langs:
- C++
helpviewer_keywords:
- DAO (Data Access Objects), QueryDefs collection
- CDaoQueryDefInfo structure
ms.assetid: e20837dc-e78d-4171-a195-1b4075fb5d2a
caps.latest.revision: 13
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 80e681345091ef54e2be2e3f1c1ea6ccaefd9d17
ms.lasthandoff: 02/24/2017

---
# <a name="cdaoquerydefinfo-structure"></a>CDaoQueryDefInfo 結構
`CDaoQueryDefInfo`結構包含定義資料存取物件 (DAO) 的 recordset 物件的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```  
struct CDaoQueryDefInfo  
{  
    CString m_strName;               // Primary  
    short m_nType;   // Primary  
    COleDateTime m_dateCreated;      // Secondary  
    COleDateTime m_dateLastUpdated;  // Secondary  
    BOOL m_bUpdatable;               // Secondary  
    BOOL m_bReturnsRecords;          // Secondary  
    CString m_strSQL;                // All  
    CString m_strConnect;            // All  
    short m_nODBCTimeout;            // All  
};  
```  
  
#### <a name="parameters"></a>參數  
 `m_strName`  
 唯一名稱的 recordset 物件。 如需詳細資訊，請參閱本主題說明 DAO 中的 「 名稱屬性 」。 呼叫[CDaoQueryDef::GetName](../../mfc/reference/cdaoquerydef-class.md#getname)直接擷取這個屬性。  
  
 `m_nType`  
 值，指出 recordset 物件的操作類型。 值可以是下列其中一項︰  
  
- **dbQSelect**選取，查詢會選取資料錄。  
  
- **dbQAction**動作 — 查詢移動或變更資料，但是不會傳回記錄。  
  
- **dbQCrosstab**交叉資料表，查詢會傳回資料試算表之類的格式。  
  
- **dbQDelete**刪除，查詢會刪除指定的資料列集。  
  
- **dbQUpdate**更新 — 查詢變更一組記錄。  
  
- **dbQAppend**附加，查詢會將新記錄新增至資料表或查詢的結尾。  
  
- **dbQMakeTable**製成資料表，查詢會從資料錄集建立新的資料表。  
  
- **dbQDDL**資料定義，影響的資料表或其組件的結構。  
  
- **dbQSQLPassThrough**傳遞 — SQL 陳述式會直接傳遞至資料庫後端，而不需要中繼處理。  
  
- **dbQSetOperation**聯集，此查詢會建立快照集類型資料錄集物件，包含所有指定的記錄，在兩種不同的資料或任何重複的記錄與多個資料表中移除。 若要包含重複的項目，將關鍵字加入**所有**querydef SQL 陳述式中。  
  
- **dbQSPTBulk**搭配**dbQSQLPassThrough**指定不會傳回記錄的查詢。  
  
> [!NOTE]
>  若要建立 SQL 通過查詢，您未設定**dbQSQLPassThrough**常數。 這會自動設定由 Microsoft Jet 資料庫引擎時建立 recordset 物件，並設定連接屬性。  
  
 如需詳細資訊，請參閱本主題說明 DAO 中的 「 型別屬性 」。  
  
 `m_dateCreated`  
 日期和建立 recordset 的時間。 若要直接擷取 querydef 的建立的日期，請呼叫[GetDateCreated](../../mfc/reference/cdaotabledef-class.md#getdatecreated)成員函式`CDaoTableDef`與資料表相關聯的物件。 如需詳細資訊，請參閱下方的註解。 在 DAO 說明請參閱主題 」 DateCreated，以下 LastUpdated 屬性 」。  
  
 `m_dateLastUpdated`  
 日期和時間的最新的變更對 querydef。 若要直接擷取資料表上次更新日期，請呼叫[GetDateLastUpdated](../../mfc/reference/cdaoquerydef-class.md#getdatelastupdated) querydef 成員函式。 如需詳細資訊，請參閱下方的註解。 並請參閱 DAO 說明主題 「 DateCreated LastUpdated 屬性 」。  
  
 `m_bUpdatable`  
 指出是否可以變更 recordset 物件。 如果這個屬性是**TRUE**，querydef 就是可更新，否則它不是。 可更新的表示可以變更 recordset 物件的查詢定義。 Recordset 物件的可更新的屬性設定為**TRUE**如果查詢定義可以更新，即使產生的資料錄集並不是可更新。 若要直接擷取這個屬性，呼叫 querydef [CanUpdate](../../mfc/reference/cdaoquerydef-class.md#canupdate)成員函式。 如需詳細資訊，請參閱本主題說明 DAO 中的 「 可更新屬性 」。  
  
 *m_bReturnsRecords*  
 指出 SQL 傳遞至外部資料庫查詢傳回的記錄。 如果這個屬性是**TRUE**，查詢會傳回記錄。 若要直接擷取這個屬性，呼叫[CDaoQueryDef::GetReturnsRecords](../../mfc/reference/cdaoquerydef-class.md#getreturnsrecords)。 並非所有的 SQL 傳遞查詢至外部資料庫傳回資料錄。 例如，SQL**更新**陳述式更新記錄，而不會傳回記錄，同時 SQL**選取**陳述式會傳回記錄。 如需詳細資訊，請參閱本主題說明 DAO 中的 「 傳回記錄屬性 」。  
  
 *m_strSQL*  
 定義 recordset 物件所執行之查詢的 SQL 陳述式。 SQL 屬性包含決定如何選取記錄，分組，並依序執行查詢時的 SQL 陳述式。 您可以使用查詢來選取要包含在動態或快照集類型的資料錄集物件中的記錄。 您也可以定義大量查詢傳回的記錄不可以修改資料。 您可以擷取這個屬性的值直接呼叫 querydef [GetSQL](../../mfc/reference/cdaoquerydef-class.md#getsql)成員函式。  
  
 `m_strConnect`  
 提供使用通過查詢中的資料庫來源的相關資訊。 這項資訊的形式的連接字串。 如需關於連接字串，和直接擷取這個屬性的值的詳細資訊，請參閱[CDaoDatabase::GetConnect](../../mfc/reference/cdaodatabase-class.md#getconnect)成員函式。  
  
 *m_nODBCTimeout*  
 ODBC 資料庫上執行查詢時，就會發生的 Microsoft Jet 資料庫引擎在逾時錯誤之前等候的秒數。 當您使用 ODBC 資料庫，例如 Microsoft SQL Server，因為網路流量或大量使用的 ODBC 伺服器可能會有延遲。 而不是無限期等候，您可以指定，便會產生錯誤之前，Microsoft Jet 引擎的等候時間長度。 預設的逾時值為 60 秒。 您可以擷取這個屬性的值直接呼叫 querydef [GetODBCTimeout](../../mfc/reference/cdaoquerydef-class.md#getodbctimeout)成員函式。 如需詳細資訊，請參閱本主題說明 DAO 中的 「 odbc 逾時屬性 」。  
  
## <a name="remarks"></a>備註  
 Querydef 是類別的物件[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)。 主要、 次要資料庫，且上述所有參考表示資訊由[GetQueryDefInfo](../../mfc/reference/cdaodatabase-class.md#getquerydefinfo)類別中的成員函式`CDaoDatabase`。  
  
 所擷取的資訊[CDaoDatabase::GetQueryDefInfo](../../mfc/reference/cdaodatabase-class.md#getquerydefinfo)成員函式會儲存在`CDaoQueryDefInfo`結構。 呼叫`GetQueryDefInfo`recordset 物件會儲存其 QueryDefs 集合中的資料庫物件。 `CDaoQueryDefInfo`也會定義`Dump`成員函式中偵錯組建。 您可以使用`Dump`來傾印的內容`CDaoQueryDefInfo`物件。 類別`CDaoDatabase`也提供直接存取的所有屬性中傳回的成員函式`CDaoQueryDefInfo`物件，因此您可能很少需要呼叫`GetQueryDefInfo`。  
  
 當您將新欄位或參數物件附加至欄位或參數的 recordset 物件集合時，如果基礎資料庫不支援指定為新物件的資料類型，會擲回例外狀況。  
  
 日期和時間設定被衍生自 querydef 已建立或上次更新的電腦。 在多使用者環境中，使用者應該直接從檔案伺服器使用取得這些設定**net 時間**命令，以避免 DateCreated 和 LastUpdated 的屬性設定不一致的地方。  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxdao.h  
  
## <a name="see-also"></a>另請參閱  
 [結構、 樣式、 回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoQueryDef 類別](../../mfc/reference/cdaoquerydef-class.md)   
 [CDaoDatabase 類別](../../mfc/reference/cdaodatabase-class.md)

