---
title: CDaoDatabase 類別
ms.date: 09/17/2019
f1_keywords:
- CDaoDatabase
- AFXDAO/CDaoDatabase
- AFXDAO/CDaoDatabase::CDaoDatabase
- AFXDAO/CDaoDatabase::CanTransact
- AFXDAO/CDaoDatabase::CanUpdate
- AFXDAO/CDaoDatabase::Close
- AFXDAO/CDaoDatabase::Create
- AFXDAO/CDaoDatabase::CreateRelation
- AFXDAO/CDaoDatabase::DeleteQueryDef
- AFXDAO/CDaoDatabase::DeleteRelation
- AFXDAO/CDaoDatabase::DeleteTableDef
- AFXDAO/CDaoDatabase::Execute
- AFXDAO/CDaoDatabase::GetConnect
- AFXDAO/CDaoDatabase::GetName
- AFXDAO/CDaoDatabase::GetQueryDefCount
- AFXDAO/CDaoDatabase::GetQueryDefInfo
- AFXDAO/CDaoDatabase::GetQueryTimeout
- AFXDAO/CDaoDatabase::GetRecordsAffected
- AFXDAO/CDaoDatabase::GetRelationCount
- AFXDAO/CDaoDatabase::GetRelationInfo
- AFXDAO/CDaoDatabase::GetTableDefCount
- AFXDAO/CDaoDatabase::GetTableDefInfo
- AFXDAO/CDaoDatabase::GetVersion
- AFXDAO/CDaoDatabase::IsOpen
- AFXDAO/CDaoDatabase::Open
- AFXDAO/CDaoDatabase::SetQueryTimeout
- AFXDAO/CDaoDatabase::m_pDAODatabase
- AFXDAO/CDaoDatabase::m_pWorkspace
helpviewer_keywords:
- CDaoDatabase [MFC], CDaoDatabase
- CDaoDatabase [MFC], CanTransact
- CDaoDatabase [MFC], CanUpdate
- CDaoDatabase [MFC], Close
- CDaoDatabase [MFC], Create
- CDaoDatabase [MFC], CreateRelation
- CDaoDatabase [MFC], DeleteQueryDef
- CDaoDatabase [MFC], DeleteRelation
- CDaoDatabase [MFC], DeleteTableDef
- CDaoDatabase [MFC], Execute
- CDaoDatabase [MFC], GetConnect
- CDaoDatabase [MFC], GetName
- CDaoDatabase [MFC], GetQueryDefCount
- CDaoDatabase [MFC], GetQueryDefInfo
- CDaoDatabase [MFC], GetQueryTimeout
- CDaoDatabase [MFC], GetRecordsAffected
- CDaoDatabase [MFC], GetRelationCount
- CDaoDatabase [MFC], GetRelationInfo
- CDaoDatabase [MFC], GetTableDefCount
- CDaoDatabase [MFC], GetTableDefInfo
- CDaoDatabase [MFC], GetVersion
- CDaoDatabase [MFC], IsOpen
- CDaoDatabase [MFC], Open
- CDaoDatabase [MFC], SetQueryTimeout
- CDaoDatabase [MFC], m_pDAODatabase
- CDaoDatabase [MFC], m_pWorkspace
ms.assetid: 8ff5b342-964d-449d-bef1-d0ff56aadf6d
ms.openlocfilehash: debba137878da49921df83da7630003a7d62db2f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369011"
---
# <a name="cdaodatabase-class"></a>CDaoDatabase 類別

表示使用數據存取物件 (DAO) 訪問資料庫的連接。 通過 Office 2013 支援 DAO。 DAO 3.6 是最終版本,它被視為過時版本。

## <a name="syntax"></a>語法

```
class CDaoDatabase : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[道資料庫::CDao資料庫](#cdaodatabase)|建構 `CDaoDatabase` 物件。 調用`Open`以將對象連接到資料庫。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDao資料庫::可以](#cantransact)|如果資料庫支援事務,則返回非零。|
|[CDao 資料庫::可以更新](#canupdate)|如果`CDaoDatabase`對像是可向上的(不只讀的),則返回非零。|
|[CDao 資料庫:關閉](#close)|關閉資料庫連接。|
|[CDao 資料庫:建立](#create)|創建基礎 DAO 資料庫物件並初始`CDaoDatabase`化該 物件。|
|[CDao 資料庫::建立關係](#createrelation)|在資料庫中的表之間定義一個新關係。|
|[CDao資料庫::DeleteQueryDef](#deletequerydef)|刪除儲存在資料庫的 QueryDefs 集合中的查詢def物件。|
|[CDao資料庫::Delete關係](#deleterelation)|刪除資料庫中表之間的現有關係。|
|[CDao資料庫::DeleteTableDef](#deletetabledef)|刪除資料庫中表的定義。 這將刪除實際表及其所有數據。|
|[CDao 資料庫:執行](#execute)|執行操作查詢。 調用`Execute`返回結果的查詢將引發異常。|
|[CDao 資料庫:抓取連線](#getconnect)|傳回用於`CDaoDatabase`將 物件連接到資料庫的連接字串。 用於ODBC。|
|[CDaoDatabase::GetName](#getname)|返回目前正在使用的資料庫的名稱。|
|[CDao 資料庫::取得查詢定義](#getquerydefcount)|返回為資料庫定義的查詢數。|
|[CDao 資料庫::獲取查詢資訊](#getquerydefinfo)|返回有關資料庫中定義的指定查詢的資訊。|
|[CDao 資料庫:取得查詢逾時](#getquerytimeout)|返回資料庫查詢操作超時後的秒數。影響對 ODBC 資料來源(僅)的所有後續打開、添加新、更新和編輯操作以及其他操作`Execute`,如調用。|
|[CDao 資料庫:取得受影響的記錄](#getrecordsaffected)|返回受上次更新、編輯或添加操作或調用`Execute`的影響的記錄數。|
|[CDao 資料庫:取得關聯數](#getrelationcount)|返回資料庫中表之間定義的關係數。|
|[CDao 資料庫:抓取關係資訊](#getrelationinfo)|返回有關資料庫中表之間定義的指定關係的資訊。|
|[CDao 資料庫:取得TableDef( C)](#gettabledefcount)|返回資料庫中定義的表數。|
|[CDao 資料庫:抓取桌面資訊](#gettabledefinfo)|返回有關資料庫中指定表的資訊。|
|[CDao 資料庫:抓取版本](#getversion)|返回與資料庫關聯的資料庫引擎的版本。|
|[CDao 資料庫::是開啟的](#isopen)|如果物件當前連接到資料庫`CDaoDatabase`,則返回非零。|
|[CDao 資料庫::開啟](#open)|建立與資料庫的連接。|
|[CDao 資料庫::設定查詢逾時](#setquerytimeout)|設定資料庫查詢操作(僅在ODBC數據源上)超時後的秒數。影響所有後續打開、添加新操作、更新和刪除操作。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CDao資料庫::m_pDAODatabase](#m_pdaodatabase)|指向基礎 DAO 資料庫物件的指標。|
|[CDao資料庫:m_pWorkspace](#m_pworkspace)|指向包含資料庫並定義其事務空間的[CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)物件的指標。|

## <a name="remarks"></a>備註

有關支援的資料庫格式的資訊,請參閱[GetName](../../mfc/reference/cdaoworkspace-class.md#getname)成員函數。 您可以在給定的「工作區」`CDaoDatabase`中同時啟動一個或多個物件,該物件由[CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)物件表示。 工作區維護打開的資料庫物件的集合,稱為資料庫集合。

## <a name="usage"></a>使用量

在創建記錄集物件時,可以隱式創建資料庫物件。 但是,您也可以顯式創建資料庫物件。 要將現有資料庫的使用,`CDaoDatabase`請執行以下任一個操作:

- 建構`CDaoDatabase`物件,將指標傳遞給打開的[CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)物件。

- 或者在不指定`CDaoDatabase`工作區的情況下建構物件(MFC 創建臨時工作區物件)。

新增 Microsoft Jet (.MDB) 資料庫,建`CDaoDatabase`構 物件並調用其[創建](#create)成員函數。 *不要*在`Open`之後`Create`打電話。

要打開現有資料庫,請建構物件`CDaoDatabase`並呼叫其[Open](#open)成員函數。

這些技術中的任何一種都將 DAO 資料庫物件追加到工作區的資料庫集合,並打開與數據的連接。 然後建構用於在連線的資料庫上操作的[CDaoRecordsetset、CDaoTableDef](../../mfc/reference/cdaorecordset-class.md)或[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)物件時,將這些物件的建構函`CDaoDatabase`數[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)傳遞給物件 。 使用完連接後,調用[Close](#close)成員函數並`CDaoDatabase`銷毀 物件。 `Close`關閉以前未關閉的任何記錄集。

## <a name="transactions"></a>交易

資料庫事務`CDaoWorkspace`處理在工作區等級提供 - 請參閱類的[BeginTrans、CommitTrans](../../mfc/reference/cdaoworkspace-class.md#begintrans)和[CommitTrans](../../mfc/reference/cdaoworkspace-class.md#committrans)[回滾](../../mfc/reference/cdaoworkspace-class.md#rollback)成員函數。

## <a name="odbc-connections"></a>ODBC 連接

使用 ODBC 資料來源的建議方法是將外部表附加到 Microsoft Jet (。MDB)資料庫。

## <a name="collections"></a>集合

每個資料庫都維護自己的表def、查詢def、記錄集和關係對象的集合。 類`CDaoDatabase`提供用於操作這些對象的成員函數。

> [!NOTE]
> 物件存儲在 DAO 中,而不是存儲在 MFC 資料庫物件中。 MFC 為表def、查詢def和記錄集物件提供類,但不為關係物件提供類。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

`CDaoDatabase`

## <a name="requirements"></a>需求

**標題:** afxdao.h

## <a name="cdaodatabasecantransact"></a><a name="cantransact"></a>CDao資料庫::可以

調用此成員函數以確定資料庫是否允許事務。

```
BOOL CanTransact();
```

### <a name="return-value"></a>傳回值

如果資料庫支援事務,則非零;否則 0。

### <a name="remarks"></a>備註

事務在資料庫的工作區中管理。

## <a name="cdaodatabasecanupdate"></a><a name="canupdate"></a>CDao 資料庫::可以更新

調用此成員函數以確定`CDaoDatabase`物件是否允許更新。

```
BOOL CanUpdate();
```

### <a name="return-value"></a>傳回值

如果物件允許更新`CDaoDatabase`,則非零;否則 0,指示在`CDaoDatabase`打開 物件時在*bReadOnly*中傳遞 TRUE,或者資料庫本身是唯讀的。 請參閱[打開](#open)成員函數。

### <a name="remarks"></a>備註

有關資料庫可備份性的資訊,請參閱 DAO 説明中的主題"可建立屬性"

## <a name="cdaodatabasecdaodatabase"></a><a name="cdaodatabase"></a>道資料庫::CDao資料庫

建構 `CDaoDatabase` 物件。

```
CDaoDatabase(CDaoWorkspace* pWorkspace = NULL);
```

### <a name="parameters"></a>參數

*p 工作空間*<br/>
指向將包含新`CDaoWorkspace`資料庫物件的物件的指標。 如果接受 NULL 的預設值,建構函數將創建一`CDaoWorkspace`個使用 預設 DAO 工作區的臨時物件。 您可以通過[m_pWorkspace](#m_pworkspace)資料成員獲取指向工作區物件的指標。

### <a name="remarks"></a>備註

建構物件後,如果要創建新的 Microsoft Jet (。MDB) 資料庫,呼叫物件的[「創建](#create)成員」函數。 相反,如果您正在打開現有資料庫,請呼叫物件的[Open](#open)成員函數。

完成該物件后,應調用其[Close](#close)成員函數,然後銷`CDaoDatabase`毀該 物件。

您可能會發現將`CDaoDatabase`物件嵌入到文檔類中很方便。

> [!NOTE]
> 如果`CDaoDatabase`打開[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)物件而不將指標傳遞到`CDaoDatabase`現有 物件,則也會隱式創建物件。 關閉記錄集物件時,此資料庫物件將關閉。

## <a name="cdaodatabaseclose"></a><a name="close"></a>CDao 資料庫:關閉

調用此成員函數以斷開與資料庫的連接,並關閉與資料庫關聯的任何打開的記錄集、表def和查詢def。

```
virtual void Close();
```

### <a name="remarks"></a>備註

最好在調用此成員函數之前自行關閉這些物件。 關閉`CDaoDatabase`物件會將其從關聯的[工作區](../../mfc/reference/cdaoworkspace-class.md)中的"資料庫"集合中刪除。 因為`Close`不會破壞`CDaoDatabase`物件,因此可以通過打開同一資料庫或其他資料庫來重用該物件。

> [!CAUTION]
> 在關閉資料庫之前,調用[Update](../../mfc/reference/cdaorecordset-class.md#update)成員函數(如果有掛`Close`起的 編輯)和所有打開的記錄集物件上的成員函數。 如果您結束的函式會在堆疊`CDaoDatabase`上宣告 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 或物件，則資料庫會關閉，任何未儲存的變更都會遺失，所有暫止的交易都會回復，而且任何暫止的資料編輯都會遺失。

> [!CAUTION]
> 如果在打開任何記錄集物件時嘗試關閉資料庫物件,或者嘗試關閉工作區物件,而屬於該特定工作區的任何資料庫物件處於打開狀態,則這些記錄集物件將關閉,任何掛起的更新或編輯都將回滾。 如果嘗試在屬於工作區物件的任何資料庫物件打開時關閉工作區物件,則操作將關閉屬於該特定工作區物件的所有資料庫物件,這可能會導致關閉未關閉的記錄集物件。 如果不關閉資料庫物件,MFC 將報告調試生成中的斷言失敗。

如果資料庫物件是在函數範圍之外定義的,並且在不關閉該函數的情況下退出該函數,則資料庫物件將保持打開狀態,直到顯式關閉或定義該物件的模組超出範圍。

## <a name="cdaodatabasecreate"></a><a name="create"></a>CDao 資料庫:建立

新增 Microsoft Jet (.MDB) 資料庫,在建`CDaoDatabase`構 物件後調用此成員函數。

```
virtual void Create(
    LPCTSTR lpszName,
    LPCTSTR lpszLocale = dbLangGeneral,
    int dwOptions = 0);
```

### <a name="parameters"></a>參數

*lpsz名稱*<br/>
字串表示式,它是要創建的資料庫檔案的名稱。 它可以是完整的路徑和檔名,如"C:\MYDB"。\\MDB"。 您必須提供名稱。 如果不提供檔案名副檔名, .MDB被追加。 如果您的網路支援統一的命名約定 (UNC),您還可以指定網路路徑,例如\\\\\\\\"_MYSERVER\\\\_MYSHARE _MYDIR _MYDB"。 只有微軟噴氣機 (.可以使用此成員函數創建 MDB 資料庫檔案。 (字串文字中需要雙背斜杠,因為""\\是C++轉義字元。

*lpszLocale*<br/>
用於指定用於創建資料庫的整理順序的字串運算式。 預設值是 `dbLangGeneral`。 可能的值包括：

- `dbLangGeneral`英語、德語、法語、葡萄牙文、義大利文和現代西班牙文

- `dbLangArabic`阿拉伯文

- `dbLangCyrillic`俄語

- `dbLangCzech`捷克文

- `dbLangDutch`荷蘭文

- `dbLangGreek`希臘文

- `dbLangHebrew`希伯來文

- `dbLangHungarian`匈牙利文

- `dbLangIcelandic`冰島文

- `dbLangNordic`北歐語言 (僅限 Microsoft Jet 資料庫引擎版本 1.0)

- `dbLangNorwdan`挪威文和丹麥文

- `dbLangPolish`波蘭文

- `dbLangSpanish`傳統西班牙文

- `dbLangSwedfin`瑞典文和芬蘭文

- `dbLangTurkish`土耳其文

*dwOptions*<br/>
指示一個或多個選項的整數。 可能的值包括：

- `dbEncrypt`創建加密資料庫。

- `dbVersion10`使用 Microsoft Jet 資料庫版本 1.0 創建資料庫。

- `dbVersion11`使用 Microsoft Jet 資料庫版本 1.1 創建資料庫。

- `dbVersion20`使用 Microsoft Jet 資料庫版本 2.0 創建資料庫。

- `dbVersion30`使用 Microsoft Jet 資料庫版本 3.0 創建資料庫。

如果省略加密常量,將創建未加密的資料庫。 只能指定一個版本常量。 如果省略版本常量,將創建使用 Microsoft Jet 資料庫版本 3.0 的資料庫。

> [!CAUTION]
> 如果資料庫未加密,即使您實現了使用者/密碼安全性,也可以直接讀取構成資料庫的二進位磁碟檔。

### <a name="remarks"></a>備註

`Create`創建資料庫檔和基礎DAO資料庫物件並初始化C++物件。 該物件將追加到關聯的工作區的「資料庫」集合中。 資料庫對象處於打開狀態;不要在`Open*``Create`之後 呼叫 。

> [!NOTE]
> 使用`Create`時,只能創建 Microsoft Jet (。MDB)資料庫。 您不能建立 ISAM 資料庫或 ODBC 資料庫。

## <a name="cdaodatabasecreaterelation"></a><a name="createrelation"></a>CDao 資料庫::建立關係

調用此成員函數以建立資料庫中主表中的一個或多個字段與外表中的一個或多個字段(資料庫中的另一個表)之間的關係。

```
void CreateRelation(
    LPCTSTR lpszName,
    LPCTSTR lpszTable,
    LPCTSTR lpszForeignTable,
    long lAttributes,
    LPCTSTR lpszField,
    LPCTSTR lpszForeignField);

void CreateRelation(CDaoRelationInfo& relinfo);
```

### <a name="parameters"></a>參數

*lpsz名稱*<br/>
關係物件的唯一名稱。 名稱必須以字母開頭,最多只能包含 40 個字元。 它可以包括數位和下劃線字元,但不能包括標點符號或空格。

*lpszTable*<br/>
關係中主表的名稱。 如果表不存在,MFC將引發[CDaoException](../../mfc/reference/cdaoexception-class.md)類型的異常。

*lpsz 外表*<br/>
關係中的外表的名稱。 如果表不存在,MFC將引發類型`CDaoException`異常。

*l 屬性*<br/>
包含有關關係類型的資訊的長值。 除其他事項外,可以使用此值強制實施引用完整性。 您可以使用位-OR 運算子 **(&#124;**) 組合以下任一值(只要組合有意義):

- `dbRelationUnique`關係是一對一的。

- `dbRelationDontEnforce`不強制執行關係(沒有引用完整性)。

- `dbRelationInherited`關係存在於包含兩個附加表的非當前資料庫中。

- `dbRelationUpdateCascade`更新將級聯(有關級聯的詳細資訊,請參閱備註)。

- `dbRelationDeleteCascade`刪除將級聯。

*lpszField*<br/>
指向 null 連接字串的指標,其中包含主錶中欄位的名稱(由*lpszTable*命名)。

*lpsz外國場*<br/>
指向空端結束的字串的指標,其中包含外表中欄位的名稱(由*lpsz外表*命名)。

*雷利福*<br/>
對包含要建立關係的資訊的[CDao 關係資訊](../../mfc/reference/cdaorelationinfo-structure.md)物件的引用。

### <a name="remarks"></a>備註

關係不能涉及來自外部資料庫的查詢或附加表。

當關係涉及兩個表中每個表中的一個字段時,請使用函數的第一個版本。 當關係涉及多個字段時,請使用第二個版本。 關係中的最大欄位數為14。

此操作創建一個基礎 DAO 關係物件,但這是 MFC 實現的詳細資訊,因為 MFC 對關係對`CDaoDatabase`象的封裝包含在類 中。 MFC 不為關係提供類。

如果將關係物件的屬性設置為啟動級聯操作,則資料庫引擎在更改相關主鍵表時會自動更新或刪除一個或多個其他表中的記錄。

例如,假設您在客戶表和訂單表之間建立級聯刪除關係。 從"客戶"表中刪除記錄時,"訂單"表中與該客戶相關的記錄也會被刪除。 此外,如果在「訂單」表和其他表之間建立級聯刪除關係,則當您從「客戶」表中刪除記錄時,將自動刪除這些表中的記錄。

有關相關信息,請參閱 DAO 説明中的主題"創建關係方法」。

## <a name="cdaodatabasedeletequerydef"></a><a name="deletequerydef"></a>CDao資料庫::DeleteQueryDef

呼叫此成員函數從`CDaoDatabase`物件的 QueryDefs 集合中刪除指定的查詢def - 保存的查詢。

```
void DeleteQueryDef(LPCTSTR lpszName);
```

### <a name="parameters"></a>參數

*lpsz名稱*<br/>
要刪除的已保存查詢的名稱。

### <a name="remarks"></a>備註

之後,不再在資料庫中定義該查詢。

有關建立查詢定義物件的資訊,請參閱類[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)。 建構物件時,查詢def物件將變為`CDaoDatabase`與特定物件關聯`CDaoQueryDef`, 將該物件傳遞給資料庫物件的指標。

## <a name="cdaodatabasedeleterelation"></a><a name="deleterelation"></a>CDao資料庫::Delete關係

呼叫此成員函數從資料庫物件的"關係"集合中刪除現有關係。

```
void DeleteRelation(LPCTSTR lpszName);
```

### <a name="parameters"></a>參數

*lpsz名稱*<br/>
要刪除的關係的名稱。

### <a name="remarks"></a>備註

之後,關係不再存在。

有關相關信息,請參閱 DAO 説明中的主題"刪除方法"。

## <a name="cdaodatabasedeletetabledef"></a><a name="deletetabledef"></a>CDao資料庫::DeleteTableDef

呼叫此成員函數從`CDaoDatabase`物件的 TableDefs 集合中刪除指定的表及其所有資料。

```
void DeleteTableDef(LPCTSTR lpszName);
```

### <a name="parameters"></a>參數

*lpsz名稱*<br/>
要刪除的表def的名稱。

### <a name="remarks"></a>備註

之後,該表不再在資料庫中定義。

> [!NOTE]
> 非常小心不要刪除系統表。

有關建立表def物件的資訊,請參閱類[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)。 當您建構物件,將指向資料庫物件的指標`CDaoDatabase`傳遞給該物件時,`CDaoTableDef`表def物件將變為與特定對象關聯。

有關相關信息,請參閱 DAO 説明中的主題"刪除方法"。

## <a name="cdaodatabaseexecute"></a><a name="execute"></a>CDao 資料庫:執行

呼叫此成員函數以在資料庫上執行操作查詢或執行 SQL 語句。

```
void Execute(
    LPCTSTR lpszSQL,
    int nOptions = dbFailOnError);
```

### <a name="parameters"></a>參數

*lpszSQL*<br/>
包含要執行的有效 SQL 指令的 null 連接端接字串的指標。

*n 選項*<br/>
指定與查詢完整性相關的選項的整數。 您可以使用位OR運算子 **(&#124;**) 組合以下任一常數(前提是組合有意義 - 例如`dbInconsistent``dbConsistent`,您不會與組合使用 。

- `dbDenyWrite`拒絕其他使用者的寫入許可權。

- `dbInconsistent`( 預設 )更新不一致。

- `dbConsistent`一致的更新。

- `dbSQLPassThrough`SQL 傳遞。 使 SQL 語句傳遞到 ODBC 數據源進行處理。

- `dbFailOnError`如果發生錯誤,回滾更新。

- `dbSeeChanges`如果其他使用者正在更改正在編輯的數據,則生成運行時錯誤。

> [!NOTE]
> 如果兩`dbInconsistent``dbConsistent`者 都包括在內,或者兩者都包括在內,則結果為預設值。 有關這些常量的說明,請參閱DAO説明中的主題"執行方法"。

### <a name="remarks"></a>備註

`Execute`僅適用於不返回結果的操作查詢或 SQL 傳遞查詢。 它不適用於返回記錄的選定查詢。

有關操作查詢的定義和資訊,請參閱 DAO 説明中的「操作查詢」和「執行方法」主題。

> [!TIP]
> 給定語法上正確的 SQL 語句和適當的許可權`Execute`,即使 無法修改或刪除單個行,成員函數也不會失敗。 因此,在使用成員`dbFailOnError`函數運行更新或`Execute`刪除 查詢時,始終使用 選項。 此選項會導致 MFC 引發[CDaoException](../../mfc/reference/cdaoexception-class.md)類型的異常,並在任何受影響的記錄被鎖定且無法更新或刪除時回滾所有成功更改。 請注意,您可以隨時調用`GetRecordsAffected`以查看受影響的記錄數。

調用資料庫物件的[GetRecords 受影響的](#getrecordsaffected)成員函數,以`Execute`確定受最近 調用影響的記錄數。 例如,`GetRecordsAffected`傳回有關在執行作業查詢時刪除、更新或插入的記錄數的資訊。 當級聯更新或刪除生效時,返回的計數不會反映相關表中的更改。

`Execute`不返回記錄集。 在`Execute`選擇記錄的查詢上使用會導致 MFC`CDaoException`引發類型異常。 (沒有`ExecuteSQL`類似於`CDatabase::ExecuteSQL`的成員函數。

## <a name="cdaodatabasegetconnect"></a><a name="getconnect"></a>CDao 資料庫:抓取連線

呼叫此成員函數以檢索用於將`CDaoDatabase`物件連接到 ODBC 或 ISAM 資料庫的連接字串。

```
CString GetConnect();
```

### <a name="return-value"></a>傳回值

如果在 ODBC 資料來源上成功呼叫 Open 的連接字串;如果已在 ODBC 資料來源上成功呼叫[Open,](#open)則連接字串。否則,一個空字串。 對於微軟噴氣式飛機 (.MDB) 資料庫,字串始終為空,除非您將其設置為與[執行](#execute)成員函`dbSQLPassThrough`數 一起使用或用於打開記錄集的選項。

### <a name="remarks"></a>備註

該字串提供有關在傳遞查詢中使用的開放資料庫或資料庫的來源的資訊。 連接字串由資料庫類型指定器和零個或多個參數組成,這些參數由分號分隔。

> [!NOTE]
> 使用 MFC DAO 類透過 ODBC 連接到資料來源的效率低於透過附加表進行連接的效率。

> [!NOTE]
> 連接字串用於根據需要將其他資訊傳遞給 ODBC 和某些 ISAM 驅動程式。 它不用於 。MDB 資料庫。 對於 Microsoft Jet 資料庫基錶,連接字串是一個空字串 (""),除非將其用於 SQL 傳遞查詢,如上面的返回值所述。

有關如何創建連接字串的說明,請參閱[Open](#open)成員函數。 在`Open`呼叫中設定連接字串後,以後可以使用它檢查設定以確定資料庫的類型、路徑、使用者 ID、密碼或 ODBC 資料來源。

## <a name="cdaodatabasegetname"></a><a name="getname"></a>CDao 資料庫:取得名稱

呼叫此成員函數以檢索目前打開的資料庫的名稱,該資料庫是現有資料庫檔的名稱或已註冊的 ODBC 資料來源的名稱。

```
CString GetName();
```

### <a name="return-value"></a>傳回值

資料庫的完整路徑和檔名(如果成功);否則,空[的 CString](../../atl-mfc-shared/reference/cstringt-class.md)。

### <a name="remarks"></a>備註

如果您的網络支援統一的命名約定 (UNC),您\\\\\\還可以 指定網络路徑,例如,"[MYSERVER\\]MYSHARE\\\\\MYDIR _MYDB。MDB"。 (字串文字中需要雙背斜杠,因為""\\是C++轉義字元。

例如,您可能希望在標題中顯示此名稱。 如果在檢索名稱時發生錯誤,MFC 將引發[CDaoException](../../mfc/reference/cdaoexception-class.md)類型的異常。

> [!NOTE]
> 為了在訪問外部資料庫時獲得更好的性能,我們建議您將外部資料庫表附加到 Microsoft Jet 資料庫 (。MDB),而不是直接連接到數據源。

資料庫類型由路徑指向的檔或目錄指示,如下所示:

|路徑名稱指向.|資料庫類型|
|--------------------------|-------------------|
|.MDB 檔案|微軟噴氣資料庫(微軟存取)|
|包含的目錄。DBF 檔案|dBASE 資料庫|
|包含的目錄。XLS 檔案|微軟Excel資料庫|
|包含的目錄。PDX 檔案|悖論資料庫|
|包含適當格式的文字資料庫檔案的目錄|文字格式資料庫|

對於 ODBC 資料庫(如 SQL Server 和 Oracle),資料庫的連接字串識別由 ODBC 註冊的數據來源名稱 (DSN)。

## <a name="cdaodatabasegetquerydefcount"></a><a name="getquerydefcount"></a>CDao 資料庫::取得查詢定義

呼叫此成員函數以檢索資料庫的 QueryDefs 集合中定義的查詢數。

```
short GetQueryDefCount();
```

### <a name="return-value"></a>傳回值

資料庫中定義的查詢數。

### <a name="remarks"></a>備註

`GetQueryDefCount`如果需要循環瀏覽查詢Defs 集合中的所有查詢def,則非常有用。 要取得有關集合中給定查詢的資訊,請參閱[GetQueryDefInfo](#getquerydefinfo)。

## <a name="cdaodatabasegetquerydefinfo"></a><a name="getquerydefinfo"></a>CDao 資料庫::獲取查詢資訊

調用此成員函數以獲取有關資料庫中定義的查詢的各種資訊。

```
void GetQueryDefInfo(
    int nIndex,
    CDaoQueryDefInfo& querydefinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetQueryDefInfo(
    LPCTSTR lpszName,
    CDaoQueryDefInfo& querydefinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
資料庫的 QueryDefs 集合中預定義查詢的索引,用於按索引查找。

*查詢definfo*<br/>
對返回請求的資訊的[CDaoQueryDefInfo](../../mfc/reference/cdaoquerydefinfo-structure.md)物件的引用。

*dwInfoOptions*<br/>
指定有關要檢索的記錄集的資訊的選項。 此處列出可用選項以及它們導致函數傳回紀錄集的原因:

- AFX_DAO_PRIMARY_INFO(預設)名稱、類型

- AFX_DAO_SECONDARY_INFO主要資訊加上:建立日期、上次更新日期、傳回記錄、可升級

- AFX_DAO_ALL_INFO主要和輔助資訊加上:SQL、連接、ODBCTimeout

*lpsz名稱*<br/>
包含資料庫中定義的查詢名稱的字串,用於按名稱查找。

### <a name="remarks"></a>備註

提供了函數的兩個版本,以便可以通過資料庫的 QueryDefs 集合中的索引或查詢的名稱來選擇查詢。

有關*查詢中*返回的信息的說明,請參閱[CDaoQueryDefinfo](../../mfc/reference/cdaoquerydefinfo-structure.md)結構。 此結構的成員對應於*dwInfoOptions*描述中列出的資訊項。 如果您請求一級資訊,您也會得到任何以前的資訊級別。

## <a name="cdaodatabasegetquerytimeout"></a><a name="getquerytimeout"></a>CDao 資料庫:取得查詢逾時

調用此成員函數以檢索當前秒數,以便在連接的資料庫上的後續操作超時之前允許。

```
short GetQueryTimeout();
```

### <a name="return-value"></a>傳回值

包含超時值(以秒為單位)的短整數。

### <a name="remarks"></a>備註

操作可能會由於網路訪問問題、查詢處理時間過長等原因而超時。 當該設置生效時,它會影響與此`CDaoDatabase`物件關聯的任何記錄集上的所有打開、添加新、更新和刪除操作。 您可以通過調用[SetQueryTimeout](#setquerytimeout)來更改當前超時設置。 打開後更改記錄集的查詢超時值不會更改記錄集的值。 例如,後續[移動](../../mfc/reference/cdaorecordset-class.md#move)操作不使用新值。 初始化資料庫引擎時,最初會設置預設值。

查詢超時的預設值取自 Windows 註冊表。 如果沒有註冊表設置,則預設值為 60 秒。 並非所有資料庫都支援設置查詢超時值的能力。 如果將查詢超時值設置為 0,則不執行超時;如果將超時設置為 0,則不執行超時。與資料庫的通信可能會停止回應。 此行為在開發期間可能很有用。 如果調用失敗,MFC 將引發[CDaoException](../../mfc/reference/cdaoexception-class.md)類型的異常。

有關相關信息,請參閱 DAO 説明中的"查詢超時屬性"主題。

## <a name="cdaodatabasegetrecordsaffected"></a><a name="getrecordsaffected"></a>CDao 資料庫:取得受影響的記錄

調用此成員函數以確定受[Execute](#execute)成員函數最近調用影響的記錄數。

```
long GetRecordsAffected();
```

### <a name="return-value"></a>傳回值

包含受影響的記錄數的長整數。

### <a name="remarks"></a>備註

傳回的值包括`Execute`使用 執行的操作查詢刪除、更新或插入的記錄數。 當級聯更新或刪除生效時,返回的計數不會反映相關表中的更改。

有關相關信息,請參閱 DAO 説明中的主題「記錄受影響的屬性」。

## <a name="cdaodatabasegetrelationcount"></a><a name="getrelationcount"></a>CDao 資料庫:取得關聯數

調用此成員函數以獲取資料庫中表之間定義的關係數。

```
short GetRelationCount();
```

### <a name="return-value"></a>傳回值

資料庫中表之間定義的關係數。

### <a name="remarks"></a>備註

`GetRelationCount`如果需要迴圈訪問資料庫關係集合中的所有已定義關係,則非常有用。 要取得有關集合中給定關係的資訊,請參閱[GetRelationInfo](#getrelationinfo)。

為了說明關係的概念,請考慮供應商表和產品表,它們可能具有一對多關係。 在此關係中,一個供應商可以提供多個產品。 其他關係是一對一和多對多。

## <a name="cdaodatabasegetrelationinfo"></a><a name="getrelationinfo"></a>CDao 資料庫:抓取關係資訊

呼叫此成員函數以獲取有關資料庫關係集合中指定關係的資訊。

```
void GetRelationInfo(
    int nIndex,
    CDaoRelationInfo& relinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetRelationInfo(
    LPCTSTR lpszName,
    CDaoRelationInfo& relinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
關係物件在資料庫的關係集合中的索引,用於按索引查找。

*雷利福*<br/>
對返回請求的資訊的[CDao 關係資訊](../../mfc/reference/cdaorelationinfo-structure.md)物件的引用。

*dwInfoOptions*<br/>
指定有關要檢索的關係的資訊的選項。 此處列出了可用選項以及它們導致函數傳回的關係的原因:

- AFX_DAO_PRIMARY_INFO(預設)名稱、表、外表

- AFX_DAO_SECONDARY_INFO屬性、欄位資訊

欄位資訊是包含關係中涉及的主表中的欄位的[CDao 關係 FieldInfo](../../mfc/reference/cdaorelationfieldinfo-structure.md)物件。

*lpsz名稱*<br/>
包含關係物件名稱的字串,用於按名稱查找。

### <a name="remarks"></a>備註

此函數的兩個版本提供索引或名稱的訪問。 有關*在 relinfo*中傳回的說明,請參閱[CDao 關係資訊](../../mfc/reference/cdaorelationinfo-structure.md)結構。 此結構的成員對應於*dwInfoOptions*描述中列出的資訊項。 如果您在一個級別請求資訊,您還會在任何以前的級別上獲取資訊。

> [!NOTE]
> 如果將關係物件的屬性設置為啟動級聯操作`dbRelationUpdateCascades`(`dbRelationDeleteCascades`或 ),則當對相關主鍵表進行更改時,Microsoft Jet 資料庫引擎會自動更新或刪除一個或多個其他表中的記錄。 例如,假設您在客戶表和訂單表之間建立級聯刪除關係。 從"客戶"表中刪除記錄時,"訂單"表中與該客戶相關的記錄也會被刪除。 此外,如果在「訂單」表和其他表之間建立級聯刪除關係,則當您從「客戶」表中刪除記錄時,將自動刪除這些表中的記錄。

## <a name="cdaodatabasegettabledefcount"></a><a name="gettabledefcount"></a>CDao 資料庫:取得TableDef( C)

調用此成員函數以檢索資料庫中定義的表數。

```
short GetTableDefCount();
```

### <a name="return-value"></a>傳回值

資料庫中定義的表defs數。

### <a name="remarks"></a>備註

`GetTableDefCount`如果需要循環訪問資料庫的 TableDefs 集合中的所有表def,則非常有用。 要取得有關集合中給定表的資訊,請參閱[GetTableDefInfo](#gettabledefinfo)。

## <a name="cdaodatabasegettabledefinfo"></a><a name="gettabledefinfo"></a>CDao 資料庫:抓取桌面資訊

調用此成員函數以獲取有關資料庫中定義的表的各種資訊。

```
void GetTableDefInfo(
    int nIndex,
    CDaoTableDefInfo& tabledefinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetTableDefInfo(
    LPCTSTR lpszName,
    CDaoTableDefInfo& tabledefinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
資料庫的 TableDefs 集合中的表def物件的索引,用於按索引查找。

*表德福*<br/>
傳回請求的資訊的[CDaoTableDefInfo](../../mfc/reference/cdaotabledefinfo-structure.md)物件的參考。

*dwInfoOptions*<br/>
指定要檢索的表的選項。 此處列出了可用選項以及它們導致函數傳回的關係的原因:

- AFX_DAO_PRIMARY_INFO(預設)名稱、可上可、屬性

- AFX_DAO_SECONDARY_INFO主要資訊加上:建立日期、上次更新日期、源表名稱、連接

- AFX_DAO_ALL_INFO主要和輔助資訊加上:驗證規則、驗證文本、記錄計數

*lpsz名稱*<br/>
表def物件的名稱,用於按名稱查找。

### <a name="remarks"></a>備註

提供了函數的兩個版本,以便您可以通過資料庫的 TableDefs 集合中的索引或表的名稱來選擇表。

有關*表中*返回的資訊的說明,請參閱[CDaoTable Definfo](../../mfc/reference/cdaotabledefinfo-structure.md)結構。 此結構的成員對應於*dwInfoOptions*描述中列出的資訊項。 如果您在一個級別請求資訊,則也獲取任何以前級別的資訊。

> [!NOTE]
> AFX_DAO_ALL_INFO選項提供的資訊可能獲取速度很慢。 在這種情況下,如果有許多記錄,計算表中的記錄可能非常耗時。

## <a name="cdaodatabasegetversion"></a><a name="getversion"></a>CDao 資料庫:抓取版本

呼叫此成員函數以確定 Microsoft Jet 資料庫檔的版本。

```
CString GetVersion();
```

### <a name="return-value"></a>傳回值

指示與物件關聯的資料庫檔的版本的[CString。](../../atl-mfc-shared/reference/cstringt-class.md)

### <a name="remarks"></a>備註

返回的值表示窗體「主要.minor」中的版本號;例如,"3.0"。 產品版本號(例如 3.0)由版本號 (3)、句點和發行號 (0) 組成。 到目前為止的版本是 1.0、1.1、2.0 和 3.0。

有關相關信息,請參閱 DAO 説明中的主題"版本屬性」。。

## <a name="cdaodatabaseisopen"></a><a name="isopen"></a>CDao 資料庫::是開啟的

調用此成員函數以確定物件`CDaoDatabase`當前是否在資料庫上打開。

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>傳回值

如果物件當前處於`CDaoDatabase`打開狀態,則非零;否則 0。

### <a name="remarks"></a>備註

## <a name="cdaodatabasem_pdaodatabase"></a><a name="m_pdaodatabase"></a>CDao資料庫::m_pDAODatabase

包含指向物件基礎的 DAO 資料庫物件的 OLE 介面的`CDaoDatabase`指標。

### <a name="remarks"></a>備註

如果需要直接訪問 DAO 介面,請使用此指標。

有關直接呼叫 DAO 的資訊,請參閱[技術說明 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。

## <a name="cdaodatabasem_pworkspace"></a><a name="m_pworkspace"></a>CDao資料庫:m_pWorkspace

包含指向包含資料庫物件的[CDao 工作區](../../mfc/reference/cdaoworkspace-class.md)物件的指標。

### <a name="remarks"></a>備註

如果需要直接訪問工作區,請使用此指標,例如,獲取指向工作區資料庫集合中其他資料庫物件的指標。

## <a name="cdaodatabaseopen"></a><a name="open"></a>CDao 資料庫::開啟

必須調用此成員函數來初始化表示現有資料庫的新`CDaoDatabase`構造物件。

```
virtual void Open(
    LPCTSTR lpszName,
    BOOL bExclusive = FALSE,
    BOOL bReadOnly = FALSE,
    LPCTSTR lpszConnect = _T(""));
```

### <a name="parameters"></a>參數

*lpsz名稱*<br/>
為現有 Microsoft Jet () 名稱的字串表示式 。MDB)資料庫檔案。 如果檔名具有副檔名,則需要它。 如果您的網路支援統一的命名約定 (UNC),您還可以指定網路路徑,例如\\\\\\\\"_MYSERVER\\\\_MYSHARE \MYDIR _MYDB"。MDB"。 (字串文字中需要雙背斜杠,因為""\\是C++轉義字元。

使用*lpszName*時,需要考慮一些注意事項。 如果是:

- 指已開放供其他用戶獨佔訪問的資料庫,MFC 將引發[CDaoException](../../mfc/reference/cdaoexception-class.md)類型的異常。 捕獲該異常,讓使用者知道資料庫不可用。

- 是空字串 ("")和*lpszConnect*是"ODBC;;",顯示一個對話框,列出所有已註冊的ODBC資料原始碼名稱,以便使用者可以選擇資料庫。 應避免直接連接到 ODBC 資料源;改用附加的表。

- 否則不引用現有資料庫或有效的ODBC數據來源名稱,MFC將引發類型`CDaoException`異常。

> [!NOTE]
> 有關DAO錯誤代碼的詳細資訊,請參閱DAOERR。H 檔。 有關相關信息,請參閱 DAO 説明中的主題"可捕獲的數據訪問錯誤」。。

*b 獨家*<br/>
如果資料庫要打開以進行獨佔(非共用)訪問,則為 TRUE 的布爾值,如果要打開資料庫以進行共享訪問,則為 FALSE。 如果省略此參數,資料庫將打開以進行共享訪問。

*b 唯讀*<br/>
如果資料庫要打開以進行唯讀訪問,則為 TRUE 的布林值,如果要打開資料庫以進行讀/寫存取,則為 FALSE。 如果省略此參數,資料庫將打開以進行讀取/寫入訪問。 所有從屬記錄集都繼承此屬性。

*lpszConnect*<br/>
用於打開資料庫的字串運算式。 此字串構成 ODBC 連接參數。 您必須提供獨佔和唯讀參數才能提供原始字串。 如果資料庫是Microsoft Jet資料庫 (。MDB),此字串為空(")。 默認值的語法 [ **_T**(") - 為 Unicode 以及應用程式的 ANSI 生成提供了可移植性。

### <a name="remarks"></a>備註

`Open`將資料庫與基礎DAO物件關聯。 在初始化記錄物件之前,不能使用資料庫物件構造記錄集、表def 或 querydef 物件。 `Open`將資料庫物件追加到關聯的工作區的資料庫集合。

使用參數如下:

- 如果您要打開微軟噴氣機 (。MDB) 資料庫,使用*lpszName*參數並傳遞*lpszConnect*參數的空字串或傳遞窗體的密碼字串";如果資料庫受密碼保護(,則PWD_密碼)。僅限 MDB 資料庫)。

- 如果要打開 ODBC 資料來源,請傳遞*lpszConnect*中的有效 ODBC 連接字串和*lpszName*中的空字串。

有關相關信息,請參閱 DAO 説明中的主題"打開資料庫方法」。

> [!NOTE]
> 為了在存取外部資料庫(包括 ISAM 資料庫和 ODBC 資料來源)時性能更好,建議您將外部資料庫表附加到 Microsoft Jet 引擎資料庫 ()。MDB),而不是直接連接到數據源。

例如,如果 DBMS 主機不可用,連接嘗試可能會超時。 如果連線嘗試失敗,`Open`將引發[CDaoException](../../mfc/reference/cdaoexception-class.md)類型的異常。

其餘註解僅適用於 ODBC 資料庫:

如果資料庫是 ODBC 資料庫`Open`,並且呼叫中的參數不包含足夠的資訊來建立連接,則 ODBC 驅動程式將打開一個對話框,從使用者處獲取必要的資訊。 呼叫`Open`時 ,連接字串*lpszConnect*將私下存儲,可透過呼叫[GetConnect](#getconnect)成員函數獲得。

如果需要,可以在調用`Open`之前打開自己的對話框,以便從使用者獲取資訊(如密碼),然後將該資訊添加到傳遞給的連接字串`Open`中。 或者,您可能希望保存傳遞的連接字串(可能位於 Windows 註冊表中),以便在應用程式下次調`Open``CDaoDatabase`用 物件時重用它。

您還可以使用連接字串進行多個級別的登錄授權(每個級別用於其他`CDaoDatabase`物件),或傳輸其他特定於資料庫的資訊。

## <a name="cdaodatabasesetquerytimeout"></a><a name="setquerytimeout"></a>CDao 資料庫::設定查詢逾時

調用此成員函數以覆蓋預設秒數,以便在後續對連接的資料庫超時執行操作之前允許。

```
void SetQueryTimeout(short nSeconds);
```

### <a name="parameters"></a>參數

*n 秒*<br/>
查詢嘗試超時之前要允許的秒數。

### <a name="remarks"></a>備註

操作可能會由於網路訪問問題、查詢處理時間過長等而超時。 如果要`SetQueryTimeout`更改查詢超時值,請先打開記錄集之前或調用記錄集的[AddNew、Update](../../mfc/reference/cdaorecordset-class.md#addnew)或[刪除](../../mfc/reference/cdaorecordset-class.md#delete)成員函數。 [Update](../../mfc/reference/cdaorecordset-class.md#update) 該設置影響所有後續[的](../../mfc/reference/cdaorecordset-class.md#open)`AddNew` `Update`Open`Delete`、 和`CDaoDatabase`對與此 物件關聯的任何記錄集的調用。 打開後更改記錄集的查詢超時值不會更改記錄集的值。 例如,後續[移動](../../mfc/reference/cdaorecordset-class.md#move)操作不使用新值。

查詢超時的預設值為60秒。 並非所有資料庫都支援設置查詢超時值的能力。 如果將查詢超時值設置為 0,則不執行超時;如果將超時設置為 0,則不執行超時。與資料庫的通信可能會停止回應。 此行為在開發期間可能很有用。

有關相關信息,請參閱 DAO 説明中的"查詢超時屬性"主題。

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CDaoWorkspace 類別](../../mfc/reference/cdaoworkspace-class.md)<br/>
[CDaoRecordset 類別](../../mfc/reference/cdaorecordset-class.md)<br/>
[CDaoTableDef 類別](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoQueryDef 類別](../../mfc/reference/cdaoquerydef-class.md)<br/>
[CDatabase 類別](../../mfc/reference/cdatabase-class.md)<br/>
[CDaoException 類別](../../mfc/reference/cdaoexception-class.md)
