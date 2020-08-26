---
title: CDaoWorkspace 類別
ms.date: 11/04/2016
f1_keywords:
- CDaoWorkspace
- AFXDAO/CDaoWorkspace
- AFXDAO/CDaoWorkspace::CDaoWorkspace
- AFXDAO/CDaoWorkspace::Append
- AFXDAO/CDaoWorkspace::BeginTrans
- AFXDAO/CDaoWorkspace::Close
- AFXDAO/CDaoWorkspace::CommitTrans
- AFXDAO/CDaoWorkspace::CompactDatabase
- AFXDAO/CDaoWorkspace::Create
- AFXDAO/CDaoWorkspace::GetDatabaseCount
- AFXDAO/CDaoWorkspace::GetDatabaseInfo
- AFXDAO/CDaoWorkspace::GetIniPath
- AFXDAO/CDaoWorkspace::GetIsolateODBCTrans
- AFXDAO/CDaoWorkspace::GetLoginTimeout
- AFXDAO/CDaoWorkspace::GetName
- AFXDAO/CDaoWorkspace::GetUserName
- AFXDAO/CDaoWorkspace::GetVersion
- AFXDAO/CDaoWorkspace::GetWorkspaceCount
- AFXDAO/CDaoWorkspace::GetWorkspaceInfo
- AFXDAO/CDaoWorkspace::Idle
- AFXDAO/CDaoWorkspace::IsOpen
- AFXDAO/CDaoWorkspace::Open
- AFXDAO/CDaoWorkspace::RepairDatabase
- AFXDAO/CDaoWorkspace::Rollback
- AFXDAO/CDaoWorkspace::SetDefaultPassword
- AFXDAO/CDaoWorkspace::SetDefaultUser
- AFXDAO/CDaoWorkspace::SetIniPath
- AFXDAO/CDaoWorkspace::SetIsolateODBCTrans
- AFXDAO/CDaoWorkspace::SetLoginTimeout
- AFXDAO/CDaoWorkspace::m_pDAOWorkspace
helpviewer_keywords:
- CDaoWorkspace [MFC], CDaoWorkspace
- CDaoWorkspace [MFC], Append
- CDaoWorkspace [MFC], BeginTrans
- CDaoWorkspace [MFC], Close
- CDaoWorkspace [MFC], CommitTrans
- CDaoWorkspace [MFC], CompactDatabase
- CDaoWorkspace [MFC], Create
- CDaoWorkspace [MFC], GetDatabaseCount
- CDaoWorkspace [MFC], GetDatabaseInfo
- CDaoWorkspace [MFC], GetIniPath
- CDaoWorkspace [MFC], GetIsolateODBCTrans
- CDaoWorkspace [MFC], GetLoginTimeout
- CDaoWorkspace [MFC], GetName
- CDaoWorkspace [MFC], GetUserName
- CDaoWorkspace [MFC], GetVersion
- CDaoWorkspace [MFC], GetWorkspaceCount
- CDaoWorkspace [MFC], GetWorkspaceInfo
- CDaoWorkspace [MFC], Idle
- CDaoWorkspace [MFC], IsOpen
- CDaoWorkspace [MFC], Open
- CDaoWorkspace [MFC], RepairDatabase
- CDaoWorkspace [MFC], Rollback
- CDaoWorkspace [MFC], SetDefaultPassword
- CDaoWorkspace [MFC], SetDefaultUser
- CDaoWorkspace [MFC], SetIniPath
- CDaoWorkspace [MFC], SetIsolateODBCTrans
- CDaoWorkspace [MFC], SetLoginTimeout
- CDaoWorkspace [MFC], m_pDAOWorkspace
ms.assetid: 64f60de6-4df1-4d4a-a65b-c489b5257d52
ms.openlocfilehash: eea3fb29f219890ebe596c5d8109257e9d422054
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88839786"
---
# <a name="cdaoworkspace-class"></a>CDaoWorkspace 類別

從單一使用者的登入到登出，管理受密碼保護的具名資料庫工作階段。 DAO 可透過 Office 2013 來支援。 DAO 3.6 是最終版本，且會被視為已淘汰。

## <a name="syntax"></a>語法

```
class CDaoWorkspace : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CDaoWorkspace：： CDaoWorkspace](#cdaoworkspace)|建立工作區物件。 之後，請呼叫 `Create` 或 `Open` 。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDaoWorkspace：： Append](#append)|將新建立的工作區附加至資料庫引擎的工作區集合。|
|[CDaoWorkspace：： BeginTrans](#begintrans)|開始新的交易，這會套用至工作區中開啟的所有資料庫。|
|[CDaoWorkspace：： Close](#close)|關閉工作區及其包含的所有物件。 暫止的交易將會回復。|
|[CDaoWorkspace：： CommitTrans](#committrans)|完成目前的交易並儲存變更。|
|[CDaoWorkspace：：壓縮](#compactdatabase)|壓縮資料庫)  (或重複專案。|
|[CDaoWorkspace：： Create](#create)|建立新的 DAO 工作區物件。|
|[CDaoWorkspace：： GetDatabaseCount](#getdatabasecount)|傳回工作區資料庫集合中的 DAO 資料庫物件數目。|
|[CDaoWorkspace：： GetDatabaseInfo](#getdatabaseinfo)|傳回在工作區的資料庫集合中定義之指定 DAO 資料庫的相關資訊。|
|[CDaoWorkspace：： GetIniPath](#getinipath)|傳回 Microsoft Jet database engine 初始化設定在 Windows 登錄中的位置。|
|[CDaoWorkspace：： GetIsolateODBCTrans](#getisolateodbctrans)|傳回值，這個值會指出牽涉到相同 ODBC 資料來源的多個交易是否透過強制多個資料來源連接來隔離。|
|[CDaoWorkspace：： GetLoginTimeout](#getlogintimeout)|傳回當使用者嘗試登入 ODBC 資料庫時發生錯誤的秒數。|
|[CDaoWorkspace：： GetName](#getname)|傳回工作區物件的使用者定義名稱。|
|[CDaoWorkspace：： GetUserName](#getusername)|傳回建立工作區時所指定的使用者名稱。 這是工作區擁有者的名稱。|
|[CDaoWorkspace：： GetVersion](#getversion)|傳回字串，其中包含與工作區相關聯的 database engine 版本。|
|[CDaoWorkspace：： GetWorkspaceCount](#getworkspacecount)|傳回資料庫引擎工作區集合中的 DAO 工作區物件數目。|
|[CDaoWorkspace：： GetWorkspaceInfo](#getworkspaceinfo)|傳回在 database engine 的工作區集合中定義之指定 DAO 工作區的相關資訊。|
|[CDaoWorkspace：：閒置](#idle)|允許資料庫引擎執行背景工作。|
|[CDaoWorkspace：： IsOpen](#isopen)|如果工作區是開啟的，則傳回非零。|
|[CDaoWorkspace：： Open](#open)|明確開啟與 DAO 預設工作區相關聯的工作區物件。|
|[CDaoWorkspace：： RepairDatabase](#repairdatabase)|嘗試修復損毀的資料庫。|
|[CDaoWorkspace：： Rollback](#rollback)|結束目前的交易，但不儲存變更。|
|[CDaoWorkspace：： SetDefaultPassword](#setdefaultpassword)|設定當建立工作區物件但沒有特定密碼時，database engine 所使用的密碼。|
|[CDaoWorkspace：： SetDefaultUser](#setdefaultuser)|設定當建立工作區物件但未指定使用者名稱時，資料庫引擎所使用的使用者名稱。|
|[CDaoWorkspace：： SetIniPath](#setinipath)|在 Windows 登錄中設定 Microsoft Jet database engine 初始化設定的位置。|
|[CDaoWorkspace：： SetIsolateODBCTrans](#setisolateodbctrans)|指定是否透過強制執行多個資料來源連接，來隔離牽涉到相同 ODBC 資料來源的多個交易。|
|[CDaoWorkspace：： SetLoginTimeout](#setlogintimeout)|設定當使用者嘗試登入 ODBC 資料來源時，發生錯誤之前的秒數。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CDaoWorkspace：： m_pDAOWorkspace](#m_pdaoworkspace)|指向基礎 DAO 工作區物件。|

## <a name="remarks"></a>備註

在大部分情況下，您不需要多個工作區，而且您不需要建立明確的工作區物件;當您開啟資料庫和記錄集物件時，會使用 DAO 的預設工作區。 不過，如有需要，您可以建立額外的工作區物件，一次執行多個會話。 每個工作區物件都可以在自己的資料庫集合中包含多個開啟的資料庫物件。 在 MFC 中，工作區主要是交易管理員，並在相同的「交易空間」中指定一組開啟的資料庫。

> [!NOTE]
> DAO 資料庫類別與以開放式資料庫連接 (ODBC) 為基礎的 MFC 資料庫類別不同。 所有 DAO 資料庫類別名稱都有一個 "CDao" 前置詞。 一般來說，根據 DAO 的 MFC 類別比以 ODBC 為基礎的 MFC 類別更有能力。 DAO 型類別會透過 Microsoft Jet 資料庫引擎（包括 ODBC 驅動程式）存取資料。 它們也支援資料定義語言 (DDL) 作業，例如透過類別建立資料庫並新增資料表和欄位，而不需要直接呼叫 DAO。

## <a name="capabilities"></a>功能

類別 `CDaoWorkspace` 提供下列各項：

- 視需要明確存取預設工作區，藉由初始化資料庫引擎來建立。 通常您會藉由建立資料庫和記錄集物件，以隱含的方式使用 DAO 的預設工作區。

- 交易空間，會將交易套用至工作區中開啟的所有資料庫。 您可以建立額外的工作區來管理不同的交易空間。

- 基礎 Microsoft Jet 資料庫引擎的許多屬性介面 (查看靜態成員函式) 。 開啟或建立工作區，或在開啟或建立之前呼叫靜態成員函式，會初始化 database engine。

- 存取資料庫引擎的工作區集合，其會儲存已附加至其中的所有作用中工作區。 您也可以建立和使用工作區，而不將它們附加至集合。

## <a name="security"></a>安全性

MFC 不會在 DAO 中執行用於安全性控制的使用者和群組集合。 如果您需要 DAO 的各方面，您必須透過直接呼叫 DAO 介面，自行進行程式設計。 如需詳細資訊，請參閱 [技術附注 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。

## <a name="usage"></a>使用方式

您可以使用類別 `CDaoWorkspace` 來：

- 明確開啟預設工作區。

   當您開啟新的 [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) 或 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 物件時，通常使用預設工作區是隱含的。 但是您可能需要明確地存取它，例如，存取 database engine 屬性或工作區集合。 請參閱下面的「隱含使用預設工作區」。

- 建立新的工作區。 如果您想要將其新增至工作區集合，請呼叫 [Append](#append) 。

- 在工作區集合中開啟現有的工作區。

在工作區集合中建立尚未存在的新工作區時，會在 [Create](#create) member 函數下說明。 在資料庫引擎會話之間，工作區物件不會以任何方式保存。 如果您的應用程式以靜態方式連結 MFC，則會結束應用程式取消初始化資料庫引擎。 如果您的應用程式會以動態方式連結 MFC，則在卸載 MFC DLL 時，資料庫引擎就會初始化。

在 [開啟](#open) 的成員函式下，明確地開啟預設工作區，或開啟工作區集合中現有的工作區。

使用 [Close](#close) 成員函式來關閉工作區，以結束工作區會話。 `Close` 關閉任何先前未關閉的資料庫，回復任何未認可的交易。

## <a name="transactions"></a>交易

DAO 會管理工作區層級的交易;因此，具有多個開啟資料庫之工作區上的交易會套用至所有資料庫。 例如，如果兩個資料庫具有未認可的更新，而您呼叫 [CommitTrans](#committrans)，則會認可所有更新。 如果您想要將交易限制為單一資料庫，您需要有個別的工作區物件。

## <a name="implicit-use-of-the-default-workspace"></a>預設工作區的隱含使用

在下列情況下，MFC 會隱含地使用 DAO 的預設工作區：

- 如果您建立新的 `CDaoDatabase` 物件，但未透過現有的物件執行此動作 `CDaoWorkspace` ，MFC 會為您建立暫時的工作區物件，該物件會對應至 DAO 的預設工作區。 如果您對多個資料庫這麼做，則所有資料庫物件都會與預設工作區相關聯。 您可以透過資料成員存取資料庫的工作區 `CDaoDatabase` 。

- 同樣地，如果您建立 `CDaoRecordset` 物件而不提供物件的指標 `CDaoDatabase` ，則 MFC 會建立暫存資料庫物件，並藉由擴充功能來建立暫存工作區物件。 您可以透過資料成員，存取記錄集的資料庫，並間接存取其工作區 `CDaoRecordset` 。

## <a name="other-operations"></a>其他作業

此外也會提供其他資料庫作業，例如修復損毀的資料庫或壓縮資料庫。

如需直接呼叫 DAO 以及 DAO 安全性的相關資訊，請參閱 [技術提示 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

`CDaoWorkspace`

## <a name="requirements"></a>規格需求

**標頭：** afxdao。h

## <a name="cdaoworkspaceappend"></a><a name="append"></a> CDaoWorkspace：： Append

呼叫 [Create](#create)之後，請呼叫這個成員函式。

```
virtual void Append();
```

### <a name="remarks"></a>備註

`Append` 將新建立的工作區物件附加至資料庫引擎的工作區集合。 資料庫引擎會話之間不會保存工作區;它們只儲存在記憶體中，而不是儲存在磁片上。 您不需要附加工作區;如果沒有，您仍然可以使用它。

附加的工作區會保留在工作區集合中，處於作用中的開啟狀態，直到您呼叫其 [Close](#close) 成員函式為止。

如需相關資訊，請參閱 DAO 說明中的「附加方法」主題。

## <a name="cdaoworkspacebegintrans"></a><a name="begintrans"></a> CDaoWorkspace：： BeginTrans

呼叫此成員函式以起始交易。

```cpp
void BeginTrans();
```

### <a name="remarks"></a>備註

在您呼叫之後 `BeginTrans` ，您對資料或資料庫結構所做的更新會在認可交易時生效。 因為工作區定義了單一交易空間，所以交易會套用至工作區中所有已開啟的資料庫。 有兩種方式可以完成交易：

- 呼叫 [CommitTrans](#committrans) 成員函數來認可交易，並將變更儲存至資料來源。

- 或呼叫 [Rollback](#rollback) 成員函式來取消交易。

當交易暫止時，關閉工作區物件或資料庫物件會回復所有暫止的交易。

如果您需要隔離某個 ODBC 資料來源上的交易與另一個 ODBC 資料來源上的交易，請參閱 [SetIsolateODBCTrans](#setisolateodbctrans) 成員函式。

## <a name="cdaoworkspacecdaoworkspace"></a><a name="cdaoworkspace"></a> CDaoWorkspace：： CDaoWorkspace

建構 `CDaoWorkspace` 物件。

```
CDaoWorkspace();
```

### <a name="remarks"></a>備註

在建立 c + + 物件之後，您有兩個選項：

- 呼叫物件的 [開啟](#open) 成員函式以開啟預設工作區，或開啟工作區集合中的現有物件。

- 或呼叫物件的 [create](#create) 成員函式來建立新的 DAO 工作區物件。 這會明確啟動新的工作區會話，您可以透過物件參考此會話 `CDaoWorkspace` 。 呼叫之後 `Create` ，如果您想要將工作區加入至資料庫引擎的工作區集合，可以呼叫 [Append](#append) 。

如需何時需要明確建立`CDaoWorkspace`物件的相關資訊，請參閱 [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) 的類別總覽。 通常，當您開啟 [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) 物件但未指定工作區，或開啟 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 物件但未指定資料庫物件時，您會使用隱含建立的工作區。 以這種方式建立的 MFC DAO 物件會使用 DAO 的預設工作區，這會建立一次並重複使用。

若要釋放工作區及其包含的物件，請呼叫工作區物件的 [Close](#close) 成員函式。

## <a name="cdaoworkspaceclose"></a><a name="close"></a> CDaoWorkspace：： Close

呼叫此成員函式以關閉工作區物件。

```
virtual void Close();
```

### <a name="remarks"></a>備註

關閉開啟的工作區物件會釋出基礎 DAO 物件，如果工作區是工作區集合的成員，則會將它從集合中移除。 呼叫 `Close` 是良好的程式設計作法。

> [!CAUTION]
> 關閉工作區物件會關閉工作區中所有已開啟的資料庫。 這會導致在資料庫中開啟的任何記錄集，也會回復任何暫止的編輯或更新。 如需相關資訊，請參閱 [CDaoDatabase：： close](../../mfc/reference/cdaodatabase-class.md#close)、 [CDaoRecordset：： close](../../mfc/reference/cdaorecordset-class.md#close)、 [CDaoTableDef：： Close](../../mfc/reference/cdaotabledef-class.md#close)和 [CDaoQueryDef：： close](../../mfc/reference/cdaoquerydef-class.md#close) 成員函式。

工作區物件不是永久性的;它們只有在參考存在時才存在。 這表示當 database engine 會話結束時，工作區和其資料庫集合不會保存。 您必須再次開啟您的工作區和資料庫 (s) ，為下一個會話重新建立它們。

如需相關資訊，請參閱 DAO 說明中的「關閉方法」主題。

## <a name="cdaoworkspacecommittrans"></a><a name="committrans"></a> CDaoWorkspace：： CommitTrans

呼叫此成員函式來認可交易，並將一組編輯和更新儲存至工作區中的一個或多個資料庫。

```cpp
void CommitTrans();
```

### <a name="remarks"></a>備註

交易是由資料庫資料或其結構的一系列變更所組成，從呼叫 [BeginTrans](#begintrans)開始。 當您完成交易時，請認可或回復， (使用 [Rollback](#rollback)) 取消變更。 依預設，若沒有交易，則會立即認可記錄的更新。 呼叫 `BeginTrans` 會導致延遲更新，直到您呼叫為止 `CommitTrans` 。

> [!CAUTION]
> 在一個工作區中，交易一律是工作區的全域交易，不限於只有一個資料庫或記錄集。 如果您在工作區交易內的一個以上的資料庫或記錄集上執行作業，則會認可 `CommitTrans` 所有暫止的更新，並 `Rollback` 還原這些資料庫和記錄集的所有作業。

當您關閉具有暫止交易的資料庫或工作區時，就會回復交易。

> [!NOTE]
> 這不是兩階段認可機制。 如果有一個更新無法認可，其他更新仍會認可。

## <a name="cdaoworkspacecompactdatabase"></a><a name="compactdatabase"></a> CDaoWorkspace：：壓縮

呼叫此成員函式，以壓縮指定的 Microsoft Jet (。MDB) 資料庫。

```
static void PASCAL CompactDatabase(
    LPCTSTR lpszSrcName,
    LPCTSTR lpszDestName,
    LPCTSTR lpszLocale = dbLangGeneral,
    int nOptions = 0);

static void PASCAL CompactDatabase(
    LPCTSTR lpszSrcName,
    LPCTSTR lpszDestName,
    LPCTSTR lpszLocale,
    int nOptions,
    LPCTSTR lpszPassword);
```

### <a name="parameters"></a>參數

*lpszSrcName*<br/>
現有封閉資料庫的名稱。 它可以是完整路徑和檔案名，例如 "C： \\ \MYDB。MDB」。 如果檔案名有副檔名，您必須指定它。 如果您的網路支援 (UNC) 的統一命名慣例，您也可以指定網路路徑，例如 " \\ \\ \\ \MYSERVER \\ \MYSHARE \\ \MYDIR \\ \MYDB。MDB」。 路徑字串中需要 (雙反斜線，因為 " \\ " 是 c + + escape 字元。 ) 

*lpszDestName*<br/>
您正在建立之壓縮資料庫的完整路徑。 您也可以使用 *lpszSrcName*來指定網路路徑。 您無法使用 *lpszDestName* 引數來指定與 *lpszSrcName*相同的資料庫檔案。

*lpszPassword*<br/>
當您想要壓縮受密碼保護的資料庫時，所使用的密碼。 請注意，如果您使用的版本 `CompactDatabase` 採用密碼，則必須提供所有參數。 此外，因為這是 connect 參數，所以它需要特殊格式，如下所示：PWD = *lpszPassword*。 例如：;PWD = "快樂"。  (前置分號是必要的。 ) 

*lpszLocale*<br/>
字串運算式，用來指定建立 *lpszDestName*的排序次序。 如果您藉由接受 (的預設值來省略此引數 `dbLangGeneral` ，請參閱下面的) ，新資料庫的地區設定與舊資料庫的地區設定相同。 可能的值包括：

- `dbLangGeneral` 英文、德文、法文、葡萄牙文、義大利文和新式西班牙文

- `dbLangArabic` 阿拉伯文

- `dbLangCyrillic` 俄語

- `dbLangCzech` 捷克文

- `dbLangDutch` 荷蘭文

- `dbLangGreek` 希臘文

- `dbLangHebrew` 希伯來文

- `dbLangHungarian` 匈牙利文

- `dbLangIcelandic` 冰島文

- `dbLangNordic` 北歐語言 (僅限 Microsoft Jet database engine 1.0 版) 

- `dbLangNorwdan` 挪威文和丹麥文

- `dbLangPolish` 波蘭文

- `dbLangSpanish` 傳統西班牙文

- `dbLangSwedfin` 瑞典文和芬蘭文

- `dbLangTurkish` 土耳其文

*nOptions*<br/>
表示目標資料庫的一或多個選項 *lpszDestName*。 如果您接受預設值來省略這個引數，則 *lpszDestName* 將會有相同的加密和與 *lpszSrcName*相同的版本。 您可以 `dbEncrypt` `dbDecrypt` 使用位 or 運算子，將或選項與其中一個版本選項結合。 指定資料庫格式的可能值（而不是資料庫引擎版本）如下：

- `dbEncrypt` 壓縮時加密資料庫。

- `dbDecrypt` 壓縮時將資料庫解密。

- `dbVersion10` 在壓縮時建立使用 Microsoft Jet database engine 1.0 版的資料庫。

- `dbVersion11` 在壓縮時建立使用 Microsoft Jet database engine 1.1 版的資料庫。

- `dbVersion20` 在壓縮時建立使用 Microsoft Jet database engine 2.0 版的資料庫。

- `dbVersion30` 在壓縮時建立使用 Microsoft Jet database engine 3.0 版的資料庫。

您可以 `dbEncrypt` `dbDecrypt` 在 options 引數中使用或，指定是否要在壓縮資料庫時加密或解密。 如果您省略加密常數，或同時包含 `dbDecrypt` 和 `dbEncrypt` ， *lpszDestName* 將會有與 *lpszSrcName*相同的加密。 您可以使用 options 引數中的其中一個版本常數，指定壓縮資料庫的資料格式版本。 這個常數只會影響 *lpszDestName*的資料格式版本。 您只能指定一個版本常數。 如果您省略了版本常數， *lpszDestName* 會有與 *lpszSrcName*相同的版本。 您只能將 *lpszDestName* 壓縮至與 *lpszSrcName*相同或更晚的版本。

> [!CAUTION]
> 如果資料庫未加密，即使您採用使用者/密碼安全性，也可以直接讀取構成資料庫的二進位磁片檔。

### <a name="remarks"></a>備註

當您變更資料庫中的資料時，資料庫檔案可能會變得分散，並使用比所需更多的磁碟空間。 您應該定期壓縮資料庫，以重組資料庫檔案。 壓縮的資料庫通常較小。 您也可以選擇在複製和壓縮資料庫時，變更排序次序、加密或資料格式的版本。

> [!CAUTION]
> 成員函式 `CompactDatabase` 不會將完整的 Microsoft Access 資料庫從某個版本正確轉換成另一個版本。 只有資料格式會轉換。 Microsoft Access 定義的物件（例如表單和報表）不會進行轉換。 但是，資料已正確轉換。

> [!TIP]
> 您也可以使用 `CompactDatabase` 複製資料庫檔案。

如需有關壓縮資料庫的詳細資訊，請參閱 DAO 說明中的「壓縮方法」主題。

## <a name="cdaoworkspacecreate"></a><a name="create"></a> CDaoWorkspace：： Create

呼叫這個成員函式來建立新的 DAO 工作區物件，並將它與 MFC 物件產生關聯 `CDaoWorkspace` 。

```
virtual void Create(
    LPCTSTR lpszName,
    LPCTSTR lpszUserName,
    LPCTSTR lpszPassword);
```

### <a name="parameters"></a>參數

*lpszName*<br/>
最多14個字元的字串，可唯一命名新的工作區物件。 您必須提供名稱。 如需相關資訊，請參閱 DAO 說明中的「名稱屬性」主題。

*lpszUserName*<br/>
工作區擁有者的使用者名稱。 如需相關需求，請參閱[SetDefaultUser](#setdefaultuser)成員函式的*lpszDefaultUser*參數。 如需相關資訊，請參閱 DAO 說明中的「使用者名稱屬性」主題。

*lpszPassword*<br/>
新工作區物件的密碼。 密碼長度最多可以有14個字元，而且可以包含 ASCII 0 (null) 以外的任何字元。 密碼會區分大小寫。 如需相關資訊，請參閱 DAO 說明中的「密碼屬性」主題。

### <a name="remarks"></a>備註

整體建立程式如下：

1. 建立 [CDaoWorkspace](#cdaoworkspace) 物件。

1. 呼叫物件的成員函式 `Create` ，以建立基礎 DAO 工作區。 您必須指定工作區名稱。

1. 如果您想要將工作區新增至資料庫引擎的工作區集合，可以選擇性地呼叫 [Append](#append) 。 您可以使用工作區，而不需要加以附加。

在 `Create` 呼叫之後，工作區物件處於開啟狀態，可供使用。 您不會 `Open` 在之後呼叫 `Create` 。 `Create`如果工作區已經存在於工作區集合中，則不會呼叫。 `Create` 如果資料庫引擎尚未針對您的應用程式初始化，則將它初始化。

## <a name="cdaoworkspacegetdatabasecount"></a><a name="getdatabasecount"></a> CDaoWorkspace：： GetDatabaseCount

呼叫此成員函式，以抓取工作區資料庫集合中的 DAO 資料庫物件數目-工作區中開啟的資料庫數目。

```
short GetDatabaseCount();
```

### <a name="return-value"></a>傳回值

工作區中開啟的資料庫數目。

### <a name="remarks"></a>備註

`GetDatabaseCount` 如果您需要對工作區的資料庫集合中所有已定義的資料庫執行迴圈，這會很有用。 若要取得集合中指定資料庫的相關資訊，請參閱 [GetDatabaseInfo](#getdatabaseinfo)。 一般用法是 `GetDatabaseCount` 針對開啟的資料庫數目進行呼叫，然後使用該數位作為循環索引，以重複呼叫 `GetDatabaseInfo` 。

## <a name="cdaoworkspacegetdatabaseinfo"></a><a name="getdatabaseinfo"></a> CDaoWorkspace：： GetDatabaseInfo

呼叫此成員函式，以取得在工作區中開啟之資料庫的各種相關資訊。

```cpp
void GetDatabaseInfo(
    int nIndex,
    CDaoDatabaseInfo& dbinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetDatabaseInfo(
    LPCTSTR lpszName,
    CDaoDatabaseInfo& dbinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
工作區資料庫集合中資料庫物件以零為基底的索引，用於依索引查閱。

*dbinfo*<br/>
[CDaoDatabaseInfo](../../mfc/reference/cdaodatabaseinfo-structure.md)物件的參考，該物件會傳回所要求的資訊。

*dwInfoOptions*<br/>
選項，可指定要取得之資料庫的相關資訊。 這裡會列出可用的選項，以及這些選項會導致函式傳回的結果：

- AFX_DAO_PRIMARY_INFO (預設) 名稱、可更新、交易

- AFX_DAO_SECONDARY_INFO 主要資訊加上：版本、排序次序、查詢超時

- AFX_DAO_ALL_INFO 主要和次要資訊，再加上： Connect

*lpszName*<br/>
資料庫物件的名稱，用於依名稱查閱。 名稱是最多14個字元的字串，可唯一命名新的工作區物件。

### <a name="remarks"></a>備註

其中一個版本的函數可讓您依索引查閱資料庫。 另一個版本可讓您依名稱查閱資料庫。

如需 *dbinfo*中所傳回信息的描述，請參閱 [CDaoDatabaseInfo](../../mfc/reference/cdaodatabaseinfo-structure.md) 結構。 此結構具有對應至 *dwInfoOptions*描述中所列之資訊專案的成員。 當您要求某個層級的資訊時，您也會取得任何先前層級的資訊。

## <a name="cdaoworkspacegetinipath"></a><a name="getinipath"></a> CDaoWorkspace：： GetIniPath

呼叫此成員函式，以取得 Microsoft Jet database engine 在 Windows 登錄中的初始化設定位置。

```
static CString PASCAL GetIniPath();
```

### <a name="return-value"></a>傳回值

包含登錄位置的 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 。

### <a name="remarks"></a>備註

您可以使用位置來取得 database engine 設定的相關資訊。 傳回的資訊實際上是登錄子機碼的名稱。

如需相關資訊，請參閱 DAO 說明中的「IniPath 屬性」和「自訂資料存取的 Windows 登錄設定」主題。

## <a name="cdaoworkspacegetisolateodbctrans"></a><a name="getisolateodbctrans"></a> CDaoWorkspace：： GetIsolateODBCTrans

呼叫這個成員函式，以取得工作區之 DAO IsolateODBCTrans 屬性的目前值。

```
BOOL GetIsolateODBCTrans();
```

### <a name="return-value"></a>傳回值

如果 ODBC 交易是隔離的，則為非零。否則為0。

### <a name="remarks"></a>備註

在某些情況下，您可能需要在相同的 ODBC 資料庫上有多個同時擱置的交易。 若要這樣做，您必須為每個交易開啟個別的工作區。 請記住，雖然每個工作區可以有自己的資料庫 ODBC 連接，但是這會使系統效能變慢。 因為通常不需要交易隔離，所以依預設會共用來自相同使用者所開啟之多個工作區物件的 ODBC 連接。

某些 ODBC 伺服器（例如 Microsoft SQL Server）不允許在單一連接上同時進行交易。 如果您在一段時間內需要有一個以上的交易在這類資料庫上暫止，請在每個工作區上將 IsolateODBCTrans 屬性設定為 TRUE （只要開啟的話）。 這會為每個工作區強制執行個別的 ODBC 連接。

如需相關資訊，請參閱 DAO 說明中的「IsolateODBCTrans 屬性」主題。

## <a name="cdaoworkspacegetlogintimeout"></a><a name="getlogintimeout"></a> CDaoWorkspace：： GetLoginTimeout

呼叫這個成員函式，以取得工作區之 DAO LoginTimeout 屬性的目前值。

```
static short PASCAL GetLoginTimeout();
```

### <a name="return-value"></a>傳回值

當您嘗試登入 ODBC 資料庫時，發生錯誤之前的秒數。

### <a name="remarks"></a>備註

此值代表當您嘗試登入 ODBC 資料庫時發生錯誤的秒數。 預設 LoginTimeout 設定為20秒。 當 LoginTimeout 設為0時，不會發生任何超時，而且與資料來源的通訊可能會停止回應。

當您嘗試登入 ODBC 資料庫（例如 Microsoft SQL Server）時，連接可能會因為網路錯誤或伺服器未執行而失敗。 您可以指定資料庫引擎在產生錯誤之前等候多久的時間，而不是等候預設的20秒進行連接。 登入伺服器時，會隱含地做為一些不同事件的一部分，例如在外部伺服器資料庫上執行查詢。

如需相關資訊，請參閱 DAO 說明中的「LoginTimeout 屬性」主題。

## <a name="cdaoworkspacegetname"></a><a name="getname"></a> CDaoWorkspace：： GetName

呼叫這個成員函式，以取得物件基礎之 DAO 工作區物件的使用者定義名稱 `CDaoWorkspace` 。

```
CString GetName();
```

### <a name="return-value"></a>傳回值

[CString](../../atl-mfc-shared/reference/cstringt-class.md) ，包含 DAO 工作區物件的使用者定義名稱。

### <a name="remarks"></a>備註

名稱在依名稱存取 database engine 工作區集合中的 DAO 工作區物件時非常有用。

如需相關資訊，請參閱 DAO 說明中的「名稱屬性」主題。

## <a name="cdaoworkspacegetusername"></a><a name="getusername"></a> CDaoWorkspace：： GetUserName

呼叫此成員函式，以取得工作區的擁有者名稱。

```
CString GetUserName();
```

### <a name="return-value"></a>傳回值

[CString](../../atl-mfc-shared/reference/cstringt-class.md) ，表示工作區物件的擁有者。

### <a name="remarks"></a>備註

若要取得或設定工作區擁有者的許可權，請直接呼叫 DAO 以檢查許可權屬性設定;這會決定使用者擁有的許可權。 若要使用許可權，您需要一個系統。MDA 檔。

如需直接呼叫 DAO 的詳細資訊，請參閱 [技術附注 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。 如需相關資訊，請參閱 DAO 說明中的「使用者名稱屬性」主題。

## <a name="cdaoworkspacegetversion"></a><a name="getversion"></a> CDaoWorkspace：： GetVersion

呼叫此成員函式，以判斷使用中的 Microsoft Jet 資料庫引擎版本。

```
static CString PASCAL GetVersion();
```

### <a name="return-value"></a>傳回值

[CString](../../atl-mfc-shared/reference/cstringt-class.md) ，表示與物件相關聯的 database engine 版本。

### <a name="remarks"></a>備註

傳回的值代表 "主要. 次要" 格式的版本號碼;例如 "3.0"。 產品版本號碼 (例如，3.0) 包含 (3) 、句號和版本號碼 (0) 的版本號碼。

如需相關資訊，請參閱 DAO 說明中的「版本屬性」主題。

## <a name="cdaoworkspacegetworkspacecount"></a><a name="getworkspacecount"></a> CDaoWorkspace：： GetWorkspaceCount

呼叫這個成員函式，以抓取資料庫引擎工作區集合中的 DAO 工作區物件數目。

```
short GetWorkspaceCount();
```

### <a name="return-value"></a>傳回值

工作區集合中開啟的工作區數目。

### <a name="remarks"></a>備註

此計數不包含任何未附加至集合的開啟工作區。 `GetWorkspaceCount` 如果您需要對工作區集合中所有已定義的工作區執行迴圈，這會很有用。 若要取得集合中指定工作區的相關資訊，請參閱 [GetWorkspaceInfo](#getworkspaceinfo)。 一般使用方式是呼叫 `GetWorkspaceCount` 開啟的工作區數目，然後使用該數位作為循環索引，以重複呼叫 `GetWorkspaceInfo` 。

## <a name="cdaoworkspacegetworkspaceinfo"></a><a name="getworkspaceinfo"></a> CDaoWorkspace：： GetWorkspaceInfo

呼叫此成員函式，以取得在會話中開啟的工作區相關資訊類型。

```cpp
void GetWorkspaceInfo(
    int nIndex,
    CDaoWorkspaceInfo& wkspcinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetWorkspaceInfo(
    LPCTSTR lpszName,
    CDaoWorkspaceInfo& wkspcinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
工作區集合中資料庫物件以零為基底的索引，用於依索引查閱。

*wkspcinfo*<br/>
[CDaoWorkspaceInfo](../../mfc/reference/cdaoworkspaceinfo-structure.md)物件的參考，該物件會傳回所要求的資訊。

*dwInfoOptions*<br/>
指定要取得之工作區相關資訊的選項。 這裡會列出可用的選項，以及這些選項會導致函式傳回的結果：

- AFX_DAO_PRIMARY_INFO (預設) 名稱

- AFX_DAO_SECONDARY_INFO 的主要資訊加上：使用者名稱

- AFX_DAO_ALL_INFO 主要和次要資訊，再加上：隔離 ODBCTrans

*lpszName*<br/>
工作區物件的名稱，用於依名稱查閱。 名稱是最多14個字元的字串，可唯一命名新的工作區物件。

### <a name="remarks"></a>備註

如需 *wkspcinfo*中所傳回信息的描述，請參閱 [CDaoWorkspaceInfo](../../mfc/reference/cdaoworkspaceinfo-structure.md) 結構。 此結構具有對應至 *dwInfoOptions*描述中所列之資訊專案的成員。 當您在某個層級要求資訊時，也會取得先前層級的資訊。

## <a name="cdaoworkspaceidle"></a><a name="idle"></a> CDaoWorkspace：：閒置

呼叫 `Idle` 以提供資料庫引擎有機會執行背景工作，因為密集的資料處理，可能不是最新狀態。

```
static void PASCAL Idle(int nAction = dbFreeLocks);
```

### <a name="parameters"></a>參數

*nAction*<br/>
要在閒置處理期間採取的動作。 目前唯一有效的動作是 `dbFreeLocks` 。

### <a name="remarks"></a>備註

這通常適用于多使用者的多工環境，在此環境中，沒有足夠的背景處理時間可讓記錄集保持在最新的記錄。

> [!NOTE]
> 使用 `Idle` 3.0 版的 Microsoft Jet 資料庫引擎建立的資料庫並不需要呼叫。 `Idle`僅適用于使用舊版建立的資料庫。

通常會移除讀取鎖定，而且只有在沒有任何其他動作 (包括滑鼠移動) 發生時，才會更新本機動態集類型記錄集物件中的資料。 如果您定期呼叫 `Idle` ，您可以透過釋放不需要的讀取鎖定，讓資料庫引擎有時間趕上背景處理工作。 將 `dbFreeLocks` 常數指定為引數會延遲處理，直到釋放所有讀取鎖定為止。

除非應用程式的多個實例正在執行，否則單一使用者環境中不需要這個成員函式。 成員函式 `Idle` 可能會提高多使用者環境中的效能，因為它會強制資料庫引擎將資料排清到磁片，釋放記憶體的鎖定。 您也可以藉由對交易進行作業的一部分來釋放讀取鎖定。

如需相關資訊，請參閱 DAO 說明中的「閒置方法」主題。

## <a name="cdaoworkspaceisopen"></a><a name="isopen"></a> CDaoWorkspace：： IsOpen

呼叫這個成員函式，以判斷 `CDaoWorkspace` 物件是否為開啟狀態，也就是是否已由呼叫 [Open](#open) 或 [Create](#create)的呼叫來初始化 MFC 物件。

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>傳回值

如果工作區物件已開啟，則為非零。否則為0。

### <a name="remarks"></a>備註

您可以呼叫處於開啟狀態之工作區的任何成員函式。

## <a name="cdaoworkspacem_pdaoworkspace"></a><a name="m_pdaoworkspace"></a> CDaoWorkspace：： m_pDAOWorkspace

基礎 DAO 工作區物件的指標。

### <a name="remarks"></a>備註

如果您需要可直接存取基礎 DAO 物件，請使用此資料成員。 您可以透過這個指標呼叫 DAO 物件的介面。

如需直接存取 DAO 物件的詳細資訊，請參閱 [技術附注 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。

## <a name="cdaoworkspaceopen"></a><a name="open"></a> CDaoWorkspace：： Open

明確開啟與 DAO 預設工作區相關聯的工作區物件。

```
virtual void Open(LPCTSTR lpszName = NULL);
```

### <a name="parameters"></a>參數

*lpszName*<br/>
要開啟之 DAO 工作區物件的名稱，此字串最多可有14個字元可唯一命名工作區。 接受預設值 Null，以明確開啟預設工作區。 如需命名需求，請參閱[Create](#create)的*lpszName*參數。 如需相關資訊，請參閱 DAO 說明中的「名稱屬性」主題。

### <a name="remarks"></a>備註

在建立 `CDaoWorkspace` 物件之後，請呼叫此成員函式來執行下列其中一項：

- 明確開啟預設工作區。 針對 *lpszName*傳遞 Null。

- `CDaoWorkspace`依名稱開啟現有的物件，也就是工作區集合的成員。 傳遞現有工作區物件的有效名稱。

`Open` 將工作區物件置於開啟狀態，而且如果資料庫引擎尚未針對您的應用程式初始化，也會將它初始化。

雖然 `CDaoWorkspace` 可以在開啟工作區之後呼叫許多成員函式，但是在資料庫引擎上運作的下列成員函式可以在 c + + 物件的結構之後，但在呼叫之前使用 `Open` ：

:::row:::
   :::column span="":::
      [創建](#create)\
      [GetIniPath](#getinipath)\
      [GetLoginTimeout](#getlogintimeout)
   :::column-end:::
   :::column span="":::
      [GetVersion](#getversion)\
      [閒置](#idle)
   :::column-end:::
   :::column span="":::
      [SetDefaultPassword](#setdefaultpassword)\
      [SetDefaultUser](#setdefaultuser)
   :::column-end:::
   :::column span="":::
      [SetIniPath](#setinipath)\
      [SetLoginTimeout](#setlogintimeout)
   :::column-end:::
:::row-end:::

## <a name="cdaoworkspacerepairdatabase"></a><a name="repairdatabase"></a> CDaoWorkspace：： RepairDatabase

如果您需要嘗試修復存取 Microsoft Jet 資料庫引擎的損毀資料庫，請呼叫此成員函式。

```
static void PASCAL RepairDatabase(LPCTSTR lpszName);
```

### <a name="parameters"></a>參數

*lpszName*<br/>
現有 Microsoft Jet 引擎資料庫檔案的路徑和檔案名。 如果您省略路徑，則只會搜尋目前的目錄。 如果您的系統支援 (UNC) 的統一命名慣例，您也可以指定網路路徑，例如： " \\ \\ \\ \MYSERVER \\ \MYSHARE \\ \MYDIR \\ \MYDB。MDB」。 路徑字串中需要 (雙反斜線，因為 " \\ " 是 c + + escape 字元。 ) 

### <a name="remarks"></a>備註

在修復之前，您必須先關閉 *lpszName* 所指定的資料庫。 在多使用者環境中，其他使用者在修復時不能開啟 *lpszName* 。 如果 *lpszName* 未關閉或無法供獨佔使用，則會發生錯誤。

此成員函式會嘗試修復未完成寫入作業所標示為可能損毀的資料庫。 如果使用 Microsoft Jet 資料庫引擎的應用程式因為電源中斷或電腦硬體問題而意外關閉，就會發生這種情況。 如果您完成此作業並呼叫 [Close](../../mfc/reference/cdaodatabase-class.md#close) 成員函式，或是您以一般方式結束應用程式，則資料庫將不會被標示為可能損毀。

> [!NOTE]
> 修復資料庫之後，最好使用 [壓縮](#compactdatabase) 成員函式來壓縮檔案，並復原磁碟空間。

如需有關修復資料庫的詳細資訊，請參閱 DAO 說明中的「RepairDatabase 方法」主題。

## <a name="cdaoworkspacerollback"></a><a name="rollback"></a> CDaoWorkspace：： Rollback

呼叫此成員函式以結束目前的交易，並將工作區中的所有資料庫還原至交易開始之前的條件。

```cpp
void Rollback();
```

### <a name="remarks"></a>備註

> [!CAUTION]
> 在一個工作區物件內，交易一律為全域工作區，而且不限於只有一個資料庫或記錄集。 如果您在工作區交易內的多個資料庫或記錄集上執行作業，則會 `Rollback` 還原所有這些資料庫和記錄集的所有作業。

如果您在未儲存或回復任何暫止交易的情況下關閉工作區物件，則會自動回復交易。 如果您呼叫 [CommitTrans](#committrans) `Rollback` ，或未先呼叫 [BeginTrans](#begintrans)，就會發生錯誤。

> [!NOTE]
> 當您開始交易時，資料庫引擎會將其作業記錄在工作站上 TEMP 環境變數所指定的目錄中。 如果交易記錄檔耗盡您暫存磁片磁碟機上的可用儲存空間，database engine 將會導致 MFC 擲回 `CDaoException` (DAO 錯誤 2004) 。 此時，如果您呼叫，則 `CommitTrans` 會認可不定數目的作業，但不會遺失剩餘的未完成作業，而且必須重新開機作業。 呼叫會釋 `Rollback` 出事務歷史記錄，並回復交易中的所有作業。

## <a name="cdaoworkspacesetdefaultpassword"></a><a name="setdefaultpassword"></a> CDaoWorkspace：： SetDefaultPassword

呼叫這個成員函式，以設定當建立工作區物件但沒有特定密碼時，database engine 所使用的預設密碼。

```
static void PASCAL SetDefaultPassword(LPCTSTR lpszPassword);
```

### <a name="parameters"></a>參數

*lpszPassword*<br/>
預設密碼。 密碼長度最多可以有14個字元，而且可以包含 ASCII 0 (null) 以外的任何字元。 密碼會區分大小寫。

### <a name="remarks"></a>備註

您所設定的預設密碼會套用至您在呼叫後所建立的新工作區。 當您建立後續的工作區時，您不需要在 [建立](#create) 呼叫中指定密碼。

若要使用這個成員函式：

1. 建立 `CDaoWorkspace` 物件但不呼叫 `Create` 。

1. 如有需要，請呼叫， `SetDefaultPassword` 然後 [SetDefaultUser](#setdefaultuser)。

1. 呼叫 `Create` 這個工作區物件或後續的物件，而不指定密碼。

根據預設，DefaultUser 屬性會設定為 "admin"，而 DefaultPassword 屬性會設定為空字串 ( "" ) 。

如需安全性的詳細資訊，請參閱 DAO 說明中的「許可權屬性」主題。 如需相關資訊，請參閱 DAO 說明中的「DefaultPassword 屬性」和「DefaultUser 屬性」主題。

## <a name="cdaoworkspacesetdefaultuser"></a><a name="setdefaultuser"></a> CDaoWorkspace：： SetDefaultUser

呼叫此成員函式，以設定當建立工作區物件但未指定使用者名稱時，資料庫引擎所使用的預設使用者名稱。

```
static void PASCAL SetDefaultUser(LPCTSTR lpszDefaultUser);
```

### <a name="parameters"></a>參數

*lpszDefaultUser*<br/>
預設的使用者名稱。 使用者名稱的長度可以是 1-20 個字元，並包含字母字元、重音字元、數位、空格和符號，除了： " (引號) 、/ (斜線) 、\ (反斜線) 、 \[ \] (方括弧) 、： (冒號) 、&#124; (管道) 、 (\< (less-than sign), > 大於正負號) 、+ (加號) 、= (等號) 、 (分號) 、、 ( 逗號) 、 (問號) 、 \* (星號) 、前置空格和控制字元 (ascii 00 到 ascii 31) 。 如需相關資訊，請參閱 DAO 說明中的「使用者名稱屬性」主題。

### <a name="remarks"></a>備註

您所設定的預設使用者名稱會套用至您在呼叫後所建立的新工作區。 當您建立後續的工作區時，您不需要在 [建立](#create) 呼叫中指定使用者名稱。

若要使用這個成員函式：

1. 建立 `CDaoWorkspace` 物件但不呼叫 `Create` 。

1. 如有需要，請呼叫， `SetDefaultUser` 然後 [SetDefaultPassword](#setdefaultpassword)。

1. 呼叫 `Create` 這個工作區物件或後續的物件，而不指定使用者名稱。

根據預設，DefaultUser 屬性會設定為 "admin"，而 DefaultPassword 屬性會設定為空字串 ( "" ) 。

如需相關資訊，請參閱 DAO 說明中的「DefaultUser 屬性」和「DefaultPassword 屬性」主題。

## <a name="cdaoworkspacesetinipath"></a><a name="setinipath"></a> CDaoWorkspace：： SetIniPath

呼叫這個成員函式，以指定 Microsoft Jet database engine 的 Windows 登錄設定位置。

```
static void PASCAL SetIniPath(LPCTSTR lpszRegistrySubKey);
```

### <a name="parameters"></a>參數

*lpszRegistrySubkey*<br/>
包含 Windows 登錄子機碼名稱的字串，此子機碼適用于 Microsoft Jet database engine 設定的位置或可安裝的 ISAM 資料庫所需的參數。

### <a name="remarks"></a>備註

`SetIniPath`只有當您需要指定特殊設定時，才需要呼叫。 如需詳細資訊，請參閱 DAO 說明中的「IniPath 屬性」主題。

> [!NOTE]
> 在 `SetIniPath` 應用程式安裝期間呼叫，而不是在應用程式執行時呼叫。 `SetIniPath` 在開啟任何工作區、資料庫或記錄集之前，必須先呼叫。否則，MFC 會擲回例外狀況。

您可以使用此機制，以使用者提供的登錄設定來設定 database engine。 這個屬性的範圍僅限於您的應用程式，而且不需要重新開機您的應用程式就無法變更。

## <a name="cdaoworkspacesetisolateodbctrans"></a><a name="setisolateodbctrans"></a> CDaoWorkspace：： SetIsolateODBCTrans

呼叫這個成員函式，以設定工作區的 DAO IsolateODBCTrans 屬性值。

```cpp
void SetIsolateODBCTrans(BOOL bIsolateODBCTrans);
```

### <a name="parameters"></a>參數

*bIsolateODBCTrans*<br/>
如果您想要開始隔離 ODBC 交易，請傳遞 TRUE。 如果您想要停止隔離 ODBC 交易，請傳遞 FALSE。

### <a name="remarks"></a>備註

在某些情況下，您可能需要在相同的 ODBC 資料庫上有多個同時擱置的交易。 若要這樣做，您必須為每個交易開啟個別的工作區。 雖然每個工作區可以有自己的資料庫 ODBC 連接，但是這會使系統效能變慢。 因為通常不需要交易隔離，所以依預設會共用來自相同使用者所開啟之多個工作區物件的 ODBC 連接。

某些 ODBC 伺服器（例如 Microsoft SQL Server）不允許在單一連接上同時進行交易。 如果您在一段時間內需要有一個以上的交易在這類資料庫上暫止，請在每個工作區上將 IsolateODBCTrans 屬性設定為 TRUE （只要開啟的話）。 這會為每個工作區強制執行個別的 ODBC 連接。

## <a name="cdaoworkspacesetlogintimeout"></a><a name="setlogintimeout"></a> CDaoWorkspace：： SetLoginTimeout

呼叫這個成員函式，以設定工作區的 DAO LoginTimeout 屬性值。

```
static void PASCAL SetLoginTimeout(short nSeconds);
```

### <a name="parameters"></a>參數

*nSeconds*<br/>
當您嘗試登入 ODBC 資料庫時，發生錯誤之前的秒數。

### <a name="remarks"></a>備註

此值代表當您嘗試登入 ODBC 資料庫時發生錯誤的秒數。 預設 LoginTimeout 設定為20秒。 當 LoginTimeout 設為0時，不會發生任何超時，而且與資料來源的通訊可能會停止回應。

當您嘗試登入 ODBC 資料庫（例如 Microsoft SQL Server）時，連接可能會因為網路錯誤或伺服器未執行而失敗。 您可以指定資料庫引擎在產生錯誤之前等候多久的時間，而不是等候預設的20秒進行連接。 登入伺服器時，會隱含地做為一些不同事件的一部分，例如在外部伺服器資料庫上執行查詢。 Timeout 值是由 LoginTimeout 屬性目前的設定所決定。

如需相關資訊，請參閱 DAO 說明中的「LoginTimeout 屬性」主題。

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CDaoDatabase 類別](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoRecordset 類別](../../mfc/reference/cdaorecordset-class.md)<br/>
[CDaoTableDef 類別](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoQueryDef 類別](../../mfc/reference/cdaoquerydef-class.md)<br/>
[CDaoException 類別](../../mfc/reference/cdaoexception-class.md)
