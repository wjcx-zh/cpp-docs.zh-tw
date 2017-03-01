---
title: "CDaoQueryDef 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDaoQueryDef
dev_langs:
- C++
helpviewer_keywords:
- QueryDef objects
- CDaoQueryDef class
- queries [Visual Studio], defining
ms.assetid: 9676a4a3-c712-44d4-8c5d-d1cc78288d3a
caps.latest.revision: 24
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
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 0bf06c68bb7072aa1907e4c730848cca9ff5e7d0
ms.lasthandoff: 02/24/2017

---
# <a name="cdaoquerydef-class"></a>CDaoQueryDef 類別
表示查詢定義 (或 "querydef")，通常是儲存在資料庫中的定義。  
  
## <a name="syntax"></a>語法  
  
```  
class CDaoQueryDef : public CObject  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CDaoQueryDef::CDaoQueryDef](#cdaoquerydef)|建構**CDaoQueryDef**物件。 接下來，呼叫**開啟**或**建立**，取決於您的需求。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CDaoQueryDef::Append](#append)|將 querydef 附加至已儲存的查詢資料庫的 QueryDefs 集合。|  
|[CDaoQueryDef::CanUpdate](#canupdate)|傳回非零，如果查詢可更新資料庫。|  
|[CDaoQueryDef::Close](#close)|關閉 recordset 物件。 當您完成時終結 c + + 物件。|  
|[CDaoQueryDef::Create](#create)|建立基本的 DAO recordset 物件。 做為暫時的查詢或呼叫 querydef**附加**將它儲存在資料庫中。|  
|[CDaoQueryDef::Execute](#execute)|執行 recordset 物件所定義的查詢。|  
|[CDaoQueryDef::GetConnect](#getconnect)|傳回 querydef 相關聯的連接字串。 此連接字串會識別資料來源。 （如 SQL 通過查詢，否則為空字串。）|  
|[CDaoQueryDef::GetDateCreated](#getdatecreated)|傳回已儲存的查詢建立的日期。|  
|[CDaoQueryDef::GetDateLastUpdated](#getdatelastupdated)|傳回已儲存的查詢上次更新的日期。|  
|[CDaoQueryDef::GetFieldCount](#getfieldcount)|傳回 querydef 所定義的欄位數目。|  
|[CDaoQueryDef::GetFieldInfo](#getfieldinfo)|傳回指定之欄位的查詢中所定義的相關資訊。|  
|[CDaoQueryDef::GetName](#getname)|傳回 querydef 名稱。|  
|[CDaoQueryDef::GetODBCTimeout](#getodbctimeout)|傳回由 ODBC （適用於 ODBC 的查詢） 的逾時值 querydef 執行時。 這會決定多久以便進行查詢的動作，才能完成。|  
|[CDaoQueryDef::GetParameterCount](#getparametercount)|傳回查詢所定義的參數數目。|  
|[CDaoQueryDef::GetParameterInfo](#getparameterinfo)|查詢會傳回指定之參數的相關資訊。|  
|[CDaoQueryDef::GetParamValue](#getparamvalue)|查詢會傳回指定之參數的值。|  
|[CDaoQueryDef::GetRecordsAffected](#getrecordsaffected)|傳回受影響的動作查詢的記錄數目。|  
|[CDaoQueryDef::GetReturnsRecords](#getreturnsrecords)|傳回非零，如果 querydef 所定義的查詢傳回的記錄。|  
|[CDaoQueryDef::GetSQL](#getsql)|傳回指定 querydef 所定義的查詢的 SQL 字串。|  
|[CDaoQueryDef::GetType](#gettype)|傳回的查詢類型︰ 刪除、 更新、 新增、 建立資料表等等。|  
|[CDaoQueryDef::IsOpen](#isopen)|如果 querydef 處於開啟狀態，可以執行，則會傳回非零值。|  
|[CDaoQueryDef::Open](#open)|開啟現有的 querydef 儲存在資料庫的 QueryDefs 集合。|  
|[CDaoQueryDef::SetConnect](#setconnect)|設定 ODBC 資料來源的 SQL 傳遞查詢的連接字串。|  
|[CDaoQueryDef::SetName](#setname)|設定已儲存的查詢，取代使用中的名稱建立 querydef 時的名稱。|  
|[CDaoQueryDef::SetODBCTimeout](#setodbctimeout)|設定用來透過 ODBC （ODBC 查詢） 的逾時值 querydef 執行時。|  
|[CDaoQueryDef::SetParamValue](#setparamvalue)|將指定之參數的值設定為查詢。|  
|[CDaoQueryDef::SetReturnsRecords](#setreturnsrecords)|指定是否 querydef 傳回記錄。 此屬性設定為**TRUE**是唯一有效的 SQL 傳遞查詢。|  
|[CDaoQueryDef::SetSQL](#setsql)|設定 SQL 字串，指定 querydef 所定義的查詢。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CDaoQueryDef::m_pDAOQueryDef](#m_pdaoquerydef)|基本的 DAO recordset 物件的 OLE 介面指標。|  
|[CDaoQueryDef::m_pDatabase](#m_pdatabase)|指標`CDaoDatabase`querydef 所關聯的物件。 Querydef 可能儲存在資料庫中。|  
  
## <a name="remarks"></a>備註  
 Querydef 是一種資料存取物件，其中包含 SQL 陳述式，描述查詢和其屬性，例如 「 建立日期 」 和 「 ODBC 逾時 」。 您也可以建立暫存的 recordset 物件，而不儲存，但可以很方便，且更有效率，來儲存經常重複使用的資料庫中的查詢。 A [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)物件會維護名為 QueryDefs 集合，包含其預存的 querydef 的集合。  
  
> [!NOTE]
>  DAO 資料庫類別所基礎開放式資料庫連接 (ODBC) 之 MFC 資料庫類別不同。 所有的 DAO 資料庫類別名稱有"CDao"前置詞。 您仍然可以使用 DAO 類別存取 ODBC 資料來源。 一般情況下，根據 DAO MFC 類別會更有能力比 ODBC; 架構的 MFC 類別DAO 架構類別可以存取資料，包括透過 ODBC 驅動程式，透過自己的資料庫引擎。 DAO 架構類別也支援資料定義語言 (DDL) 作業，例如加入資料表透過類別，而不需要直接呼叫 DAO。  
  
## <a name="usage"></a>使用方式  
 使用 recordset 物件可以是與現有的儲存查詢或建立新的儲存查詢或暫存的查詢︰  
  
1.  在所有情況下，第一次建構`CDaoQueryDef`物件，提供一個指向[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)查詢所屬的物件。  
  
2.  然後執行下列作業，按照您的需求︰  
  
    -   若要使用現有的儲存查詢，呼叫 recordset 物件的[開啟](#open)成員函式，提供的已儲存的查詢名稱。  
  
    -   若要建立新儲存的查詢，呼叫 recordset 物件的[建立](#create)成員函式，提供查詢的名稱。 然後呼叫[附加](#append)藉由附加資料庫的 QueryDefs 集合來儲存查詢。 **建立**querydef 放在開啟狀態，因此在呼叫**建立**沒有呼叫**開啟**。  
  
    -   若要建立暫存 querydef，呼叫**建立**。 傳送的查詢名稱為空字串。 請勿呼叫**附加**。  
  
 當您完成使用 recordset 物件時，呼叫其[關閉](#close)成員函式，然後損毀的 recordset 物件。  
  
> [!TIP]
>  建立已儲存的查詢最簡單的作法是建立它們，然後將它們儲存在使用 Microsoft Access 資料庫中。 然後您可以開啟，並在您的 MFC 程式碼中使用它們。  
  
## <a name="purposes"></a>用途  
 您可以使用 recordset 物件基於下列目的︰  
  
-   若要建立`CDaoRecordset`物件  
  
-   若要呼叫物件的**Execute**成員函式來直接執行動作查詢或 SQL 傳遞查詢  
  
 您可以使用 recordset 物件的任何類型的查詢，包括 select、 動作、 交叉分析、 刪除、 更新、 製成資料表、 資料定義、 SQL 傳遞、 union、 附加及大量查詢。 查詢的類型取決於您所提供的 SQL 陳述式的內容。 查詢類型的相關資訊，請參閱**Execute**和[GetType](#gettype)成員函式。 資料錄集通常用於傳回資料列的查詢，通常使用**選取...從**關鍵字。 **執行**最常用於大量作業。 如需詳細資訊，請參閱[Execute](#execute)和[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)。  
  
## <a name="querydefs-and-recordsets"></a>Querydefs 和資料錄集  
 若要使用 recordset 物件來建立`CDaoRecordset`物件，通常是建立或開啟 querydef 上面所述。 然後建構資料錄集物件，將指標傳遞到 recordset 物件，當您呼叫[cdaorecordset:: Open](../../mfc/reference/cdaorecordset-class.md#open)。 您傳遞 querydef 必須處於開啟狀態。 如需詳細資訊，請參閱類別[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)。  
  
 您無法使用 querydef 來建立資料錄集 （recordset 的最常見的使用），除非它是處於開啟狀態。 Querydef 進入開啟狀態，藉由呼叫**開啟**或**建立**。  
  
## <a name="external-databases"></a>外部資料庫  
 Recordset 物件是使用外部資料庫引擎的原生 SQL 方言的慣用的方式。 比方說，您可以建立 Transact SQL 查詢 （如 Microsoft SQL Server 上使用），並將它儲存在 querydef 物件。 當您需要使用不是根據 Microsoft Jet 資料庫引擎的 SQL 查詢時，您必須提供指向外部資料來源的連接字串。 具有有效的連接字串的查詢會略過資料庫引擎，並將查詢直接傳遞至外部資料庫伺服器以進行處理。  
  
> [!TIP]
>  使用 ODBC 資料表，最好是將它們連接至 Microsoft Jet (。MDB) 資料庫。  
  
 如需相關資訊，請參閱 「 Recordset 物件 」、 「 QueryDefs 集合 」 和 「 CdbDatabase 物件 」 DAO SDK 中的主題。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDaoQueryDef`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxdao.h  
  
##  <a name="a-nameappenda--cdaoquerydefappend"></a><a name="append"></a>CDaoQueryDef::Append  
 呼叫此成員函式之後您呼叫,[建立](#create)來建立新的 recordset 物件。  
  
```  
virtual void Append();
```  
  
### <a name="remarks"></a>備註  
 **附加**querydef 儲存在資料庫中，將物件附加到資料庫的 QueryDefs 集合。 您可以使用 querydef 為暫存物件不會附加，但如果您想要保存，您必須呼叫**附加**。  
  
 如果您嘗試新增暫存 recordset 物件，MFC 會擲回例外狀況型別[CDaoException](../../mfc/reference/cdaoexception-class.md)。  
  
##  <a name="a-namecanupdatea--cdaoquerydefcanupdate"></a><a name="canupdate"></a>CDaoQueryDef::CanUpdate  
 呼叫此成員函式，以判斷您是否可以修改 querydef — 例如，變更其名稱或 SQL 字串。  
  
```  
BOOL CanUpdate();
```  
  
### <a name="return-value"></a>傳回值  
 您可以修改 querydef; 如果為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 您可以修改 querydef 如果︰  
  
-   它不基礎資料庫已經開啟為唯讀。  
  
-   您有更新資料庫的權限。  
  
     這取決於您是否有實作安全性功能。 MFC 不提供支援的安全性。您必須實作它自己呼叫 DAO 直接或使用 Microsoft Access。 請參閱主題 DAO 說明中的 「 權限屬性 」。  
  
##  <a name="a-namecdaoquerydefa--cdaoquerydefcdaoquerydef"></a><a name="cdaoquerydef"></a>CDaoQueryDef::CDaoQueryDef  
 建構**CDaoQueryDef**物件。  
  
```  
CDaoQueryDef(CDaoDatabase* pDatabase);
```  
  
### <a name="parameters"></a>參數  
 `pDatabase`  
 開啟指標[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)物件。  
  
### <a name="remarks"></a>備註  
 物件可代表儲存在資料庫的 QueryDefs 集合、 新的查詢儲存在集合中或暫時查詢，不是要儲存現有 querydef。 接下來的步驟取決於 querydef 類型︰  
  
-   如果此物件代表現有的 querydef，呼叫物件的[開啟](#open)成員函式，將它初始化。  
  
-   如果此物件代表要儲存新 querydef，呼叫物件的[建立](#create)成員函式。 這會將物件加入資料庫的 QueryDefs 集合。 然後呼叫`CDaoQueryDef`成員函式來設定物件的屬性。 最後，呼叫[附加](#append)。  
  
-   如果此物件代表暫存 querydef （不儲存在資料庫中），呼叫**建立**，傳遞查詢的名稱為空字串。 在呼叫**建立**，初始化 querydef 藉由直接設定其屬性。 請勿呼叫**附加**。  
  
 若要設定 recordset 的屬性，您可以使用[SetName](#setname)， [SetSQL](#setsql)， [SetConnect](#setconnect)， [SetODBCTimeout](#setodbctimeout)，和[SetReturnsRecords](#setreturnsrecords)成員函式。  
  
 當您完成 recordset 物件時，呼叫其[關閉](#close)成員函式。 如果您有 querydef 的指標，使用**刪除**終結 c + + 物件的運算子。  
  
##  <a name="a-nameclosea--cdaoquerydefclose"></a><a name="close"></a>CDaoQueryDef::Close  
 當您完成使用 recordset 物件，請呼叫此成員函式。  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>備註  
 關閉 querydef 釋出基本的 DAO 物件但不會終結儲存的 DAO recordset 物件或 c + +`CDaoQueryDef`物件。 這不是相同[CDaoDatabase::DeleteQueryDef](../../mfc/reference/cdaodatabase-class.md#deletequerydef)，會刪除 querydef DAO （如果沒有暫存 querydef） 中的資料庫 QueryDefs 集合中。  
  
##  <a name="a-namecreatea--cdaoquerydefcreate"></a><a name="create"></a>CDaoQueryDef::Create  
 呼叫此成員函式，以建立新儲存的查詢或新的暫時查詢。  
  
```  
virtual void Create(
    LPCTSTR lpszName = NULL,  
    LPCTSTR lpszSQL = NULL);
```  
  
### <a name="parameters"></a>參數  
 `lpszName`  
 查詢資料庫中儲存唯一的名稱。 如需字串的詳細資訊，請參閱主題 DAO 說明中的 「 CreateQueryDef 方法 」。 如果您接受預設值為空字串，則會建立暫存 querydef。 這類查詢不會儲存在 QueryDefs 集合。  
  
 `lpszSQL`  
 定義查詢的 SQL 字串。 如果您接受預設值的**NULL**，您必須稍後呼叫[SetSQL](#setsql)設定字串。 在那之前，查詢是未定義。 但是，您可以使用未定義的查詢開啟資料錄集。如需詳細資訊，請參閱 < 備註 >。 您可以新增 querydef 至 QueryDefs 集合之前，必須定義 SQL 陳述式。  
  
### <a name="remarks"></a>備註  
 如果您傳遞的名稱`lpszName`，您就可以呼叫[附加](#append)querydef 儲存資料庫的 QueryDefs 集合中。 否則，該物件是暫存 querydef 並不會儲存。 在任一情況下，querydef 處於開啟狀態，而且您可以使用它來建立[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)物件或呼叫 querydef [Execute](#execute)成員函式。  
  
 如果您未提供的 SQL 陳述式`lpszSQL`，您無法執行與查詢**Execute**但您可以使用它來建立資料錄集。 在此情況下，MFC 會使用資料錄集的預設 SQL 陳述式。  
  
##  <a name="a-nameexecutea--cdaoquerydefexecute"></a><a name="execute"></a>CDaoQueryDef::Execute  
 呼叫此成員函式，以執行查詢的 recordset 物件所定義。  
  
```  
virtual void Execute(int nOptions = dbFailOnError);
```  
  
### <a name="parameters"></a>參數  
 `nOptions`  
 整數，會決定查詢的特性。 如需相關資訊，請參閱主題 DAO 說明中的 「 執行方法 」。 您可以使用位元 OR 運算子 ( **|**) 來結合這個引數的下列常數︰  
  
- **dbDenyWrite**拒絕其他使用者寫入權限。  
  
- **dbInconsistent**不一致的更新。  
  
- **dbConsistent**一致更新。  
  
- **dbSQLPassThrough** SQL 傳遞。 使 SQL 陳述式傳遞至 ODBC 資料庫處理。  
  
- **dbFailOnError**預設值。 回復更新發生錯誤和錯誤報告給使用者。  
  
- **dbSeeChanges**產生執行階段錯誤，另一位使用者會改變您正在編輯的資料。  
  
> [!NOTE]
>  詞彙的解釋為 「 不一致 」 和 「 一致 」，請參閱 DAO 說明中的 「 執行方法 」。  
  
### <a name="remarks"></a>備註  
 以這種方式執行時使用的 Recordset 物件只能代表下列查詢類型的其中一個︰  
  
-   執行查詢  
  
-   SQL 傳遞查詢  
  
 **執行**不適用於傳回記錄，例如 select 查詢的查詢。 **執行**常用於大量作業的查詢，例如**更新**，**插入**，或**SELECT INTO**，或資料定義語言 (DDL) 作業。  
  
> [!TIP]
>  若要使用 ODBC 資料來源的慣用的方法是將資料表連接至 Microsoft Jet (。MDB) 資料庫。 如需詳細資訊，請參閱主題 < 存取外部資料庫使用 DAO 「 DAO 說明中。  
  
 呼叫[GetRecordsAffected](#getrecordsaffected) recordset 物件來判斷受影響的最新的記錄數目的成員函式**Execute**呼叫。 例如，`GetRecordsAffected`傳回的刪除、 更新或插入時執行動作查詢的記錄數目的相關資訊。 傳回的計數不會反映串聯更新或刪除時的相關資料表中的變更會生效。  
  
 如果您同時包含**dbInconsistent**和**dbConsistent**或如果您包含兩者皆非，結果會是預設值， **dbInconsistent**。  
  
 **執行**不會傳回資料錄集。 使用**Execute**選取資料錄的查詢上會導致擲回例外狀況型別 MFC [CDaoException](../../mfc/reference/cdaoexception-class.md)。  
  
##  <a name="a-namegetconnecta--cdaoquerydefgetconnect"></a><a name="getconnect"></a>CDaoQueryDef::GetConnect  
 呼叫此成員函式可取得 querydef 的資料來源相關聯的連接字串。  
  
```  
CString GetConnect();
```  
  
### <a name="return-value"></a>傳回值  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md)包含 querydef 的連接字串。  
  
### <a name="remarks"></a>備註  
 此函數僅適用於 ODBC 資料來源和某些 ISAM 驅動程式。 它不使用 Microsoft Jet (。MDB) 資料庫;在此情況下，`GetConnect`會傳回空字串。 如需詳細資訊，請參閱[SetConnect](#setconnect)。  
  
> [!TIP]
>  使用 ODBC 資料表，最好是將連接它們。MDB 的資料庫。 如需詳細資訊，請參閱主題 < 存取外部資料庫使用 DAO 「 DAO 說明中。  
  
 如需連接字串資訊，請參閱主題 DAO 說明中的 「 連接屬性 」。  
  
##  <a name="a-namegetdatecreateda--cdaoquerydefgetdatecreated"></a><a name="getdatecreated"></a>CDaoQueryDef::GetDateCreated  
 呼叫此成員函式，以取得 recordset 物件的建立的日期。  
  
```  
COleDateTime GetDateCreated();
```  
  
### <a name="return-value"></a>傳回值  
 A [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)物件，其中包含的日期和時間 querydef 所建立。  
  
### <a name="remarks"></a>備註  
 如需相關資訊，請參閱 DAO 說明主題 「 DateCreated LastUpdated 屬性 」。  
  
##  <a name="a-namegetdatelastupdateda--cdaoquerydefgetdatelastupdated"></a><a name="getdatelastupdated"></a>CDaoQueryDef::GetDateLastUpdated  
 呼叫此成員函式，取得日期 recordset 物件上次更新 — 時的任何屬性已變更，例如其名稱、 其 SQL 字串或其連接字串。  
  
```  
COleDateTime GetDateLastUpdated();
```  
  
### <a name="return-value"></a>傳回值  
 A [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)物件，其中包含 querydef 上次更新的時間與日期。  
  
### <a name="remarks"></a>備註  
 如需相關資訊，請參閱 DAO 說明主題 「 DateCreated LastUpdated 屬性 」。  
  
##  <a name="a-namegetfieldcounta--cdaoquerydefgetfieldcount"></a><a name="getfieldcount"></a>CDaoQueryDef::GetFieldCount  
 呼叫此成員函式擷取查詢中的欄位數目。  
  
```  
short GetFieldCount();
```  
  
### <a name="return-value"></a>傳回值  
 在查詢中定義的欄位數目。  
  
### <a name="remarks"></a>備註  
 `GetFieldCount`可用於循環使用 querydef 中的所有欄位。 針對該目的，使用`GetFieldCount`搭配[GetFieldInfo](#getfieldinfo)。  
  
##  <a name="a-namegetfieldinfoa--cdaoquerydefgetfieldinfo"></a><a name="getfieldinfo"></a>CDaoQueryDef::GetFieldInfo  
 呼叫此成員函式，以取得各種 querydef 中定義欄位的相關資訊。  
  
```  
void GetFieldInfo(
    int nIndex,  
    CDaoFieldInfo& fieldinfo,  
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

 
void GetFieldInfo(
    LPCTSTR lpszName,  
    CDaoFieldInfo& fieldinfo,  
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 依索引查閱 querydef 欄位集合中所要的欄位以零為起始的索引。  
  
 `fieldinfo`  
 參考`CDaoFieldInfo`物件，傳回要求的資訊。  
  
 `dwInfoOptions`  
 指定要擷取之欄位的相關資訊的選項。 此處列出可用的選項以及它們會導致函式傳回︰  
  
- `AFX_DAO_PRIMARY_INFO`（預設值）屬性名稱、 類型、 大小  
  
- `AFX_DAO_SECONDARY_INFO`加上的主要資訊︰ 所需的序數位置、 允許長度為零、 來源欄位、 外部索引名稱、 來源資料表、 定序順序  
  
- `AFX_DAO_ALL_INFO`主要和次要資訊加上︰ 預設值，驗證文字驗證規則  
  
 `lpszName`  
 字串，包含依名稱查閱所需的欄位名稱。 您可以使用[CString](../../atl-mfc-shared/reference/cstringt-class.md)。  
  
### <a name="remarks"></a>備註  
 如需在傳回的資訊說明`fieldinfo`，請參閱[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)結構。 此結構有對應的描述性資訊底下的成員`dwInfoOptions`上方。 如果您要求一個層級的資訊，您會取得任何先前的層級的資訊。  
  
##  <a name="a-namegetnamea--cdaoquerydefgetname"></a><a name="getname"></a>CDaoQueryDef::GetName  
 呼叫此成員函式擷取 querydef 所表示的查詢名稱。  
  
```  
CString GetName();
```  
  
### <a name="return-value"></a>傳回值  
 查詢的名稱。  
  
### <a name="remarks"></a>備註  
 Querydef 名稱是唯一的使用者定義名稱。 如需 querydef 名稱的詳細資訊，請參閱主題 DAO 說明中的 「 名稱屬性 」。  
  
##  <a name="a-namegetodbctimeouta--cdaoquerydefgetodbctimeout"></a><a name="getodbctimeout"></a>CDaoQueryDef::GetODBCTimeout  
 呼叫此成員函式至 ODBC 資料來源的查詢逾時之前，擷取目前的時間限制。  
  
```  
short GetODBCTimeout();
```  
  
### <a name="return-value"></a>傳回值  
 逾時之前查詢的秒數。  
  
### <a name="remarks"></a>備註  
 此時間限制的相關資訊，請參閱主題 DAO 說明中的 「 odbc 逾時屬性 」。  
  
> [!TIP]
>  使用 ODBC 資料表，最好是將它們連接至 Microsoft Jet (。MDB) 資料庫。 如需詳細資訊，請參閱主題 < 存取外部資料庫使用 DAO 「 DAO 說明中。  
  
##  <a name="a-namegetparametercounta--cdaoquerydefgetparametercount"></a><a name="getparametercount"></a>CDaoQueryDef::GetParameterCount  
 呼叫此成員函式擷取已儲存的查詢中的參數數目。  
  
```  
short GetParameterCount();
```  
  
### <a name="return-value"></a>傳回值  
 在查詢中定義的參數數目。  
  
### <a name="remarks"></a>備註  
 `GetParameterCount`可用於循環使用 querydef 中的所有參數。 針對該目的，使用`GetParameterCount`搭配[GetParameterInfo](#getparameterinfo)。  
  
 如需相關資訊，請參閱 「 參數物件 」、 「 參數集合 」 和 「 參數宣告 (SQL) 」 DAO 說明中的主題。  
  
##  <a name="a-namegetparameterinfoa--cdaoquerydefgetparameterinfo"></a><a name="getparameterinfo"></a>CDaoQueryDef::GetParameterInfo  
 呼叫此成員函式可取得 querydef 中定義之參數的相關資訊。  
  
```  
void GetParameterInfo(
    int nIndex,  
    CDaoParameterInfo& paraminfo,  
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

 
void GetParameterInfo(
    LPCTSTR lpszName,  
    CDaoParameterInfo& paraminfo,  
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 在 querydef 參數集合中，依索引查閱所需的參數以零為起始的索引。  
  
 `paraminfo`  
 參考[CDaoParameterInfo](../../mfc/reference/cdaoparameterinfo-structure.md)物件，傳回要求的資訊。  
  
 `dwInfoOptions`  
 指定要擷取之參數的相關資訊的選項。 可用的選項為以及它會導致函式傳回此處所列︰  
  
- `AFX_DAO_PRIMARY_INFO`（預設值）名稱、 類型  
  
 `lpszName`  
 字串，包含依名稱查閱所需的參數名稱。 您可以使用[CString](../../atl-mfc-shared/reference/cstringt-class.md)。  
  
### <a name="remarks"></a>備註  
 如需在傳回的資訊說明`paraminfo`，請參閱[CDaoParameterInfo](../../mfc/reference/cdaoparameterinfo-structure.md)結構。 此結構有對應的描述性資訊底下的成員`dwInfoOptions`上方。  
  
 如需相關資訊，請參閱 「 參數宣告 (SQL) 」 DAO 說明中的主題。  
  
##  <a name="a-namegetparamvaluea--cdaoquerydefgetparamvalue"></a><a name="getparamvalue"></a>CDaoQueryDef::GetParamValue  
 呼叫此成員函式擷取儲存 querydef 參數集合中的指定參數的目前值。  
  
```  
virtual COleVariant GetParamValue(LPCTSTR lpszName);  
virtual COleVariant GetParamValue(int nIndex);
```  
  
### <a name="parameters"></a>參數  
 `lpszName`  
 您想依名稱查閱其值的參數名稱。  
  
 `nIndex`  
 依索引查閱 querydef 參數集合中的參數以零為起始的索引。 您可以取得這個值與呼叫[GetParameterCount](#getparametercount)和[GetParameterInfo](#getparameterinfo)。  
  
### <a name="return-value"></a>傳回值  
 類別的物件[COleVariant](../../mfc/reference/colevariant-class.md) ，其中包含參數的值。  
  
### <a name="remarks"></a>備註  
 您可以依名稱或其集合中的序數位置來存取參數。  
  
 如需相關資訊，請參閱 「 參數宣告 (SQL) 」 DAO 說明中的主題。  
  
##  <a name="a-namegetrecordsaffecteda--cdaoquerydefgetrecordsaffected"></a><a name="getrecordsaffected"></a>CDaoQueryDef::GetRecordsAffected  
 呼叫此成員函式，來判斷多少筆記錄的最後一個呼叫所影響[Execute](#execute)。  
  
```  
long GetRecordsAffected();
```  
  
### <a name="return-value"></a>傳回值  
 受影響的記錄數目。  
  
### <a name="remarks"></a>備註  
 傳回的計數不會反映串聯更新或刪除時的相關資料表中的變更會生效。  
  
 如需相關資訊，請參閱本主題說明 DAO 中的 「 RecordsAffected 屬性 」。  
  
##  <a name="a-namegetreturnsrecordsa--cdaoquerydefgetreturnsrecords"></a><a name="getreturnsrecords"></a>CDaoQueryDef::GetReturnsRecords  
 呼叫此成員函式可判斷 querydef 為基礎的查詢會傳回記錄。  
  
```  
BOOL GetReturnsRecords();
```  
  
### <a name="return-value"></a>傳回值  
 如果 querydef 以查詢為基礎為非零傳回記錄。否則為 0。  
  
### <a name="remarks"></a>備註  
 此成員函式僅用於 SQL 傳遞查詢。 如需 SQL 查詢的詳細資訊，請參閱[Execute](#execute)成員函式。 如需使用 SQL 傳遞查詢的詳細資訊，請參閱[SetReturnsRecords](#setreturnsrecords)成員函式。  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 傳回記錄屬性 」。  
  
##  <a name="a-namegetsqla--cdaoquerydefgetsql"></a><a name="getsql"></a>CDaoQueryDef::GetSQL  
 呼叫此成員函式擷取定義 querydef 為基礎的查詢的 SQL 陳述式。  
  
```  
CString GetSQL();
```  
  
### <a name="return-value"></a>傳回值  
 定義 querydef 為基礎的查詢的 SQL 陳述式。  
  
### <a name="remarks"></a>備註  
 您將會再可能剖析關鍵字、 資料表名稱等的字串。  
  
 如需相關資訊，請參閱 「 SQL 屬性 」、 「 比較的 Microsoft Jet 資料庫引擎 SQL 和 ANSI SQL 」 和 「 查詢資料庫的 SQL 中程式碼 」 DAO 說明中的主題。  
  
##  <a name="a-namegettypea--cdaoquerydefgettype"></a><a name="gettype"></a>CDaoQueryDef::GetType  
 呼叫此成員函式，以判斷 querydef 的查詢類型。  
  
```  
short GetType();
```  
  
### <a name="return-value"></a>傳回值  
 查詢 querydef 所定義的型別。 值，請參閱 < 備註 >。  
  
### <a name="remarks"></a>備註  
 查詢型別設定中指定的內容 querydef SQL 字串當您建立 querydef 或呼叫現有 querydef [SetSQL](#setsql)成員函式。 此函式所傳回的查詢類型可以是下列值之一︰  
  
- **dbQSelect**選取  
  
- **dbQAction**動作  
  
- **dbQCrosstab**交叉資料表  
  
- **dbQDelete**刪除  
  
- **dbQUpdate**更新  
  
- **dbQAppend**附加  
  
- **dbQMakeTable**製成資料表  
  
- **dbQDDL**資料定義  
  
- **dbQSQLPassThrough**傳遞  
  
- **dbQSetOperation**聯集  
  
- **dbQSPTBulk**搭配**dbQSQLPassThrough**指定不會傳回記錄的查詢。  
  
> [!NOTE]
>  若要建立 SQL 通過查詢，不需要設定**dbSQLPassThrough**常數。 這會自動設定由 Microsoft Jet 資料庫引擎時建立 recordset 物件，並設定連接字串。  
  
 如需 SQL 字串的詳細資訊，請參閱[GetSQL](#getsql)。 查詢類型的相關資訊，請參閱[Execute](#execute)。  
  
##  <a name="a-nameisopena--cdaoquerydefisopen"></a><a name="isopen"></a>CDaoQueryDef::IsOpen  
 呼叫此成員函式，以判斷是否`CDaoQueryDef`物件目前已開啟。  
  
```  
BOOL IsOpen() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果為非零`CDaoQueryDef`物件是目前已開啟，否則為 0。  
  
### <a name="remarks"></a>備註  
 Querydef 必須是處於開啟狀態，才能使用它來呼叫[Execute](#execute)或建立[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)物件。 可能處於開啟狀態呼叫的 querydef[建立](#create)（適用於新的 recordset) 或[開啟](#open)（適用於現有的 recordset)。  
  
##  <a name="a-namempdatabasea--cdaoquerydefmpdatabase"></a><a name="m_pdatabase"></a>CDaoQueryDef::m_pDatabase  
 包含一個指向[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) recordset 物件相關聯的物件。  
  
### <a name="remarks"></a>備註  
 如果您需要直接存取資料庫，請使用這個指標 — 比方說，若要取得其他 querydef 或資料錄集的指標物件在集合中的資料庫。  
  
##  <a name="a-namempdaoquerydefa--cdaoquerydefmpdaoquerydef"></a><a name="m_pdaoquerydef"></a>CDaoQueryDef::m_pDAOQueryDef  
 包含基本的 DAO recordset 物件的 OLE 介面的指標。  
  
### <a name="remarks"></a>備註  
 這個指標提供完整性和一致性與其他類別。 不過，因為 MFC 而完全封裝 DAO querydefs，您不太可能需要它。 如果您使用它，這樣謹慎 — 特別是，除非您知道您所進行的作業再變更指標的值。  
  
##  <a name="a-nameopena--cdaoquerydefopen"></a><a name="open"></a>CDaoQueryDef::Open  
 呼叫此成員函式，以開啟先前儲存在資料庫的 QueryDefs 集合 querydef。  
  
```  
virtual void Open(LPCTSTR lpszName = NULL);
```  
  
### <a name="parameters"></a>參數  
 `lpszName`  
 字串，其中包含以開啟已儲存的 querydef 名稱。 您可以使用[CString](../../atl-mfc-shared/reference/cstringt-class.md)。  
  
### <a name="remarks"></a>備註  
 Querydef 開啟後，您可以呼叫其[Execute](#execute)成員函式或使用建立 querydef [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)物件。  
  
##  <a name="a-namesetconnecta--cdaoquerydefsetconnect"></a><a name="setconnect"></a>CDaoQueryDef::SetConnect  
 呼叫此成員函式設定 recordset 物件的連接字串。  
  
```  
void SetConnect(LPCTSTR lpszConnect);
```  
  
### <a name="parameters"></a>參數  
 `lpszConnect`  
 字串，包含相關聯的連接字串[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)物件。  
  
### <a name="remarks"></a>備註  
 連接字串用來將額外的資訊傳遞給 ODBC 和視特定 ISAM 驅動程式。 不適用於 Microsoft Jet (。MDB) 資料庫。  
  
> [!TIP]
>  使用 ODBC 資料表，最好是將連接它們。MDB 的資料庫。  
  
 執行至 ODBC 資料來源代表 SQL 通過查詢 querydef 之前, 設定的連接字串具有`SetConnect`呼叫[SetReturnsRecords](#setreturnsrecords)來指定查詢是否傳回記錄。  
  
 如需有關連接字串的結構和範例連接字串元件的詳細資訊，請參閱 DAO 說明中的 「 連接屬性 」。  
  
##  <a name="a-namesetnamea--cdaoquerydefsetname"></a><a name="setname"></a>CDaoQueryDef::SetName  
 如果您想要變更的是非暫時 querydef 名稱，請呼叫此成員函式。  
  
```  
void SetName(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>參數  
 `lpszName`  
 字串，包含新的名稱相關聯的暫時性查詢[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)物件。  
  
### <a name="remarks"></a>備註  
 Querydef 名稱是唯一的使用者定義的名稱。 您可以呼叫`SetName`之前 recordset 物件會附加至 QueryDefs 集合。  
  
##  <a name="a-namesetodbctimeouta--cdaoquerydefsetodbctimeout"></a><a name="setodbctimeout"></a>CDaoQueryDef::SetODBCTimeout  
 呼叫此成員函式來設定 ODBC 資料來源的查詢逾時之前的時間限制。  
  
```  
void SetODBCTimeout(short nODBCTimeout);
```  
  
### <a name="parameters"></a>參數  
 *nODBCTimeout*  
 逾時之前查詢的秒數。  
  
### <a name="remarks"></a>備註  
 此成員函式可讓您覆寫預設連接的資料來源 」 逾時。 」 的後續操作之前的秒數 由於網路存取問題、 過多的查詢處理時間等作業可能會逾時。 呼叫`SetODBCTimeout`之前執行此 querydef 的查詢，如果您想要變更查詢逾時值。 （如 ODBC 會重複使用連線，逾時值是相同的連接上的所有用戶端相同）。  
  
 查詢逾時的預設值為 60 秒。  
  
##  <a name="a-namesetparamvaluea--cdaoquerydefsetparamvalue"></a><a name="setparamvalue"></a>CDaoQueryDef::SetParamValue  
 呼叫此成員函式在執行階段中 querydef 設定參數的值。  
  
```  
virtual void SetParamValue(
    LPCTSTR lpszName,  
    const COleVariant& varValue);

 
virtual void SetParamValue(
    int nIndex,  
    const COleVariant& varValue);
```  
  
### <a name="parameters"></a>參數  
 `lpszName`  
 您想要設定其值的參數名稱。  
  
 `varValue`  
 若要設定; 值請參閱 < 備註 >。  
  
 `nIndex`  
 Recordset 的參數集合中的參數序數位置。 您可以取得這個值與呼叫[GetParameterCount](#getparametercount)和[GetParameterInfo](#getparameterinfo)。  
  
### <a name="remarks"></a>備註  
 參數必須有已建立為 querydef SQL 字串的一部分。 您可以依名稱或其集合中的序數位置來存取參數。  
  
 指定要設定為值`COleVariant`物件。 如需有關設定所要的值，然後輸入您`COleVariant`物件，請參閱類別[COleVariant](../../mfc/reference/colevariant-class.md)。  
  
##  <a name="a-namesetreturnsrecordsa--cdaoquerydefsetreturnsrecords"></a><a name="setreturnsrecords"></a>CDaoQueryDef::SetReturnsRecords  
 呼叫此成員函式，來建立 SQL 通過查詢至外部資料庫的程序的一部分。  
  
```  
void SetReturnsRecords(BOOL bReturnsRecords);
```  
  
### <a name="parameters"></a>參數  
 *bReturnsRecords*  
 傳遞**TRUE**如果外部資料庫上的查詢傳回的記錄; 否則**FALSE**。  
  
### <a name="remarks"></a>備註  
 在這種情況下，您必須建立 querydef，並設定其屬性，使用其他`CDaoQueryDef`成員函式。 外部資料庫的說明，請參閱[SetConnect](#setconnect)。  
  
##  <a name="a-namesetsqla--cdaoquerydefsetsql"></a><a name="setsql"></a>CDaoQueryDef::SetSQL  
 呼叫此成員函式設定 querydef 執行的 SQL 陳述式。  
  
```  
void SetSQL(LPCTSTR lpszSQL);
```  
  
### <a name="parameters"></a>參數  
 `lpszSQL`  
 字串，包含完整 SQL 陳述式，適用於執行。 這個字串的語法取決於 DBMS，查詢目標。 使用 Microsoft Jet 資料庫引擎中語法的討論，請參閱 「 建置 SQL 陳述式中程式碼 」 DAO 說明中的主題。  
  
### <a name="remarks"></a>備註  
 一般會使用`SetSQL`是 SQL 的通過查詢中使用的 recordset 物件的設定。 （針對目標 DBMS SQL 傳遞查詢的語法，請參閱您的 DBMS 的文件）。  
  
## <a name="see-also"></a>另請參閱  
 [CObject 類別](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CDaoRecordset 類別](../../mfc/reference/cdaorecordset-class.md)   
 [CDaoDatabase 類別](../../mfc/reference/cdaodatabase-class.md)   
 [CDaoTableDef 類別](../../mfc/reference/cdaotabledef-class.md)   
 [CDaoException 類別](../../mfc/reference/cdaoexception-class.md)

