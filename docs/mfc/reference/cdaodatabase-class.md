---
title: "CDaoDatabase 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- database classes [C++], DAO
- CDaoDatabase class, vs. CDatabase class
- CDaoDatabase class, and workspace
- CDaoDatabase class
- CDatabase class, vs. CDaoDatabase class
ms.assetid: 8ff5b342-964d-449d-bef1-d0ff56aadf6d
caps.latest.revision: 23
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: c173ea0c0132752c08504053d9b00cdec8d3f69b
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="cdaodatabase-class"></a>CDaoDatabase 類別
表示資料庫的連接，您可以透過這個連接來操作資料。  
  
## <a name="syntax"></a>語法  
  
```  
class CDaoDatabase : public CObject  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CDaoDatabase::CDaoDatabase](#cdaodatabase)|建構 `CDaoDatabase` 物件。 呼叫**開啟**來連接到資料庫的物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CDaoDatabase::CanTransact](#cantransact)|傳回非零，如果資料庫支援交易。|  
|[CDaoDatabase::CanUpdate](#canupdate)|傳回非零值如果`CDaoDatabase`是可更新的物件 （非唯讀狀態）。|  
|[CDaoDatabase::Close](#close)|關閉資料庫連接。|  
|[CDaoDatabase::Create](#create)|建立基本的 DAO 資料庫物件並初始化`CDaoDatabase`物件。|  
|[CDaoDatabase::CreateRelation](#createrelation)|在資料庫中定義新的資料表之間的關聯性。|  
|[CDaoDatabase::DeleteQueryDef](#deletequerydef)|刪除儲存在資料庫的 QueryDefs 集合 recordset 物件。|  
|[CDaoDatabase::DeleteRelation](#deleterelation)|刪除資料庫中資料表之間的現有關聯性。|  
|[CDaoDatabase::DeleteTableDef](#deletetabledef)|刪除資料庫中資料表的定義。 這會刪除實際的資料表和所有資料。|  
|[CDaoDatabase::Execute](#execute)|執行動作查詢。 呼叫**Execute**的查詢會傳回的結果就會擲回例外狀況。|  
|[CDaoDatabase::GetConnect](#getconnect)|傳回用來連接的連接字串`CDaoDatabase`資料庫物件。 使用 ODBC。|  
|[CDaoDatabase::GetName](#getname)|傳回目前使用中資料庫的名稱。|  
|[CDaoDatabase::GetQueryDefCount](#getquerydefcount)|傳回針對資料庫定義的查詢數目。|  
|[CDaoDatabase::GetQueryDefInfo](#getquerydefinfo)|傳回指定的查詢資料庫中定義的相關資訊。|  
|[CDaoDatabase::GetQueryTimeout](#getquerytimeout)|傳回的資料庫之後的秒數查詢作業會逾時。 會影響到所有後續開啟、 新增、 更新和編輯作業和 ODBC 資料來源上的其他作業，例如 （僅限） **Execute**呼叫。|  
|[CDaoDatabase::GetRecordsAffected](#getrecordsaffected)|傳回的記錄數目會受到最新的更新，編輯或加入作業或藉由呼叫**Execute**。|  
|[CDaoDatabase::GetRelationCount](#getrelationcount)|傳回資料庫中資料表之間定義關聯的數目。|  
|[CDaoDatabase::GetRelationInfo](#getrelationinfo)|傳回指定資料庫中資料表之間定義關聯性的相關資訊。|  
|[Cdaodatabase:: Gettabledefcount](#gettabledefcount)|傳回資料庫中定義的資料表數目。|  
|[Cdaodatabase:: Gettabledefinfo](#gettabledefinfo)|傳回資料庫中的指定資料表的相關資訊。|  
|[CDaoDatabase::GetVersion](#getversion)|傳回與資料庫相關聯的資料庫引擎版本。|  
|[CDaoDatabase::IsOpen](#isopen)|傳回非零值如果`CDaoDatabase`物件目前連接至資料庫。|  
|[CDaoDatabase::Open](#open)|建立資料庫的連接。|  
|[CDaoDatabase::SetQueryTimeout](#setquerytimeout)|設定資料庫之後的秒數查詢作業 （在 ODBC 資料來源只） 會逾時。 會影響到所有後續開啟、 新增、 更新和刪除作業。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CDaoDatabase::m_pDAODatabase](#m_pdaodatabase)|基礎的 DAO 資料庫物件的指標。|  
|[CDaoDatabase::m_pWorkspace](#m_pworkspace)|指標[CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)物件，包含資料庫，並定義其交易空間。|  
  
## <a name="remarks"></a>備註  
 如需支援的資料庫格式資訊，請參閱[GetName](../../mfc/reference/cdaoworkspace-class.md#getname)成員函式。 您可以有一或多個`CDaoDatabase`作用一次的物件，指定 「 工作區中，「 由[CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)物件。 工作區會維持開啟的資料庫物件，呼叫資料庫集合的集合。  
  
> [!NOTE]
>  MFC DAO 資料庫類別所 ODBC 為基礎之 MFC 資料庫類別不同。 所有的 DAO 資料庫類別名稱有"CDao"前置詞。 類別`CDaoDatabase`提供介面類似於 ODBC 類別的[CDatabase](../../mfc/reference/cdatabase-class.md)。 主要差異在於`CDatabase`透過開放式資料庫連接 (ODBC) 和 ODBC 驅動程式存取該 DBMS DBMS。 `CDaoDatabase`透過資料存取物件 (DAO) 為基礎的 Microsoft Jet 資料庫引擎會存取資料。 一般情況下，根據 DAO MFC 類別會更有能力比 ODBC; 架構的 MFC 類別DAO 架構類別可以存取資料，包括透過 ODBC 驅動程式，透過自己的資料庫引擎。 DAO 架構類別也支援資料定義語言 (DDL) 作業，例如加入資料表透過類別，而不需要直接呼叫 DAO。  
  
## <a name="usage"></a>使用方式  
 當您建立資料錄集物件時，您可以以隱含方式建立資料庫物件。 但是，您也可以明確建立資料庫物件。 若要使用現有的資料庫，明確地用`CDaoDatabase`，執行下列其中一項︰  
  
-   建構`CDaoDatabase`物件，將指標傳遞至已開啟的[CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)物件。  
  
-   建構或`CDaoDatabase`物件，而不指定工作區 （MFC 所建立的暫存工作區物件）。  
  
 若要建立新的 Microsoft Jet (。MDB) 資料庫，建構`CDaoDatabase`物件，然後呼叫其[建立](#create)成員函式。 請勿*不*呼叫**開啟**之後**建立**。  
  
 若要開啟現有的資料庫，建構`CDaoDatabase`物件，然後呼叫其[開啟](#open)成員函式。  
  
 任何這些技術將 DAO 資料庫物件附加至工作區的資料庫集合，並開啟資料連接。 當您然後建構[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)， [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)，或[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)物件來操作連接的資料庫，這些物件的建構函式將指標傳遞至您`CDaoDatabase`物件。 當您完成使用連接時，呼叫[關閉](#close)成員函式，並摧毀`CDaoDatabase`物件。 **關閉**關閉先前未關閉任何資料錄集。  
  
## <a name="transactions"></a>異動  
 資料庫交易處理會提供在工作區層級，請參閱[BeginTrans](../../mfc/reference/cdaoworkspace-class.md#begintrans)， [CommitTrans](../../mfc/reference/cdaoworkspace-class.md#committrans)，和[回復](../../mfc/reference/cdaoworkspace-class.md#rollback)類別成員函式`CDaoWorkspace`。  
  
## <a name="odbc-connections"></a>ODBC 連接  
 若要使用 ODBC 資料來源的建議的方式是將外部資料表連接至 Microsoft Jet (。MDB) 資料庫。  
  
## <a name="collections"></a>集合  
 每個資料庫維護它自己的 tabledef、 querydef、 資料錄集和物件關聯的集合。 類別`CDaoDatabase`提供成員函式來操作這些物件。  
  
> [!NOTE]
>  物件存 DAO，不在 MFC 資料庫物件。 MFC 提供 tabledef、 querydef，與資料錄集物件，但不適用於物件關聯的類別。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDaoDatabase`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxdao.h  
  
##  <a name="cantransact"></a>CDaoDatabase::CanTransact  
 呼叫此成員函式，來判斷資料庫是否允許交易。  
  
```  
BOOL CanTransact();
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果資料庫支援交易。否則為 0。  
  
### <a name="remarks"></a>備註  
 資料庫的工作區中，會管理交易。  
  
##  <a name="canupdate"></a>CDaoDatabase::CanUpdate  
 呼叫此成員函式，以判斷是否`CDaoDatabase`物件允許更新。  
  
```  
BOOL CanUpdate();
```  
  
### <a name="return-value"></a>傳回值  
 如果為非零`CDaoDatabase`物件可讓更新; 否則為 0，表示該您傳遞**TRUE**中`bReadOnly`當您開啟`CDaoDatabase`物件或資料庫本身是唯讀。 請參閱[開啟](#open)成員函式。  
  
### <a name="remarks"></a>備註  
 資料庫可更新性的相關資訊，請參閱主題 DAO 說明中的 「 可更新屬性 」。  
  
##  <a name="cdaodatabase"></a>CDaoDatabase::CDaoDatabase  
 建構 `CDaoDatabase` 物件。  
  
```  
CDaoDatabase(CDaoWorkspace* pWorkspace = NULL);
```  
  
### <a name="parameters"></a>參數  
 *pWorkspace*  
 指標`CDaoWorkspace`將包含新的資料庫物件的物件。 如果您接受預設值的**NULL**，建構函式會建立暫存`CDaoWorkspace`會使用預設 DAO 工作區的物件。 您可以取得透過 workspace 物件的指標[m_pWorkspace](#m_pworkspace)資料成員。  
  
### <a name="remarks"></a>備註  
 之後建構物件，如果您要建立新的 Microsoft Jet (。MDB) 資料庫，請呼叫物件的[建立](#create)成員函式。 如果您是，相反地，開啟現有的資料庫，呼叫物件的[開啟](#open)成員函式。  
  
 當您完成物件時，您應該呼叫其[關閉](#close)成員函式，然後損毀`CDaoDatabase`物件。  
  
 您可能會想要內嵌`CDaoDatabase`文件類別中的物件。  
  
> [!NOTE]
>  A`CDaoDatabase`物件也會建立隱含如果您開啟[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)物件，而不將指標傳遞至現有`CDaoDatabase`物件。 當您關閉資料錄集物件，此資料庫物件已關閉。  
  
##  <a name="close"></a>CDaoDatabase::Close  
 呼叫此成員函式，以中斷與資料庫並關閉任何開啟的資料錄集、 tabledefs 和資料庫相關聯的 querydefs。  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>備註  
 這些物件自行關閉之前呼叫此成員函式的最佳作法是它。 關閉`CDaoDatabase`物件它從集合中移除資料庫中相關聯[工作區](../../mfc/reference/cdaoworkspace-class.md)。 因為**關閉**不會終結`CDaoDatabase`物件時，您可以藉由開啟相同的資料庫或不同的資料庫來重複使用該物件。  
  
> [!CAUTION]
>  呼叫[更新](../../mfc/reference/cdaorecordset-class.md#update)成員函式 （如果有暫止的編輯） 和**關閉**之前關閉資料庫的所有開啟的資料錄集物件上的成員函式。 如果您結束宣告的函式[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)或`CDaoDatabase`物件在堆疊上，資料庫關閉後，任何未儲存的變更都會遺失，所有擱置的交易都會復原，而且任何暫止的編輯您的資料都會遺失。  
  
> [!CAUTION]
>  如果您嘗試開啟的任何資料錄集物件時，關閉資料庫物件，或您嘗試關閉工作區物件屬於該特定工作區的任何資料庫物件開啟時，將會關閉資料錄集物件和任何擱置中的更新或編輯將會回復。 如果您嘗試關閉工作區物件，它屬於任何資料庫物件開啟時，作業會關閉所有屬於該特定工作區物件，可能會導致正在關閉未封閉的資料錄集物件的資料庫物件。 如果您未關閉資料庫物件，MFC 會報告在偵錯組建中的發生判斷提示失敗。  
  
 如果資料庫物件定義函式的範圍之外，您不需關閉結束函式的資料庫物件會維持開啟，直到明確關閉或已定義的模組已超出範圍。  
  
##  <a name="create"></a>CDaoDatabase::Create  
 若要建立新的 Microsoft Jet (。MDB) 資料庫，請呼叫此成員函式之後您建構,`CDaoDatabase`物件。  
  
```  
virtual void Create(
    LPCTSTR lpszName,  
    LPCTSTR lpszLocale = dbLangGeneral,  
    int dwOptions = 0);
```  
  
### <a name="parameters"></a>參數  
 `lpszName`  
 字串運算式，這是您所建立的資料庫檔案的名稱。 它可以是完整路徑和檔名，例如"c:\\\MYDB。MDB 」。 您必須提供名稱。 如果您未提供檔案名稱副檔名。MDB 會附加。 如果您的網路支援的統一命名慣例 (UNC)，您也可以指定網路路徑，例如 「\\\\\\\MYSERVER\\\MYSHARE\\\MYDIR\\\MYDB 」。 只有 Microsoft Jet (。MDB) 資料庫檔案可以使用此成員函式來建立。 (字串常值中都需要兩個反斜線，因為 「\\」 是 c + + 逸出字元。)  
  
 `lpszLocale`  
 字串運算式，用來指定用於建立資料庫的定序順序。 預設值是**dbLangGeneral**。 可能的值為：  
  
- **dbLangGeneral**英文、 德文、 法文、 葡萄牙文、 義大利文、 和現代西班牙文  
  
- **dbLangArabic**阿拉伯文  
  
- **dbLangCyrillic**俄文  
  
- **dbLangCzech**捷克文  
  
- **dbLangDutch**荷蘭文  
  
- **dbLangGreek**希臘文  
  
- **dbLangHebrew**希伯來文  
  
- **dbLangHungarian**匈牙利文  
  
- **dbLangIcelandic**冰島文  
  
- **dbLangNordic**北歐語言 （Microsoft Jet 資料庫引擎版本 1.0 僅）  
  
- **dbLangNorwdan**挪威文和丹麥文  
  
- **dbLangPolish**波蘭文  
  
- **dbLangSpanish**西班牙文  
  
- **dbLangSwedfin**瑞典文和芬蘭文  
  
- **dbLangTurkish**土耳其文  
  
 `dwOptions`  
 整數，表示一或多個選項。 可能的值為：  
  
- **dbEncrypt**建立加密的資料庫。  
  
- **dbVersion10**與 Microsoft Jet 資料庫版本 1.0 建立的資料庫。  
  
- **dbVersion11** Microsoft Jet 資料庫 1.1 版中建立資料庫。  
  
- **dbVersion20**使用 Microsoft Jet 資料庫版本 2.0 建立資料庫。  
  
- **dbVersion30**與 Microsoft Jet 資料庫版本 3.0 建立的資料庫。  
  
 如果您省略加密常數時，會建立未加密的資料庫。 您可以指定只有一個版本的常數。 如果您省略版本常數時，會建立使用 Microsoft Jet 資料庫版本 3.0 的資料庫。  
  
> [!CAUTION]
>  如果未加密的資料庫，它可能的話，即使是實作直接讀取二進位磁碟檔案構成資料庫的使用者/密碼安全性。  
  
### <a name="remarks"></a>備註  
 **建立**建立資料庫檔案與基礎 DAO 資料庫物件並初始化 c + + 物件。 物件會附加至相關聯的工作區的資料庫集合。 資料庫物件是處於開啟狀態。請勿呼叫**開啟**之後**建立**。  
  
> [!NOTE]
>  使用**建立**，您可以建立只有 Microsoft Jet (。MDB) 資料庫。 您無法建立 ISAM 資料庫。  
  
##  <a name="createrelation"></a>CDaoDatabase::CreateRelation  
 呼叫此成員函式，來建立以資料庫中的主資料表中的一個或多個欄位和外部資料表 （在資料庫中的另一個資料表） 中的一或多個欄位之間的關聯。  
  
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
 `lpszName`  
 關聯性物件的唯一名稱。 名稱必須以字母開頭，並可以包含最多 40 個字元。 它可以包含數字和底線字元，但不能包含標點符號或空格。  
  
 `lpszTable`  
 關聯性中主資料表的名稱。 如果資料表不存在，MFC 會擲回例外狀況型別[CDaoException](../../mfc/reference/cdaoexception-class.md)。  
  
 `lpszForeignTable`  
 關聯性中的外部索引資料表名稱。 如果資料表不存在，MFC 會擲回例外狀況型別`CDaoException`。  
  
 `lAttributes`  
 Long 值，包含關聯性類型的相關資訊。 您可以使用此值，強制執行參考完整性，以及其他項目。 您可以使用位元 OR 運算子 ( **|**) 來結合下列值之一 （只要組合意義）︰  
  
- **dbRelationUnique**關聯性是一對一。  
  
- **dbRelationDontEnforce**關聯性不是強制執行 （沒有參考完整性）。  
  
- **dbRelationInherited**包含兩個連結的資料表的非資料庫中存在關聯性。  
  
- **dbRelationUpdateCascade**更新將會重疊顯示 （如需串聯，聯集的詳細資訊，請參閱 < 備註 >）。  
  
- **dbRelationDeleteCascade**會串聯刪除。  
  
 *lpszField*  
 以 null 終止的字串，包含主要資料表中的欄位名稱的指標 (名為`lpszTable`)。  
  
 *lpszForeignField*  
 以 null 終止的字串，包含外部索引資料表中的欄位名稱的指標 (名為`lpszForeignTable`)。  
  
 *relinfo*  
 參考[CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md)物件，其中包含您想要建立關係的詳細資訊。  
  
### <a name="remarks"></a>備註  
 關聯性不能包含查詢或附加的資料表從外部資料庫。  
  
 當關聯牽涉到兩個資料表中的一個欄位時，請使用第一個版本的函式。 當關聯牽涉到多個欄位時，請使用第二個版本。 在關聯中的欄位的數目上限為 14。  
  
 這個動作會建立基本的 DAO 關聯物件，但這是 MFC 實作細節，因為物件關聯的 MFC 的封裝包含在類別內`CDaoDatabase`。 MFC 未提供的關聯性的類別。  
  
 如果您設定此關聯性物件的屬性，以啟動 重疊顯示作業，資料庫引擎會自動更新或變更相關的主要索引鍵資料表時，會刪除一或多個其他資料表中的記錄。  
  
 例如，假設您建立串聯刪除 Customers 資料表和訂單資料表之間的關聯性。 當您從 [客戶] 資料表刪除記錄時，也會一併刪除與該客戶的 Orders 資料表中的記錄。 此外，如果您要建立 Orders 資料表與其他資料表之間的串聯刪除關聯性，這些資料表的資料會自動刪除您的客戶資料表中刪除記錄時。  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 CreateRelation 方法 」。  
  
##  <a name="deletequerydef"></a>CDaoDatabase::DeleteQueryDef  
 呼叫此成員函式刪除指定的 querydef — 儲存查詢 — 從`CDaoDatabase`物件的 QueryDefs 集合。  
  
```  
void DeleteQueryDef(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>參數  
 `lpszName`  
 若要刪除已儲存的查詢名稱。  
  
### <a name="remarks"></a>備註  
 之後，資料庫中不會再定義該查詢。  
  
 如需建立 recordset 物件的詳細資訊，請參閱類別[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)。 Recordset 物件產生關聯時具有特定`CDaoDatabase`物件在建構時`CDaoQueryDef`物件，它將指標傳遞到資料庫物件。  
  
##  <a name="deleterelation"></a>CDaoDatabase::DeleteRelation  
 呼叫此成員函式從資料庫物件的關聯性集合中刪除現有的關聯性。  
  
```  
void DeleteRelation(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>參數  
 `lpszName`  
 若要刪除關聯性的名稱。  
  
### <a name="remarks"></a>備註  
 之後，關聯性不存在。  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 刪除方法 」。  
  
##  <a name="deletetabledef"></a>CDaoDatabase::DeleteTableDef  
 呼叫此成員函式，若要刪除指定的資料表及其所有資料從`CDaoDatabase`物件的 TableDefs 集合。  
  
```  
void DeleteTableDef(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>參數  
 `lpszName`  
 若要刪除 tabledef 名稱。  
  
### <a name="remarks"></a>備註  
 之後，該資料表不會再定義資料庫中。  
  
> [!NOTE]
>  要非常小心，不要刪除系統資料表。  
  
 如需建立 tabledef 物件的詳細資訊，請參閱類別[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)。 Tabledef 物件產生關聯時具有特定`CDaoDatabase`物件在建構時`CDaoTableDef`物件，它將指標傳遞到資料庫物件。  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 刪除方法 」。  
  
##  <a name="execute"></a>CDaoDatabase::Execute  
 呼叫此成員函式來執行動作查詢，或在資料庫上執行 SQL 陳述式。  
  
```  
void Execute(
    LPCTSTR lpszSQL,  
    int nOptions = dbFailOnError);
```  
  
### <a name="parameters"></a>參數  
 `lpszSQL`  
 以 null 終止的字串，包含有效的 SQL 命令執行的指標。  
  
 `nOptions`  
 整數，指定查詢的完整性與相關選項。 您可以使用位元 OR 運算子 ( **|**) 來結合任何下列常數 (提供合理的組合 — 例如，您不想結合**dbInconsistent**與**dbConsistent**):  
  
- **dbDenyWrite**拒絕其他使用者寫入權限。  
  
- **dbInconsistent**不一致 （預設值） 的更新。  
  
- **dbConsistent**一致更新。  
  
- **dbSQLPassThrough** SQL 傳遞。 使 SQL 陳述式可傳遞至 ODBC 資料來源進行處理。  
  
- **dbFailOnError**發生錯誤時復原更新。  
  
- **dbSeeChanges**產生執行階段錯誤，另一位使用者會改變您正在編輯的資料。  
  
> [!NOTE]
>  如果兩個**dbInconsistent**和**dbConsistent**隨附或如果不包含在內，結果會是預設值。 如需這些常數的說明，請參閱主題 DAO 說明中的 「 執行方法 」。  
  
### <a name="remarks"></a>備註  
 **執行**僅適用於執行查詢或 SQL 傳遞查詢不會傳回結果。 它不適用於 select 查詢，傳回記錄。  
  
 如需定義和執行查詢的相關資訊，請參閱 「 動作查詢 」 和 「 執行方法 」 DAO 說明中的主題。  
  
> [!TIP]
>  在指定的語法正確的 SQL 陳述式和適當的權限， **Execute**成員函式不會導致失敗甚至如果不是可以修改或刪除單一資料列。 因此，一定要使用**dbFailOnError**選項使用時**Execute**成員函式來執行更新或刪除查詢。 這個選項會讓 MFC 擲回例外狀況型別[CDaoException](../../mfc/reference/cdaoexception-class.md)且會回復所有成功的變更，如果任何受影響的記錄都會被鎖定，無法更新或刪除。 請注意，您一律可以致電`GetRecordsAffected`查看影響的記錄數。  
  
 呼叫[GetRecordsAffected](#getrecordsaffected)決定受影響的最新的記錄數目的資料庫物件的成員函式**Execute**呼叫。 例如，`GetRecordsAffected`傳回的刪除、 更新或插入時執行動作查詢的記錄數目的相關資訊。 傳回的計數不會反映串聯更新或刪除時的相關資料表中的變更會生效。  
  
 **執行**不會傳回資料錄集。 使用**Execute**選取資料錄的查詢上會導致擲回例外狀況型別 MFC `CDaoException`。 (沒有任何`ExecuteSQL`成員函式類似於`CDatabase::ExecuteSQL`。)  
  
##  <a name="getconnect"></a>CDaoDatabase::GetConnect  
 呼叫此成員函式，來擷取連接字串，用來連接`CDaoDatabase`至 ODBC 或 ISAM 資料庫物件。  
  
```  
CString GetConnect();
```  
  
### <a name="return-value"></a>傳回值  
 連接字串，如果[開啟](#open)已順利在 ODBC 資料來源上呼叫，否則為空字串。 針對 Microsoft Jet (。MDB) 資料庫中，字串永遠是空除非您將搭配**dbSQLPassThrough**選項搭配[Execute](#execute)成員函式，或用於開啟資料錄集。  
  
### <a name="remarks"></a>備註  
 字串會提供開啟的資料庫或傳遞查詢所用的資料庫來源的相關資訊。 連接字串是由資料庫類型規範，並以分號分隔的零或多個參數所組成。  
  
> [!NOTE]
>  使用 MFC DAO 類別透過 ODBC 資料來源連接是比較沒有效率，比起透過附加的資料表。  
  
> [!NOTE]
>  連接字串用來將額外的資訊傳遞給 ODBC 和視特定 ISAM 驅動程式。 針對不使用它。MDB 的資料庫。 Microsoft Jet 資料庫基底資料表的連接字串是空字串 ("") 除了當您將它用於 SQL 的通過查詢傳回上述值之下所述。  
  
 請參閱[開啟](#open)成員函式，如需如何建立連接字串的說明。 一旦設定連接字串**開啟**呼叫時，您可以稍後使用它來檢查來判斷型別、 路徑、 資料庫的使用者識別碼、 密碼或 ODBC 資料來源的設定。  
  
##  <a name="getname"></a>CDaoDatabase::GetName  
 呼叫此成員函式，以擷取目前開啟的資料庫，這是現有的資料庫檔案名稱的名稱或已註冊的 ODBC 資料來源的名稱。  
  
```  
CString GetName();
```  
  
### <a name="return-value"></a>傳回值  
 完整路徑和檔案名稱的資料庫，如果登錄成功。否則，空[CString](../../atl-mfc-shared/reference/cstringt-class.md)。  
  
### <a name="remarks"></a>備註  
 如果您的網路支援的統一命名慣例 (UNC)，您也可以指定網路路徑，例如，"\\\\\\\MYSERVER\\\MYSHARE\\\MYDIR\\\MYDB。MDB 」。 (字串常值中都需要兩個反斜線，因為 「\\」 是 c + + 逸出字元。)  
  
 您可能，比方說，要在標題中顯示此名稱。 如果正在擷取名稱時發生錯誤，MFC 會擲回例外狀況型別[CDaoException](../../mfc/reference/cdaoexception-class.md)。  
  
> [!NOTE]
>  為了達到最佳效能時存取外部資料庫，我們建議您將在外部資料庫資料表連接至 Microsoft Jet 資料庫 (。MDB) 而不是直接連接到資料來源。  
  
 資料庫類型會以檔案或目錄路徑指向目標，如下所示︰  
  
|路徑名稱指向...|資料庫類型|  
|--------------------------|-------------------|  
|.MDB 檔|Microsoft Jet 資料庫 (Microsoft Access)|  
|包含的目錄。DBF 檔案|dBASE 資料庫|  
|包含的目錄。XLS 檔案|Microsoft Excel 資料庫|  
|包含的目錄。PDX 檔案|Paradox 資料庫|  
|包含適當格式化的文字資料庫檔案目錄|文字格式的資料庫|  
  
 例如 SQL Server 和 Oracle 的 ODBC 資料庫，資料庫的連接字串會識別已註冊的 ODBC 資料來源名稱 (DSN)。  
  
##  <a name="getquerydefcount"></a>CDaoDatabase::GetQueryDefCount  
 呼叫此成員函式擷取資料庫的 QueryDefs 集合中定義的查詢數目。  
  
```  
short GetQueryDefCount();
```  
  
### <a name="return-value"></a>傳回值  
 資料庫中定義的查詢數目。  
  
### <a name="remarks"></a>備註  
 `GetQueryDefCount`如果您要循環 QueryDefs 集合中的所有 querydefs，非常有用。 若要取得集合中指定查詢的相關資訊，請參閱[GetQueryDefInfo](#getquerydefinfo)。  
  
##  <a name="getquerydefinfo"></a>CDaoDatabase::GetQueryDefInfo  
 呼叫此成員函式，以取得不同的資料庫中定義的查詢的相關資訊。  
  
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
 `nIndex`  
 在資料庫的 QueryDefs 集合中，依索引查閱預先定義查詢的索引。  
  
 *querydefinfo*  
 參考[CDaoQueryDefInfo](../../mfc/reference/cdaoquerydefinfo-structure.md)物件，傳回要求的資訊。  
  
 `dwInfoOptions`  
 指定要擷取的資料錄集的相關資訊的選項。 此處列出可用的選項以及它們會導致函式傳回的相關資料錄集︰  
  
- `AFX_DAO_PRIMARY_INFO`（預設值）名稱、 類型  
  
- `AFX_DAO_SECONDARY_INFO`加上的主要資訊︰ 建立日期、 上次更新日期，傳回記錄、 可更新的  
  
- `AFX_DAO_ALL_INFO`主要和次要資訊加上︰ SQL、 連接，odbc 逾時  
  
 `lpszName`  
 字串，包含在資料庫中，依名稱查閱已定義的查詢名稱。  
  
### <a name="remarks"></a>備註  
 兩個版本的函式會提供資料庫的 QueryDefs 集合中的索引或查詢的名稱，您可以選取查詢。  
  
 如需在傳回的資訊說明*querydefinfo*，請參閱[CDaoQueryDefInfo](../../mfc/reference/cdaoquerydefinfo-structure.md)結構。 此結構具有成員資訊的描述中列出的項目所對應`dwInfoOptions`。 如果您要求一個層級的資訊，您會取得任何先前的層級的資訊。  
  
##  <a name="getquerytimeout"></a>CDaoDatabase::GetQueryTimeout  
 呼叫此成員函式擷取目前連接的資料庫上的後續作業的逾時前所允許的秒數。  
  
```  
short GetQueryTimeout();
```  
  
### <a name="return-value"></a>傳回值  
 短整數，包含以秒為單位的逾時值。  
  
### <a name="remarks"></a>備註  
 由於網路存取問題、 過多的查詢處理時間等作業可能會逾時。 設定生效時，它會影響所有開啟的、 新增、 更新和刪除作業與此相關聯的資料錄集`CDaoDatabase`物件。 您可以變更目前的逾時設定，藉由呼叫[SetQueryTimeout](#setquerytimeout)。 在開啟之後變更資料錄集的查詢逾時值不會變更資料錄集的值。 例如，後續[移動](../../mfc/reference/cdaorecordset-class.md#move)作業不會使用新的值。 資料庫引擎初始化時，初始設定的預設值。  
  
 查詢逾時的預設值是取自 Windows 登錄。 如果沒有登錄設定，預設值為 60 秒。 並非所有資料庫都支援設定查詢逾時值的能力。 如果您設定查詢逾時值為 0，就會發生不會逾時;與資料庫通訊可能會停止回應。 在開發期間，這種行為可能很有用的。 如果呼叫失敗，MFC 會擲回例外狀況型別[CDaoException](../../mfc/reference/cdaoexception-class.md)。  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 QueryTimeout 屬性 」。  
  
##  <a name="getrecordsaffected"></a>CDaoDatabase::GetRecordsAffected  
 呼叫此成員函式，來判斷受影響的呼叫最新的記錄數目[Execute](#execute)成員函式。  
  
```  
long GetRecordsAffected();
```  
  
### <a name="return-value"></a>傳回值  
 長整數，其中包含受影響的記錄數目。  
  
### <a name="remarks"></a>備註  
 傳回的值包括刪除、 更新或執行動作查詢所插入的記錄數目**Execute**。 傳回的計數不會反映串聯更新或刪除時的相關資料表中的變更會生效。  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 RecordsAffected 屬性 」。  
  
##  <a name="getrelationcount"></a>CDaoDatabase::GetRelationCount  
 呼叫此成員函式來取得資料庫中資料表之間定義關聯的編號。  
  
```  
short GetRelationCount();
```  
  
### <a name="return-value"></a>傳回值  
 定義資料庫中資料表之間的關聯性數目。  
  
### <a name="remarks"></a>備註  
 **GetRelationCount**如果您要循環使用中資料庫的關聯性集合的所有已定義關聯就很有用。 若要取得集合中的指定關聯性的相關資訊，請參閱[GetRelationInfo](#getrelationinfo)。  
  
 若要說明的關聯性的概念，請考慮供應商資料表和一個 Products 資料表，其中可能有一對多關聯性。 在這種關係，一家供應商可以提供多項產品。 其他關聯性是一對一和多對多。  
  
##  <a name="getrelationinfo"></a>CDaoDatabase::GetRelationInfo  
 呼叫此成員函式可取得指定的關聯資料庫的關聯性集合中的相關資訊。  
  
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
 `nIndex`  
 關聯性中的物件索引查閱資料庫的關聯性集合的索引。  
  
 *relinfo*  
 參考[CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md)物件，傳回要求的資訊。  
  
 `dwInfoOptions`  
 指定要擷取的關聯有關的資訊的選項。 此處列出可用的選項以及它們會導致函式傳回有關關聯性︰  
  
- `AFX_DAO_PRIMARY_INFO`（預設值）名稱、 資料表的外部資料表  
  
- `AFX_DAO_SECONDARY_INFO`欄位資訊的屬性  
  
 欄位資訊[CDaoRelationFieldInfo](../../mfc/reference/cdaorelationfieldinfo-structure.md)物件，其中包含參與關聯性的主資料表的欄位。  
  
 `lpszName`  
 字串，包含依名稱查閱關聯性物件的名稱。  
  
### <a name="remarks"></a>備註  
 此函式的兩個版本提供存取索引或名稱。 如需在傳回的資訊說明*relinfo*，請參閱[CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md)結構。 此結構具有成員資訊的描述中列出的項目所對應`dwInfoOptions`。 如果您要求一個層級的資訊，也會取得資訊以及任何先前的層級。  
  
> [!NOTE]
>  如果您設定關聯性啟用串聯作業物件的屬性 ( **dbRelationUpdateCascades**或**dbRelationDeleteCascades**)、 Microsoft Jet 資料庫引擎會自動更新或刪除記錄檔中其中一個或多個其他資料表時變更相關主索引鍵的資料表。 例如，假設您建立串聯刪除 Customers 資料表和訂單資料表之間的關聯性。 當您從 [客戶] 資料表刪除記錄時，也會一併刪除與該客戶的 Orders 資料表中的記錄。 此外，如果您要建立 Orders 資料表與其他資料表之間的串聯刪除關聯性，這些資料表的資料會自動刪除您的客戶資料表中刪除記錄時。  
  
##  <a name="gettabledefcount"></a>Cdaodatabase:: Gettabledefcount  
 呼叫此成員函式擷取的資料庫中定義的資料表數目。  
  
```  
short GetTableDefCount();
```  
  
### <a name="return-value"></a>傳回值  
 Tabledefs 資料庫中定義的數目。  
  
### <a name="remarks"></a>備註  
 `GetTableDefCount`如果您要循環使用資料庫的 TableDefs 集合中的所有 tabledefs，非常有用。 若要取得集合中指定資料表的相關資訊，請參閱[GetTableDefInfo](#gettabledefinfo)。  
  
##  <a name="gettabledefinfo"></a>Cdaodatabase:: Gettabledefinfo  
 呼叫此成員函式，以取得不同的資料庫中定義資料表的相關資訊。  
  
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
 `nIndex`  
 在資料庫的 TableDefs 集合中，依索引查閱 tabledef 物件的索引。  
  
 `tabledefinfo`  
 參考[CDaoTableDefInfo](../../mfc/reference/cdaotabledefinfo-structure.md)物件，傳回要求的資訊。  
  
 `dwInfoOptions`  
 指定要擷取資料表的相關資訊的選項。 此處列出可用的選項以及它們會導致函式傳回有關關聯性︰  
  
- `AFX_DAO_PRIMARY_INFO`（預設值）名稱、 可更新屬性  
  
- `AFX_DAO_SECONDARY_INFO`加上的主要資訊︰ 日期 Created、 上次更新日期，來源資料表名稱，連接  
  
- `AFX_DAO_ALL_INFO`主要和次要資訊加上︰ 驗證規則，驗證文字記錄計數  
  
 `lpszName`  
 依名稱查閱 tabledef 物件的名稱。  
  
### <a name="remarks"></a>備註  
 因此您可以選取資料表，資料庫的 TableDefs 集合中的索引或資料表的名稱不會提供兩個版本的函式。  
  
 如需在傳回的資訊說明`tabledefinfo`，請參閱[CDaoTableDefInfo](../../mfc/reference/cdaotabledefinfo-structure.md)結構。 此結構具有成員資訊的描述中列出的項目所對應`dwInfoOptions`。 如果您要求一個層級的資訊，您會取得任何先前的層資訊。  
  
> [!NOTE]
>  `AFX_DAO_ALL_INFO`選項提供可能會很慢，若要取得的資訊。 在此情況下，計算資料表中的記錄可能非常耗時如果有多筆記錄。  
  
##  <a name="getversion"></a>CDaoDatabase::GetVersion  
 呼叫此成員函式可判斷 Microsoft Jet 資料庫檔案的版本。  
  
```  
CString GetVersion();
```  
  
### <a name="return-value"></a>傳回值  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md) ，表示與物件相關聯的資料庫檔案的版本。  
  
### <a name="remarks"></a>備註  
 傳回的值代表 「 major.minor 」; 在表單中的版本號碼例如，「&3;.0 」。 產品版本號碼 (例如 3.0) 所組成的版本號碼 (3)、 句號和版次號碼 (0)。 至今的版本是 1.0、 1.1、 2.0 和 3.0。  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 版本屬性 」。  
  
##  <a name="isopen"></a>CDaoDatabase::IsOpen  
 呼叫此成員函式，以判斷是否`CDaoDatabase`物件是目前開啟的資料庫。  
  
```  
BOOL IsOpen() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果為非零`CDaoDatabase`物件是目前已開啟，否則為 0。  
  
### <a name="remarks"></a>備註  
  
##  <a name="m_pdaodatabase"></a>CDaoDatabase::m_pDAODatabase  
 包含 DAO 資料庫物件基礎的 OLE 介面的指標`CDaoDatabase`物件。  
  
### <a name="remarks"></a>備註  
 如果您需要直接存取 DAO 介面，請使用這個指標。  
  
 呼叫 DAO 的詳細資訊，請參閱[技術提示 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。  
  
##  <a name="m_pworkspace"></a>CDaoDatabase::m_pWorkspace  
 包含一個指向[CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)物件，其中包含資料庫物件。  
  
### <a name="remarks"></a>備註  
 如果您需要直接存取工作區，請使用這個指標 — 例如，若要取得工作區的資料庫集合中其他資料庫物件的指標。  
  
##  <a name="open"></a>CDaoDatabase::Open  
 您必須呼叫此成員函式，來初始化新建構`CDaoDatabase`表示現有的資料庫物件。  
  
```  
virtual void Open(
    LPCTSTR lpszName,  
    BOOL bExclusive = FALSE,  
    BOOL bReadOnly = FALSE,  
    LPCTSTR lpszConnect = _T(""));
```  
  
### <a name="parameters"></a>參數  
 `lpszName`  
 現有的 Microsoft Jet 名稱的字串運算式 (。MDB) 資料庫檔案。 如果檔名的副檔名，它是必要項目。 如果您的網路支援的統一命名慣例 (UNC)，您也可以指定網路路徑，例如 「\\\\\\\MYSERVER\\\MYSHARE\\\MYDIR\\\MYDB。MDB 」。 (字串常值中都需要兩個反斜線，因為 「\\」 是 c + + 逸出字元。)  
  
 適用一些考量事項時使用`lpszName`。 如果它︰  
  
-   參考資料庫已由其他使用者，MFC 擲回例外狀況類型的獨佔存取開啟[CDaoException](../../mfc/reference/cdaoexception-class.md)。 攔截該例外狀況，讓您知道資料庫是無法使用的使用者。  
  
-   為空字串 ("") 和*lpszConnect*是"ODBC;"，並顯示對話方塊，列出所有已註冊的 ODBC 資料來源名稱，因此使用者可以選取資料庫。 您應該避免直接連接至 ODBC 資料來源。請改用連結的資料表。  
  
-   否則未參考到現有的資料庫或有效的 ODBC 資料來源名稱，MFC 擲回例外狀況類型的`CDaoException`。  
  
> [!NOTE]
>  如需 DAO 錯誤碼的詳細資訊，請參閱 DAOERR。H 檔案。 如需相關資訊，請參閱 「 可截獲資料存取錯誤 」 DAO 說明中的主題。  
  
 `bExclusive`  
 布林值，是**TRUE**資料庫是否為獨佔 （非共用） 的存取權開啟和**FALSE**如果資料庫是要被開啟來共用存取。 如果您省略這個引數，資料庫被開啟的共用存取。  
  
 `bReadOnly`  
 布林值，是**TRUE**資料庫是否為唯讀存取開啟和**FALSE**如果資料庫是要被開啟來讀取/寫入存取。 如果您省略這個引數，資料庫的讀取/寫入存取權開啟。 所有相依的資料錄集繼承這個屬性。  
  
 `lpszConnect`  
 字串運算式，用來開啟資料庫。 此字串會構成 ODBC 連接引數。 您必須提供要提供來源字串的專有和唯讀引數。 如果資料庫是 Microsoft Jet 資料庫 (。MDB)，此字串是空的 ("")。 預設值的語法 — **_T**("")，Unicode 為 ANSI 可攜性建置的應用程式提供。  
  
### <a name="remarks"></a>備註  
 **開啟**基礎的 DAO 物件產生關聯的資料庫。 您無法建構資料錄集、 tabledef 或 querydef 物件初始化之前使用的資料庫物件。 **開啟**將資料庫物件附加至相關聯的工作區的資料庫集合。  
  
 使用參數，如下所示︰  
  
-   如果您開啟 Microsoft Jet (。MDB) 資料庫中，使用`lpszName`參數，並傳入為空字串的`lpszConnect`參數或傳遞格式的密碼字串";PWD = 密碼 「 如果資料庫有密碼保護 (。MDB 的資料庫只）。  
  
-   如果您開啟 ODBC 資料來源，則傳遞有效的 ODBC 連接字串中`lpszConnect`中的空字串和`lpszName`。  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 OpenDatabase 方法 」。  
  
> [!NOTE]
>  針對存取外部資料庫，包括 ISAM 資料庫和 ODBC 資料來源時，較佳的效能，建議您將在外部資料庫資料表連接至 Microsoft Jet 引擎資料庫 (。MDB) 而不是直接連接到資料來源。  
  
 就可以連線嘗試逾時的時候，比方說，DBMS 主機無法使用時。 如果連線嘗試失敗，**開啟**擲回例外狀況型別[CDaoException](../../mfc/reference/cdaoexception-class.md)。  
  
 其餘的註解只適用於 ODBC 資料庫︰  
  
 如果資料庫是 ODBC 資料庫和中的參數程式**開啟**呼叫未包含足夠的資訊來進行連接，ODBC 驅動程式會開啟對話方塊，以向使用者取得必要的資訊。 當您呼叫**開啟**，連接字串，`lpszConnect`私下儲存，可透過呼叫[GetConnect](#getconnect)成員函式。  
  
 如果您希望，您就可以開啟您自己的對話方塊中，才能呼叫**開啟**取得資訊的使用者，例如密碼，然後將該資訊 」 到連接字串傳遞給**開啟**。 或者您可能想要節省您傳遞 （也許是在 Windows 登錄中），您就可以重複使用它的下一步的連接字串的時間應用程式會呼叫**開啟**上`CDaoDatabase`物件。  
  
 您也可以使用的連接字串的多個層級的登入授權 (各適用於不同`CDaoDatabase`物件) 或傳遞特定資料庫的其他資訊。  
  
##  <a name="setquerytimeout"></a>CDaoDatabase::SetQueryTimeout  
 呼叫此成員函式，來覆寫預設連接的資料庫逾時的後續作業前允許的秒數。  
  
```  
void SetQueryTimeout(short nSeconds);
```  
  
### <a name="parameters"></a>參數  
 `nSeconds`  
 逾時可讓查詢嘗試之前的秒數。  
  
### <a name="remarks"></a>備註  
 由於網路存取問題、 過多的查詢處理時間等作業可能會逾時。 呼叫`SetQueryTimeout`開啟資料錄集之前或在呼叫資料錄集的前[AddNew](../../mfc/reference/cdaorecordset-class.md#addnew)，[更新](../../mfc/reference/cdaorecordset-class.md#update)，或[刪除](../../mfc/reference/cdaorecordset-class.md#delete)成員函式，如果您想要變更查詢逾時值。 此設定會影響所有後續[開啟](../../mfc/reference/cdaorecordset-class.md#open)， `AddNew`，**更新**，和**刪除**呼叫任何與此相關聯的資料錄集`CDaoDatabase`物件。 在開啟之後變更資料錄集的查詢逾時值不會變更資料錄集的值。 例如，後續[移動](../../mfc/reference/cdaorecordset-class.md#move)作業不會使用新的值。  
  
 查詢逾時的預設值為 60 秒。 並非所有資料庫都支援設定查詢逾時值的能力。 如果您設定查詢逾時值為 0，就會發生不會逾時;與資料庫之間的通訊可能會停止回應。 在開發期間，這種行為可能很有用的。  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 QueryTimeout 屬性 」。  
  
## <a name="see-also"></a>另請參閱  
 [CObject 類別](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CDaoWorkspace 類別](../../mfc/reference/cdaoworkspace-class.md)   
 [CDaoRecordset 類別](../../mfc/reference/cdaorecordset-class.md)   
 [CDaoTableDef 類別](../../mfc/reference/cdaotabledef-class.md)   
 [CDaoQueryDef 類別](../../mfc/reference/cdaoquerydef-class.md)   
 [CDatabase 類別](../../mfc/reference/cdatabase-class.md)   
 [CDaoException 類別](../../mfc/reference/cdaoexception-class.md)

