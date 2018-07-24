---
title: CDaoWorkspace 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7e6210f8c1b1fd1bd19efb74ca68c7a1bed3f7f1
ms.sourcegitcommit: 7eadb968405bcb92ffa505e3ad8ac73483e59685
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2018
ms.locfileid: "39209127"
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
|[CDaoWorkspace::CDaoWorkspace](#cdaoworkspace)|建構工作區的物件。 之後，呼叫`Create`或`Open`。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CDaoWorkspace::Append](#append)|將新建立的工作區附加至為資料庫引擎的工作區集合。|  
|[CDaoWorkspace::BeginTrans](#begintrans)|開始新交易，這會套用到所有資料庫開啟工作區中。|  
|[CDaoWorkspace::Close](#close)|關閉工作區和所有其包含的物件。 暫止的交易都會回復。|  
|[CDaoWorkspace::CommitTrans](#committrans)|完成目前的交易，並儲存變更。|  
|[CDaoWorkspace::CompactDatabase](#compactdatabase)|壓縮 （或重複項目） 的資料庫。|  
|[CDaoWorkspace::Create](#create)|建立新的 DAO workspace 物件。|  
|[CDaoWorkspace::GetDatabaseCount](#getdatabasecount)|工作區的資料庫集合中傳回 DAO 資料庫物件的數目。|  
|[CDaoWorkspace::GetDatabaseInfo](#getdatabaseinfo)|傳回指定的 DAO 資料庫工作區的資料庫集合中定義的相關資訊。|  
|[CDaoWorkspace::GetIniPath](#getinipath)|傳回引擎的初始化設定 Microsoft Jet 資料庫的位置，在 Windows 登錄中。|  
|[CDaoWorkspace::GetIsolateODBCTrans](#getisolateodbctrans)|傳回值，這個值，指出是否包含相同的 ODBC 資料來源的多個交易是透過隔離強制多個連接到資料來源。|  
|[CDaoWorkspace::GetLoginTimeout](#getlogintimeout)|傳回當使用者嘗試登入 ODBC 資料庫時，就會發生錯誤之前等候的秒數。|  
|[CDaoWorkspace::GetName](#getname)|傳回的工作區中物件的使用者定義名稱。|  
|[CDaoWorkspace::GetUserName](#getusername)|傳回的工作區建立時指定的使用者名稱。 這是工作區擁有者的名稱。|  
|[CDaoWorkspace::GetVersion](#getversion)|傳回字串，包含與工作區相關聯的 database engine 版本。|  
|[CDaoWorkspace::GetWorkspaceCount](#getworkspacecount)|資料庫引擎的工作區集合中傳回工作區的 DAO 物件的數目。|  
|[CDaoWorkspace::GetWorkspaceInfo](#getworkspaceinfo)|傳回指定資料庫引擎的工作區集合中定義的 DAO 工作區的相關資訊。|  
|[CDaoWorkspace::Idle](#idle)|可讓資料庫引擎執行的背景工作。|  
|[CDaoWorkspace::IsOpen](#isopen)|傳回非零值，如果工作區開啟。|  
|[CDaoWorkspace::Open](#open)|明確地開啟 DAO 的預設工作區相關聯的工作區物件。|  
|[CDaoWorkspace::RepairDatabase](#repairdatabase)|嘗試修復損毀的資料庫。|  
|[CDaoWorkspace::Rollback](#rollback)|結束目前的交易，並不會儲存所做的變更。|  
|[CDaoWorkspace::SetDefaultPassword](#setdefaultpassword)|設定 database engine 將使用工作區中建立物件時不需要特定密碼的密碼。|  
|[CDaoWorkspace::SetDefaultUser](#setdefaultuser)|設定工作區會建立一個物件而不需要特定的使用者名稱時，database engine 會使用使用者名稱。|  
|[CDaoWorkspace::SetIniPath](#setinipath)|設定引擎的初始化設定 Microsoft Jet 資料庫的位置，在 Windows 登錄中。|  
|[CDaoWorkspace::SetIsolateODBCTrans](#setisolateodbctrans)|指定是否包含相同的 ODBC 資料來源的多個交易上隔離的強制執行多個連接到資料來源。|  
|[CDaoWorkspace::SetLoginTimeout](#setlogintimeout)|設定當使用者嘗試登入 ODBC 資料來源時，就會發生錯誤之前等候的秒數。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CDaoWorkspace::m_pDAOWorkspace](#m_pdaoworkspace)|指向基礎 DAO workspace 物件。|  
  
## <a name="remarks"></a>備註  
 在大部分情況下，您不需要多個工作區，，和您不需要建立明確的工作區的物件;當您開啟的資料庫和資料錄集物件時，他們會使用 DAO 的預設工作區。 不過，如有需要您可以執行多個工作階段一次建立額外的工作區的物件。 工作區中的每個物件可以包含它自己的資料庫集合中的多個開啟的資料庫物件。 在 MFC 中，工作區是主要的交易管理員會指定一組開放的資料庫，全都在同一個 「 交易空間。 」  
  
> [!NOTE]
>  DAO 資料庫類別是開放式資料庫連接 (ODBC) 為基礎的 MFC 資料庫類別有所區別。 所有的 DAO 資料庫類別名稱有"CDao"前置詞。 一般情況下，根據 DAO MFC 類別是更有能力比 ODBC 為基礎的 MFC 類別。 DAO 類別會透過 Microsoft Jet 資料庫引擎，包括 ODBC 驅動程式存取資料。 它們也支援資料定義語言 (DDL) 作業，例如建立資料庫，以及在加入資料表和欄位透過類別，而不必直接呼叫 DAO。  
  
## <a name="capabilities"></a>功能  
 類別`CDaoWorkspace`提供下列：  
  
-   明確存取權，如有需要以建立初始化 database engine 的預設工作區。 通常您使用 DAO 的預設工作區以隱含方式建立資料庫和資料錄集物件。  
  
-   在工作區中，開啟交易套用至所有資料庫的交易空間。 您可以建立額外的工作區來管理個別的交易空間。  
  
-   為基礎的 Microsoft Jet 資料庫引擎的許多屬性的介面 （請參閱靜態成員函式）。 開啟或建立工作區，或呼叫靜態成員函式之前開啟或建立、 初始化 database engine。  
  
-   資料庫引擎的工作區集合，其中會儲存所有附加到它的作用中工作區的存取。 您也可以建立和使用工作區，而不將它們附加至集合。  
  
## <a name="security"></a>安全性  
 MFC DAO，用於安全性控制在未實作的使用者和群組的集合。 如果您需要的 DAO 層面時，您必須編寫它們自行透過直接呼叫 DAO 介面。 如需資訊，請參閱[技術提示 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。  
  
## <a name="usage"></a>使用量  
 您可以使用類別`CDaoWorkspace`來：  
  
-   明確地開啟預設工作區。  
  
     通常是隱含的預設工作區使用，當您開啟新[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)或是[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)物件。 但是您可能需要明確存取它，例如，若要存取資料庫引擎內容] 或 [工作區集合。 下面，請參閱 「 隱含使用預設工作區 」。  
  
-   建立新的工作區。 呼叫[Append](#append)如果您想要將它們新增至工作區集合。  
  
-   開啟現有的工作區的工作區集合中。  
  
 建立新的工作區不存在集合是底下所述的工作區中[建立](#create)成員函式。 工作區的物件不會以任何方式資料庫引擎的工作階段之間保存。 如果您的應用程式以靜態方式連結 MFC，結束應用程式未初始化 database engine。 如果您的應用程式以動態方式連結 mfc，MFC DLL 卸載時，資料庫引擎未初始化。  
  
 明確地開啟預設工作區中，或開啟現有的工作區中的工作區集合，描述於[開啟](#open)成員函式。  
  
 關閉工作區，以結束工作區的工作階段[關閉](#close)成員函式。 `Close` 關閉任何資料庫，您還沒有關閉之前，回復所有未認可的交易。  
  
## <a name="transactions"></a>異動  
 DAO 管理層級之交易的工作區;因此，在具有多個開啟的資料庫的工作區的交易套用至所有資料庫。 例如，如果這兩個資料庫有未認可的更新，而且您呼叫[CommitTrans](#committrans)，所有更新都已認可。 如果您想要限制到單一資料庫的交易，它需要個別的工作區物件。  
  
## <a name="implicit-use-of-the-default-workspace"></a>隱含使用預設工作區  
 MFC 使用 DAO 的預設工作區，在下列情況下，以隱含方式：  
  
-   如果您建立新`CDaoDatabase`物件，但未透過現有`CDaoWorkspace`物件，MFC 會建立暫存工作區的物件，其對應至 DAO 的預設工作區。 如果您這樣做，多個資料庫，所有資料庫物件都是預設工作區相關聯。 您可以存取資料庫的工作區，透過`CDaoDatabase`資料成員。  
  
-   同樣地，如果您建立`CDaoRecordset`物件，而不提供的指標`CDaoDatabase`物件，MFC 會建立暫存資料庫物件和延伸模組，暫存工作區的物件。 您可以透過存取資料錄集的資料庫，並間接其工作區中，`CDaoRecordset`資料成員。  
  
## <a name="other-operations"></a>其他作業  
 也提供其他資料庫作業，例如修復損毀的資料庫或壓縮的資料庫。  
  
 呼叫 DAO 直接以及 DAO 安全性的相關資訊，請參閱 <<c0> [ 技術提示 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDaoWorkspace`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxdao.h  
  
##  <a name="append"></a>  CDaoWorkspace::Append  
 呼叫此成員函式之後您呼叫,[建立](#create)。  
  
```  
virtual void Append();
```  
  
### <a name="remarks"></a>備註  
 `Append` 新建立的工作區將物件附加至為資料庫引擎的工作區集合。 工作區不會保存資料庫引擎的工作階段; 之間它們會儲存只在記憶體中，不在磁碟上。 您沒有附加工作區中;如果您不這樣做，您仍然可以使用它。  
  
 附加的工作區會保留在工作區集合中，在使用中，開啟的狀態，直到您呼叫其[關閉](#close)成員函式。  
  
 如需相關資訊，請參閱 DAO [說明] 中的 「 附加方法 」。  
  
##  <a name="begintrans"></a>  CDaoWorkspace::BeginTrans  
 呼叫此成員函式，為起始交易。  
  
```  
void BeginTrans();
```  
  
### <a name="remarks"></a>備註  
 在您呼叫後`BeginTrans`，您對您的資料庫或資料結構的更新會在認可交易時，才會生效。 工作區會定義單一的交易空間，因為交易適用於在工作區中所有開啟的資料庫。 有兩種方式可完成交易：  
  
-   呼叫[CommitTrans](#committrans)成員函式來認可交易，並將變更儲存至資料來源。  
  
-   或致電[Rollback](#rollback)成員函式，以取消交易。  
  
 關閉工作區物件或資料庫物件，交易暫止時復原所有暫止的交易。  
  
 如果您需要找出與另一個 ODBC 資料來源上的一個 ODBC 資料來源上的交易，請參閱[SetIsolateODBCTrans](#setisolateodbctrans)成員函式。  
  
##  <a name="cdaoworkspace"></a>  CDaoWorkspace::CDaoWorkspace  
 建構 `CDaoWorkspace` 物件。  
  
```  
CDaoWorkspace();
```  
  
### <a name="remarks"></a>備註  
 之後建構 c + + 物件，您會有兩個選項：  
  
-   呼叫物件的[開啟](#open)開啟預設工作區，或開啟現有的物件，在工作區集合中的成員函式。  
  
-   或呼叫物件的[建立](#create)來建立新的 DAO workspace 物件的成員函式。 此明確啟動新的工作區中工作階段，您可以透過參照`CDaoWorkspace`物件。 之後呼叫`Create`，您可以呼叫[附加](#append)如果您想要新增至資料庫引擎的工作區集合工作區。  
  
 請參閱適用於類別概觀[CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)如需當您需要明確建立`CDaoWorkspace`物件。 通常，您可以使用當您開啟時以隱含方式建立的工作區[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)物件，而不指定工作區，或當您開啟[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)物件，而不指定資料庫物件。 以此方式建立的 MFC DAO 物件使用 DAO 的預設工作區，這是建立一次，並重複使用。  
  
 若要釋放的工作區和其所包含的物件，呼叫 workspace 物件[關閉](#close)成員函式。  
  
##  <a name="close"></a>  CDaoWorkspace::Close  
 呼叫此成員函式來關閉工作區的物件。  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>備註  
 關閉開啟的工作區物件釋出基礎的 DAO 物件，如果工作區的工作區集合的成員從集合移除它。 呼叫`Close`是良好的程式設計作法。  
  
> [!CAUTION]
>  關閉工作區的物件會關閉任何開啟的資料庫，在工作區。 這會導致在資料庫中，關閉開啟的任何資料錄集，以及任何暫止的編輯或更新都會回復。 如需相關資訊，請參閱[CDaoDatabase::Close](../../mfc/reference/cdaodatabase-class.md#close)， [CDaoRecordset::Close](../../mfc/reference/cdaorecordset-class.md#close)， [CDaoTableDef::Close](../../mfc/reference/cdaotabledef-class.md#close)，和[CDaoQueryDef::Close](../../mfc/reference/cdaoquerydef-class.md#close)成員函式。  
  
 工作區的物件不是永久性;它們只存在於雖然對它們的參照存在。 這表示，資料庫引擎的工作階段結束時，工作區和它的資料庫集合不會保存。 您必須重新建立它們的下一個工作階段一次開啟您的工作區和資料庫。  
  
 如需相關資訊，請參閱 DAO [說明] 中的 「 關閉方法 」。  
  
##  <a name="committrans"></a>  CDaoWorkspace::CommitTrans  
 呼叫此成員函式認可的交易，儲存的編輯和更新的群組工作區中的一個或多個資料庫。  
  
```  
void CommitTrans();
```  
  
### <a name="remarks"></a>備註  
 交易包含變更資料庫的資料或它的結構，以呼叫為開頭的一系列[BeginTrans](#begintrans)。 當您完成交易時，請認可或回復它 （取消所做的變更） 與[Rollback](#rollback)。 根據預設，而不需要交易記錄的更新會認可立即。 呼叫`BeginTrans`會導致承諾的更新會延遲，直到您呼叫`CommitTrans`。  
  
> [!CAUTION]
>  在一個工作區中，交易都通用的工作區，並不限於只有一個資料庫或資料錄集。 如果您執行多個資料庫或交易內可以有工作區的資料錄集的作業`CommitTrans`所有擱置更新、 認可和`Rollback`還原這些資料庫和資料錄集的所有作業。  
  
 當您關閉資料庫或與工作區中暫止的交易時，交易是全部回復。  
  
> [!NOTE]
>  這不是兩階段交易認可機制。 如果一項更新無法認可，其他人仍將會認可。  
  
##  <a name="compactdatabase"></a>  CDaoWorkspace::CompactDatabase  
 呼叫此成員函式壓縮指定的 Microsoft Jet (。MDB) 資料庫。  
  
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
 *lpszSrcName*  
 將現有的名稱會關閉資料庫。 它可以是完整路徑和檔案名稱，例如"c:\\\MYDB。MDB"。 如果檔案名稱的副檔名，您必須指定它。 如果您的網路支援的統一命名慣例 (UNC)，您也可以指定網路路徑，例如"\\\\\\\MYSERVER\\\MYSHARE\\\MYDIR\\\MYDB。MDB"。 (因為路徑字串中需要兩個反斜線"\\」 是 c + + 逸出字元。)  
  
 *lpszDestName*  
 您要建立已壓縮的資料庫的完整路徑。 您也可以指定網路路徑做為與*lpszSrcName*。 您無法使用*lpszDestName*引數來指定相同的資料庫檔案*lpszSrcName*。  
  
 *lpszPassword*  
 這種密碼用於當您想要壓縮密碼保護的資料庫。 請注意，如果您使用新版`CompactDatabase`採用密碼，您必須提供所有的參數。 此外，因為這是連接參數，它需要特殊格式化，如下所示:;PWD = *lpszPassword*。 例如:;PWD = 「 高興 」。 （開頭分號是必要的）。  
  
 *lpszLocale*  
 字串運算式，用來指定定序建立的次序*lpszDestName*。 如果您省略這個引數所接受的預設值`dbLangGeneral`（參見下方），新資料庫的地區設定是舊的資料庫相同。 可能的值為：  
  
- `dbLangGeneral` 英文、 德文、 法文、 葡萄牙文、 義大利文、 和現代的西班牙文  
  
- `dbLangArabic` 阿拉伯文  
  
- `dbLangCyrillic` 俄文  
  
- `dbLangCzech` 捷克文  
  
- `dbLangDutch` 荷蘭文  
  
- `dbLangGreek` 希臘文  
  
- `dbLangHebrew` 希伯來文  
  
- `dbLangHungarian` 匈牙利文  
  
- `dbLangIcelandic` 冰島文  
  
- `dbLangNordic` 日耳曼語 （Microsoft Jet 資料庫引擎版本 1.0 僅）  
  
- `dbLangNorwdan` 挪威文和丹麥文  
  
- `dbLangPolish` 波蘭文  
  
- `dbLangSpanish` 西班牙文  
  
- `dbLangSwedfin` 瑞典文和芬蘭文  
  
- `dbLangTurkish` 土耳其文  
  
 *nOptions*  
 表示目標資料庫的一或多個選項*lpszDestName*。 如果您省略這個引數接受預設值*lpszDestName*將會有相同的加密和相同的版本*lpszSrcName*。 您可以結合`dbEncrypt`或`dbDecrypt`選項搭配使用的位元 OR 運算子的版本選項的其中一個。 可能的值，指定資料庫的格式，而非資料庫引擎版本，如下：  
  
- `dbEncrypt` 同時壓縮加密的資料庫。  
  
- `dbDecrypt` 解密時壓縮的資料庫。  
  
- `dbVersion10` 建立使用 Microsoft Jet 資料庫引擎版本 1.0 而壓縮的資料庫。  
  
- `dbVersion11` 建立使用 Microsoft Jet 資料庫引擎版本 1.1，同時壓縮的資料庫。  
  
- `dbVersion20` 建立使用 Microsoft Jet 資料庫引擎版本 2.0 時壓縮的資料庫。  
  
- `dbVersion30` 建立使用 Microsoft Jet 資料庫引擎版本 3.0 同時壓縮的資料庫。  
  
 您可以使用`dbEncrypt`或`dbDecrypt`選項引數，指定是否加密或解密資料庫，因為它會壓縮。 如果您省略加密常數，或如果您同時包含`dbDecrypt`並`dbEncrypt`， *lpszDestName*必須為相同的加密*lpszSrcName*。 您可以選項引數中使用其中一個版本的常數，指定已壓縮的資料庫的資料格式的版本。 這個常數會影響的資料格式的版本*lpszDestName*。 您可以指定只有一個版本的常數。 如果您省略版本常數*lpszDestName*會有相同的版本*lpszSrcName*。 您可以壓縮*lpszDestName*僅為相同的版本或更新版本，比*lpszSrcName*。  
  
> [!CAUTION]
>  如果未加密的資料庫，它是可行的即使您實作直接讀取二進位磁碟檔案構成資料庫的使用者/密碼安全性。  
  
### <a name="remarks"></a>備註  
 當您變更資料庫中的資料時，資料庫檔案可以變得分散，並使用不必要的更多磁碟空間。 定期，您應該壓縮資料庫，以重組資料庫檔案。 已壓縮的資料庫是通常比較小。 您也可以選擇變更定序順序、 加密或資料格式的版本，當您複製並壓縮資料庫。  
  
> [!CAUTION]
>  `CompactDatabase`成員函式不會正確地將轉換的完整的 Microsoft Access 資料庫從一個版本到另一個。 已轉換的資料格式。 Microsoft Access 定義物件，例如表單和報表，不會轉換。 不過，資料會正確地轉換。  
  
> [!TIP]
>  您也可以使用`CompactDatabase`複製資料庫檔案。  
  
 如需有關壓縮資料庫的詳細資訊，請參閱的 DAO [說明] 中的 「 壓縮資料庫方法 」。  
  
##  <a name="create"></a>  CDaoWorkspace::Create  
 呼叫此成員函式，來建立新的 DAO workspace 物件和其關聯的 MFC`CDaoWorkspace`物件。  
  
```  
virtual void Create(
    LPCTSTR lpszName,  
    LPCTSTR lpszUserName,  
    LPCTSTR lpszPassword);
```  
  
### <a name="parameters"></a>參數  
 *lpszName*  
 最多 14 個字元的字串可唯一地命名新的 workspace 物件。 您必須提供名稱。 如需相關資訊，請參閱 DAO [說明] 中的 「 名稱屬性 」。  
  
 *lpszUserName*  
 工作區的擁有者的使用者名稱。 如需需求，請參閱*lpszDefaultUser*參數來[SetDefaultUser](#setdefaultuser)成員函式。 如需相關資訊，請參閱 DAO [說明] 中的 「 使用者名稱屬性 」。  
  
 *lpszPassword*  
 新的 workspace 物件的密碼。 密碼長度最多 14 個字元，而且可以包含 ASCII 0 (null) 以外的任何字元。 密碼會區分大小寫。 如需相關資訊，請參閱 DAO [說明] 中的 「 密碼屬性 」。  
  
### <a name="remarks"></a>備註  
 整體的建立程序是：  
  
1.  建構[CDaoWorkspace](#cdaoworkspace)物件。  
  
2.  呼叫物件的`Create`成員函式來建立基礎的 DAO 工作區。 您必須指定工作區名稱。  
  
3.  選擇性地呼叫[Append](#append)如果您想要新增至資料庫引擎的工作區集合工作區。 您可以使用工作區，不會附加它。  
  
 之後`Create`呼叫時，工作區物件處於開啟狀態，可供使用。 您不能呼叫`Open`之後`Create`。 您不能呼叫`Create`如果已經存在的工作區集合中的工作區。 `Create` 初始化 database engine，如果它不已經初始化應用程式。  
  
##  <a name="getdatabasecount"></a>  CDaoWorkspace::GetDatabaseCount  
 呼叫此成員函式，來擷取工作區的資料庫集合中的 DAO 資料庫物件的數目 — 開啟工作區中的資料庫數目。  
  
```  
short GetDatabaseCount();
```  
  
### <a name="return-value"></a>傳回值  
 開啟工作區中的資料庫數目。  
  
### <a name="remarks"></a>備註  
 `GetDatabaseCount` 如果您要循環的工作區的資料庫集合中的所有已定義資料庫，非常有用。 若要取得集合中指定資料庫的相關資訊，請參閱[GetDatabaseInfo](#getdatabaseinfo)。 通常是用來呼叫`GetDatabaseCount`開啟的資料庫數目，然後使用該數字當做迴圈索引來重複呼叫`GetDatabaseInfo`。  
  
##  <a name="getdatabaseinfo"></a>  CDaoWorkspace::GetDatabaseInfo  
 呼叫此成員函式，以取得不同種類的工作區中，資料庫開啟的相關資訊。  
  
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
 *nIndex*  
 工作區的資料庫集合，依索引查閱中的資料庫物件之以零起始的索引。  
  
 *dbinfo*  
 參考[CDaoDatabaseInfo](../../mfc/reference/cdaodatabaseinfo-structure.md)傳回要求之資訊的物件。  
  
 *dwInfoOptions*  
 指定要擷取的資料庫相關資訊的選項。 以下列出可用的選項以及它們會導致此函數傳回：  
  
- AFX_DAO_PRIMARY_INFO （預設值） 的名稱，可更新的交易  
  
- AFX_DAO_SECONDARY_INFO 主要資訊加上： 版本、 定序順序，查詢逾時  
  
- AFX_DAO_ALL_INFO 主要和次要資料庫資訊加上： 連線  
  
 *lpszName*  
 依名稱查閱資料庫物件名稱。 最多 14 個字元字串，可唯一地命名新的 workspace 物件的名稱。  
  
### <a name="remarks"></a>備註  
 一個版本的函式可讓您依索引查閱資料庫。 另一個版本可讓您依名稱查閱資料庫。  
  
 如需在傳回的資訊的說明*dbinfo*，請參閱[CDaoDatabaseInfo](../../mfc/reference/cdaodatabaseinfo-structure.md)結構。 此結構具有上述描述中的資訊的項目所對應的成員*dwInfoOptions*。 當您要求一層級的資訊時，您會取得任何先前的層的資訊。  
  
##  <a name="getinipath"></a>  CDaoWorkspace::GetIniPath  
 呼叫此成員函式，以取得 Microsoft Jet 資料庫的位置引擎的 Windows 登錄中的初始化設定。  
  
```  
static CString PASCAL GetIniPath();
```  
  
### <a name="return-value"></a>傳回值  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md)包含的登錄位置。  
  
### <a name="remarks"></a>備註  
 您可以使用位置，以取得有關設定資料庫引擎的資訊。 傳回的資訊是實際的登錄子機碼名稱。  
  
 如需相關資訊，請參閱 「 IniPath 屬性 」 和 「 自訂 Windows 登錄設定的資料存取 」 DAO [說明] 中的主題。  
  
##  <a name="getisolateodbctrans"></a>  CDaoWorkspace::GetIsolateODBCTrans  
 呼叫此成員函式，以取得工作區的 DAO IsolateODBCTrans 屬性的目前值。  
  
```  
BOOL GetIsolateODBCTrans();
```  
  
### <a name="return-value"></a>傳回值  
 外掛式; ODBC 交易時，非零值。否則為 0。  
  
### <a name="remarks"></a>備註  
 在某些情況下，您可能需要在相同的 ODBC 資料庫上有多個同時交易暫止。 若要這樣做，您需要開啟個別的工作區中，每一筆交易。 請記住，雖然每個工作區可以有它自己的 ODBC 連接到資料庫，這會降低系統效能。 因為交易隔離通常不需要，從相同的使用者開啟多個工作區中物件的 ODBC 連接共用預設。  
  
 某些 ODBC 伺服器，例如 Microsoft SQL Server，不允許在單一連接上同時交易。 如果您需要有一個以上一次暫止對這類資料庫的交易，IsolateODBCTrans 屬性設為 TRUE 每個工作區，您將它開啟。 這會強制不同的 ODBC 連接，每個工作區。  
  
 如需相關資訊，請參閱 DAO [說明] 中的 < IsolateODBCTrans 屬性 >。  
  
##  <a name="getlogintimeout"></a>  CDaoWorkspace::GetLoginTimeout  
 呼叫此成員函式，以取得工作區的 DAO LoginTimeout 屬性的目前值。  
  
```  
static short PASCAL GetLoginTimeout();
```  
  
### <a name="return-value"></a>傳回值  
 當您嘗試登入 ODBC 資料庫時，就會發生錯誤之前的秒數。  
  
### <a name="remarks"></a>備註  
 這個值表示當您嘗試登入 ODBC 資料庫時，就會發生錯誤之前的秒數。 預設 LoginTimeout 值為 20 秒。 當 LoginTimeout 設定為 0 時，不會逾時，就會發生，並與資料來源之間的通訊可能會停止回應。  
  
 當您嘗試登入 ODBC 資料庫，例如 Microsoft SQL Server，連接可能會失敗，因為網路錯誤或因為伺服器未執行。 而非等候預設值 20 秒來連接，您可以指定它會產生錯誤之前，資料庫引擎的等候時間長度。 登入伺服器會以隱含的方式不同的事件，例如外部伺服器資料庫上執行查詢的數字部分。  
  
 如需相關資訊，請參閱 DAO [說明] 中的 < LoginTimeout 屬性 >。  
  
##  <a name="getname"></a>  CDaoWorkspace::GetName  
 呼叫此成員函式，以取得使用者定義的名稱，DAO 工作區物件基礎`CDaoWorkspace`物件。  
  
```  
CString GetName();
```  
  
### <a name="return-value"></a>傳回值  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md)包含 DAO workspace 物件的使用者定義名稱。  
  
### <a name="remarks"></a>備註  
 名稱可用於存取 DAO 工作區集合中的物件為資料庫引擎的工作區名稱。  
  
 如需相關資訊，請參閱 DAO [說明] 中的 「 名稱屬性 」。  
  
##  <a name="getusername"></a>  CDaoWorkspace::GetUserName  
 呼叫此成員函式，以取得工作區的擁有者的名稱。  
  
```  
CString GetUserName();
```  
  
### <a name="return-value"></a>傳回值  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md)表示 workspace 物件的擁有者。  
  
### <a name="remarks"></a>備註  
 若要取得或設定工作區擁有者的權限，呼叫 DAO，直接以檢查權限屬性設定;這會決定哪些權限使用者所具備。 若要使用的權限，您需要一個系統。MDA 檔案。  
  
 如需詳細資訊呼叫 DAO 直接[技術提示 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。 如需相關資訊，請參閱 DAO [說明] 中的 「 使用者名稱屬性 」。  
  
##  <a name="getversion"></a>  CDaoWorkspace::GetVersion  
 呼叫此成員函式，若要判斷使用中的 Microsoft Jet database engine 版本。  
  
```  
static CString PASCAL GetVersion();
```  
  
### <a name="return-value"></a>傳回值  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md) ，表示與物件相關聯的 database engine 版本。  
  
### <a name="remarks"></a>備註  
 傳回的值代表版本號碼，格式為"major.minor";例如，"3.0"。 產品版本號碼 (例如 3.0) 所組成的版本號碼 (3)、 句號和版次號碼 (0)。  
  
 如需相關資訊，請參閱 DAO [說明] 中的 「 版本屬性 」。  
  
##  <a name="getworkspacecount"></a>  CDaoWorkspace::GetWorkspaceCount  
 呼叫此成員函式可擷取的 DAO 資料庫引擎的工作區集合中的工作區中物件數目。  
  
```  
short GetWorkspaceCount();
```  
  
### <a name="return-value"></a>傳回值  
 開啟工作區集合中的工作區數目。  
  
### <a name="remarks"></a>備註  
 這個計數不包含任何開啟的工作區，不會附加至集合。 `GetWorkspaceCount` 如果您要循環的工作區集合中所有已定義的工作區，非常有用。 若要取得集合中指定的工作區的相關資訊，請參閱[GetWorkspaceInfo](#getworkspaceinfo)。 通常是用來呼叫`GetWorkspaceCount`開啟的工作區的數目，然後使用該數字當做迴圈索引來重複呼叫`GetWorkspaceInfo`。  
  
##  <a name="getworkspaceinfo"></a>  CDaoWorkspace::GetWorkspaceInfo  
 呼叫此成員函式，以取得不同種類的工作階段中，工作區中開啟的相關資訊。  
  
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
 *nIndex*  
 工作區集合中，依索引查閱中的資料庫物件之以零起始的索引。  
  
 *wkspcinfo*  
 參考[CDaoWorkspaceInfo](../../mfc/reference/cdaoworkspaceinfo-structure.md)傳回要求之資訊的物件。  
  
 *dwInfoOptions*  
 指定要擷取的工作區的相關資訊的選項。 以下列出可用的選項以及它們會導致此函數傳回：  
  
- AFX_DAO_PRIMARY_INFO （預設值） 的名稱  
  
- AFX_DAO_SECONDARY_INFO 主要資訊加上： 使用者名稱  
  
- AFX_DAO_ALL_INFO 主要和次要資料庫資訊加上： 隔離 ODBCTrans  
  
 *lpszName*  
 依名稱查閱工作區中物件的名稱。 最多 14 個字元字串，可唯一地命名新的 workspace 物件的名稱。  
  
### <a name="remarks"></a>備註  
 如需在傳回的資訊的說明*wkspcinfo*，請參閱[CDaoWorkspaceInfo](../../mfc/reference/cdaoworkspaceinfo-structure.md)結構。 此結構具有上述描述中的資訊的項目所對應的成員*dwInfoOptions*。 當您要求一層級的資訊時，您會取得先前的層級的資訊。  
  
##  <a name="idle"></a>  CDaoWorkspace::Idle  
 呼叫`Idle`提供資料庫引擎執行可能不是最新狀態因為密集的資料處理的背景工作的機會。  
  
```  
static void PASCAL Idle(int nAction = dbFreeLocks);
```  
  
### <a name="parameters"></a>參數  
 *4%n 動作*  
 要在閒置處理期間所採取的動作。 目前唯一有效的動作是`dbFreeLocks`。  
  
### <a name="remarks"></a>備註  
 這通常是在多使用者，在其中沒有足夠的背景處理時間，來保留目前資料錄集中的所有記錄的多工環境中，則為 true。  
  
> [!NOTE]
>  呼叫`Idle`並不需要與使用 Microsoft Jet 資料庫引擎的 3.0 版建立的資料庫。 使用`Idle`只針對使用舊版建立的資料庫。  
  
 通常，會移除鎖定的讀取和本機的動態類型資料錄集物件中的資料會更新 （包括移動滑鼠） 的任何其他動作不發生時，才。 如果您定期呼叫`Idle`，提供 database engine，旨在趕上上背景處理工作的方式釋出的時間不需要讀取鎖定。 指定`dbFreeLocks`做為引數的常數會延遲處理，直到會釋放所有的讀取的鎖定。  
  
 此成員函式不會需要在單一使用者環境中，除非應用程式的多個執行個體正在執行。 `Idle`成員函式可能會增加多使用者環境中的效能，因為它會強制 database engine，將資料排清至磁碟，釋放鎖定的記憶體。 您也可以藉由作業在交易期間釋放讀取的鎖定。  
  
 如需相關資訊，請參閱 DAO [說明] 中的 「 閒置方法 」。  
  
##  <a name="isopen"></a>  CDaoWorkspace::IsOpen  
 呼叫此成員函式，以判斷是否`CDaoWorkspace`物件已開啟，也就是是否 MFC 物件已初始化的呼叫所[開啟](#open)或呼叫[建立](#create)。  
  
```  
BOOL IsOpen() const;  
```  
  
### <a name="return-value"></a>傳回值  
 Workspace 物件已開啟; 如果為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 您可以呼叫任何成員函式的工作區中處於開啟狀態。  
  
##  <a name="m_pdaoworkspace"></a>  CDaoWorkspace::m_pDAOWorkspace  
 基礎的 DAO 工作區中物件的指標。  
  
### <a name="remarks"></a>備註  
 如果您需要直接存取基礎的 DAO 物件，請使用此資料成員。 您可以呼叫透過這個指標的 DAO 物件的介面。  
  
 如需直接存取的 DAO 物件的詳細資訊，請參閱 <<c0> [ 技術提示 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。  
  
##  <a name="open"></a>  CDaoWorkspace::Open  
 明確地開啟 DAO 的預設工作區相關聯的工作區物件。  
  
```  
virtual void Open(LPCTSTR lpszName = NULL);
```  
  
### <a name="parameters"></a>參數  
 *lpszName*  
 若要開啟 DAO 工作區中物件的名稱 — 的唯一名稱的工作區最多 14 個字元字串。 接受預設值 NULL 來明確地開啟 預設工作區。 命名需求，請參閱*lpszName*參數[建立](#create)。 如需相關資訊，請參閱 DAO [說明] 中的 「 名稱屬性 」。  
  
### <a name="remarks"></a>備註  
 之後建構`CDaoWorkspace`物件，請呼叫此成員函式，執行下列其中一項：  
  
-   明確地開啟預設工作區。 傳遞 NULL 做*lpszName*。  
  
-   開啟現有`CDaoWorkspace`物件、 工作區集合中，依名稱的成員。 傳遞現有的工作區中物件的有效名稱。  
  
 `Open` 工作區會將物件放到開啟狀態，也初始化 database engine，如果它不已經初始化應用程式。  
  
 雖然許多`CDaoWorkspace`後的 c + + 物件，但呼叫前建構成員函式只能呼叫，開啟工作區之後，下列成員函式，資料庫引擎上操作，就可以`Open`:  
  
||||  
|-|-|-|  
|[建立](#create)|[GetVersion](#getversion)|[SetDefaultUser](#setdefaultuser)|  
|[GetIniPath](#getinipath)|[閒置](#idle)|[SetIniPath](#setinipath)|  
|[GetLoginTimeout](#getlogintimeout)|[SetDefaultPassword](#setdefaultpassword)|[SetLoginTimeout](#setlogintimeout)|  
  
##  <a name="repairdatabase"></a>  CDaoWorkspace::RepairDatabase  
 如果您要嘗試修復損毀的資料庫存取 Microsoft Jet database engine，請呼叫此成員函式。  
  
```  
static void PASCAL RepairDatabase(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>參數  
 *lpszName*  
 路徑和檔案名稱指定為現有的 Microsoft Jet 引擎資料庫檔案。 如果您省略路徑，則會搜尋目前的目錄。 如果您的系統支援的統一命名慣例 (UNC)，您也可以指定網路路徑，例如:"\\\\\\\MYSERVER\\\MYSHARE\\\MYDIR\\\MYDB。MDB"。 (因為，將所需的路徑字串中的兩個反斜線"\\」 是 c + + 逸出字元。)  
  
### <a name="remarks"></a>備註  
 您必須先關閉所指定的資料庫*lpszName*修復它之前。 在多使用者環境中，不能有其他使用者*lpszName*開啟您要修復它時。 如果*lpszName*未關閉或無法使用獨佔使用，則會發生錯誤。  
  
 此成員函式會嘗試修復已標示為可能已經損毀的未完成的寫入作業的資料庫。 如果使用 Microsoft Jet 資料庫引擎的應用程式已意外關閉，因為發生電源中斷或電腦的硬體問題，也可能會發生。 如果您完成此作業，並且呼叫[關閉](../../mfc/reference/cdaodatabase-class.md#close)成員函式，或結束應用程式以一般方式，資料庫不會被標示為可能已經損毀。  
  
> [!NOTE]
>  修復資料庫之後, 它也是個不錯的主意，壓縮其使用[壓縮資料庫](#compactdatabase)重組的檔案，並復原磁碟空間的成員函式。  
  
 如需有關如何修復資料庫的詳細資訊，請參閱的 DAO [說明] 中的 「 RepairDatabase 方法 」。  
  
##  <a name="rollback"></a>  CDaoWorkspace::Rollback  
 呼叫此成員函式來結束目前的交易，並將工作區中的所有資料庫都還原到其條件中，交易已開始之前。  
  
```  
void Rollback();
```  
  
### <a name="remarks"></a>備註  
  
> [!CAUTION]
>  在一個工作區物件中，交易都通用的工作區，並不限於只有一個資料庫或資料錄集。 如果您執行多個資料庫或交易內可以有工作區的資料錄集的作業`Rollback`還原上的所有資料庫與資料錄集的所有作業。  
  
 如果您關閉工作區物件但不儲存，或回復任何暫止的交易時，會自動回復交易。 如果您呼叫[CommitTrans](#committrans)或是`Rollback`但是未先呼叫[BeginTrans](#begintrans)，就會發生錯誤。  
  
> [!NOTE]
>  當您開始交易時，database engine 會保留在 TEMP 環境變數，在工作站上所指定的目錄中的檔案中記錄其作業。 如果交易記錄檔用盡了您的暫存磁碟機上的可用儲存空間，database engine 將會導致擲回的 MFC `CDaoException` （DAO 錯誤 2004年）。 此時，如果您呼叫`CommitTrans`、 不定數目的作業已認可，但其餘未完成的作業都會遺失，且必須重新啟動作業。 呼叫`Rollback`釋放交易記錄檔，並回復在交易中所有的作業。  
  
##  <a name="setdefaultpassword"></a>  CDaoWorkspace::SetDefaultPassword  
 呼叫此成員函式，可以設定工作區會建立一個物件而不需要特定的密碼時，會使用 database engine 的預設密碼。  
  
```  
static void PASCAL SetDefaultPassword(LPCTSTR lpszPassword);
```  
  
### <a name="parameters"></a>參數  
 *lpszPassword*  
 預設的密碼。 密碼長度最多 14 個字元，而且可以包含 ASCII 0 (null) 以外的任何字元。 密碼會區分大小寫。  
  
### <a name="remarks"></a>備註  
 您所設定的預設密碼適用於您在呼叫後建立新的工作區。 當您建立後續的工作區時，您不需要指定密碼的[建立](#create)呼叫。  
  
 若要使用此成員函式：  
  
1.  建構`CDaoWorkspace`物件，但不要呼叫`Create`。  
  
2.  呼叫`SetDefaultPassword`而且，如果您想[SetDefaultUser](#setdefaultuser)。  
  
3.  呼叫`Create`針對此工作區物件或後續其他的而不指定密碼。  
  
 根據預設，DefaultUser 屬性設定為"admin"和 DefaultPassword 屬性設為空字串 ("")。  
  
 如需有關安全性的詳細資訊，請參閱 DAO [說明] 中的 < 權限屬性 >。 如需相關資訊，請參閱 「 DefaultPassword 屬性 」 和 「 DefaultUser 屬性 」，DAO [說明] 中的主題。  
  
##  <a name="setdefaultuser"></a>  CDaoWorkspace::SetDefaultUser  
 呼叫此成員函式，可以設定工作區會建立一個物件而不需要特定的使用者名稱時，會使用 database engine 的預設使用者名稱。  
  
```  
static void PASCAL SetDefaultUser(LPCTSTR lpszDefaultUser);
```  
  
### <a name="parameters"></a>參數  
 *lpszDefaultUser*  
 預設的使用者名稱。 使用者名稱可以是 1 到 20 個字元，並將包含字母字元、 重音的字元、 數字、 空格和符號，除了:"（引號） / （斜線），\\ （反斜線）， \[ \] （括號）: （冒號）， &#124; (管道）， \< (較少-符號)，> (大於-符號)、 + （加號）、 = （等於正負號），;（以分號），（逗號），（問號）， \* （星號），前置空格和控制字元 (ASCII 00 到 ASCII 31)。 如需相關資訊，請參閱 DAO [說明] 中的 「 使用者名稱屬性 」。  
  
### <a name="remarks"></a>備註  
 您所設定的預設使用者名稱適用於您在呼叫後建立新的工作區。 當您建立後續的工作區時，您不需要指定使用者名稱[建立](#create)呼叫。  
  
 若要使用此成員函式：  
  
1.  建構`CDaoWorkspace`物件，但不要呼叫`Create`。  
  
2.  呼叫`SetDefaultUser`而且，如果您想[SetDefaultPassword](#setdefaultpassword)。  
  
3.  呼叫`Create`針對此工作區物件或後續其他的而不指定使用者名稱。  
  
 根據預設，DefaultUser 屬性設定為"admin"和 DefaultPassword 屬性設為空字串 ("")。  
  
 如需相關資訊，請參閱 「 DefaultUser 屬性 」 和 「 DefaultPassword 屬性 」，DAO [說明] 中的主題。  
  
##  <a name="setinipath"></a>  CDaoWorkspace::SetIniPath  
 呼叫此成員函式來指定 Microsoft Jet 資料庫引擎的 Windows 登錄設定的位置。  
  
```  
static void PASCAL SetIniPath(LPCTSTR lpszRegistrySubKey);
```  
  
### <a name="parameters"></a>參數  
 *lpszRegistrySubkey*  
 字串，包含 Windows 登錄子機碼的 Microsoft Jet 資料庫引擎設定] 或 [可安裝 ISAM 資料庫所需的參數位置的名稱。  
  
### <a name="remarks"></a>備註  
 呼叫`SetIniPath`只有在必須指定特殊的設定。 如需詳細資訊，請參閱主題 DAO [說明] 中的 < IniPath 屬性 >。  
  
> [!NOTE]
>  呼叫`SetIniPath`應用程式在安裝期間，不應用程式執行時。 `SetIniPath` 您開啟任何工作區、 資料庫或資料錄集; 之前，必須呼叫否則，MFC 會擲回例外狀況。  
  
 若要以使用者提供的登錄設定來設定 database engine，您可以使用這項機制。 這個屬性的範圍僅限於您的應用程式，且無法變更不需要重新啟動您的應用程式。  
  
##  <a name="setisolateodbctrans"></a>  CDaoWorkspace::SetIsolateODBCTrans  
 呼叫此成員函式設定的工作區的 DAO IsolateODBCTrans 屬性值。  
  
```  
void SetIsolateODBCTrans(BOOL bIsolateODBCTrans);
```  
  
### <a name="parameters"></a>參數  
 *bIsolateODBCTrans*  
 如果您想要隔離 ODBC 交易，請傳遞 TRUE。 如果您想要停止隔離 ODBC 交易，請傳遞 FALSE。  
  
### <a name="remarks"></a>備註  
 在某些情況下，您可能需要在相同的 ODBC 資料庫上有多個同時交易暫止。 若要這樣做，您需要開啟個別的工作區中，每一筆交易。 雖然每個工作區可以有它自己的 ODBC 連接到資料庫，這會降低系統效能。 因為交易隔離通常不需要，從相同的使用者開啟多個工作區中物件的 ODBC 連接共用預設。  
  
 某些 ODBC 伺服器，例如 Microsoft SQL Server，不允許在單一連接上同時交易。 如果您需要有一個以上一次暫止對這類資料庫的交易，IsolateODBCTrans 屬性設為 TRUE 每個工作區，您將它開啟。 這會強制不同的 ODBC 連接，每個工作區。  
  
##  <a name="setlogintimeout"></a>  CDaoWorkspace::SetLoginTimeout  
 呼叫此成員函式設定的工作區的 DAO LoginTimeout 屬性值。  
  
```  
static void PASCAL SetLoginTimeout(short nSeconds);
```  
  
### <a name="parameters"></a>參數  
 *nSeconds*  
 當您嘗試登入 ODBC 資料庫時，就會發生錯誤之前的秒數。  
  
### <a name="remarks"></a>備註  
 這個值表示當您嘗試登入 ODBC 資料庫時，就會發生錯誤之前的秒數。 預設 LoginTimeout 值為 20 秒。 當 LoginTimeout 設定為 0 時，不會逾時，就會發生，並與資料來源之間的通訊可能會停止回應。  
  
 當您嘗試登入 ODBC 資料庫，例如 Microsoft SQL Server，連接可能會失敗，因為網路錯誤或因為伺服器未執行。 而非等候預設值 20 秒來連接，您可以指定它會產生錯誤之前，資料庫引擎的等候時間長度。 登入伺服器會以隱含的方式不同的事件，例如外部伺服器資料庫上執行查詢的數字部分。 逾時值取決於 LoginTimeout 屬性的目前設定。  
  
 如需相關資訊，請參閱 DAO [說明] 中的 < LoginTimeout 屬性 >。  
  
## <a name="see-also"></a>另請參閱  
 [CObject 類別](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CDaoDatabase 類別](../../mfc/reference/cdaodatabase-class.md)   
 [CDaoRecordset 類別](../../mfc/reference/cdaorecordset-class.md)   
 [CDaoTableDef 類別](../../mfc/reference/cdaotabledef-class.md)   
 [CDaoQueryDef 類別](../../mfc/reference/cdaoquerydef-class.md)   
 [CDaoException 類別](../../mfc/reference/cdaoexception-class.md)
