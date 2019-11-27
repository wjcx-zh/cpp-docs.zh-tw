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
ms.openlocfilehash: 4c594b1ddfc1464417506557bb8743c4979be677
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74304293"
---
# <a name="cdaodatabase-class"></a>CDaoDatabase 類別

表示使用資料存取物件（DAO）的 Access 資料庫連接。 DAO 受到 Office 2013 的支援。 DAO 3.6 是最後的版本，被視為已淘汰。

## <a name="syntax"></a>語法

```
class CDaoDatabase : public CObject
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CDaoDatabase：： CDaoDatabase](#cdaodatabase)|建構 `CDaoDatabase` 物件。 呼叫 `Open` 以將物件連接到資料庫。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDaoDatabase：： CanTransact](#cantransact)|如果資料庫支援交易，則傳回非零。|
|[CDaoDatabase：： CanUpdate](#canupdate)|如果 `CDaoDatabase` 物件是可更新的（非唯讀），則傳回非零。|
|[CDaoDatabase：： Close](#close)|關閉資料庫連接。|
|[CDaoDatabase：： Create](#create)|建立基礎 DAO 資料庫物件，並初始化 `CDaoDatabase` 物件。|
|[CDaoDatabase：： CreateRelation](#createrelation)|定義資料庫中資料表之間的新關聯性。|
|[CDaoDatabase：:D eleteQueryDef](#deletequerydef)|刪除儲存在資料庫 QueryDefs 集合中的 querydef 物件。|
|[CDaoDatabase：:D eleteRelation](#deleterelation)|刪除資料庫中資料表之間的現有關聯。|
|[CDaoDatabase：:D eleteTableDef](#deletetabledef)|刪除資料庫中資料表的定義。 這會刪除實際的資料表及其所有資料。|
|[CDaoDatabase：： Execute](#execute)|執行動作查詢。 針對傳回結果的查詢呼叫 `Execute` 會擲回例外狀況。|
|[CDaoDatabase：： GetConnect](#getconnect)|傳回用來將 `CDaoDatabase` 物件連接至資料庫的連接字串。 用於 ODBC。|
|[CDaoDatabase：： GetName](#getname)|傳回目前使用中的資料庫名稱。|
|[CDaoDatabase：： GetQueryDefCount](#getquerydefcount)|傳回針對資料庫定義的查詢數目。|
|[CDaoDatabase：： GetQueryDefInfo](#getquerydefinfo)|傳回資料庫中所定義之指定查詢的相關資訊。|
|[CDaoDatabase：： GetQueryTimeout](#getquerytimeout)|傳回資料庫查詢作業將會超時的秒數。會影響 ODBC 資料來源上的所有後續開啟、加入新的、更新和編輯作業和其他作業（僅限 `Execute` 呼叫）。|
|[CDaoDatabase：： GetRecordsAffected](#getrecordsaffected)|傳回受上次更新、編輯或加入作業影響，或呼叫 `Execute`的記錄數目。|
|[CDaoDatabase：： GetRelationCount](#getrelationcount)|傳回在資料庫中的資料表之間定義的關聯性數目。|
|[CDaoDatabase：： GetRelationInfo](#getrelationinfo)|傳回在資料庫的資料表之間定義之指定關聯的相關資訊。|
|[CDaoDatabase：： GetTableDefCount](#gettabledefcount)|傳回資料庫中定義的資料表數目。|
|[CDaoDatabase：： GetTableDefInfo](#gettabledefinfo)|傳回資料庫中指定之資料表的相關資訊。|
|[CDaoDatabase：： GetVersion](#getversion)|傳回與資料庫相關聯的資料庫引擎版本。|
|[CDaoDatabase：： IsOpen](#isopen)|如果 `CDaoDatabase` 物件目前連接到資料庫，則傳回非零。|
|[CDaoDatabase：： Open](#open)|建立資料庫的連接。|
|[CDaoDatabase：： SetQueryTimeout](#setquerytimeout)|設定資料庫查詢作業（僅限 ODBC 資料來源）將會超時的秒數。會影響所有後續的開啟、新增、更新和刪除作業。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CDaoDatabase：： m_pDAODatabase](#m_pdaodatabase)|基礎 DAO 資料庫物件的指標。|
|[CDaoDatabase：： m_pWorkspace](#m_pworkspace)|[CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)物件的指標，其中包含資料庫並定義其交易空間。|

## <a name="remarks"></a>備註

如需所支援資料庫格式的詳細資訊，請參閱[GetName](../../mfc/reference/cdaoworkspace-class.md#getname)成員函式。 在指定的「工作區」中，您可以一次使用一個或多個 `CDaoDatabase` 物件，其以[CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)物件表示。 工作區會維護一個開放式資料庫物件的集合，稱為「資料庫集合」。

## <a name="usage"></a>使用方式

當您建立記錄集物件時，可以隱含地建立資料庫物件。 但是您也可以明確地建立資料庫物件。 若要使用現有的資料庫明確搭配 `CDaoDatabase`，請執行下列其中一項動作：

- 建立 `CDaoDatabase` 物件，並將指標傳遞至開啟的[CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)物件。

- 或在不指定工作區的情況下，建立 `CDaoDatabase` 物件（MFC 會建立暫存工作區物件）。

建立新的 Microsoft Jet （。MDB）資料庫，請建立 `CDaoDatabase` 物件，並呼叫它的[Create](#create)成員函式。 請*不要*在 `Create`後呼叫 `Open`。

若要開啟現有的資料庫，請建立 `CDaoDatabase` 物件，並呼叫其[open](#open)成員函式。

其中任何一項技術會將 DAO 資料庫物件附加至工作區的資料庫集合，並開啟與資料的連接。 當您接著建立[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)、 [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)或[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)物件來操作已連接的資料庫時，請傳遞這些物件的函式給您 `CDaoDatabase` 物件的指標。 當您使用連接完成時，請呼叫[Close](#close)成員函式，並終結 `CDaoDatabase` 物件。 `Close` 關閉先前尚未關閉的任何記錄集。

## <a name="transactions"></a>交易

資料庫交易處理是在工作區層級提供的，請參閱[BeginTrans](../../mfc/reference/cdaoworkspace-class.md#begintrans)、 [CommitTrans](../../mfc/reference/cdaoworkspace-class.md#committrans)和 class `CDaoWorkspace`的[Rollback](../../mfc/reference/cdaoworkspace-class.md#rollback)成員函式。

## <a name="odbc-connections"></a>ODBC 連接

使用 ODBC 資料來源的建議方式是將外部資料表附加至 Microsoft Jet （。MDB）資料庫。

## <a name="collections"></a>集合

每個資料庫都會維護它自己的 tabledef、querydef、recordset 和關聯性物件集合。 類別 `CDaoDatabase` 提供用來操作這些物件的成員函式。

> [!NOTE]
>  物件會儲存在 DAO 中，而不是在 MFC 資料庫物件中。 MFC 提供 tabledef、querydef 和 recordset 物件的類別，但不適用於關聯物件。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

`CDaoDatabase`

## <a name="requirements"></a>需求

**標頭：** afxdao。h

##  <a name="cantransact"></a>CDaoDatabase：： CanTransact

呼叫這個成員函式，以判斷資料庫是否允許交易。

```
BOOL CanTransact();
```

### <a name="return-value"></a>傳回值

如果資料庫支援交易，則為非零值;否則為0。

### <a name="remarks"></a>備註

交易是在資料庫的工作區中進行管理。

##  <a name="canupdate"></a>CDaoDatabase：： CanUpdate

呼叫這個成員函式，以判斷 `CDaoDatabase` 物件是否允許更新。

```
BOOL CanUpdate();
```

### <a name="return-value"></a>傳回值

如果 `CDaoDatabase` 物件允許更新，則為非零值;否則為0，表示當您開啟 `CDaoDatabase` 物件或資料庫本身為唯讀時，您是在*bReadOnly*中傳遞 TRUE。 請參閱[Open](#open)成員函式。

### <a name="remarks"></a>備註

如需資料庫可更新性的詳細資訊，請參閱 DAO 說明中的「可更新屬性」主題。

##  <a name="cdaodatabase"></a>CDaoDatabase：： CDaoDatabase

建構 `CDaoDatabase` 物件。

```
CDaoDatabase(CDaoWorkspace* pWorkspace = NULL);
```

### <a name="parameters"></a>參數

*pWorkspace*<br/>
將包含新資料庫物件之 `CDaoWorkspace` 物件的指標。 如果您接受預設值 Null，則此函式會建立一個使用預設 DAO 工作區的暫時 `CDaoWorkspace` 物件。 您可以透過[m_pWorkspace](#m_pworkspace)資料成員取得工作區物件的指標。

### <a name="remarks"></a>備註

在建立物件之後，如果您要建立新的 Microsoft Jet （。MDB）資料庫，請呼叫物件的[Create](#create)成員函式。 如果您改為開啟現有的資料庫，請呼叫物件的[Open](#open)成員函式。

當您完成物件時，您應該呼叫它的[Close](#close)成員函式，然後終結 `CDaoDatabase` 物件。

您可能會發現，將 `CDaoDatabase` 物件內嵌在檔類別中是很方便的。

> [!NOTE]
>  如果您開啟[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)物件，但未傳遞現有 `CDaoDatabase` 物件的指標，則也會隱含地建立 `CDaoDatabase` 物件。 當您關閉記錄集物件時，這個資料庫物件會關閉。

##  <a name="close"></a>CDaoDatabase：： Close

呼叫這個成員函式以中斷與資料庫的連接，並關閉與資料庫相關聯的任何開啟的記錄集、tabledefs 和 querydefs。

```
virtual void Close();
```

### <a name="remarks"></a>備註

在您呼叫這個成員函式之前，請先關閉這些物件，這是很好的作法。 關閉 `CDaoDatabase` 物件，會將它從相關[工作區](../../mfc/reference/cdaoworkspace-class.md)的資料庫集合中移除。 因為 `Close` 不會摧毀 `CDaoDatabase` 物件，所以您可以藉由開啟相同的資料庫或不同的資料庫來重複使用物件。

> [!CAUTION]
>  在您關閉資料庫之前，請先呼叫[Update](../../mfc/reference/cdaorecordset-class.md#update)成員函式（如果有暫止的編輯）和所有開啟的記錄集物件上的 `Close` 成員函式。 如果您結束的函式會在堆疊[上宣告 ](../../mfc/reference/cdaorecordset-class.md)CDaoRecordset`CDaoDatabase` 或物件，則資料庫會關閉，任何未儲存的變更都會遺失，所有暫止的交易都會回復，而且任何暫止的資料編輯都會遺失。

> [!CAUTION]
>  如果您嘗試在任何記錄集物件開啟時關閉資料庫物件，或如果您嘗試在任何屬於該特定工作區的資料庫物件開啟時關閉工作區物件，這些記錄集物件將會關閉，而且任何暫止的更新或編輯都會是已回復。 如果您嘗試在任何屬於它的資料庫物件開啟時關閉工作區物件，此作業會關閉屬於該特定工作區物件的所有資料庫物件，這可能會導致關閉的記錄集物件無法使用。 如果您未關閉資料庫物件，MFC 會在 debug build 中報告判斷提示失敗。

如果資料庫物件定義在函式的範圍之外，而且您在未關閉函數的情況下結束它，則資料庫物件會保持開啟狀態，直到明確關閉或其定義所在的模組超出範圍。

##  <a name="create"></a>CDaoDatabase：： Create

建立新的 Microsoft Jet （。MDB）資料庫，在您建立 `CDaoDatabase` 物件之後，請呼叫這個成員函式。

```
virtual void Create(
    LPCTSTR lpszName,
    LPCTSTR lpszLocale = dbLangGeneral,
    int dwOptions = 0);
```

### <a name="parameters"></a>參數

*lpszName*<br/>
字串運算式，這是您要建立之資料庫檔案的名稱。 它可以是完整路徑和檔案名，例如 "C：\\\MYDB。MDB」。 您必須提供名稱。 如果您未提供副檔名，則為。已附加 MDB。 如果您的網路支援統一命名慣例（UNC），您也可以指定網路路徑，例如 "\\\\\\\MYSERVER\\\MYSHARE\\\MYDIR\\\MYDB"。 僅限 Microsoft Jet （。MDB）可以使用這個成員函式建立資料庫檔案。 （字串常值中必須有兩個反斜線，因為 " C++\\" 是 escape 字元）。

*lpszLocale*<br/>
用來指定建立資料庫之排序次序的字串運算式。 預設值是 `dbLangGeneral`。 可能的值為：

- `dbLangGeneral` 英文、德文、法文、葡萄牙文、義大利文和新式西班牙文

- `dbLangArabic` 阿拉伯文

- `dbLangCyrillic` 俄文

- `dbLangCzech` 捷克文

- `dbLangDutch` 荷蘭文

- `dbLangGreek` 希臘文

- `dbLangHebrew` 希伯來文

- `dbLangHungarian` 匈牙利文

- `dbLangIcelandic` 冰島文

- `dbLangNordic` 北歐語言（僅限 Microsoft Jet database engine 1.0 版）

- `dbLangNorwdan` 挪威文和丹麥文

- `dbLangPolish` 波蘭文

- `dbLangSpanish` 傳統西班牙文

- `dbLangSwedfin` 瑞典文和芬蘭文

- `dbLangTurkish` 土耳其文

*dwOptions*<br/>
表示一或多個選項的整數。 可能的值為：

- `dbEncrypt` 建立加密的資料庫。

- `dbVersion10` 使用 Microsoft Jet 資料庫版本1.0 建立資料庫。

- `dbVersion11` 使用 Microsoft Jet 資料庫版本1.1 建立資料庫。

- `dbVersion20` 使用 Microsoft Jet 資料庫版本2.0 建立資料庫。

- `dbVersion30` 使用 Microsoft Jet 資料庫版本3.0 建立資料庫。

如果您省略加密常數，則會建立未加密的資料庫。 您只能指定一個版本常數。 如果您省略版本常數，則會建立使用 Microsoft Jet 資料庫3.0 版的資料庫。

> [!CAUTION]
>  如果資料庫未加密，即使您執行使用者/密碼安全性，也可能會直接讀取構成資料庫的二進位磁片檔案。

### <a name="remarks"></a>備註

`Create` 會建立資料庫檔案和基礎 DAO 資料庫物件，並初始化C++物件。 物件會附加到相關聯的工作區資料庫集合。 資料庫物件處於開啟狀態;請不要在 `Create`後呼叫 `Open*`。

> [!NOTE]
>  使用 `Create`，您只可以建立 Microsoft Jet （）。MDB）資料庫。 您不能建立 ISAM 資料庫或 ODBC 資料庫。

##  <a name="createrelation"></a>CDaoDatabase：： CreateRelation

呼叫這個成員函式，以建立資料庫中主資料表的一個或多個欄位之間的關聯性，以及外部資料表中的一或多個欄位（資料庫中的另一個資料表）。

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

*lpszName*<br/>
關聯性物件的唯一名稱。 名稱必須以字母開頭，且最多可包含40個字元。 它可以包含數位和底線字元，但不能包含標點符號或空格。

*lpszTable*<br/>
關聯性中的主資料表名稱。 如果資料表不存在，則 MFC 會擲回[CDaoException](../../mfc/reference/cdaoexception-class.md)類型的例外狀況。

*lpszForeignTable*<br/>
關聯性中的外部資料表名稱。 如果資料表不存在，則 MFC 會擲回 `CDaoException`類型的例外狀況。

*lAttributes*<br/>
包含關聯性類型相關資訊的長數值。 您可以使用這個值來強制執行參考完整性，還有其他專案。 您可以使用位 OR 運算子（ **&#124;** ）來結合下列任何值（只要組合合理）：

- `dbRelationUnique` 關聯性為一對一。

- 不會強制執行 `dbRelationDontEnforce` 關聯性（沒有參考完整性）。

- `dbRelationInherited` 關聯性存在於包含兩個附加資料表的 noncurrent 資料庫中。

- `dbRelationUpdateCascade` 更新會重迭（如需有關 cascade 的詳細資訊，請參閱備註）。

- `dbRelationDeleteCascade` 刪除會重迭。

*lpszField*<br/>
以 null 終止的字串指標，其中包含主表中的功能變數名稱（由*lpszTable*命名）。

*lpszForeignField*<br/>
以 null 終止的字串指標，其中包含外部資料表中的功能變數名稱（由*lpszForeignTable*命名）。

*relinfo*<br/>
[CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md)物件的參考，其中包含您想要建立之關聯性的相關資訊。

### <a name="remarks"></a>備註

關聯性不能牽涉到來自外部資料庫的查詢或附加資料表。

當關聯牽涉到這兩個數據表中的每一個欄位時，請使用函式的第一個版本。 當關聯牽涉到多個欄位時，請使用第二個版本。 關聯中的欄位數目上限為14。

此動作會建立基礎 DAO 關聯性物件，但這是 MFC 的執行詳細資料，因為 MFC 的關聯物件封裝包含在類別 `CDaoDatabase`內。 MFC 不提供關聯的類別。

如果您設定關聯性物件的屬性來啟動 cascade 作業，則資料庫引擎會在對相關主鍵資料表進行變更時，自動更新或刪除一個或多個其他資料表中的記錄。

例如，假設您在 Customers 資料表與 Orders 資料表之間建立串聯刪除關聯性。 當您刪除 Customers 資料表中的記錄時，也會一併刪除與該客戶相關的 Orders 資料表中的記錄。 此外，如果您在 Orders 資料表與其他資料表之間建立串聯刪除關聯性，當您刪除 Customers 資料表中的記錄時，就會自動刪除這些資料表中的記錄。

如需相關資訊，請參閱 DAO 說明中的「CreateRelation 方法」主題。

##  <a name="deletequerydef"></a>CDaoDatabase：:D eleteQueryDef

呼叫這個成員函式，從 `CDaoDatabase` 物件的 QueryDefs 集合中刪除指定的 querydef （已儲存的查詢）。

```
void DeleteQueryDef(LPCTSTR lpszName);
```

### <a name="parameters"></a>參數

*lpszName*<br/>
要刪除之已儲存查詢的名稱。

### <a name="remarks"></a>備註

之後，該查詢就不會再定義于資料庫中。

如需建立 querydef 物件的詳細資訊，請參閱類別[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)。 當您建立 `CDaoQueryDef` 物件時，會將 querydef 物件與特定 `CDaoDatabase` 物件產生關聯，並將指標傳遞至資料庫物件。

##  <a name="deleterelation"></a>CDaoDatabase：:D eleteRelation

呼叫這個成員函式，從資料庫物件的關聯集合中刪除現有的關聯性。

```
void DeleteRelation(LPCTSTR lpszName);
```

### <a name="parameters"></a>參數

*lpszName*<br/>
要刪除之關聯性的名稱。

### <a name="remarks"></a>備註

之後，關聯就不再存在。

如需相關資訊，請參閱 DAO 說明中的「刪除方法」主題。

##  <a name="deletetabledef"></a>CDaoDatabase：:D eleteTableDef

呼叫這個成員函式，從 `CDaoDatabase` 物件的 TableDefs 集合中刪除指定的資料表及其所有資料。

```
void DeleteTableDef(LPCTSTR lpszName);
```

### <a name="parameters"></a>參數

*lpszName*<br/>
要刪除之 tabledef 的名稱。

### <a name="remarks"></a>備註

之後，該資料表就不會再定義于資料庫中。

> [!NOTE]
>  請務必小心，不要刪除系統資料表。

如需建立 tabledef 物件的詳細資訊，請參閱類別[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)。 當您建立 `CDaoTableDef` 物件時，tabledef 物件會與特定 `CDaoDatabase` 物件產生關聯，並將指標傳遞至資料庫物件。

如需相關資訊，請參閱 DAO 說明中的「刪除方法」主題。

##  <a name="execute"></a>CDaoDatabase：： Execute

呼叫這個成員函式以執行動作查詢，或在資料庫上執行 SQL 語句。

```
void Execute(
    LPCTSTR lpszSQL,
    int nOptions = dbFailOnError);
```

### <a name="parameters"></a>參數

*lpszSQL*<br/>
以 null 終止的字串指標，其中包含要執行的有效 SQL 命令。

*nOptions*<br/>
整數，指定與查詢完整性相關的選項。 您可以使用位 OR 運算子（ **&#124;** ）來結合下列任何常數（假設組合合理，例如，您不會將 `dbInconsistent` 結合 `dbConsistent`）：

- `dbDenyWrite` 拒絕其他使用者的寫入權限。

- `dbInconsistent` （預設值）不一致的更新。

- `dbConsistent` 一致的更新。

- `dbSQLPassThrough` SQL 傳遞。 導致將 SQL 語句傳遞至 ODBC 資料來源進行處理。

- 如果發生錯誤，`dbFailOnError` 復原更新。

- 如果另一位使用者正在變更您正在編輯的資料，`dbSeeChanges` 會產生執行階段錯誤。

> [!NOTE]
>  如果同時包含 `dbInconsistent` 和 `dbConsistent`，或兩者都未包含，則結果會是預設值。 如需這些常數的說明，請參閱 DAO [說明] 中的「執行方法」主題。

### <a name="remarks"></a>備註

`Execute` 僅適用于動作查詢或不會傳回結果的 SQL 傳遞查詢。 它不適用於傳回記錄的 select 查詢。

如需動作查詢的定義和資訊，請參閱 DAO 說明中的「動作查詢」和「執行方法」主題。

> [!TIP]
>  假設語法正確的 SQL 語句和適當的許可權，即使不是可以修改或刪除的單一資料列，`Execute` 成員函式也不會失敗。 因此，當使用 `Execute` 成員函式來執行 update 或 delete 查詢時，請一律使用 `dbFailOnError` 選項。 此選項會使 MFC 擲回[CDaoException](../../mfc/reference/cdaoexception-class.md)類型的例外狀況，並在任何受影響的記錄已鎖定且無法更新或刪除時，回復所有成功的變更。 請注意，您一律可以呼叫 `GetRecordsAffected`，以查看有多少記錄受到影響。

呼叫 database 物件的[GetRecordsAffected](#getrecordsaffected)成員函式，以判斷受最近 `Execute` 呼叫影響的記錄數目。 例如，`GetRecordsAffected` 會傳回執行動作查詢時，刪除、更新或插入之記錄數目的相關資訊。 當串聯更新或刪除作用中時，傳回的計數不會反映相關資料表中的變更。

`Execute` 不會傳回記錄集。 在選取記錄的查詢上使用 `Execute`，會導致 MFC 擲回類型 `CDaoException`的例外狀況。 （沒有類似于 `CDatabase::ExecuteSQL`的 `ExecuteSQL` 成員函式）。

##  <a name="getconnect"></a>CDaoDatabase：： GetConnect

呼叫這個成員函式，以取出用來將 `CDaoDatabase` 物件連接到 ODBC 或 ISAM 資料庫的連接字串。

```
CString GetConnect();
```

### <a name="return-value"></a>傳回值

如果已在 ODBC 資料來源上成功呼叫[Open](#open) ，則為連接字串;否則為空字串。 適用于 Microsoft Jet （。MDB）資料庫，除非您將它設定為與用於[執行](#execute)成員函式的 `dbSQLPassThrough` 選項搭配使用，或是用來開啟記錄集，否則字串一律是空的。

### <a name="remarks"></a>備註

此字串提供有關已開啟資料庫的來源，或用於傳遞查詢之資料庫的資訊。 連接字串是由資料庫類型規範和零或多個以分號分隔的參數所組成。

> [!NOTE]
>  使用 MFC DAO 類別透過 ODBC 連接到資料來源，會比透過附加資料表連接的效率更低。

> [!NOTE]
>  連接字串是用來視需要將其他資訊傳遞至 ODBC 和特定的 ISAM 驅動程式。 它不會用於。MDB 資料庫。 對於 Microsoft Jet 資料庫基表而言，連接字串是空字串（""），除非您將它用於 SQL 傳遞查詢，如上述的傳回值中所述。

如需如何建立連接字串的說明，請參閱[Open](#open)成員函式。 在 `Open` 呼叫中設定連接字串之後，您稍後可以使用它來檢查設定，以決定資料庫的類型、路徑、使用者識別碼、密碼或 ODBC 資料來源。

##  <a name="getname"></a>CDaoDatabase：： GetName

呼叫這個成員函式來抓取目前開啟之資料庫的名稱，這是現有資料庫檔案的名稱或已註冊之 ODBC 資料來源的名稱。

```
CString GetName();
```

### <a name="return-value"></a>傳回值

如果成功，則為資料庫的完整路徑和檔案名;否則為空白[CString](../../atl-mfc-shared/reference/cstringt-class.md)。

### <a name="remarks"></a>備註

如果您的網路支援統一命名慣例（UNC），您也可以指定網路路徑，例如 "\\\\\\\MYSERVER\\\MYSHARE\\\MYDIR\\\MYDB。MDB」。 （字串常值中必須有兩個反斜線，因為 " C++\\" 是 escape 字元）。

例如，您可能想要在標題中顯示此名稱。 如果在抓取名稱時發生錯誤，MFC 會擲回類型[CDaoException](../../mfc/reference/cdaoexception-class.md)的例外狀況。

> [!NOTE]
>  若要在存取外部資料庫時獲得更好的效能，建議您將外部資料庫資料表附加至 Microsoft Jet 資料庫（。MDB），而不是直接連接到資料來源。

資料庫類型是由路徑所指向的檔案或目錄所表示，如下所示：

|Pathname 指向.。|資料庫類型|
|--------------------------|-------------------|
|.MDB 檔|Microsoft Jet 資料庫（Microsoft Access）|
|包含的目錄。DBF 檔案|dBASE 資料庫|
|包含的目錄。XLS 檔案|Microsoft Excel 資料庫|
|包含的目錄。PDX 檔案|Paradox 資料庫|
|包含適當格式之文字資料庫檔案的目錄|文字格式資料庫|

若為 ODBC 資料庫（例如 SQL Server 和 Oracle），資料庫的連接字串會識別 ODBC 所註冊的資料來源名稱（DSN）。

##  <a name="getquerydefcount"></a>CDaoDatabase：： GetQueryDefCount

呼叫這個成員函式，以抓取資料庫的 QueryDefs 集合中所定義的查詢數目。

```
short GetQueryDefCount();
```

### <a name="return-value"></a>傳回值

資料庫中定義的查詢數目。

### <a name="remarks"></a>備註

如果您需要對 QueryDefs 集合中的所有 querydefs 執行迴圈，`GetQueryDefCount` 會很有用。 若要取得集合中指定查詢的相關資訊，請參閱[GetQueryDefInfo](#getquerydefinfo)。

##  <a name="getquerydefinfo"></a>CDaoDatabase：： GetQueryDefInfo

呼叫這個成員函式可取得有關資料庫中所定義之查詢的各種資訊類型。

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
資料庫的 QueryDefs 集合中預先定義之查詢的索引，用於依索引查閱。

*querydefinfo*<br/>
傳回所要求之資訊的[CDaoQueryDefInfo](../../mfc/reference/cdaoquerydefinfo-structure.md)物件參考。

*dwInfoOptions*<br/>
指定要取得之記錄集相關資訊的選項。 這裡列出可用的選項，以及它們會讓函式傳回記錄集的相關資訊：

- AFX_DAO_PRIMARY_INFO （預設）名稱，輸入

- AFX_DAO_SECONDARY_INFO 主要資訊加上：建立日期、上次更新日期、傳回記錄、可更新

- AFX_DAO_ALL_INFO 主要和次要資訊，加上： SQL、Connect、ODBCTimeout

*lpszName*<br/>
包含資料庫中所定義之查詢名稱的字串，用於依名稱查閱。

### <a name="remarks"></a>備註

系統會提供兩個版本的函式，讓您可以依據資料庫的 QueryDefs 集合或查詢的名稱來選取查詢。

如需*querydefinfo*中所傳回信息的描述，請參閱[CDaoQueryDefInfo](../../mfc/reference/cdaoquerydefinfo-structure.md)結構。 此結構的成員會對應至*dwInfoOptions*的描述中所列的資訊專案。 如果您要求一層資訊，您也可以取得任何先前的資訊層級。

##  <a name="getquerytimeout"></a>CDaoDatabase：： GetQueryTimeout

呼叫這個成員函式，以取得在連接的資料庫上的後續作業超時之前允許的目前秒數。

```
short GetQueryTimeout();
```

### <a name="return-value"></a>傳回值

包含超時值（以秒為單位）的短整數。

### <a name="remarks"></a>備註

作業可能會因為網路存取問題、過多的查詢處理時間等等而超時。 當設定生效時，它會影響與此 `CDaoDatabase` 物件相關聯之任何記錄集上的所有開啟、新增、更新和刪除作業。 您可以藉由呼叫[SetQueryTimeout](#setquerytimeout)來變更目前的超時設定。 在開啟後變更記錄集的查詢超時值，並不會變更記錄集的值。 例如，後續的[移動](../../mfc/reference/cdaorecordset-class.md#move)作業不會使用新的值。 初始化資料庫引擎時，一開始會設定預設值。

查詢超時的預設值是取自 Windows 登錄。 如果沒有登錄設定，預設值為60秒。 並非所有資料庫都支援設定查詢超時值的能力。 如果您將查詢超時值設定為0，就不會發生任何超時;而且與資料庫的通訊可能會停止回應。 這種行為在開發期間可能會很有用。 如果呼叫失敗，MFC 會擲回[CDaoException](../../mfc/reference/cdaoexception-class.md)類型的例外狀況。

如需相關資訊，請參閱 DAO 說明中的「QueryTimeout 屬性」主題。

##  <a name="getrecordsaffected"></a>CDaoDatabase：： GetRecordsAffected

呼叫這個成員函式，以判斷受最新的[Execute](#execute)成員函式呼叫所影響的記錄數目。

```
long GetRecordsAffected();
```

### <a name="return-value"></a>傳回值

長整數，其中包含受影響的記錄數目。

### <a name="remarks"></a>備註

傳回的值包括以 `Execute`執行的動作查詢所刪除、更新或插入的記錄數目。 當串聯更新或刪除作用中時，傳回的計數不會反映相關資料表中的變更。

如需相關資訊，請參閱 DAO 說明中的「RecordsAffected 屬性」主題。

##  <a name="getrelationcount"></a>CDaoDatabase：： GetRelationCount

呼叫這個成員函式，以取得在資料庫中的資料表之間定義的關聯性數目。

```
short GetRelationCount();
```

### <a name="return-value"></a>傳回值

在資料庫中的資料表之間定義的關聯性數目。

### <a name="remarks"></a>備註

如果您需要對資料庫的關聯集合中所有已定義的關聯執行迴圈，`GetRelationCount` 會很有用。 若要取得集合中指定關聯的相關資訊，請參閱[GetRelationInfo](#getrelationinfo)。

若要說明關聯性的概念，請考慮供應商資料表和 Products 資料表，這可能會有一對多關聯性。 在此關聯性中，一個供應商可以提供多項產品。 其他關係為一對一和多對多關聯性。

##  <a name="getrelationinfo"></a>CDaoDatabase：： GetRelationInfo

呼叫這個成員函式，以取得有關資料庫關聯性集合中指定之關聯性的資訊。

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
在資料庫的關聯集合中，用於依索引查閱的關係物件索引。

*relinfo*<br/>
傳回所要求之資訊的[CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md)物件參考。

*dwInfoOptions*<br/>
指定要取得之關聯性資訊的選項。 這裡列出可用的選項，以及它們會讓函式傳回關聯的相關資訊：

- AFX_DAO_PRIMARY_INFO （預設）名稱、資料表、外部資料表

- AFX_DAO_SECONDARY_INFO 屬性，欄位資訊

欄位資訊是一個[CDaoRelationFieldInfo](../../mfc/reference/cdaorelationfieldinfo-structure.md)物件，其中包含與關聯之主資料表中的欄位。

*lpszName*<br/>
包含關聯性物件名稱的字串，用於依名稱查閱。

### <a name="remarks"></a>備註

此函式的兩個版本可依索引或名稱提供存取權。 如需*relinfo*中所傳回信息的描述，請參閱[CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md)結構。 此結構的成員會對應至*dwInfoOptions*的描述中所列的資訊專案。 如果您要求某一層級的資訊，您也可以取得任何先前層級的資訊。

> [!NOTE]
>  如果您設定關聯性物件的屬性來啟動 cascade 作業（`dbRelationUpdateCascades` 或 `dbRelationDeleteCascades`），Microsoft Jet 資料庫引擎會在對相關主鍵資料表進行變更時，自動更新或刪除一個或多個其他資料表中的記錄。 例如，假設您在 Customers 資料表與 Orders 資料表之間建立串聯刪除關聯性。 當您刪除 Customers 資料表中的記錄時，也會一併刪除與該客戶相關的 Orders 資料表中的記錄。 此外，如果您在 Orders 資料表與其他資料表之間建立串聯刪除關聯性，當您刪除 Customers 資料表中的記錄時，就會自動刪除這些資料表中的記錄。

##  <a name="gettabledefcount"></a>CDaoDatabase：： GetTableDefCount

呼叫這個成員函式，以抓取資料庫中所定義的資料表數目。

```
short GetTableDefCount();
```

### <a name="return-value"></a>傳回值

資料庫中定義的 tabledefs 數目。

### <a name="remarks"></a>備註

如果您需要對資料庫 TableDefs 集合中的所有 tabledefs 執行迴圈，`GetTableDefCount` 會很有用。 若要取得集合中特定資料表的相關資訊，請參閱[GetTableDefInfo](#gettabledefinfo)。

##  <a name="gettabledefinfo"></a>CDaoDatabase：： GetTableDefInfo

呼叫這個成員函式可取得有關資料庫中所定義之資料表的各種資訊。

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
資料庫 TableDefs 集合中 tabledef 物件的索引，用於依索引查閱。

*tabledefinfo*<br/>
傳回所要求之資訊的[CDaoTableDefInfo](../../mfc/reference/cdaotabledefinfo-structure.md)物件參考。

*dwInfoOptions*<br/>
指定要取得之資料表相關資訊的選項。 這裡列出可用的選項，以及它們會讓函式傳回關聯的相關資訊：

- AFX_DAO_PRIMARY_INFO （預設）名稱、可更新、屬性

- AFX_DAO_SECONDARY_INFO 的主要資訊，加上：建立日期、上次更新日期、來源資料表名稱、連接

- AFX_DAO_ALL_INFO 主要和次要資訊，加上：驗證規則、驗證文字、記錄計數

*lpszName*<br/>
Tabledef 物件的名稱，用於依名稱查閱。

### <a name="remarks"></a>備註

系統會提供兩個版本的函式，因此您可以依資料庫的 TableDefs 集合中的索引或資料表的名稱來選取資料表。

如需*tabledefinfo*中所傳回信息的描述，請參閱[CDaoTableDefInfo](../../mfc/reference/cdaotabledefinfo-structure.md)結構。 此結構的成員會對應至*dwInfoOptions*的描述中所列的資訊專案。 如果您要求某一層級的資訊，您也可以取得任何先前層級的資訊。

> [!NOTE]
>  AFX_DAO_ALL_INFO 選項會提供可能變慢的資訊。 在此情況下，如果有許多記錄，計算資料表中的記錄可能會很耗時。

##  <a name="getversion"></a>CDaoDatabase：： GetVersion

呼叫這個成員函式，以判斷 Microsoft Jet 資料庫檔案的版本。

```
CString GetVersion();
```

### <a name="return-value"></a>傳回值

[CString](../../atl-mfc-shared/reference/cstringt-class.md) ，表示與物件相關聯的資料庫檔案版本。

### <a name="remarks"></a>備註

傳回的值代表「主要. 次要」格式的版本號碼;例如，"3.0"。 產品版本號碼（例如3.0）包含版本號碼（3）、句點和版本號碼（0）。 至今的版本為1.0、1.1、2.0 和3.0。

如需相關資訊，請參閱 DAO 說明中的「版本屬性」主題。

##  <a name="isopen"></a>CDaoDatabase：： IsOpen

呼叫這個成員函式，以判斷目前是否在資料庫上開啟 `CDaoDatabase` 物件。

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>傳回值

如果 `CDaoDatabase` 物件目前為開啟，則為非零。否則為0。

### <a name="remarks"></a>備註

##  <a name="m_pdaodatabase"></a>CDaoDatabase：： m_pDAODatabase

包含 `CDaoDatabase` 物件基礎之 DAO 資料庫物件的 OLE 介面的指標。

### <a name="remarks"></a>備註

如果您需要直接存取 DAO 介面，請使用此指標。

如需直接呼叫 DAO 的相關資訊，請參閱[技術附注 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。

##  <a name="m_pworkspace"></a>CDaoDatabase：： m_pWorkspace

包含[CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)物件的指標，其中包含資料庫物件。

### <a name="remarks"></a>備註

如果您需要直接存取工作區，請使用此指標，例如，若要取得工作區資料庫集合中其他資料庫物件的指標。

##  <a name="open"></a>CDaoDatabase：： Open

您必須呼叫這個成員函式，以初始化新建立的 `CDaoDatabase` 物件，以代表現有的資料庫。

```
virtual void Open(
    LPCTSTR lpszName,
    BOOL bExclusive = FALSE,
    BOOL bReadOnly = FALSE,
    LPCTSTR lpszConnect = _T(""));
```

### <a name="parameters"></a>參數

*lpszName*<br/>
字串運算式，這是現有 Microsoft Jet （的名稱。MDB）資料庫檔案。 如果檔案名具有副檔名，則為必要。 如果您的網路支援統一命名慣例（UNC），您也可以指定網路路徑，例如 "\\\\\\\MYSERVER\\\MYSHARE\\\MYDIR\\\MYDB。MDB」。 （字串常值中必須有兩個反斜線，因為 " C++\\" 是 escape 字元）。

使用*lpszName*時，有一些考慮適用。 如果是：

- 參考已開放給另一個使用者獨佔存取的資料庫，MFC 會擲回[CDaoException](../../mfc/reference/cdaoexception-class.md)類型的例外狀況。 攔截該例外狀況，讓您的使用者知道資料庫無法使用。

- 是空字串（""），而*lpszConnect*是 "ODBC;"，會顯示一個對話方塊，其中會列出所有已註冊的 ODBC 資料來源名稱，讓使用者可以選取資料庫。 您應該避免直接連接到 ODBC 資料來源;請改用附加的資料表。

- 否則，不會參考現有的資料庫或有效的 ODBC 資料來源名稱，MFC 會擲回 `CDaoException`類型的例外狀況。

> [!NOTE]
>  如需 DAO 錯誤碼的詳細資訊，請參閱 DAOERR。H 檔案。 如需相關資訊，請參閱 DAO 說明中的「可捕獲的資料存取錯誤」主題。

*bExclusive*<br/>
布林值，如果資料庫要針對獨佔（非共用）存取開啟，則為 TRUE，如果要針對共用存取開啟資料庫，則為 FALSE。 如果您省略這個引數，則會開啟資料庫以供共用存取。

*bReadOnly*<br/>
布林值，如果資料庫要針對唯讀存取開啟，則為 TRUE，如果要開啟資料庫進行讀取/寫入存取，則為 FALSE。 如果您省略這個引數，則會開啟資料庫以供讀取/寫入存取。 所有相依記錄集都會繼承這個屬性。

*lpszConnect*<br/>
用來開啟資料庫的字串運算式。 此字串構成 ODBC connect 引數。 您必須提供專有和唯讀引數，才能提供來源字串。 如果資料庫是 Microsoft Jet 資料庫（。MDB），這個字串是空的（""）。 預設值（ **_T**（""）的語法-提供 Unicode 的可攜性，以及應用程式的 ANSI 組建。

### <a name="remarks"></a>備註

`Open` 會使資料庫與基礎 DAO 物件產生關聯。 在初始化之前，您無法使用資料庫物件來建立記錄集、tabledef 或 querydef 物件。 `Open` 會將資料庫物件附加至相關工作區的資料庫集合。

使用參數，如下所示：

- 如果您要開啟 Microsoft Jet （。MDB）資料庫，請使用*lpszName*參數並為*lpszConnect*參數傳遞空字串，或傳遞格式為 "; 的密碼字串。PWD = password "如果資料庫受到密碼保護（。僅 MDB 資料庫）。

- 如果您要開啟 ODBC 資料來源，請在*lpszConnect*中傳遞有效的 ODBC 連接字串和*lpszName*中的空字串。

如需相關資訊，請參閱 DAO 說明中的「OpenDatabase 方法」主題。

> [!NOTE]
>  若要在存取外部資料庫（包括 ISAM 資料庫和 ODBC 資料來源）時獲得更好的效能，建議您將外部資料庫資料表附加至 Microsoft Jet engine 資料庫（。MDB），而不是直接連接到資料來源。

例如，如果 DBMS 主機無法使用，連接嘗試可能會超時。 如果連接嘗試失敗，`Open` 會擲回[CDaoException](../../mfc/reference/cdaoexception-class.md)類型的例外狀況。

其餘的備註僅適用于 ODBC 資料庫：

如果資料庫是 ODBC 資料庫，而您 `Open` 呼叫中的參數未包含足夠的資訊來進行連接，則 ODBC 驅動程式會開啟一個對話方塊，以取得使用者所需的資訊。 當您呼叫 `Open`時，您的連接字串*lpszConnect*會私下儲存，而且可以藉由呼叫[GetConnect](#getconnect)成員函式來取得。

如有需要，您可以在呼叫 `Open` 以取得使用者的資訊（例如密碼），然後將該資訊新增至您傳遞給 `Open`的連接字串中，以開啟您自己的對話方塊。 或者，您可能想要儲存您傳遞的連接字串（可能是在 Windows 登錄中），以便下次應用程式呼叫 `CDaoDatabase` 物件上的 `Open` 時，可以重複使用它。

您也可以針對多個登入授權層級（分別用於不同的 `CDaoDatabase` 物件）使用連接字串，或傳達其他資料庫特定資訊。

##  <a name="setquerytimeout"></a>CDaoDatabase：： SetQueryTimeout

呼叫這個成員函式，以覆寫連接的資料庫在後續作業超時之前允許的預設秒數。

```
void SetQueryTimeout(short nSeconds);
```

### <a name="parameters"></a>參數

*nSeconds*<br/>
查詢嘗試超時之前允許的秒數。

### <a name="remarks"></a>備註

作業可能會因為網路存取問題、過多的查詢處理時間等等而超時。 在開啟記錄集之前，或在通話記錄集的[AddNew](../../mfc/reference/cdaorecordset-class.md#addnew)、 [Update](../../mfc/reference/cdaorecordset-class.md#update)或[Delete](../../mfc/reference/cdaorecordset-class.md#delete)成員函式時，如果您想要變更查詢超時值，請先呼叫 `SetQueryTimeout`。 此設定會影響與此 `CDaoDatabase` 物件相關聯之任何記錄集的所有後續[開啟](../../mfc/reference/cdaorecordset-class.md#open)、`AddNew`、`Update`和 `Delete` 呼叫。 在開啟後變更記錄集的查詢超時值，並不會變更記錄集的值。 例如，後續的[移動](../../mfc/reference/cdaorecordset-class.md#move)作業不會使用新的值。

查詢超時的預設值為60秒。 並非所有資料庫都支援設定查詢超時值的能力。 如果您將查詢超時值設定為0，就不會發生任何超時;與資料庫的通訊可能會停止回應。 這種行為在開發期間可能會很有用。

如需相關資訊，請參閱 DAO 說明中的「QueryTimeout 屬性」主題。

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CDaoWorkspace 類別](../../mfc/reference/cdaoworkspace-class.md)<br/>
[CDaoRecordset 類別](../../mfc/reference/cdaorecordset-class.md)<br/>
[CDaoTableDef 類別](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoQueryDef 類別](../../mfc/reference/cdaoquerydef-class.md)<br/>
[CDatabase 類別](../../mfc/reference/cdatabase-class.md)<br/>
[CDaoException 類別](../../mfc/reference/cdaoexception-class.md)
