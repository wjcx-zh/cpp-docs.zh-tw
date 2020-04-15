---
title: CDaoQueryDefInfo 結構
ms.date: 11/04/2016
f1_keywords:
- CDaoQueryDefInfo
helpviewer_keywords:
- DAO (Data Access Objects), QueryDefs collection
- CDaoQueryDefInfo structure [MFC]
ms.assetid: e20837dc-e78d-4171-a195-1b4075fb5d2a
ms.openlocfilehash: e2f0325237a30989637821464c63a4d8b8000b1e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368941"
---
# <a name="cdaoquerydefinfo-structure"></a>CDaoQueryDefInfo 結構

該`CDaoQueryDefInfo`結構包含有關為數據訪問物件 (DAO) 定義的查詢def物件的資訊。

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

*m_strName*<br/>
唯一地命名查詢def物件。 有關詳細資訊,請參閱 DAO 説明中的主題"名稱屬性"。 調用[CDaoQueryDef:獲取名稱](../../mfc/reference/cdaoquerydef-class.md#getname)以直接檢索此屬性。

*m_nType*<br/>
指示查詢def物件的操作類型的值。 這個值可以是下列值之一：

- `dbQSelect`選擇 = 查詢選擇記錄。

- `dbQAction`操作 — 查詢移動或更改數據,但不返回記錄。

- `dbQCrosstab`交叉選項卡 – 查詢以類似電子表格的格式返回資料。

- `dbQDelete`刪除 = 查詢刪除一組指定的列。

- `dbQUpdate`更新 = 查詢更改一組記錄。

- `dbQAppend`追加 - 查詢將新記錄添加到表或查詢的末尾。

- `dbQMakeTable`製作表 – 查詢從記錄集創建新表。

- `dbQDDL`數據定義 – 查詢影響表或其部件的結構。

- `dbQSQLPassThrough`傳遞 – SQL 語句直接傳遞到資料庫後端,無需中間處理。

- `dbQSetOperation`聯合 = 查詢創建一個快照類型記錄集物件,其中包含來自兩個或多個表中所有指定記錄的數據,並刪除了任何重複的記錄。 要包括重複項,請在查詢def的 SQL 語句中添加關鍵字**ALL。**

- `dbQSPTBulk``dbQSQLPassThrough`用於指定不返回記錄的查詢。

> [!NOTE]
> 要創建 SQL 傳遞查詢,請不要`dbQSQLPassThrough`設置常 量。 當您創建查詢def物件並設置 Connect 屬性時,Microsoft Jet 資料庫引擎會自動設置此設置。

有關詳細資訊,請參閱 DAO 説明中的主題"類型屬性"。

*m_dateCreated*<br/>
創建查詢def的日期和時間。 要直接檢索創建查詢def的日期,請調用與表關聯的`CDaoTableDef`物件的[GetDateCreated](../../mfc/reference/cdaotabledef-class.md#getdatecreated)成員函數。 有關詳細資訊,請參閱下面的註釋。 另請參閱 DAO 説明中的主題" 創建日期,上次更新的屬性」。

*m_dateLastUpdated*<br/>
對查詢 def 進行的最新更改的日期和時間。 要直接檢索表上次更新的日期,請調用查詢def的[GetDateLast 更新](../../mfc/reference/cdaoquerydef-class.md#getdatelastupdated)成員函數。 有關詳細資訊,請參閱下面的註釋。 並查看 DAO 説明中的主題" 建立日期,上次更新的屬性。

*m_bUpdatable*<br/>
指示是否可以對查詢def物件進行更改。 如果此屬性為 TRUE,則查詢def 是可升的;如果此屬性為 TRUE,則查詢 def 是可向上的。否則,它不是。 可上可意味著可以更改查詢def物件的查詢定義。 如果查詢定義可以更新,即使生成的記錄集不可更新,查詢def物件的 Upda 可屬性也設置為 TRUE。 要直接檢索此屬性,請調用查詢def 的[CanUpdate](../../mfc/reference/cdaoquerydef-class.md#canupdate)成員函數。 有關詳細資訊,請參閱 DAO 説明中的主題"可增加屬性」。

*m_bReturnsRecords*<br/>
指示對外部資料庫的 SQL 傳遞查詢是否返回記錄。 如果此屬性為 TRUE,則查詢將返回記錄。 要直接檢查此屬性,請執行電[CdaoQueryDef::取得傳回紀錄](../../mfc/reference/cdaoquerydef-class.md#getreturnsrecords)。 並非所有 SQL 傳遞到外部資料庫的查詢都返回記錄。 例如,SQL **UPDATE**語句在不返回記錄的情況下更新記錄,而 SQL **SELECT**語句會返回記錄。 有關詳細資訊,請參閱 DAO 説明中的主題"返回記錄屬性"。

*m_strSQL*<br/>
定義由查詢def物件執行的查詢的SQL語句。 SQL 屬性包含 SQL 語句,用於確定在執行查詢時記錄的選擇、分組和排序方式。 可以使用查詢選擇要包含在動態集或快照類型記錄集物件中的記錄。 您還可以定義批量查詢以修改數據,而無需返回記錄。 您可以通過調用查詢def的[GetSQL](../../mfc/reference/cdaoquerydef-class.md#getsql)成員函數直接檢索此屬性的值。

*m_strConnect*<br/>
提供有關傳遞查詢中使用的資料庫源的資訊。 此資訊採用連接字串的形式。 有關連接字串的詳細資訊,以及有關直接檢索此屬性值的資訊,請參閱[CDao 資料庫::GetConnect](../../mfc/reference/cdaodatabase-class.md#getconnect)成員函數。

*m_nODBCTimeout*<br/>
在 ODBC 資料庫上運行查詢之前,Microsoft Jet 資料庫引擎等待的秒數。 當您使用 ODBC 資料庫(如 Microsoft SQL Server)時,可能會由於網路流量或大量使用 ODBC 伺服器而出現延遲。 您可以指定 Microsoft Jet 引擎在產生錯誤之前等待多長時間,而不是無限期地等待。 預設超時值為 60 秒。 您可以通過調用查詢def的[GetODBCTimeout](../../mfc/reference/cdaoquerydef-class.md#getodbctimeout)成員函數直接檢索此屬性的值。 有關詳細資訊,請參閱 DAO 説明中的主題"ODBCTimeout 屬性"。

## <a name="remarks"></a>備註

查詢def是類別[CDaoQueryDef 的物件](../../mfc/reference/cdaoquerydef-class.md)。 對上述主要、次要和所有的引用指示類別中的[GetQueryDefInfo](../../mfc/reference/cdaodatabase-class.md#getquerydefinfo)成員函數如何`CDaoDatabase`傳回資訊 。

[CDao 資料庫檢索的資訊::getQueryDefInfo](../../mfc/reference/cdaodatabase-class.md#getquerydefinfo)成員函數`CDaoQueryDefInfo`存儲在結構 中。 調用`GetQueryDefInfo`其 QueryDefs 集合中的資料庫物件,其中儲存查詢def物件。 `CDaoQueryDefInfo`還在調試生成中`Dump`定義成員函數。 可以使用`Dump`轉`CDaoQueryDefInfo`儲 對象的內容。 類別`CDaoDatabase`提供成員函數,用於直接存`CDaoQueryDefInfo`取物件中傳回的所有屬性,因此您可能很少需要`GetQueryDefInfo`呼叫 。

將新欄位或參數物件追加到查詢def物件的欄位或參數集合時,如果基礎資料庫不支援為新物件指定的數據類型,則將引發異常。

日期和時間設置派生自創建或上次更新查詢def 的電腦。 在多使用者環境中,使用者應使用**網路時間**命令直接從檔伺服器獲取這些設置,以避免在 Date"創建"和"上次更新"屬性設置中出現差異。

## <a name="requirements"></a>需求

**標題:** afxdao.h

## <a name="see-also"></a>另請參閱

[結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoQueryDef 類別](../../mfc/reference/cdaoquerydef-class.md)<br/>
[CDaoDatabase 類別](../../mfc/reference/cdaodatabase-class.md)
