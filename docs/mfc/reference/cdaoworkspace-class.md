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
ms.openlocfilehash: c492c806d64b1cfe0e4f73b3bb880ec7bd0a7e80
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754669"
---
# <a name="cdaoworkspace-class"></a>CDaoWorkspace 類別

從單一使用者的登入到登出，管理受密碼保護的具名資料庫工作階段。 通過 Office 2013 支援 DAO。 DAO 3.6 是最終版本,它被視為過時版本。

## <a name="syntax"></a>語法

```
class CDaoWorkspace : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CDao工作區:CDao工作區](#cdaoworkspace)|構造工作區物件。 之後,致電`Create`或`Open`。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDao工作:附加](#append)|將新創建的工作區追加到資料庫引擎的工作區集合中。|
|[CDao工作:開始轉換](#begintrans)|開始一個新事務,該事務適用於工作區中打開的所有資料庫。|
|[CDao工作區:關閉](#close)|關閉工作區及其包含的所有物件。 掛起的事務將回滾。|
|[CDao工作區:提交轉換](#committrans)|完成當前事務並保存更改。|
|[CDao工作區:壓縮資料庫](#compactdatabase)|壓縮(或複製)資料庫。|
|[CDao工作區:建立](#create)|創建新的 DAO 工作區物件。|
|[CDao工作區:取得資料庫計數](#getdatabasecount)|返回工作區的資料庫集合中的 DAO 資料庫物件數。|
|[CDao工作區:取得資料庫資訊](#getdatabaseinfo)|返回有關工作區資料庫集合中定義的指定DAO資料庫的資訊。|
|[CDao工作:取得IniPath](#getinipath)|在 Windows 註冊表中傳回 Microsoft Jet 資料庫引擎的初始化設定的位置。|
|[CDao工作:取得隔離BCTrans](#getisolateodbctrans)|返回一個值,指示是否通過強制多個連接到數據源隔離涉及同一 ODBC 數據源的多個事務。|
|[CDao工作區:取得登入逾時](#getlogintimeout)|返回用戶嘗試登錄到 ODBC 資料庫時發生錯誤的秒數。|
|[CDao工作區:取得名稱](#getname)|返回工作區物件的使用者定義的名稱。|
|[CDao工作區:取得使用者名稱](#getusername)|返回創建工作區時指定的使用者名稱。 這是工作區擁有者的名稱。|
|[CDao 工作:抓取版本](#getversion)|返回包含與工作區關聯的資料庫引擎版本的字串。|
|[CDao工作區:取得工作區計數](#getworkspacecount)|返回資料庫引擎的工作區集合中的 DAO 工作區物件數。|
|[CDao工作空間:取得工作資訊](#getworkspaceinfo)|返回有關資料庫引擎工作區集合中定義的指定DAO工作區的資訊。|
|[CDao工作區:空閒](#idle)|允許資料庫引擎執行後台任務。|
|[CDao工作區:是開放的](#isopen)|如果工作區處於打開狀態,則返回非零。|
|[CDao工作區:開啟](#open)|顯式打開與 DAO 的預設工作區關聯的工作區物件。|
|[CDao工作區:修復資料庫](#repairdatabase)|嘗試修復損壞的資料庫。|
|[CDao工作區:回滾](#rollback)|結束當前事務,不保存更改。|
|[CDao工作區:設定預設密碼](#setdefaultpassword)|設定資料庫引擎在沒有特定密碼的情況下創建工作區物件時使用的密碼。|
|[CDao 工作區:設定預設使用者](#setdefaultuser)|設置創建沒有特定使用者名的工作區物件時資料庫引擎使用的使用者名。|
|[CDao工作區:SetIniPath](#setinipath)|在 Windows 註冊表中設置 Microsoft Jet 資料庫引擎的初始化設置的位置。|
|[CDao工作區:設定隔離BCTrans](#setisolateodbctrans)|指定是否通過強制多個連接到數據源來隔離涉及同一 ODBC 資料來源的多個事務。|
|[CDao工作區:設定登入逾時](#setlogintimeout)|設置用戶嘗試登錄到 ODBC 資料來源時發生錯誤的秒數。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CDao工作:m_pDAOWorkspace](#m_pdaoworkspace)|指向基礎 DAO 工作區物件。|

## <a name="remarks"></a>備註

在大多數情況下,您將不需要多個工作區,並且不需要創建顯式工作區物件;因此,您將不需要創建多個工作區物件。打開資料庫和記錄集物件時,它們將使用DAO的預設工作區。 但是,如果需要,可以通過創建其他工作區物件來一次運行多個會話。 每個工作區物件都可以在其自己的資料庫集合中包含多個打開的資料庫物件。 在 MFC 中,工作區主要是事務管理器,指定一組打開的資料庫,所有這些資料庫都位於相同的"事務空間"

> [!NOTE]
> DAO 資料庫類不同於基於開放資料庫連接 (ODBC) 的 MFC 資料庫類。 所有 DAO 資料庫類名稱都有「CDao」首碼。 通常,基於 DAO 的 MFC 類比基於 ODBC 的 MFC 類更有能力。 基於 DAO 的類透過 Microsoft Jet 資料庫引擎存取數據,包括 ODBC 驅動程式。 它們還支援數據定義語言 (DDL) 操作,例如創建資料庫並通過類添加表和欄位,而無需直接調用 DAO。

## <a name="capabilities"></a>功能

類別`CDaoWorkspace`提供以下內容:

- 如果需要,可以顯式訪問通過初始化資料庫引擎創建的預設工作區。 通常,通過創建資料庫和記錄集對象來隱式使用 DAO 的預設工作區。

- 事務應用於工作區中打開的所有資料庫的事務空間。 您可以創建其他工作區來管理單獨的事務空間。

- 基礎 Microsoft Jet 資料庫引擎的許多屬性的介面(請參閱靜態成員函數)。 打開或創建工作區,或在打開或創建之前調用靜態成員函數,將初始化資料庫引擎。

- 訪問資料庫引擎的工作區集合,該集合存儲已追加到它的所有活動工作區。 您還可以創建和使用工作區,而無需將它們追加到集合中。

## <a name="security"></a>安全性

MFC 不實現 DAO 中用於安全控制的使用者和組集合。 如果您需要 DAO 的這些方面,則必須通過直接調用 DAO 介面自行程式設計。 有關詳細資訊,請參閱[技術說明 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。

## <a name="usage"></a>使用量

您可以使用類別`CDaoWorkspace`:

- 顯式打開預設工作區。

   通常,當您打開新的[CDao 資料庫](../../mfc/reference/cdaodatabase-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)物件時,對預設工作區的使用是隱式的。 但是,您可能需要顯式訪問它, 例如,訪問資料庫引擎屬性或工作區集合。 請參閱下面的"默認工作區的隱式使用」。

- 創建新工作區。 如果要將它們新增到工作區集合,請呼叫[附錄](#append)。

- 在工作區集合中打開現有工作區。

創建工作區集合中不存在的新工作區將在[「創建](#create)成員」函數下進行說明。 工作區物件不會在資料庫引擎會話之間以任何方式保留。 如果應用程式以靜態方式連結 MFC,則結束應用程式將取消初始化資料庫引擎。 如果應用程式動態連結到 MFC,則在卸載 MFC DLL 時,資料庫引擎將取消初始化。

顯式打開預設工作區或在工作區集合中打開現有工作區,在["打開](#open)"成員函數下進行了說明。

通過[關閉成員函數](#close)關閉工作區,結束工作區會話。 `Close`關閉以前未關閉的任何資料庫,回滾任何未提交的事務。

## <a name="transactions"></a>交易

DAO 在工作區級別管理事務;因此,具有多個打開資料庫的工作區上的事務將應用於所有資料庫。 例如,如果兩個資料庫具有未提交的更新,並且調用[CommitTrans,](#committrans)則所有更新都已提交。 如果要將事務限制為單個資料庫,則需要單獨的工作區物件。

## <a name="implicit-use-of-the-default-workspace"></a>隱含使用預設工作區

在以下情況下,MFC 隱式使用 DAO 的預設工作區:

- 如果創建新`CDaoDatabase`物件但不通過`CDaoWorkspace`現有 物件創建,MFC 會為您創建一個臨時工作區物件,該物件對應於 DAO 的預設工作區。 如果對多個資料庫執行此操作,則所有資料庫物件都與預設工作區相關聯。 您可以`CDaoDatabase`通過 資料成員存取資料庫的工作區。

- 同樣,如果創建`CDaoRecordset`物件而不提供`CDaoDatabase`指向 物件的指標,MFC 將創建一個臨時資料庫物件,並通過擴展創建臨時工作區物件。 您可以`CDaoRecordset`通過 資料成員訪問記錄集的資料庫,並間接訪問其工作區。

## <a name="other-operations"></a>其他操作

還提供其他資料庫操作,例如修復損壞的資料庫或壓縮資料庫。

有關直接呼叫 DAO 的資訊以及有關 DAO 安全性的資訊,請參閱[技術說明 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

`CDaoWorkspace`

## <a name="requirements"></a>需求

**標題:** afxdao.h

## <a name="cdaoworkspaceappend"></a><a name="append"></a>CDao工作:附加

調用[Create](#create)後調用此成員函數。

```
virtual void Append();
```

### <a name="remarks"></a>備註

`Append`將新創建的工作區物件追加到資料庫引擎的工作區集合中。 工作區不會在資料庫引擎會話之間保留;但是,在資料庫引擎會話之間,工作區不會保留。它們只存儲在記憶體中,而不是存儲在磁碟上。 您不必追加工作區;因此,您不必追加工作區。如果沒有,您仍然可以使用它。

附加工作區將保留在工作區集合中,處於活動打開狀態,直到調用其[Close](#close)成員函數。

有關相關信息,請參閱 DAO 説明中的主題"附加方法"。

## <a name="cdaoworkspacebegintrans"></a><a name="begintrans"></a>CDao工作:開始轉換

調用此成員函數以啟動事務。

```cpp
void BeginTrans();
```

### <a name="remarks"></a>備註

調用`BeginTrans`後,對數據或資料庫結構進行的更新在提交事務時生效。 由於工作區定義單個事務空間,因此事務將應用於工作區中的所有打開的資料庫。 有兩種方法可以完成事務:

- 呼叫[CommitTrans](#committrans)成員函數提交事務並將更改儲存到資料來源。

- 或者調用[回滾](#rollback)成員函數以取消事務。

在事務掛起時關閉工作區對象或資料庫物件會回滾所有掛起的事務。

如果需要將一個 ODBC 資料來源上的事務與另一個 ODBC 資料來源上的事務隔離開來,請參閱[Set 隔離 ODBCTrans](#setisolateodbctrans)成員函數。

## <a name="cdaoworkspacecdaoworkspace"></a><a name="cdaoworkspace"></a>CDao工作區:CDao工作區

建構 `CDaoWorkspace` 物件。

```
CDaoWorkspace();
```

### <a name="remarks"></a>備註

建構C++物件後,有兩個選項:

- 呼叫物件的[Open](#open)成員函數以打開預設工作區或打開工作區集合中的現有物件。

- 或者調用物件的[「創建](#create)成員」函數以創建新的 DAO 工作區物件。 這將顯式啟動一個新的工作區工作階段,您可以透過物件引用`CDaoWorkspace`該 工作階段。 呼叫`Create`後,如果要將工作區加入資料庫引擎的工作區集合,可以呼叫[附加程式](#append)。

如需何時需要明確建立`CDaoWorkspace`物件的相關資訊，請參閱 [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) 的類別總覽。 通常,在打開[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)物件而不指定工作區時,或者在不指定資料庫物件的情況下打開[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)物件時,可以使用隱式創建的工作區。 以這種方式創建的 MFC DAO 物件使用 DAO 的預設工作區,該工作區創建一次並重複使用。

要釋放工作區及其包含的物件,請調用工作區物件的[Close](#close)成員函數。

## <a name="cdaoworkspaceclose"></a><a name="close"></a>CDao工作區:關閉

調用此成員函數以關閉工作區物件。

```
virtual void Close();
```

### <a name="remarks"></a>備註

關閉打開的工作區物件將釋放基礎 DAO 物件,如果工作區是工作區集合的成員,則將其從集合中刪除。 調用`Close`是很好的程式設計實踐。

> [!CAUTION]
> 關閉工作區物件將關閉工作區中的任何打開的資料庫。 這將導致資料庫中打開的任何記錄集也關閉,並且任何掛起的編輯或更新都將回滾。 有關相關信息,請參閱[CDao 資料庫:關閉](../../mfc/reference/cdaodatabase-class.md#close)[,CDaoRecordset::關閉](../../mfc/reference/cdaorecordset-class.md#close)[,CDaoTableDef::關閉](../../mfc/reference/cdaotabledef-class.md#close),和[CDaoQueryDef:關閉](../../mfc/reference/cdaoquerydef-class.md#close)成員函數。

工作區物件不是永久性的;因此,工作區物件不是永久的。它們只存在於對它們的引用存在時。 這意味著當資料庫引擎會話結束時,工作區及其資料庫集合不會持久化。 您必須通過再次打開工作區和資料庫來為下一個會話重新創建它們。

有關相關信息,請參閱 DAO 説明中的主題" 關閉方法"

## <a name="cdaoworkspacecommittrans"></a><a name="committrans"></a>CDao工作區:提交轉換

呼叫此成員函數以提交事務 —保存一組編輯和更新到工作區中的一個或多個資料庫。

```cpp
void CommitTrans();
```

### <a name="remarks"></a>備註

事務包括對資料庫數據或其結構的一系列更改,從調用[BeginTrans](#begintrans)開始。 完成事務後,要麼提交它,要麼回滾(取消更改),使用[回滾](#rollback)。 默認情況下,在沒有事務的情況下,將立即提交對記錄的更新。 呼叫`BeginTrans`會導致更新的承諾延遲到呼`CommitTrans`叫 。

> [!CAUTION]
> 在一個工作區中,事務始終是工作區的全域事務,並且不僅限於一個資料庫或記錄集。 如果對工作區事務中的多個資料庫或記錄集執行操作,則`CommitTrans`提交所有掛起的更新,並`Rollback`還原這些資料庫和記錄集上的所有操作。

當您關閉具有掛起事務的資料庫或工作區時,這些事務都將回滾。

> [!NOTE]
> 這不是兩階段提交機制。 如果一個更新無法提交,其他更新仍將提交。

## <a name="cdaoworkspacecompactdatabase"></a><a name="compactdatabase"></a>CDao工作區:壓縮資料庫

呼叫此成員函數以壓縮指定的 Microsoft Jet (。MDB)資料庫。

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

*lpszSrc名稱*<br/>
現有已關閉資料庫的名稱。 它可以是完整的路徑和檔名,如"C:\MYDB"。\\MDB"。 如果檔名具有副檔名,則必須指定它。 如果您的網路支援統一的命名約定 (UNC),您還可以指定網路路徑,例如\\\\\\\\"_MYSERVER\\\\_MYSHARE \MYDIR _MYDB"。MDB"。 (路徑字串中需要雙背斜杠,因為""\\是C++轉義字元。

*lpszDest 名稱*<br/>
要創建壓縮資料庫的完整路徑。 您還可以指定網路路徑與*lpszSrcName*一樣。 無法使用*lpszDestName*參數指定與*lpszSrcName*相同的資料庫檔案。

*lpsz密碼*<br/>
密碼,用於壓縮受密碼保護的資料庫。 請注意,如果使用的密碼版本`CompactDatabase`,則必須提供所有參數。 此外,由於這是連接參數,它需要特殊的格式,如下所示:PWD= *lpsz 密碼*。 例如:PWD="快樂"。 (需要前導分號。

*lpszLocale*<br/>
指定用於建立*lpszDestName 的*排序的字串表示式。 如果通過接受`dbLangGeneral`的 預設值(見下文)省略此參數,則新資料庫的區位設置與舊資料庫的區值相同。 可能的值包括：

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

*n 選項*<br/>
指示目標資料庫的一個或多個選項 *,lpszDestName*。 如果透過預設值省略此參數,*則 lpszDestName*將具有相同的加密和與*lpszSrcName*相同的版本。 您可以使用位`dbEncrypt`-OR`dbDecrypt`運算子將 或 選項與其中一個版本選項合併。 指定資料庫格式 (而不是資料庫引擎版本)的可能值是:

- `dbEncrypt`壓縮時加密資料庫。

- `dbDecrypt`壓縮時解密資料庫。

- `dbVersion10`創建一個資料庫,該資料庫在壓縮時使用 Microsoft Jet 資料庫引擎版本 1.0。

- `dbVersion11`創建一個資料庫,該資料庫在壓縮時使用 Microsoft Jet 資料庫引擎版本 1.1。

- `dbVersion20`創建一個資料庫,該資料庫在壓縮時使用 Microsoft Jet 資料庫引擎版本 2.0。

- `dbVersion30`創建一個資料庫,該資料庫在壓縮時使用 Microsoft Jet 資料庫引擎版本 3.0。

您可以使用`dbEncrypt``dbDecrypt`或 在選項參數中指定是加密還是解密資料庫。 如果省略`dbDecrypt`了加密常量,或者如果同時包含和`dbEncrypt`,則*lpszDestName*將具有與*lpszSrcName*相同的加密。 可以使用選項參數中的一個版本常量來指定壓縮資料庫的數據格式版本。 此常量僅影響*lpszDestName*的資料格式的版本。 只能指定一個版本常量。 如果省略版本常量 *,lpszDestName*將具有與*lpszSrcName*相同的版本。 您只能將*lpszDestName*壓縮到與*lpszSrcName*相同或更晚的版本。

> [!CAUTION]
> 如果資料庫未加密,即使您實現了使用者/密碼安全性,也可以直接讀取構成資料庫的二進位磁碟檔。

### <a name="remarks"></a>備註

更改資料庫中的數據時,資料庫檔可能會變得碎片化,並且使用超過必要的磁碟空間。 應定期壓縮資料庫以碎片整理資料庫檔。 壓縮的資料庫通常較小。 您還可以選擇在複製和壓縮資料庫時更改整理順序、加密或數據格式的版本。

> [!CAUTION]
> 成員`CompactDatabase`函數無法將完整的 Microsoft Access 資料庫從一個版本正確轉換為另一個版本。 僅轉換數據格式。 不會轉換 Microsoft 存取定義的物件(如表單和報表)。 但是,數據將正確轉換。

> [!TIP]
> 您還可以使用`CompactDatabase`複製資料庫檔。

有關壓縮資料庫的詳細資訊,請參閱DAO説明中的主題"壓縮資料庫方法"。

## <a name="cdaoworkspacecreate"></a><a name="create"></a>CDao工作區:建立

調用此成員函數以創建新的 DAO 工作區物件並將其與`CDaoWorkspace`MFC 物件關聯。

```
virtual void Create(
    LPCTSTR lpszName,
    LPCTSTR lpszUserName,
    LPCTSTR lpszPassword);
```

### <a name="parameters"></a>參數

*lpsz名稱*<br/>
具有最多 14 個字元的字串,用於為新工作區物件唯一命名。 您必須提供名稱。 有關相關信息,請參閱 DAO 説明中的主題"名稱屬性"。

*lpszUser 名稱*<br/>
工作區擁有者的使用者名。 有關要求,請參閱[「設置預設使用者」](#setdefaultuser)成員函數的*lpszDefaultUser*參數。 有關相關信息,請參閱 DAO 説明中的「使用者名屬性」主題。

*lpsz密碼*<br/>
新工作區對象的密碼。 密碼最多只能長 14 個字元,並且可以包含除 ASCII 0(空)以外的任何字元。 密碼會區分大小寫。 有關相關信息,請參閱 DAO 説明中的主題"密碼屬性」。。

### <a name="remarks"></a>備註

整個建立過程是:

1. 構造[CDao 工作區](#cdaoworkspace)物件。

1. 調用物件`Create`的成員函數以創建基礎 DAO 工作區。 必須指定工作區名稱。

1. 如果要將工作區加入資料庫引擎的工作區集合,則可以呼叫[附加程式](#append)。 您可以使用工作區,而無需附加它。

`Create`調用后,工作區對象處於打開狀態,可供使用。 您不會在之後`Open``Create`打電話。 如果工作區集合中`Create`已存在工作區,則不調用該工作區。 `Create`如果資料庫引擎尚未為應用程式初始化,則初始化資料庫引擎。

## <a name="cdaoworkspacegetdatabasecount"></a><a name="getdatabasecount"></a>CDao工作區:取得資料庫計數

呼叫此成員函數以檢索工作區的資料庫集合中的 DAO 資料庫物件數 - 工作區中的打開資料庫數。

```
short GetDatabaseCount();
```

### <a name="return-value"></a>傳回值

工作區中的打開資料庫數。

### <a name="remarks"></a>備註

`GetDatabaseCount`如果需要迴圈訪問工作區的資料庫集合中的所有已定義的資料庫,則非常有用。 要取得有關集合中給定資料庫的資訊,請參閱[GetDatabaseInfo](#getdatabaseinfo)。 典型用法是調用`GetDatabaseCount`打開的資料庫數,然後將該數位用作重複調`GetDatabaseInfo`用 的迴圈索引。

## <a name="cdaoworkspacegetdatabaseinfo"></a><a name="getdatabaseinfo"></a>CDao工作區:取得資料庫資訊

調用此成員函數以獲取有關工作區中打開的資料庫的各種資訊。

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
工作區的「資料庫」集合中資料庫物件的零基索引,用於按索引查找。

*德布福*<br/>
傳回請求的資訊的[CDaoDatabaseInfo](../../mfc/reference/cdaodatabaseinfo-structure.md)物件的參考。

*dwInfoOptions*<br/>
指定要檢索的資料庫資訊的選項。 此處列出可用的選項以及它們導致函數傳回的內容:

- AFX_DAO_PRIMARY_INFO(預設)名稱、可上可交易、交易記錄

- AFX_DAO_SECONDARY_INFO主要資訊加上:版本、整理順序、查詢超時

- AFX_DAO_ALL_INFO主與輔助資訊加上: 連線

*lpsz名稱*<br/>
資料庫物件的名稱,用於按名稱查找。 該名稱是一個字串,最多包含 14 個字元,用於唯一命名新工作區物件。

### <a name="remarks"></a>備註

函數的一個版本允許您按索引查找資料庫。 另一個版本允許您按名稱查找資料庫。

有關*dbinfo*中傳回的說明,請參閱[CDao 資料庫資訊](../../mfc/reference/cdaodatabaseinfo-structure.md)結構。 此結構的成員對應於*dwInfoOptions*描述中列出的資訊項。 當您在一個級別請求資訊時,您也獲取任何先前級別的資訊。

## <a name="cdaoworkspacegetinipath"></a><a name="getinipath"></a>CDao工作:取得IniPath

呼叫此成員函數以獲取 Microsoft Jet 資料庫引擎在 Windows 註冊表中的初始化設定的位置。

```
static CString PASCAL GetIniPath();
```

### <a name="return-value"></a>傳回值

包含註冊表位置的[CString。](../../atl-mfc-shared/reference/cstringt-class.md)

### <a name="remarks"></a>備註

您可以使用該位置獲取有關資料庫引擎設置的資訊。 返回的信息實際上是註冊表子鍵的名稱。

有關相關資訊,請參閱 DAO 説明中的"IniPath 屬性"和"自訂數據存取的 Windows 註冊表設置"的主題。

## <a name="cdaoworkspacegetisolateodbctrans"></a><a name="getisolateodbctrans"></a>CDao工作:取得隔離BCTrans

呼叫此成員函數獲取工作區的 DAO 隔離 ODBCTrans 屬性的當前值。

```
BOOL GetIsolateODBCTrans();
```

### <a name="return-value"></a>傳回值

如果 ODBC 事務是隔離的,則非零;否則 0。

### <a name="remarks"></a>備註

在某些情況下,您可能需要在同一 ODBC 資料庫上同時掛起多個事務。 為此,您需要為每個事務打開單獨的工作區。 請記住,儘管每個工作區都可以具有與資料庫的ODBC連接,但這會降低系統性能。 由於通常不需要事務隔離,因此默認情況下共用同一使用者打開的多個工作區物件的ODBC連接。

某些 ODBC 伺服器(如 Microsoft SQL Server)不允許在單個連接上同時進行事務。 如果需要一次有多個事務針對此類資料庫掛起,則在打開每個工作區時將隔離ODBCTrans屬性設置為 TRUE。 這將強制為每個工作區建立單獨的 ODBC 連接。

有關相關信息,請參閱 DAO 説明中的主題「隔離ODBCTrans屬性」。。

## <a name="cdaoworkspacegetlogintimeout"></a><a name="getlogintimeout"></a>CDao工作區:取得登入逾時

調用此成員函數獲取工作區的 DAO 登錄超時屬性的當前值。

```
static short PASCAL GetLoginTimeout();
```

### <a name="return-value"></a>傳回值

嘗試登錄到 ODBC 資料庫時出錯前的秒數。

### <a name="remarks"></a>備註

此值表示嘗試登入 ODBC 資料庫時發生錯誤的秒數。 默認的登錄超時設置為 20 秒。 當 LoginTimeout 設置為 0 時,不會發生超時,並且與數據源的通信可能會停止回應。

當您嘗試登入到 ODBC 資料庫(如 Microsoft SQL Server)時,連接可能會由於網路錯誤或伺服器未執行而失敗。 您可以指定資料庫引擎在生成錯誤之前等待多長時間,而不是等待預設的 20 秒連接。 登錄到伺服器是許多不同事件的一部分,例如在外部伺服器資料庫上運行查詢。

有關相關信息,請參閱 DAO 説明中的「登錄超時屬性」主題。

## <a name="cdaoworkspacegetname"></a><a name="getname"></a>CDao工作區:取得名稱

呼叫此成員函數以獲取`CDaoWorkspace`物件基礎的 DAO 工作區物件的使用者定義的名稱。

```
CString GetName();
```

### <a name="return-value"></a>傳回值

包含 DAO 工作區物件的使用者定義名稱的[CString。](../../atl-mfc-shared/reference/cstringt-class.md)

### <a name="remarks"></a>備註

該名稱可用於按名稱訪問資料庫引擎的工作區集合中的 DAO 工作區物件。

有關相關信息,請參閱 DAO 説明中的主題"名稱屬性"。

## <a name="cdaoworkspacegetusername"></a><a name="getusername"></a>CDao工作區:取得使用者名稱

調用此成員函數以獲取工作區擁有者的名稱。

```
CString GetUserName();
```

### <a name="return-value"></a>傳回值

表示工作區物件擁有者的[CString。](../../atl-mfc-shared/reference/cstringt-class.md)

### <a name="remarks"></a>備註

要獲取或設置工作區擁有者的許可權,請直接調用 DAO 以檢查"許可權"屬性設置;否則,請直接調用 DAO 以檢查"許可權"屬性設置。這將確定使用者具有的許可權。 要使用許可權,您需要一個 SYSTEM。MDA 檔。

有關直接呼叫 DAO 的資訊,請參閱[技術說明 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。 有關相關信息,請參閱 DAO 説明中的「使用者名屬性」主題。

## <a name="cdaoworkspacegetversion"></a><a name="getversion"></a>CDao 工作:抓取版本

呼叫此成員函數以確定正在使用的 Microsoft Jet 資料庫引擎的版本。

```
static CString PASCAL GetVersion();
```

### <a name="return-value"></a>傳回值

指示與物件關聯的資料庫引擎的版本的[CString。](../../atl-mfc-shared/reference/cstringt-class.md)

### <a name="remarks"></a>備註

返回的值表示窗體「主要.minor」中的版本號;例如,"3.0"。 產品版本號(例如 3.0)由版本號 (3)、句點和發行號 (0) 組成。

有關相關信息,請參閱 DAO 説明中的主題"版本屬性」。。

## <a name="cdaoworkspacegetworkspacecount"></a><a name="getworkspacecount"></a>CDao工作區:取得工作區計數

呼叫此成員函數以檢索資料庫引擎工作區集合中的 DAO 工作區物件數。

```
short GetWorkspaceCount();
```

### <a name="return-value"></a>傳回值

工作區集合中的打開工作區數。

### <a name="remarks"></a>備註

此計數不包括未追加到集合中的任何打開工作區。 `GetWorkspaceCount`如果需要迴圈訪問工作區集合中的所有已定義的工作區,則非常有用。 要取得有關集合中給定工作區的資訊,請參閱[GetWorkspaceInfo](#getworkspaceinfo)。 典型用法是調用`GetWorkspaceCount`打開工作區的數量,然後將該數位用作重複調`GetWorkspaceInfo`用 的迴圈索引。

## <a name="cdaoworkspacegetworkspaceinfo"></a><a name="getworkspaceinfo"></a>CDao工作空間:取得工作資訊

調用此成員函數以獲取有關會話中打開的工作區的各種資訊。

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
工作區集合中資料庫物件的零基索引,用於按索引查找。

*沃克斯普福*<br/>
傳回請求的資訊的[CDaoWorkspaceInfo](../../mfc/reference/cdaoworkspaceinfo-structure.md)物件的參考。

*dwInfoOptions*<br/>
指定要檢索的工作區的資訊的選項。 此處列出可用的選項以及它們導致函數傳回的內容:

- AFX_DAO_PRIMARY_INFO (預設)名稱

- AFX_DAO_SECONDARY_INFO主要資訊加:使用者名

- AFX_DAO_ALL_INFO主要和次要資訊加上:隔離 ODBCTrans

*lpsz名稱*<br/>
工作區物件的名稱,用於按名稱查找。 該名稱是一個字串,最多包含 14 個字元,用於唯一命名新工作區物件。

### <a name="remarks"></a>備註

有關在*wkspcinfo 中*傳回的資訊說明,請參閱[CDaoWorkspaceInfo](../../mfc/reference/cdaoworkspaceinfo-structure.md)結構。 此結構的成員對應於*dwInfoOptions*描述中列出的資訊項。 當您在一個級別請求資訊時,您也會得到以前級別的資訊。

## <a name="cdaoworkspaceidle"></a><a name="idle"></a>CDao工作區:空閒

調用`Idle`為資料庫引擎提供執行由於數據處理密集而可能不是最新的後台任務的機會。

```
static void PASCAL Idle(int nAction = dbFreeLocks);
```

### <a name="parameters"></a>參數

*nAction*<br/>
在空閒處理期間執行的操作。 目前唯一有效的操作是`dbFreeLocks`。

### <a name="remarks"></a>備註

在多使用者多任務處理環境中,通常如此,在這種環境中,沒有足夠的後台處理時間來保持記錄集中的所有記錄。

> [!NOTE]
> 使用`Idle`Microsoft Jet 資料庫引擎的 3.0 版本創建的資料庫不需要調用。 僅適用於`Idle`使用早期版本的資料庫。

通常,讀取鎖被刪除,並且僅當沒有發生其他操作(包括滑鼠移動)時,才會更新本地動態集類型記錄集對象中的數據。 如果定期調用`Idle`,則通過釋放不需要的讀取鎖,為資料庫引擎提供時間來跟蹤後台處理任務。 指定`dbFreeLocks`常量作為參數延遲處理,直到釋放所有讀取鎖。

除非應用程式有多個實例正在運行,否則在單用戶環境中不需要此成員函數。 成員`Idle`函數可能會提高多用戶環境中的性能,因為它強制資料庫引擎將數據刷新到磁碟,從而釋放記憶體上的鎖。 還可以通過使操作成為事務的一部分來釋放讀取鎖。

有關相關信息,請參閱 DAO 説明中的主題"空閒方法"。

## <a name="cdaoworkspaceisopen"></a><a name="isopen"></a>CDao工作區:是開放的

呼叫此成員函數以確定`CDaoWorkspace`物件是否打開,即 MFC 物件是否已透過呼叫[Open](#open)或對[Create](#create)進行初始化。

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>傳回值

如果工作區對象處於打開狀態,則非零;否則 0。

### <a name="remarks"></a>備註

可以調用處於打開狀態的工作區的任何成員函數。

## <a name="cdaoworkspacem_pdaoworkspace"></a><a name="m_pdaoworkspace"></a>CDao工作:m_pDAOWorkspace

指向基礎 DAO 工作區物件的指標。

### <a name="remarks"></a>備註

如果需要直接存取基礎 DAO 物件,請使用此資料成員。 可以通過此指標調用DAO物件的介面。

有關直接存取 DAO 物件的資訊,請參閱[技術說明 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。

## <a name="cdaoworkspaceopen"></a><a name="open"></a>CDao工作區:開啟

顯式打開與 DAO 的預設工作區關聯的工作區物件。

```
virtual void Open(LPCTSTR lpszName = NULL);
```

### <a name="parameters"></a>參數

*lpsz名稱*<br/>
要開啟的 DAO 工作區物件的名稱 - 具有最多 14 個字元的字串,該字串對工作區進行唯一命名。 接受預設值 NULL 以顯式打開預設工作區。 有關命名要求,請參閱[創建](#create)的*lpszName*參數。 有關相關信息,請參閱 DAO 説明中的主題"名稱屬性"。

### <a name="remarks"></a>備註

建構`CDaoWorkspace`物件後,呼叫此成員函數執行以下操作之一:

- 顯式打開預設工作區。 透過 NULL 表示*lpszName*。

- 按名稱打開`CDaoWorkspace`現有物件(工作區集合的成員)。 傳遞現有工作區物件的有效名稱。

`Open`將工作區物件置於打開狀態,如果尚未為應用程式初始化資料庫引擎,則還會初始化資料庫引擎。

儘管許多`CDaoWorkspace`成員函數只能在打開工作區後調用,但在構造C++物件後,但在調`Open`用 :

||||
|-|-|-|
|[建立](#create)|[取得版本](#getversion)|[設定預設使用者](#setdefaultuser)|
|[取得 Iinpath](#getinipath)|[Idle](#idle)|[設定IniPath](#setinipath)|
|[取得登入逾時](#getlogintimeout)|[設定預設密碼](#setdefaultpassword)|[設定登入逾時](#setlogintimeout)|

## <a name="cdaoworkspacerepairdatabase"></a><a name="repairdatabase"></a>CDao工作區:修復資料庫

如果需要嘗試修復存取 Microsoft Jet 資料庫引擎的損壞資料庫,請呼叫此成員函數。

```
static void PASCAL RepairDatabase(LPCTSTR lpszName);
```

### <a name="parameters"></a>參數

*lpsz名稱*<br/>
現有 Microsoft Jet 引擎資料庫檔案的路徑和檔名。 如果省略路徑,則僅搜索當前目錄。 如果您的系統支援統一的命名約定 (UNC),您\\\\\\還可以 指定網络路徑,例如:"\MYSERVER\\_MYSHARE\\\\\MYDIR \MYDB。MDB"。 (路徑字串中需要雙背斜杠,因為""\\是C++轉義字元。

### <a name="remarks"></a>備註

在修復資料庫之前,必須關閉*lpszName*指定的資料庫。 在多使用者環境中,其他使用者在修復 lpszName 時無法打開*lpszName。* 如果*lpszName*未關閉或不能獨佔使用,則會發生錯誤。

此成員函數嘗試修復被不完整寫入操作標記為可能損壞的資料庫。 如果使用 Microsoft Jet 資料庫引擎的應用程式由於停電或電腦硬體問題而意外關閉,則可能發生此情況。 如果完成該操作並調用[Close](../../mfc/reference/cdaodatabase-class.md#close)成員函數,或者以通常的方式退出應用程式,則資料庫將不會標記為可能已損壞。

> [!NOTE]
> 修復資料庫後,最好使用[CompactDatabase](#compactdatabase)成員函數壓縮它,以碎片整理檔並恢復磁碟空間。

有關修復資料庫的詳細資訊,請參閱DAO説明中的主題"修復資料庫方法"。

## <a name="cdaoworkspacerollback"></a><a name="rollback"></a>CDao工作區:回滾

調用此成員函數以結束當前事務,並在事務開始之前將工作區中的所有資料庫還原到其條件。

```cpp
void Rollback();
```

### <a name="remarks"></a>備註

> [!CAUTION]
> 在一個工作區物件中,事務始終是工作區的全域事務,並且不僅限於一個資料庫或記錄集。 如果對工作區事務中的多個資料庫或記錄集執行操作,則`Rollback`還原所有這些資料庫和記錄集上的所有操作。

如果關閉工作區物件而不保存或回滾任何掛起的事務,則事務將自動回滾。 如果您呼叫[CommitTrans](#committrans)`Rollback`或沒有首先呼叫[BeginTrans,](#begintrans)則會發生錯誤。

> [!NOTE]
> 開始事務時,資料庫引擎將其操作記錄在工作站上的 TEMP 環境變數指定的目錄中的檔中。 如果事務日誌檔耗盡了 TEMP 驅動器上的可用存儲,則資料庫引擎將導致 MFC`CDaoException`引發 (DAO 錯誤 2004)。 此時,如果調用`CommitTrans`,將提交不確定數量的操作,但剩餘的未完成的操作將丟失,並且必須重新啟動該操作。 調用`Rollback`將釋放事務日誌並回滾事務中的所有操作。

## <a name="cdaoworkspacesetdefaultpassword"></a><a name="setdefaultpassword"></a>CDao工作區:設定預設密碼

呼叫此成員函數以設定資料庫引擎在沒有特定密碼的情況下創建工作區物件時使用的預設密碼。

```
static void PASCAL SetDefaultPassword(LPCTSTR lpszPassword);
```

### <a name="parameters"></a>參數

*lpsz密碼*<br/>
默認密碼。 密碼最多只能長 14 個字元,並且可以包含除 ASCII 0(空)以外的任何字元。 密碼會區分大小寫。

### <a name="remarks"></a>備註

您設定的默認密碼應用於調用後創建的新工作區。 建立後續工作區時,不需要在[「創建](#create)」調用中指定密碼。

要使用此成員函數:

1. 建構`CDaoWorkspace`物件但不呼`Create`叫 。

1. 打電話`SetDefaultPassword`,如果您願意,[請設定預設使用者](#setdefaultuser)。

1. 呼叫`Create`此工作區物件或後續物件,而不指定密碼。

預設情況下,默認使用者屬性設置為"管理員",默認密碼屬性設置為空字串 ("")。

有關安全性的詳細資訊,請參閱DAO説明中的主題"許可權屬性"。 有關相關資訊,請參閱 DAO 説明中的「默認密碼屬性」和「默認使用者屬性」 主題。

## <a name="cdaoworkspacesetdefaultuser"></a><a name="setdefaultuser"></a>CDao 工作區:設定預設使用者

呼叫此成員函數以設定資料庫引擎在沒有特定使用者名的情況下創建工作區物件時使用的預設使用者名。

```
static void PASCAL SetDefaultUser(LPCTSTR lpszDefaultUser);
```

### <a name="parameters"></a>參數

*lpszDefaultUser*<br/>
默認使用者名。 使用者名可以是 1 - 20 個字元長,包括字母字元、重音字元、數位、空格和符號,但:"(引號)、/(前斜杠)、*(斜杠\[\])、(括弧 )、:(冒號)、&#124;(\<管道)、(小於 符號)、>(大於符號)、*(加號)、*(等號);(分號)、、、(逗號)、(問號\*)、(星號)、前導空格和控制字元(ASCII 00 到 ASCII 31)。 有關相關信息,請參閱 DAO 説明中的「使用者名屬性」主題。

### <a name="remarks"></a>備註

您設定的預設用戶名將應用於調用後創建的新工作區。 創建後續工作區時,不需要在[「創建](#create)」調用中指定使用者名。

要使用此成員函數:

1. 建構`CDaoWorkspace`物件但不呼`Create`叫 。

1. 打電話`SetDefaultUser`,如果您願意,[請設定預設密碼](#setdefaultpassword)。

1. 調用`Create`此工作區物件或後續物件,而不指定使用者名。

預設情況下,默認使用者屬性設置為"管理員",默認密碼屬性設置為空字串 ("")。

有關相關資訊,請參閱 DAO 説明中的"默認使用者屬性"和"默認密碼屬性"主題。

## <a name="cdaoworkspacesetinipath"></a><a name="setinipath"></a>CDao工作區:SetIniPath

呼叫此成員函數以指定 Microsoft Jet 資料庫引擎的 Windows 註冊表設置的位置。

```
static void PASCAL SetIniPath(LPCTSTR lpszRegistrySubKey);
```

### <a name="parameters"></a>參數

*lpsz註冊子鍵*<br/>
包含 Windows 註冊表子鍵名稱的字串,用於 Microsoft Jet 資料庫引擎設定的位置或可安裝 ISAM 資料庫所需的參數。

### <a name="remarks"></a>備註

僅當`SetIniPath`需要指定特殊設置時才調用。 有關詳細資訊,請參閱 DAO 説明中的主題"IniPath 屬性」。。

> [!NOTE]
> 在`SetIniPath`應用程式安裝期間調用,而不是在應用程式運行時調用。 `SetIniPath`在打開任何工作區、資料庫或記錄集之前,必須調用;否則,MFC會引發異常。

您可以使用此機制使用使用者提供的註冊表設置配置資料庫引擎。 此屬性的範圍僅限於您的應用程式,如果不重新啟動應用程式,則無法更改。

## <a name="cdaoworkspacesetisolateodbctrans"></a><a name="setisolateodbctrans"></a>CDao工作區:設定隔離BCTrans

呼叫此成員函數以設定工作區的 DAO 隔離 ODBCTrans 屬性的值。

```cpp
void SetIsolateODBCTrans(BOOL bIsolateODBCTrans);
```

### <a name="parameters"></a>參數

*b 隔離ODBCTrans*<br/>
如果要開始隔離 ODBC 事務,則傳遞 TRUE。 如果要停止隔離 ODBC 事務,則傳遞 FALSE。

### <a name="remarks"></a>備註

在某些情況下,您可能需要在同一 ODBC 資料庫上同時掛起多個事務。 為此,您需要為每個事務打開單獨的工作區。 儘管每個工作區都可以有自己的 ODBC 連接到資料庫,但這會降低系統性能。 由於通常不需要事務隔離,因此默認情況下共用同一使用者打開的多個工作區物件的ODBC連接。

某些 ODBC 伺服器(如 Microsoft SQL Server)不允許在單個連接上同時進行事務。 如果需要一次有多個事務針對此類資料庫掛起,則在打開每個工作區時將隔離ODBCTrans屬性設置為 TRUE。 這將強制為每個工作區建立單獨的 ODBC 連接。

## <a name="cdaoworkspacesetlogintimeout"></a><a name="setlogintimeout"></a>CDao工作區:設定登入逾時

調用此成員函數以設置工作區的 DAO 登錄超時屬性的值。

```
static void PASCAL SetLoginTimeout(short nSeconds);
```

### <a name="parameters"></a>參數

*n 秒*<br/>
嘗試登錄到 ODBC 資料庫時出錯前的秒數。

### <a name="remarks"></a>備註

此值表示嘗試登入 ODBC 資料庫時發生錯誤的秒數。 默認的登錄超時設置為 20 秒。 當 LoginTimeout 設置為 0 時,不會發生超時,並且與數據源的通信可能會停止回應。

當您嘗試登入到 ODBC 資料庫(如 Microsoft SQL Server)時,連接可能會由於網路錯誤或伺服器未執行而失敗。 您可以指定資料庫引擎在生成錯誤之前等待多長時間,而不是等待預設的 20 秒連接。 登錄到伺服器是許多不同事件的一部分,例如在外部伺服器資料庫上運行查詢。 超時值由 LoginTimeout 屬性的當前設置決定。

有關相關信息,請參閱 DAO 説明中的「登錄超時屬性」主題。

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CDaoDatabase 類別](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoRecordset 類別](../../mfc/reference/cdaorecordset-class.md)<br/>
[CDaoTableDef 類別](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoQueryDef 類別](../../mfc/reference/cdaoquerydef-class.md)<br/>
[CDaoException 類別](../../mfc/reference/cdaoexception-class.md)
