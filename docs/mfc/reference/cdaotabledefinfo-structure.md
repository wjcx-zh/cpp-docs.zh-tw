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
- CDaoTableDefInfo structure
- DAO (Data Access Objects), TableDefs collection
ms.assetid: c01ccebb-5615-434e-883c-4f60eac943dd
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 4d1ac5ca00f98f8c34332ce2eb1a180ab715e6ba
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

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
 指出是否可以變更的資料表。 判斷資料表是否為可更新的快速方式是開啟`CDaoTableDef`資料表物件並呼叫物件的[CanUpdate](../../mfc/reference/cdaotabledef-class.md#canupdate)成員函式。 `CanUpdate`一律會傳回非零 (**TRUE**) 針對新建立的 tabledef 物件和 0 (**FALSE**) 附加的 tabledef 物件。 只以其目前的使用者具有寫入權限的資料庫可以附加新 tabledef 物件。 如果資料表包含無法更新欄位，`CanUpdate`會傳回 0。 當一或多個欄位是可更新，`CanUpdate`傳回非零值。 您可以編輯可更新的欄位。 如需詳細資訊，請參閱本主題說明 DAO 中的 「 可更新屬性 」。  
  
 `m_lAttributes`  
 指定資料表 tabledef 物件所代表的特性。 若要擷取目前的 tabledef 屬性，請呼叫其[GetAttributes](../../mfc/reference/cdaotabledef-class.md#getattributes)成員函式。 傳回的值可以是兩個長常數組合 (使用位元 OR (**|**) 運算子):  
  
- **dbAttachExclusive**使用 Microsoft Jet 資料庫引擎的資料庫，表示資料表是以獨佔開啟附加的資料表。  
  
- **dbAttachSavePWD**使用 Microsoft Jet 資料庫引擎的資料庫，表示使用者識別碼和密碼附加的資料表會儲存連接資訊。  
  
- **dbSystemObject**表示資料表是由 Microsoft Jet 資料庫引擎所提供的系統資料表。 (唯讀)。  
  
- **dbHiddenObject**表示資料表是由 Microsoft Jet 資料庫引擎 （用於暫時） 提供的隱藏的資料表。 (唯讀)。  
  
- **dbAttachedTable**表示資料表是從非 ODBC 資料庫，例如 Paradox 資料庫連接的資料表。  
  
- **dbAttachedODBC**表示資料表為附加從 ODBC 資料庫，例如 Microsoft SQL Server 資料表。  
  
 `m_dateCreated`  
 日期時間與建立資料表。 若要直接擷取資料表的建立的日期，請呼叫[GetDateCreated](../../mfc/reference/cdaotabledef-class.md#getdatecreated)成員函式`CDaoTableDef`與資料表相關聯的物件。 如需詳細資訊，請參閱下方的註解。 如需相關資訊，請參閱 DAO 說明主題 「 DateCreated LastUpdated 屬性 」。  
  
 `m_dateLastUpdated`  
 時間與日期資料表的設計所做的最新變更。 若要直接擷取資料表上次更新日期，請呼叫[GetDateLastUpdated](../../mfc/reference/cdaotabledef-class.md#getdatelastupdated)成員函式`CDaoTableDef`與資料表相關聯的物件。 如需詳細資訊，請參閱下方的註解。 如需相關資訊，請參閱 DAO 說明主題 「 DateCreated LastUpdated 屬性 」。  
  
 *m_strSrcTableName*  
 如果有的話，請指定附加資料表的名稱。 若要直接擷取來源資料表名稱，請呼叫[GetSourceTableName](../../mfc/reference/cdaotabledef-class.md#getsourcetablename)成員函式`CDaoTableDef`與資料表相關聯的物件。  
  
 `m_strConnect`  
 提供開啟的資料庫來源的相關資訊。 您可以檢查這個屬性，藉由呼叫[GetConnect](../../mfc/reference/cdaotabledef-class.md#getconnect)成員函式您`CDaoTableDef`物件。 如需有關連接字串，請參閱`GetConnect`。  
  
 `m_strValidationRule`  
 驗證 tabledef 欄位中的資料已變更或加入至資料表的這些值。 使用 Microsoft Jet 資料庫引擎的資料庫支援驗證。 若要直接擷取驗證規則，請呼叫[GetValidationRule](../../mfc/reference/cdaotabledef-class.md#getvalidationrule)成員函式`CDaoTableDef`與資料表相關聯的物件。 如需相關資訊，請參閱主題 DAO 說明中的 「 ValidationRule 屬性 」。  
  
 `m_strValidationText`  
 值，指定如果不符合驗證規則屬性所指定的驗證規則，您的應用程式應該會顯示訊息的文字。 如需相關資訊，請參閱主題 DAO 說明中的 「 驗證屬性 」。  
  
 *m_lRecordCount*  
 存取 tabledef 物件中的記錄數目。 這個屬性設定為唯讀。 若要直接擷取記錄計數，呼叫[GetRecordCount](../../mfc/reference/cdaotabledef-class.md#getrecordcount)成員函式`CDaoTableDef`物件。 文件`GetRecordCount`描述記錄筆數。 請注意，擷取這個計數可能會很耗時的作業是否資料表包含多筆記錄。  
  
## <a name="remarks"></a>備註  
 Tabledef 是類別的物件[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)。 主要、 次要資料庫，且上述所有參考表示資訊由[GetTableDefInfo](../../mfc/reference/cdaodatabase-class.md#gettabledefinfo)類別中的成員函式`CDaoDatabase`。  
  
 所擷取的資訊[cdaodatabase:: Gettabledefinfo](../../mfc/reference/cdaodatabase-class.md#gettabledefinfo)成員函式會儲存在`CDaoTableDefInfo`結構。 呼叫`GetTableDefInfo`成員函式`CDaoDatabase`tabledef 物件會儲存其 TableDefs 集合中的物件。 `CDaoTableDefInfo`也會定義`Dump`成員函式中偵錯組建。 您可以使用`Dump`來傾印的內容`CDaoTableDefInfo`物件。  
  
 日期和時間設定被衍生自的基底資料表建立或上次更新的電腦。 在多使用者環境中，使用者應該取得這些設定，直接從檔案伺服器以避免不一致的地方 DateCreated 和 LastUpdated 屬性設定。  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxdao.h  
  
## <a name="see-also"></a>另請參閱  
 [結構、 樣式、 回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoTableDef 類別](../../mfc/reference/cdaotabledef-class.md)   
 [CDaoDatabase 類別](../../mfc/reference/cdaodatabase-class.md)

