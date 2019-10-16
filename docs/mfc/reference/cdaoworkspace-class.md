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
ms.openlocfilehash: 3e4ded466b673bff3c0630e798877b69d1ca384d
ms.sourcegitcommit: 2f96e2fda591d7b1b28842b2ea24e6297bcc3622
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2019
ms.locfileid: "71096059"
---
# <a name="cdaoworkspace-class"></a>CDaoWorkspace 類別

從單一使用者的登入到登出，管理受密碼保護的具名資料庫工作階段。

## <a name="syntax"></a>語法

```
class CDaoWorkspace : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CDaoWorkspace::CDaoWorkspace](#cdaoworkspace)|建立工作區物件。 之後，請`Create`呼叫`Open`或。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDaoWorkspace::Append](#append)|將新建立的工作區附加至資料庫引擎的工作區集合。|
|[CDaoWorkspace::BeginTrans](#begintrans)|開始新的交易，其適用于工作區中開啟的所有資料庫。|
|[CDaoWorkspace::Close](#close)|關閉工作區及其包含的所有物件。 暫止交易已回復。|
|[CDaoWorkspace::CommitTrans](#committrans)|完成目前的交易並儲存變更。|
|[CDaoWorkspace::CompactDatabase](#compactdatabase)|壓縮（或重複）資料庫。|
|[CDaoWorkspace::Create](#create)|建立新的 DAO 工作區物件。|
|[CDaoWorkspace::GetDatabaseCount](#getdatabasecount)|傳回工作區資料庫集合中的 DAO 資料庫物件數目。|
|[CDaoWorkspace::GetDatabaseInfo](#getdatabaseinfo)|傳回在工作區的資料庫集合中所定義之指定 DAO 資料庫的相關資訊。|
|[CDaoWorkspace::GetIniPath](#getinipath)|傳回 Microsoft Jet 資料庫引擎初始化設定在 Windows 登錄中的位置。|
|[CDaoWorkspace::GetIsolateODBCTrans](#getisolateodbctrans)|傳回值，指出是否透過強制多個資料來源連接來隔離牽涉到相同 ODBC 資料來源的多個交易。|
|[CDaoWorkspace::GetLoginTimeout](#getlogintimeout)|傳回當使用者嘗試登入 ODBC 資料庫時，發生錯誤之前的秒數。|
|[CDaoWorkspace::GetName](#getname)|傳回工作區物件的使用者定義名稱。|
|[CDaoWorkspace::GetUserName](#getusername)|傳回建立工作區時所指定的使用者名稱。 這是工作區擁有者的名稱。|
|[CDaoWorkspace::GetVersion](#getversion)|傳回字串，其中包含與工作區相關聯的資料庫引擎版本。|
|[CDaoWorkspace::GetWorkspaceCount](#getworkspacecount)|傳回資料庫引擎的工作區集合中 DAO 工作區物件的數目。|
|[CDaoWorkspace::GetWorkspaceInfo](#getworkspaceinfo)|傳回在資料庫引擎的工作區集合中定義之指定 DAO 工作區的相關資訊。|
|[CDaoWorkspace::Idle](#idle)|允許 database engine 執行背景工作。|
|[CDaoWorkspace::IsOpen](#isopen)|如果工作區已開啟，則傳回非零。|
|[CDaoWorkspace::Open](#open)|明確開啟與 DAO 的預設工作區相關聯的工作區物件。|
|[CDaoWorkspace::RepairDatabase](#repairdatabase)|嘗試修復損毀的資料庫。|
|[CDaoWorkspace::Rollback](#rollback)|結束目前的交易，而不儲存變更。|
|[CDaoWorkspace::SetDefaultPassword](#setdefaultpassword)|設定在建立工作區物件但沒有特定密碼時，資料庫引擎所使用的密碼。|
|[CDaoWorkspace::SetDefaultUser](#setdefaultuser)|設定在建立工作區物件但沒有特定的使用者名稱時，資料庫引擎所使用的使用者名稱。|
|[CDaoWorkspace::SetIniPath](#setinipath)|在 Windows 登錄中設定 Microsoft Jet 資料庫引擎初始化設定的位置。|
|[CDaoWorkspace::SetIsolateODBCTrans](#setisolateodbctrans)|指定是否藉由強制執行資料來源的多個連接，來隔離牽涉到相同 ODBC 資料來源的多個交易。|
|[CDaoWorkspace::SetLoginTimeout](#setlogintimeout)|設定當使用者嘗試登入 ODBC 資料來源時發生錯誤的秒數。|

### <a name="public-data-members"></a>公用資料成員

|名稱|說明|
|----------|-----------------|
|[CDaoWorkspace::m_pDAOWorkspace](#m_pdaoworkspace)|指向基礎 DAO 工作區物件。|

## <a name="remarks"></a>備註

在大部分情況下，您將不需要多個工作區，而且您不需要建立明確的工作區物件。當您開啟資料庫和記錄集物件時，它們會使用 DAO 的預設工作區。 不過，如有需要，您可以藉由建立額外的工作區物件，一次執行多個會話。 每個工作區物件可以在自己的資料庫集合中包含多個開啟的資料庫物件。 在 MFC 中，工作區主要是交易管理員，指定一組開啟的資料庫全都位於相同的「交易空間」中。

> [!NOTE]
>  DAO 資料庫類別與以開放式資料庫連接（ODBC）為基礎的 MFC 資料庫類別不同。 所有的 DAO 資料庫類別名稱都具有 "CDao" 前置詞。 一般而言，以 DAO 為基礎的 MFC 類別比以 ODBC 為基礎的 MFC 類別更有能力。 以 DAO 為基礎的類別會透過 Microsoft Jet 資料庫引擎（包括 ODBC 驅動程式）存取資料。 它們也支援資料定義語言（DDL）作業，例如透過類別建立資料庫和加入資料表和欄位，而不需要直接呼叫 DAO。

## <a name="capabilities"></a>功能

類別`CDaoWorkspace`提供下列各項：

- 明確存取（如有需要）到預設工作區（藉由初始化資料庫引擎所建立）。 通常您會藉由建立資料庫和記錄集物件，隱含地使用 DAO 的預設工作區。

- 交易空間，適用于工作區中開啟的所有資料庫。 您可以建立其他工作區來管理個別的交易空間。

- 基礎 Microsoft Jet 資料庫引擎的許多屬性介面（請參閱靜態成員函式）。 開啟或建立工作區，或在開啟或建立之前呼叫靜態成員函式，會初始化資料庫引擎。

- 資料庫引擎的工作區集合的存取權，它會儲存已附加至其中的所有作用中工作區。 您也可以建立及使用工作區，而不將其附加至集合。

## <a name="security"></a>安全性

MFC 不會在 DAO 中執行使用者和群組集合，用於安全性控制。 如果您需要 DAO 的這些層面，您必須透過直接呼叫 DAO 介面，自行進行程式設計。 如需相關資訊，請參閱[技術附注 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。

## <a name="usage"></a>使用量

您可以使用類別`CDaoWorkspace`來執行下列動作：

- 明確開啟預設工作區。

   當您開啟新的[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)或[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)物件時，通常會隱含使用預設工作區。 但是，您可能需要明確地存取它，例如，用來存取資料庫引擎屬性或工作區集合。 請參閱下面的「隱含使用預設工作區」。

- 建立新的工作區。 如果您想要將其新增至工作區集合，請呼叫 [[附加](#append)]。

- 開啟工作區集合中的現有工作區。

建立不存在於工作區集合中的新工作區，會在[Create](#create)成員函式下說明。 工作區物件不會以任何方式保存在資料庫引擎會話之間。 如果您的應用程式以靜態方式連結 MFC，則結束應用程式取消初始化資料庫引擎。 如果您的應用程式以動態方式連結 MFC，則在卸載 MFC DLL 時，資料庫引擎會未初始化。

明確地開啟預設工作區，或在工作區集合中開啟現有的工作區，會在[Open](#open)成員函式下加以說明。

藉由關閉具有[Close](#close)成員函式的工作區來結束工作區會話。 `Close`關閉先前尚未關閉的任何資料庫，並回復任何未認可的交易。

## <a name="transactions"></a>異動
DAO 3.6 是最終版本，並被視為已淘汰。 管理工作區層級的交易;因此，在具有多個開啟資料庫的工作區上，交易會套用至所有資料庫。 例如，如果兩個資料庫有未認可的更新，而且您呼叫[CommitTrans](#committrans)，則會認可所有的更新。 如果您想要將交易限制為單一資料庫，您需要有個別的工作區物件。

## <a name="implicit-use-of-the-default-workspace"></a>隱含使用預設工作區

在下列情況下，MFC 會隱含地使用 DAO 的預設工作區：

- 如果您建立新`CDaoDatabase`的物件，但不透過現有`CDaoWorkspace`的物件執行此動作，MFC 會為您建立暫存工作區物件，這會對應到 DAO 的預設工作區。 如果您針對多個資料庫執行此動作，則所有資料庫物件都會與預設工作區建立關聯。 您可以透過`CDaoDatabase`資料成員存取資料庫的工作區。

- 同樣地，如果您在`CDaoRecordset`不提供`CDaoDatabase`物件指標的情況下建立物件，MFC 會建立暫存資料庫物件，並藉由擴充功能暫存工作區物件。 您可以透過`CDaoRecordset`資料成員，存取記錄集的資料庫，並間接存取其工作區。

## <a name="other-operations"></a>其他作業

也會提供其他資料庫作業，例如修復損毀的資料庫或壓縮資料庫。

如需直接呼叫 DAO 以及關於 DAO 安全性的詳細資訊，請參閱[技術提示 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

`CDaoWorkspace`

## <a name="requirements"></a>需求

**標頭：** afxdao。h

##  <a name="append"></a>CDaoWorkspace：： Append

呼叫[Create](#create)之後，請呼叫這個成員函式。

```
virtual void Append();
```

### <a name="remarks"></a>備註

`Append`將新建立的工作區物件附加至資料庫引擎的工作區集合。 資料庫引擎會話之間不會保存工作區;它們只會儲存在記憶體中，而不是儲存在磁片上。 您不需要附加工作區;如果沒有這麼做，您仍然可以使用它。

附加的工作區會保留在工作區集合中，處於作用中的開啟狀態，直到您呼叫其[Close](#close)成員函式為止。

如需相關資訊，請參閱 DAO 說明中的「附加方法」主題。

##  <a name="begintrans"></a>CDaoWorkspace：： BeginTrans

呼叫這個成員函式以起始交易。

```
void BeginTrans();
```

### <a name="remarks"></a>備註

在您呼叫`BeginTrans`之後，您對資料或資料庫結構所做的更新會在您認可交易時生效。 因為工作區會定義單一交易空間，所以該交易會套用至工作區中所有開啟的資料庫。 有兩種方式可以完成交易：

- 呼叫[CommitTrans](#committrans)成員函式來認可交易，並將變更儲存至資料來源。

- 或呼叫[Rollback](#rollback)成員函式來取消交易。

當交易暫止時關閉工作區物件或資料庫物件，會回復所有暫止的交易。

如果您需要從另一個 ODBC 資料來源上的某個 ODBC 資料來源隔離交易，請參閱[SetIsolateODBCTrans](#setisolateodbctrans)成員函式。

##  <a name="cdaoworkspace"></a>CDaoWorkspace::CDaoWorkspace

建構 `CDaoWorkspace` 物件。

```
CDaoWorkspace();
```

### <a name="remarks"></a>備註

在建立C++物件之後，您有兩個選項：

- 呼叫物件的[open](#open)成員函式來開啟預設工作區，或開啟工作區集合中的現有物件。

- 或呼叫物件的[create](#create)成員函式，以建立新的 DAO 工作區物件。 這會明確啟動新的工作區會話，您可以透過`CDaoWorkspace`物件來參考它。 呼叫`Create`之後，如果您想要將工作區加入至 database engine 的工作區集合，您可以呼叫 [[附加](#append)]。

如需何時需要明確建立`CDaoWorkspace`物件的相關資訊，請參閱 [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) 的類別總覽。 通常，當您在未指定工作區的情況下開啟[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)物件時，或在未指定資料庫物件的情況下開啟[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)物件時，會以隱含的方式使用建立的工作區。 以這種方式建立的 MFC DAO 物件會使用 DAO 的預設工作區，這會建立一次並重複使用。

若要釋放工作區及其包含的物件，請呼叫工作區物件的[Close](#close)成員函式。

##  <a name="close"></a>CDaoWorkspace：： Close

呼叫這個成員函式以關閉工作區物件。

```
virtual void Close();
```

### <a name="remarks"></a>備註

關閉開啟的工作區物件會釋放基礎 DAO 物件，如果工作區是工作區集合的成員，則會將它從集合中移除。 呼叫`Close`是良好的程式設計作法。

> [!CAUTION]
>  關閉工作區物件會關閉工作區中任何已開啟的資料庫。 這會導致資料庫中開啟的任何記錄集也會關閉，而且任何暫止的編輯或更新都會復原。 如需相關資訊，請參閱[CDaoDatabase：： close](../../mfc/reference/cdaodatabase-class.md#close)、 [CDaoRecordset：： close](../../mfc/reference/cdaorecordset-class.md#close)、 [CDaoTableDef：： Close](../../mfc/reference/cdaotabledef-class.md#close)和[CDaoQueryDef：： close](../../mfc/reference/cdaoquerydef-class.md#close)成員函式。

工作區物件不是永久的;它們只有在參考存在時才存在。 這表示當資料庫引擎會話結束時，工作區和其資料庫集合不會保存。 您必須再次開啟您的工作區和資料庫，才能為下一個會話重新建立它們。

如需相關資訊，請參閱 DAO 說明中的「關閉方法」主題。

##  <a name="committrans"></a>CDaoWorkspace：： CommitTrans

呼叫此成員函式以認可交易-將一組編輯和更新儲存至工作區中的一個或多個資料庫。

```
void CommitTrans();
```

### <a name="remarks"></a>備註

交易是由資料庫資料或其結構的一系列變更所組成，從呼叫[BeginTrans](#begintrans)開始。 當您完成交易時，請認可它，或使用[Rollback](#rollback)將它復原（取消變更）。 根據預設，如果沒有交易，就會立即認可記錄的更新。 呼叫會使更新的認可延遲，直到您呼叫`CommitTrans`為止。 `BeginTrans`

> [!CAUTION]
>  在一個工作區中，交易一律會全域用於工作區，而且不會僅限於一個資料庫或記錄集。 如果您在工作區交易中的多個資料庫或記錄集上執行`CommitTrans`作業，則會認可所有`Rollback`暫止的更新，並還原這些資料庫和記錄集上的所有作業。

當您關閉具有暫止交易的資料庫或工作區時，就會回復交易。

> [!NOTE]
>  這不是兩階段的認可機制。 如果其中一個更新無法認可，其他人仍會認可。

##  <a name="compactdatabase"></a>CDaoWorkspace：：壓縮

呼叫這個成員函式以壓縮指定的 Microsoft Jet （。MDB）資料庫。

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
現有、已關閉之資料庫的名稱。 它可以是完整路徑和檔案名，例如 "C：\\\MYDB。MDB」。 如果檔案名具有副檔名，您就必須指定它。 如果您的網路支援統一命名慣例（UNC），您也可以指定網路路徑，\\例如 "\\ \\ \\\MYSERVER\\\MYSHARE \MYDIR\\\MYDB。MDB」。 （路徑字串中需要兩個反斜線，因為\\"" 是C++ escape 字元）。

*lpszDestName*<br/>
您正在建立之壓縮資料庫的完整路徑。 您也可以使用*lpszSrcName*指定網路路徑。 您不能使用*lpszDestName*引數來指定與*lpszSrcName*相同的資料庫檔案。

*lpszPassword*<br/>
當您想要壓縮受密碼保護的資料庫時，所使用的密碼。 請注意，如果您使用的是`CompactDatabase`採用密碼的版本，則必須提供所有參數。 此外，因為這是連接參數，所以它需要特殊格式，如下所示：;PWD = *lpszPassword*。 例如：;PWD = "高興"。 （需要前置分號）。

*lpszLocale*<br/>
字串運算式，用來指定建立*lpszDestName*的排序次序。 如果您藉由接受的預設值`dbLangGeneral`來省略這個引數（如下所示），則新資料庫的地區設定會與舊資料庫相同。 可能的值為：

- `dbLangGeneral`英文、德文、法文、葡萄牙文、義大利文和新式西班牙文

- `dbLangArabic`阿拉伯文

- `dbLangCyrillic`俄語

- `dbLangCzech`捷克文

- `dbLangDutch`荷蘭文

- `dbLangGreek`希臘文

- `dbLangHebrew`希伯來文

- `dbLangHungarian`匈牙利文

- `dbLangIcelandic`冰島文

- `dbLangNordic`北歐語言（僅限 Microsoft Jet database engine 1.0 版）

- `dbLangNorwdan`挪威文和丹麥文

- `dbLangPolish`波蘭文

- `dbLangSpanish`傳統西班牙文

- `dbLangSwedfin`瑞典文和芬蘭文

- `dbLangTurkish`土耳其文

*nOptions*<br/>
表示目標資料庫的一個或多個選項*lpszDestName*。 如果您藉由接受預設值來省略這個引數，則*lpszDestName*會具有相同的加密和與*lpszSrcName*相同的版本。 您可以使用位`dbEncrypt` or `dbDecrypt`運算子，將或選項與其中一個版本選項結合。 指定資料庫格式的可能值，而不是資料庫引擎版本，包括：

- `dbEncrypt`壓縮時加密資料庫。

- `dbDecrypt`壓縮時解密資料庫。

- `dbVersion10`在壓縮時，建立使用 Microsoft Jet database engine 1.0 版的資料庫。

- `dbVersion11`在壓縮時，建立使用 Microsoft Jet database engine 1.1 版的資料庫。

- `dbVersion20`在壓縮時，建立使用 Microsoft Jet database engine 2.0 版的資料庫。

- `dbVersion30`在壓縮時，建立使用 Microsoft Jet database engine 3.0 版的資料庫。

您可以在`dbEncrypt` [ `dbDecrypt`選項] 引數中使用或，指定是否要在壓縮資料庫時加密或解密它。 如果您省略加密常數`dbDecrypt` ，或是同時包含和`dbEncrypt`，則*lpszDestName*會具有與*lpszSrcName*相同的加密。 您可以使用 options 引數中的其中一個版本常數，為壓縮的資料庫指定資料格式的版本。 這個常數只會影響*lpszDestName*的資料格式版本。 您只能指定一個版本常數。 如果您省略版本常數， *lpszDestName*的版本會與*lpszSrcName*相同。 您只能將*lpszDestName*壓縮到與*lpszSrcName*相同或更晚的版本。

> [!CAUTION]
>  如果資料庫未加密，即使您執行使用者/密碼安全性，也可能會直接讀取構成資料庫的二進位磁片檔案。

### <a name="remarks"></a>備註

當您變更資料庫中的資料時，資料庫檔案可能會被分割，並使用比所需更多的磁碟空間。 您應該定期壓縮資料庫，以重組資料庫檔案。 壓縮的資料庫通常較小。 您也可以在複製並壓縮資料庫時，選擇變更排序次序、加密或資料格式的版本。

> [!CAUTION]
>  `CompactDatabase`成員函式不會將完整的 Microsoft Access 資料庫從某個版本正確轉換為另一個版本。 只會轉換資料格式。 Microsoft Access 定義的物件，例如表單和報表，則不會轉換。 不過，資料已正確轉換。

> [!TIP]
>  您也可以使用`CompactDatabase`來複製資料庫檔案。

如需有關壓縮資料庫的詳細資訊，請參閱 DAO 說明中的「壓縮方法」主題。

##  <a name="create"></a>CDaoWorkspace：： Create

呼叫這個成員函式來建立新的 DAO 工作區物件，並將它`CDaoWorkspace`與 MFC 物件產生關聯。

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
新工作區物件的密碼。 密碼長度最多可達14個字元，而且可以包含 ASCII 0 （null）以外的任何字元。 密碼會區分大小寫。 如需相關資訊，請參閱 DAO 說明中的「密碼屬性」主題。

### <a name="remarks"></a>備註

整體建立程式如下：

1. 建立[CDaoWorkspace](#cdaoworkspace)物件。

1. 呼叫物件的`Create`成員函式，以建立基礎 DAO 工作區。 您必須指定工作區名稱。

1. 如果您想要將工作區加入至 database engine 的工作區集合，請選擇性地呼叫[Append](#append) 。 您可以使用工作區，而不需要將它附加。

`Create`呼叫之後，工作區物件會處於開啟狀態，可供使用。 您不會在`Open`之後`Create`呼叫。 如果工作區已`Create`存在於工作區集合中，您就不會呼叫。 `Create`如果資料庫引擎尚未針對您的應用程式初始化，則將其初始化。

##  <a name="getdatabasecount"></a>CDaoWorkspace::GetDatabaseCount

呼叫這個成員函式，以取得工作區的資料庫集合中的 DAO 資料庫物件數目，也就是工作區中開啟的資料庫數目。

```
short GetDatabaseCount();
```

### <a name="return-value"></a>傳回值

工作區中開啟的資料庫數目。

### <a name="remarks"></a>備註

`GetDatabaseCount`如果您需要對工作區資料庫集合中所有已定義的資料庫執行迴圈，這會很有用。 若要取得集合中指定資料庫的相關資訊，請參閱[oomads.getdatabaseinfo](#getdatabaseinfo)。 一般使用方式是針對`GetDatabaseCount`開啟的資料庫數目呼叫，然後使用該數位做為重複`GetDatabaseInfo`呼叫的循環索引。

##  <a name="getdatabaseinfo"></a>CDaoWorkspace：： Oomads.getdatabaseinfo

呼叫這個成員函式可取得工作區中開啟之資料庫的各種相關資訊。

```
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
工作區資料庫集合中資料庫物件之以零為起始的索引，用於依索引查閱。

*dbinfo*<br/>
傳回所要求之資訊的[CDaoDatabaseInfo](../../mfc/reference/cdaodatabaseinfo-structure.md)物件參考。

*dwInfoOptions*<br/>
指定要抓取之資料庫相關資訊的選項。 這裡列出可用的選項，以及它們會導致函式傳回的內容：

- AFX_DAO_PRIMARY_INFO （預設）名稱、可更新、交易

- AFX_DAO_SECONDARY_INFO 主要資訊加上：版本、排序次序、查詢超時

- AFX_DAO_ALL_INFO 主要和次要資訊，加上：連線

*lpszName*<br/>
資料庫物件的名稱，用於依名稱查閱。 名稱是最多14個字元的字串，可唯一命名新的工作區物件。

### <a name="remarks"></a>備註

函數的其中一個版本可讓您依索引查閱資料庫。 另一個版本可讓您依名稱查閱資料庫。

如需*dbinfo*中所傳回信息的描述，請參閱[CDaoDatabaseInfo](../../mfc/reference/cdaodatabaseinfo-structure.md)結構。 此結構的成員會對應至*dwInfoOptions*的描述中所列的資訊專案。 當您要求某一層級的資訊時，您也會取得任何先前層級的資訊。

##  <a name="getinipath"></a>CDaoWorkspace::GetIniPath

呼叫這個成員函式，以取得 Microsoft Jet 資料庫引擎初始化設定在 Windows 登錄中的位置。

```
static CString PASCAL GetIniPath();
```

### <a name="return-value"></a>傳回值

包含登錄位置的[CString](../../atl-mfc-shared/reference/cstringt-class.md) 。

### <a name="remarks"></a>備註

您可以使用此位置取得資料庫引擎設定的相關資訊。 傳回的資訊實際上是登錄子機碼的名稱。

如需相關資訊，請參閱 DAO 說明中的「IniPath 屬性」和「自訂資料存取的 Windows 登錄設定」主題。

##  <a name="getisolateodbctrans"></a>CDaoWorkspace::GetIsolateODBCTrans

呼叫這個成員函式，以取得工作區的 DAO IsolateODBCTrans 屬性目前的值。

```
BOOL GetIsolateODBCTrans();
```

### <a name="return-value"></a>傳回值

如果 ODBC 交易已隔離，則為非零值;否則為0。

### <a name="remarks"></a>備註

在某些情況下，您可能需要在相同的 ODBC 資料庫上有多個同時擱置的交易。 若要這樣做，您必須為每個交易開啟個別的工作區。 請記住，雖然每個工作區可以有自己的 ODBC 連接至資料庫，但這會降低系統效能。 因為通常不需要交易隔離，所以依預設會共用來自相同使用者所開啟之多個工作區物件的 ODBC 連接。

某些 ODBC 伺服器（例如 Microsoft SQL Server）不允許在單一連接上同時進行交易。 如果您需要在一段時間內對這類資料庫有一個以上的交易，請在每個工作區上將 IsolateODBCTrans 屬性設定為 [TRUE]。 這會針對每個工作區強制使用個別的 ODBC 連接。

如需相關資訊，請參閱 DAO 說明中的「IsolateODBCTrans 屬性」主題。

##  <a name="getlogintimeout"></a>CDaoWorkspace：： GetLoginTimeout

呼叫這個成員函式，以取得工作區的 DAO LoginTimeout 屬性目前的值。

```
static short PASCAL GetLoginTimeout();
```

### <a name="return-value"></a>傳回值

當您嘗試登入 ODBC 資料庫時，發生錯誤之前的秒數。

### <a name="remarks"></a>備註

此值代表當您嘗試登入 ODBC 資料庫時，發生錯誤之前的秒數。 預設的 LoginTimeout 設定為20秒。 當 LoginTimeout 設定為0時，不會發生任何超時，而且與資料來源的通訊可能會停止回應。

當您嘗試登入 ODBC 資料庫（例如 Microsoft SQL Server）時，連接可能會因為網路錯誤或伺服器未執行而失敗。 您可以指定資料庫引擎在產生錯誤之前等待多久，而不是等待預設的20秒連接。 登入伺服器時，會以隱含的方式在一些不同的事件中進行，例如在外部伺服器資料庫上執行查詢。

如需相關資訊，請參閱 DAO 說明中的「LoginTimeout 屬性」主題。

##  <a name="getname"></a>CDaoWorkspace：： GetName

呼叫這個成員函式，以取得`CDaoWorkspace`物件基礎之 DAO 工作區物件的使用者定義名稱。

```
CString GetName();
```

### <a name="return-value"></a>傳回值

[CString](../../atl-mfc-shared/reference/cstringt-class.md) ，其中包含 DAO 工作區物件的使用者定義名稱。

### <a name="remarks"></a>備註

名稱適用于依名稱存取資料庫引擎之工作區集合中的 DAO 工作區物件。

如需相關資訊，請參閱 DAO 說明中的「名稱屬性」主題。

##  <a name="getusername"></a>CDaoWorkspace：： GetUserName

呼叫這個成員函式以取得工作區擁有者的名稱。

```
CString GetUserName();
```

### <a name="return-value"></a>傳回值

[CString](../../atl-mfc-shared/reference/cstringt-class.md) ，表示工作區物件的擁有者。

### <a name="remarks"></a>備註

若要取得或設定工作區擁有者的許可權，請直接呼叫 DAO 來檢查許可權屬性設定。這會決定使用者擁有的許可權。 若要使用許可權，您需要一個系統。MDA 檔案。

如需直接呼叫 DAO 的相關資訊，請參閱[技術附注 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。 如需相關資訊，請參閱 DAO 說明中的「使用者名稱屬性」主題。

##  <a name="getversion"></a>CDaoWorkspace：： GetVersion

呼叫這個成員函式，以判斷使用中的 Microsoft Jet 資料庫引擎版本。

```
static CString PASCAL GetVersion();
```

### <a name="return-value"></a>傳回值

[CString](../../atl-mfc-shared/reference/cstringt-class.md) ，表示與物件相關聯的資料庫引擎版本。

### <a name="remarks"></a>備註

傳回的值代表「主要. 次要」格式的版本號碼;例如，"3.0"。 產品版本號碼（例如3.0）包含版本號碼（3）、句點和版本號碼（0）。

如需相關資訊，請參閱 DAO 說明中的「版本屬性」主題。

##  <a name="getworkspacecount"></a>CDaoWorkspace::GetWorkspaceCount

呼叫這個成員函式，以抓取資料庫引擎的工作區集合中的 DAO 工作區物件數目。

```
short GetWorkspaceCount();
```

### <a name="return-value"></a>傳回值

工作區集合中開啟的工作區數目。

### <a name="remarks"></a>備註

此計數不包含任何未附加至集合的開啟工作區。 `GetWorkspaceCount`如果您需要對工作區集合中所有已定義的工作區執行迴圈，這會很有用。 若要取得集合中指定工作區的相關資訊，請參閱[GetWorkspaceInfo](#getworkspaceinfo)。 一般使用方式是針對`GetWorkspaceCount`開啟的工作區數目呼叫，然後使用該數位做為重複`GetWorkspaceInfo`呼叫的循環索引。

##  <a name="getworkspaceinfo"></a>CDaoWorkspace::GetWorkspaceInfo

呼叫這個成員函式，以取得在會話中開啟之工作區的各種相關資訊類型。

```
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
工作區集合中資料庫物件之以零為基底的索引，用於依索引查閱。

*wkspcinfo*<br/>
傳回所要求之資訊的[CDaoWorkspaceInfo](../../mfc/reference/cdaoworkspaceinfo-structure.md)物件參考。

*dwInfoOptions*<br/>
指定要抓取之工作區相關資訊的選項。 這裡列出可用的選項，以及它們會導致函式傳回的內容：

- AFX_DAO_PRIMARY_INFO （預設值）名稱

- AFX_DAO_SECONDARY_INFO 主要資訊加上：使用者名稱

- AFX_DAO_ALL_INFO 主要和次要資訊，加上：隔離 ODBCTrans

*lpszName*<br/>
工作區物件的名稱，用於依名稱查閱。 名稱是最多14個字元的字串，可唯一命名新的工作區物件。

### <a name="remarks"></a>備註

如需*wkspcinfo*中所傳回信息的描述，請參閱[CDaoWorkspaceInfo](../../mfc/reference/cdaoworkspaceinfo-structure.md)結構。 此結構的成員會對應至*dwInfoOptions*的描述中所列的資訊專案。 當您要求某一層級的資訊時，您也會取得先前層級的資訊。

##  <a name="idle"></a>CDaoWorkspace：： Idle

呼叫`Idle`以提供資料庫引擎，讓您有機會執行可能不是最新的背景工作，因為密集的資料處理。

```
static void PASCAL Idle(int nAction = dbFreeLocks);
```

### <a name="parameters"></a>參數

*nAction*<br/>
在閒置處理期間所要採取的動作。 目前唯一有效的動作是`dbFreeLocks`。

### <a name="remarks"></a>備註

這通常適用于多使用者、多工的環境，其中沒有足夠的背景處理時間可讓記錄集的所有記錄保持在最新的。

> [!NOTE]
>  使用`Idle` 3.0 版的 Microsoft Jet 資料庫引擎建立的資料庫不需要呼叫。 `Idle`僅用於使用舊版建立的資料庫。

通常會移除讀取鎖定，而且只有在沒有任何其他動作（包括滑鼠移動）發生時，才會更新本機動態集型別記錄集物件中的資料。 如果您定期呼叫`Idle`，您可以藉由釋放不必要的讀取鎖定，讓資料庫引擎有時間趕上背景處理工作。 `dbFreeLocks`將常數指定為引數會延遲處理，直到釋放所有讀取鎖定為止。

除非應用程式有多個實例正在執行，否則不需要在單一使用者環境中使用這個成員函式。 `Idle`成員函式可能會提高多使用者環境的效能，因為它會強制資料庫引擎將資料排清到磁片，釋放記憶體的鎖定。 您也可以藉由進行交易的作業部分來釋放讀取鎖定。

如需相關資訊，請參閱 DAO 說明中的「閒置方法」主題。

##  <a name="isopen"></a>CDaoWorkspace：： IsOpen

呼叫這個成員函式來判斷`CDaoWorkspace`物件是否已開啟，也就是，MFC 物件是否已由呼叫[open](#open)或[建立](#create)呼叫所初始化。

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>傳回值

如果工作區物件是開啟的，則為非零。否則為0。

### <a name="remarks"></a>備註

您可以呼叫處於開啟狀態之工作區的任何成員函式。

##  <a name="m_pdaoworkspace"></a>CDaoWorkspace::m_pDAOWorkspace

基礎 DAO 工作區物件的指標。

### <a name="remarks"></a>備註

如果您需要對基礎 DAO 物件的直接存取權，請使用此資料成員。 您可以透過這個指標呼叫 DAO 物件的介面。

如需直接存取 DAO 物件的相關資訊，請參閱[技術附注 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。

##  <a name="open"></a>CDaoWorkspace：： Open

明確開啟與 DAO 的預設工作區相關聯的工作區物件。

```
virtual void Open(LPCTSTR lpszName = NULL);
```

### <a name="parameters"></a>參數

*lpszName*<br/>
要開啟的 DAO 工作區物件名稱-最多14個字元的字串，可唯一命名工作區。 接受預設值 Null 以明確開啟預設工作區。 如需命名需求，請參閱[Create](#create)的*lpszName*參數。 如需相關資訊，請參閱 DAO 說明中的「名稱屬性」主題。

### <a name="remarks"></a>備註

在建立`CDaoWorkspace`物件之後，請呼叫此成員函式來執行下列其中一項動作：

- 明確開啟預設工作區。 針對*lpszName*傳遞 Null。

- 依名稱開啟`CDaoWorkspace`現有的物件，也就是工作區集合的成員。 為現有的工作區物件傳遞有效的名稱。

`Open`將工作區物件置於開啟狀態，而且如果資料庫引擎尚未針對您的應用程式初始化，也會將其初始化。

雖然在`CDaoWorkspace`開啟工作區之後，才可以呼叫許多成員函式，但下列成員函式（在資料庫引擎上運作）可在C++物件的結構之後，但在呼叫`Open`之前使用:

||||
|-|-|-|
|[建立](#create)|[GetVersion](#getversion)|[SetDefaultUser](#setdefaultuser)|
|[GetIniPath](#getinipath)|[忙](#idle)|[SetIniPath](#setinipath)|
|[GetLoginTimeout](#getlogintimeout)|[SetDefaultPassword](#setdefaultpassword)|[SetLoginTimeout](#setlogintimeout)|

##  <a name="repairdatabase"></a>CDaoWorkspace::RepairDatabase

如果您需要嘗試修復存取 Microsoft Jet 資料庫引擎的損毀資料庫，請呼叫這個成員函式。

```
static void PASCAL RepairDatabase(LPCTSTR lpszName);
```

### <a name="parameters"></a>參數

*lpszName*<br/>
現有 Microsoft Jet 引擎資料庫檔案的路徑和檔案名。 如果您省略路徑，則只會搜尋目前的目錄。 如果您的系統支援統一命名慣例（UNC），您也可以指定網路路徑，例如\\： "\\ \\ \\\MYSERVER\\\MYSHARE \MYDIR\\\MYDB。MDB」。 （路徑字串中需要兩個反斜線，因為\\"" 是C++ escape 字元）。

### <a name="remarks"></a>備註

您必須先關閉*lpszName*所指定的資料庫，才能修復它。 在多使用者環境中，其他使用者在修復時無法開啟*lpszName* 。 如果*lpszName*未關閉或無法供獨佔使用，則會發生錯誤。

此成員函式會嘗試修復未完成的寫入作業標示為可能已損毀的資料庫。 如果使用 Microsoft Jet database engine 的應用程式因為停電或電腦硬體問題而意外關閉，就可能發生這種情況。 如果您完成作業並呼叫[Close](../../mfc/reference/cdaodatabase-class.md#close)成員函式，或以一般方式結束應用程式，則資料庫將不會被標示為可能已損毀。

> [!NOTE]
>  修復資料庫之後，使用[壓縮](#compactdatabase)成員函式來壓縮檔案並復原磁碟空間，也是個不錯的主意。

如需修復資料庫的詳細資訊，請參閱 DAO 說明中的「RepairDatabase 方法」主題。

##  <a name="rollback"></a>CDaoWorkspace：： Rollback

呼叫此成員函式以結束目前的交易，並將工作區中的所有資料庫還原為其條件，然後才開始交易。

```
void Rollback();
```

### <a name="remarks"></a>備註

> [!CAUTION]
>  在一個工作區物件中，交易一律會全域用於工作區，而且不會僅限於一個資料庫或記錄集。 如果您在工作區交易中的多個資料庫或記錄集上執行`Rollback`作業，則會還原所有這些資料庫和記錄集上的所有作業。

如果您關閉工作區物件但未儲存或回復任何暫止的交易，則會自動回復交易。 如果您呼叫[CommitTrans](#committrans) ， `Rollback`或沒有第一次呼叫[BeginTrans](#begintrans)，就會發生錯誤。

> [!NOTE]
>  當您開始交易時，資料庫引擎會將其作業記錄在保存在工作站上 TEMP 環境變數所指定之目錄中的檔案中。 如果交易記錄檔耗盡暫存磁片磁碟機上的可用儲存體，則資料庫引擎會導致 MFC 擲`CDaoException`回（DAO 錯誤2004）。 此時，如果您呼叫`CommitTrans`，則會認可不確定的作業數目，但剩餘的未完成作業會遺失，而且必須重新開機此操作。 呼叫`Rollback`會釋放交易記錄檔，並復原交易中的所有作業。

##  <a name="setdefaultpassword"></a>CDaoWorkspace::SetDefaultPassword

呼叫這個成員函式可設定在建立工作區物件但沒有特定密碼時，資料庫引擎所使用的預設密碼。

```
static void PASCAL SetDefaultPassword(LPCTSTR lpszPassword);
```

### <a name="parameters"></a>參數

*lpszPassword*<br/>
預設密碼。 密碼長度最多可達14個字元，而且可以包含 ASCII 0 （null）以外的任何字元。 密碼會區分大小寫。

### <a name="remarks"></a>備註

您所設定的預設密碼會套用至您在呼叫之後所建立的新工作區。 當您建立後續的工作區時，您不需要在[建立](#create)呼叫中指定密碼。

若要使用這個成員函式：

1. 建立物件但不呼叫`Create`。 `CDaoWorkspace`

1. 如`SetDefaultPassword`有需要，請呼叫，並[SetDefaultUser](#setdefaultuser)。

1. 針對`Create`此工作區物件或後續的呼叫，而不指定密碼。

根據預設，DefaultUser 屬性會設定為 "admin"，而 DefaultPassword 屬性會設定為空字串（""）。

如需安全性的詳細資訊，請參閱 DAO 說明中的「許可權屬性」主題。 如需相關資訊，請參閱 DAO 說明中的「DefaultPassword 屬性」和「DefaultUser 屬性」主題。

##  <a name="setdefaultuser"></a>CDaoWorkspace::SetDefaultUser

呼叫這個成員函式可設定在建立工作區物件但沒有特定使用者名稱時，資料庫引擎所使用的預設使用者名稱。

```
static void PASCAL SetDefaultUser(LPCTSTR lpszDefaultUser);
```

### <a name="parameters"></a>參數

*lpszDefaultUser*<br/>
預設的使用者名稱。 使用者名稱的長度可以是 1-20 個字元，而且包含字母字元、重音字元、數位、空格和符號，但不包括： "（引號）、/（正斜線）、\ （反\[斜杠）、 \] （方括弧）、：（ &#124;冒號）、（pipe）、 \< （小於符號）、> （大於符號）、+ （加號）、= （等號）、、（分號）、、（逗號）、（問號）、 \* （星號）、前置空格和控制字元（ascii 00 到 ascii 31）。 如需相關資訊，請參閱 DAO 說明中的「使用者名稱屬性」主題。

### <a name="remarks"></a>備註

您設定的預設使用者名稱會套用至您在呼叫之後所建立的新工作區。 當您建立後續的工作區時，您不需要在[create](#create)呼叫中指定使用者名稱。

若要使用這個成員函式：

1. 建立物件但不呼叫`Create`。 `CDaoWorkspace`

1. 如`SetDefaultUser`有需要，請呼叫，並[SetDefaultPassword](#setdefaultpassword)。

1. 針對`Create`此工作區物件或後續的呼叫，而不指定使用者名稱。

根據預設，DefaultUser 屬性會設定為 "admin"，而 DefaultPassword 屬性會設定為空字串（""）。

如需相關資訊，請參閱 DAO 說明中的「DefaultUser 屬性」和「DefaultPassword 屬性」主題。

##  <a name="setinipath"></a>CDaoWorkspace::SetIniPath

呼叫這個成員函式可指定 Microsoft Jet database engine 的 Windows 登錄設定位置。

```
static void PASCAL SetIniPath(LPCTSTR lpszRegistrySubKey);
```

### <a name="parameters"></a>參數

*lpszRegistrySubkey*<br/>
包含 Windows 登錄子機碼名稱的字串，其為 Microsoft Jet 資料庫引擎設定的位置或可安裝之 ISAM 資料庫所需的參數。

### <a name="remarks"></a>備註

只有`SetIniPath`在您需要指定特殊設定時，才能呼叫。 如需詳細資訊，請參閱 DAO 說明中的「IniPath 屬性」主題。

> [!NOTE]
>  在`SetIniPath`應用程式安裝期間呼叫，而不是在應用程式執行時呼叫。 `SetIniPath`在您開啟任何工作區、資料庫或記錄集之前，必須先呼叫;否則，MFC 會擲回例外狀況。

您可以使用這個機制，以使用者提供的登錄設定來設定 database engine。 這個屬性的範圍僅限於您的應用程式，不需重新開機應用程式就能變更。

##  <a name="setisolateodbctrans"></a>CDaoWorkspace::SetIsolateODBCTrans

呼叫這個成員函式可設定工作區的 DAO IsolateODBCTrans 屬性值。

```
void SetIsolateODBCTrans(BOOL bIsolateODBCTrans);
```

### <a name="parameters"></a>參數

*bIsolateODBCTrans*<br/>
如果您想要開始隔離 ODBC 交易，請傳遞 TRUE。 如果您想要停止隔離 ODBC 交易，請傳遞 FALSE。

### <a name="remarks"></a>備註

在某些情況下，您可能需要在相同的 ODBC 資料庫上有多個同時擱置的交易。 若要這樣做，您必須為每個交易開啟個別的工作區。 雖然每個工作區可以有自己的 ODBC 連接至資料庫，但這會降低系統效能。 因為通常不需要交易隔離，所以依預設會共用來自相同使用者所開啟之多個工作區物件的 ODBC 連接。

某些 ODBC 伺服器（例如 Microsoft SQL Server）不允許在單一連接上同時進行交易。 如果您需要在一段時間內對這類資料庫有一個以上的交易，請在每個工作區上將 IsolateODBCTrans 屬性設定為 [TRUE]。 這會針對每個工作區強制使用個別的 ODBC 連接。

##  <a name="setlogintimeout"></a>CDaoWorkspace：： SetLoginTimeout

呼叫這個成員函式可設定工作區的 DAO LoginTimeout 屬性值。

```
static void PASCAL SetLoginTimeout(short nSeconds);
```

### <a name="parameters"></a>參數

*nSeconds*<br/>
當您嘗試登入 ODBC 資料庫時，發生錯誤之前的秒數。

### <a name="remarks"></a>備註

此值代表當您嘗試登入 ODBC 資料庫時，發生錯誤之前的秒數。 預設的 LoginTimeout 設定為20秒。 當 LoginTimeout 設定為0時，不會發生任何超時，而且與資料來源的通訊可能會停止回應。

當您嘗試登入 ODBC 資料庫（例如 Microsoft SQL Server）時，連接可能會因為網路錯誤或伺服器未執行而失敗。 您可以指定資料庫引擎在產生錯誤之前等待多久，而不是等待預設的20秒連接。 登入伺服器時，會以隱含方式做為許多不同事件的一部分，例如在外部伺服器資料庫上執行查詢。 Timeout 值是由 LoginTimeout 屬性的目前設定所決定。

如需相關資訊，請參閱 DAO 說明中的「LoginTimeout 屬性」主題。

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CDaoDatabase 類別](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoRecordset 類別](../../mfc/reference/cdaorecordset-class.md)<br/>
[CDaoTableDef 類別](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoQueryDef 類別](../../mfc/reference/cdaoquerydef-class.md)<br/>
[CDaoException 類別](../../mfc/reference/cdaoexception-class.md)
