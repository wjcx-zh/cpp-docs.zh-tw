---
title: "CDaoTableDefInfo 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDaoTableDefInfo
dev_langs:
- C++
helpviewer_keywords:
- CDaoTableDefInfo structure [MFC]
- DAO (Data Access Objects), TableDefs collection
ms.assetid: c01ccebb-5615-434e-883c-4f60eac943dd
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e949cb0348cb55fcee5a940b5753a5a8197e600b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cdaotabledefinfo-structure"></a>CDaoTableDefInfo 結構
`CDaoTableDefInfo`結構包含 tabledef 物件定義的資料存取物件 (DAO) 的相關資訊。  
  
## <a name="syntax"></a>語法  
  
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
  
#### <a name="parameters"></a>參數  
 `m_strName`  
 唯一命名 tabledef 的物件。 若要直接擷取這個屬性的值，呼叫 tabledef 物件[GetName](../../mfc/reference/cdaotabledef-class.md#getname)成員函式。 如需詳細資訊，請參閱本主題說明 DAO 中的 「 名稱屬性 」。  
  
 `m_bUpdatable`  
 指出是否可以變更資料表。 若要判斷資料表是否可更新的快速方式是開啟`CDaoTableDef`資料表物件，並呼叫物件的[CanUpdate](../../mfc/reference/cdaotabledef-class.md#canupdate)成員函式。 `CanUpdate`一律會傳回非零 (**TRUE**) 新建的 tabledef 物件和 0 (**FALSE**) 附加的 tabledef 物件。 新的 tabledef 物件可以附加至其目前的使用者具有寫入權限的資料庫。 如果資料表包含無法更新欄位，`CanUpdate`傳回 0。 當一或多個欄位是可更新，`CanUpdate`傳回非零值。 您可以編輯可更新的欄位。 如需詳細資訊，請參閱本主題說明 DAO 中的 「 可更新屬性 」。  
  
 `m_lAttributes`  
 指定 tabledef 物件所代表之資料表的特性。 若要擷取目前的 tabledef 屬性，請呼叫其[GetAttributes](../../mfc/reference/cdaotabledef-class.md#getattributes)成員函式。 傳回的值可以是這些長常數的組合 (使用位元 OR (**&#124;**) 運算子):  
  
- **dbAttachExclusive**使用 Microsoft Jet 資料庫引擎的資料庫，表示資料表是專供開啟附加的資料表。  
  
- **dbAttachSavePWD**使用 Microsoft Jet 資料庫引擎的資料庫，表示的使用者識別碼和密碼附加資料表會儲存連接資訊。  
  
- **dbSystemObject**表示資料表為 Microsoft Jet database engine 所提供的系統資料表。 (唯讀)。  
  
- **dbHiddenObject**表示資料表為 Microsoft Jet database engine （供暫時使用） 所提供的隱藏的資料表。 (唯讀)。  
  
- **dbAttachedTable**表示資料表為附加來自非 ODBC 資料庫，例如 Paradox 資料庫資料表。  
  
- **dbAttachedODBC**表示資料表為附加來自 ODBC 資料庫，例如 Microsoft SQL Server 資料表。  
  
 `m_dateCreated`  
 日期和時間建立資料表。 若要直接擷取資料表的建立的日期，請呼叫[GetDateCreated](../../mfc/reference/cdaotabledef-class.md#getdatecreated)成員函式`CDaoTableDef`與資料表相關聯的物件。 如需詳細資訊，請參閱下方的註解。 如需相關資訊，請參閱 DAO 說明主題 「 DateCreated LastUpdated 屬性 」。  
  
 `m_dateLastUpdated`  
 日期和時間的設計資料表所做的最新變更。 若要直接擷取上次更新資料表的日期，請呼叫[GetDateLastUpdated](../../mfc/reference/cdaotabledef-class.md#getdatelastupdated)成員函式`CDaoTableDef`與資料表相關聯的物件。 如需詳細資訊，請參閱下方的註解。 如需相關資訊，請參閱 DAO 說明主題 「 DateCreated LastUpdated 屬性 」。  
  
 *m_strSrcTableName*  
 如果有的話，請指定附加資料表的名稱。 若要直接擷取來源資料表名稱，請呼叫[GetSourceTableName](../../mfc/reference/cdaotabledef-class.md#getsourcetablename)成員函式`CDaoTableDef`與資料表相關聯的物件。  
  
 `m_strConnect`  
 提供有關開啟的資料庫來源的資訊。 您可以檢查這個屬性，藉由呼叫[GetConnect](../../mfc/reference/cdaotabledef-class.md#getconnect)成員函式的程式`CDaoTableDef`物件。 如需有關連接字串，請參閱`GetConnect`。  
  
 `m_strValidationRule`  
 會驗證 tabledef 欄位中的資料，因為已變更或加入至資料表的這些值。 驗證只支援使用 Microsoft Jet 資料庫引擎的資料庫。 若要直接擷取驗證規則，請呼叫[GetValidationRule](../../mfc/reference/cdaotabledef-class.md#getvalidationrule)成員函式`CDaoTableDef`與資料表相關聯的物件。 如需相關資訊，請參閱主題 DAO [說明] 中的 < 驗證規則屬性 >。  
  
 `m_strValidationText`  
 值，指定如果沒有符合驗證規則屬性所指定的驗證規則，您的應用程式應該會顯示訊息的文字。 如需相關資訊，請參閱主題 DAO [說明] 中的 < 驗證文字屬性 >。  
  
 *m_lRecordCount*  
 存取 tabledef 物件中的記錄數目。 此屬性設定為唯讀。 若要直接擷取的記錄計數，呼叫[GetRecordCount](../../mfc/reference/cdaotabledef-class.md#getrecordcount)成員函式`CDaoTableDef`物件。 文件`GetRecordCount`描述記錄計數。 請注意，擷取這個計數可能很耗時的作業。 是否資料表包含許多記錄。  
  
## <a name="remarks"></a>備註  
 Tabledef 是類別的物件[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)。 參考主要、 次要資料庫，且所有上述表示所傳回的資訊是如何[GetTableDefInfo](../../mfc/reference/cdaodatabase-class.md#gettabledefinfo)類別中的成員函式`CDaoDatabase`。  
  
 所擷取的資訊[cdaodatabase:: Gettabledefinfo](../../mfc/reference/cdaodatabase-class.md#gettabledefinfo)成員函式會儲存在`CDaoTableDefInfo`結構。 呼叫`GetTableDefInfo`成員函式`CDaoDatabase`tabledef 物件會儲存其 TableDefs 集合中的物件。 `CDaoTableDefInfo`也會定義`Dump`成員函式在偵錯組建。 您可以使用`Dump`來傾印的內容`CDaoTableDefInfo`物件。  
  
 日期和時間設定被衍生自基底資料表已在其建立，或上次更新的電腦。 在多使用者環境中，使用者應該會收到這些設定，直接從檔案伺服器以避免不一致的地方 DateCreated 和 LastUpdated 屬性設定。  
  
## <a name="requirements"></a>需求  
 **標頭：** afxdao.h  
  
## <a name="see-also"></a>請參閱  
 [結構、 樣式、 回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoTableDef 類別](../../mfc/reference/cdaotabledef-class.md)   
 [CDaoDatabase 類別](../../mfc/reference/cdaodatabase-class.md)
