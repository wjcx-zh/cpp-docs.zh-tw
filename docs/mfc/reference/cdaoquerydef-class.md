---
title: CDaoQueryDef 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoQueryDef
- AFXDAO/CDaoQueryDef
- AFXDAO/CDaoQueryDef::CDaoQueryDef
- AFXDAO/CDaoQueryDef::Append
- AFXDAO/CDaoQueryDef::CanUpdate
- AFXDAO/CDaoQueryDef::Close
- AFXDAO/CDaoQueryDef::Create
- AFXDAO/CDaoQueryDef::Execute
- AFXDAO/CDaoQueryDef::GetConnect
- AFXDAO/CDaoQueryDef::GetDateCreated
- AFXDAO/CDaoQueryDef::GetDateLastUpdated
- AFXDAO/CDaoQueryDef::GetFieldCount
- AFXDAO/CDaoQueryDef::GetFieldInfo
- AFXDAO/CDaoQueryDef::GetName
- AFXDAO/CDaoQueryDef::GetODBCTimeout
- AFXDAO/CDaoQueryDef::GetParameterCount
- AFXDAO/CDaoQueryDef::GetParameterInfo
- AFXDAO/CDaoQueryDef::GetParamValue
- AFXDAO/CDaoQueryDef::GetRecordsAffected
- AFXDAO/CDaoQueryDef::GetReturnsRecords
- AFXDAO/CDaoQueryDef::GetSQL
- AFXDAO/CDaoQueryDef::GetType
- AFXDAO/CDaoQueryDef::IsOpen
- AFXDAO/CDaoQueryDef::Open
- AFXDAO/CDaoQueryDef::SetConnect
- AFXDAO/CDaoQueryDef::SetName
- AFXDAO/CDaoQueryDef::SetODBCTimeout
- AFXDAO/CDaoQueryDef::SetParamValue
- AFXDAO/CDaoQueryDef::SetReturnsRecords
- AFXDAO/CDaoQueryDef::SetSQL
- AFXDAO/CDaoQueryDef::m_pDAOQueryDef
- AFXDAO/CDaoQueryDef::m_pDatabase
dev_langs:
- C++
helpviewer_keywords:
- CDaoQueryDef [MFC], CDaoQueryDef
- CDaoQueryDef [MFC], Append
- CDaoQueryDef [MFC], CanUpdate
- CDaoQueryDef [MFC], Close
- CDaoQueryDef [MFC], Create
- CDaoQueryDef [MFC], Execute
- CDaoQueryDef [MFC], GetConnect
- CDaoQueryDef [MFC], GetDateCreated
- CDaoQueryDef [MFC], GetDateLastUpdated
- CDaoQueryDef [MFC], GetFieldCount
- CDaoQueryDef [MFC], GetFieldInfo
- CDaoQueryDef [MFC], GetName
- CDaoQueryDef [MFC], GetODBCTimeout
- CDaoQueryDef [MFC], GetParameterCount
- CDaoQueryDef [MFC], GetParameterInfo
- CDaoQueryDef [MFC], GetParamValue
- CDaoQueryDef [MFC], GetRecordsAffected
- CDaoQueryDef [MFC], GetReturnsRecords
- CDaoQueryDef [MFC], GetSQL
- CDaoQueryDef [MFC], GetType
- CDaoQueryDef [MFC], IsOpen
- CDaoQueryDef [MFC], Open
- CDaoQueryDef [MFC], SetConnect
- CDaoQueryDef [MFC], SetName
- CDaoQueryDef [MFC], SetODBCTimeout
- CDaoQueryDef [MFC], SetParamValue
- CDaoQueryDef [MFC], SetReturnsRecords
- CDaoQueryDef [MFC], SetSQL
- CDaoQueryDef [MFC], m_pDAOQueryDef
- CDaoQueryDef [MFC], m_pDatabase
ms.assetid: 9676a4a3-c712-44d4-8c5d-d1cc78288d3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b3af520de7e92a887f9a49fea7262d7f51b74082
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2018
ms.locfileid: "36954630"
---
# <a name="cdaoquerydef-class"></a>CDaoQueryDef 類別
表示查詢定義 (或 "querydef")，通常是儲存在資料庫中的定義。  
  
## <a name="syntax"></a>語法  
  
```  
class CDaoQueryDef : public CObject  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CDaoQueryDef::CDaoQueryDef](#cdaoquerydef)|建構 `CDaoQueryDef` 物件。 接下來呼叫`Open`或`Create`，視您的需求。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CDaoQueryDef::Append](#append)|將 querydef 附加至資料庫的 QueryDefs 集合做為已儲存的查詢。|  
|[CDaoQueryDef::CanUpdate](#canupdate)|傳回非零，如果查詢可更新資料庫。|  
|[CDaoQueryDef::Close](#close)|關閉 recordset 物件。 當您完成時，請摧毀 c + + 物件。|  
|[CDaoQueryDef::Create](#create)|建立基本的 DAO recordset 物件。 做為暫時查詢或呼叫 querydef`Append`將它儲存在資料庫中。|  
|[CDaoQueryDef::Execute](#execute)|執行查詢的 recordset 物件所定義。|  
|[CDaoQueryDef::GetConnect](#getconnect)|傳回與 querydef 相關聯的連接字串。 連接字串會識別資料來源。 （如 SQL 通過查詢，否則為空字串。）|  
|[CDaoQueryDef::GetDateCreated](#getdatecreated)|傳回儲存的查詢建立的日期。|  
|[CDaoQueryDef::GetDateLastUpdated](#getdatelastupdated)|傳回上次更新的儲存的查詢的日期。|  
|[CDaoQueryDef::GetFieldCount](#getfieldcount)|傳回 querydef 所定義的欄位數目。|  
|[CDaoQueryDef::GetFieldInfo](#getfieldinfo)|傳回指定欄位的查詢中所定義的相關資訊。|  
|[CDaoQueryDef::GetName](#getname)|傳回 querydef 名稱。|  
|[CDaoQueryDef::GetODBCTimeout](#getodbctimeout)|傳回用於 ODBC （ODBC 的查詢） 的逾時值 querydef 執行時。 這會決定多久以便進行查詢的動作，才能完成。|  
|[CDaoQueryDef::GetParameterCount](#getparametercount)|傳回定義查詢參數的數目。|  
|[CDaoQueryDef::GetParameterInfo](#getparameterinfo)|指定參數的相關資訊傳回給查詢。|  
|[CDaoQueryDef::GetParamValue](#getparamvalue)|指定參數的值傳回給查詢。|  
|[CDaoQueryDef::GetRecordsAffected](#getrecordsaffected)|傳回受影響的動作查詢記錄數目。|  
|[CDaoQueryDef::GetReturnsRecords](#getreturnsrecords)|傳回非零，如果 querydef 所定義的查詢傳回的記錄。|  
|[CDaoQueryDef::GetSQL](#getsql)|傳回 SQL 字串，指定 querydef 所定義的查詢。|  
|[CDaoQueryDef::GetType](#gettype)|傳回的查詢類型： 刪除、 更新、 附加、 建立資料表等等。|  
|[CDaoQueryDef::IsOpen](#isopen)|如果 querydef 已開啟，而且可以執行，則會傳回非零值。|  
|[CDaoQueryDef::Open](#open)|開啟現有的 querydef 儲存在資料庫的 QueryDefs 集合中。|  
|[CDaoQueryDef::SetConnect](#setconnect)|ODBC 資料來源上設定 SQL 傳遞查詢的連接字串。|  
|[CDaoQueryDef::SetName](#setname)|設定名稱的已儲存的查詢，建立 querydef 時取代中使用的名稱。|  
|[CDaoQueryDef::SetODBCTimeout](#setodbctimeout)|設定用於 ODBC （ODBC 的查詢） 的逾時值 querydef 執行時。|  
|[CDaoQueryDef::SetParamValue](#setparamvalue)|將指定參數的值設定查詢。|  
|[CDaoQueryDef::SetReturnsRecords](#setreturnsrecords)|指定是否 querydef 傳回記錄。 將此屬性設定為**TRUE**是唯一有效的 SQL 傳遞查詢。|  
|[CDaoQueryDef::SetSQL](#setsql)|設定 SQL 字串，指定 querydef 所定義的查詢。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CDaoQueryDef::m_pDAOQueryDef](#m_pdaoquerydef)|基本的 DAO recordset 物件的 OLE 介面指標。|  
|[CDaoQueryDef::m_pDatabase](#m_pdatabase)|指標`CDaoDatabase`querydef 在相關聯的物件。 Querydef 可能儲存在資料庫中，或不。|  
  
## <a name="remarks"></a>備註  
 Querydef 是資料存取物件，包含 SQL 陳述式，描述查詢和其屬性，例如 「 建立日期 」 和 「 ODBC 逾時。 」 您也可以建立暫存的 recordset 物件，而不儲存，但可以很方便，且更有效率，來儲存經常重複使用的資料庫中的查詢。 A [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)物件會維護一個稱為 QueryDefs 集合，包含其儲存的 querydefs 的集合。  
  
> [!NOTE]
>  DAO 資料庫類別是不同的基礎上開放式資料庫連接 (ODBC) 之 MFC 資料庫類別。 所有的 DAO 資料庫類別名稱有"CDao"前置詞。 您仍然可以使用 DAO 類別存取 ODBC 資料來源。 一般情況下，根據 DAO MFC 類別會更能夠比 ODBC; 為基礎的 MFC 類別DAO 類別都可以存取資料，包括透過 ODBC 驅動程式，透過它們自己的資料庫引擎。 DAO 類別也支援資料定義語言 (DDL) 作業，例如新增而不需要直接呼叫 DAO 類別，透過資料表。  
  
## <a name="usage"></a>使用量  
 使用 querydef 物件可能是使用現有已儲存的查詢，或建立新的儲存查詢或暫存的查詢：  
  
1.  在所有情況下，第一次，以建構`CDaoQueryDef`物件，提供的指標[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)查詢所屬的物件。  
  
2.  然後，執行下列命令，視您想要：  
  
    -   若要使用現有已儲存的查詢，呼叫 recordset 物件的[開啟](#open)成員函式，提供的儲存查詢名稱。  
  
    -   若要建立新儲存的查詢，呼叫 recordset 物件的[建立](#create)成員函式，提供查詢的名稱。 然後呼叫[附加](#append)藉由附加至資料庫的 QueryDefs 集合儲存查詢。 `Create` querydef 放在開啟狀態，因此在呼叫`Create`沒有呼叫`Open`。  
  
    -   若要建立暫存 querydef，呼叫`Create`。 將傳遞查詢名稱為空字串。 請不要呼叫 `Append`。  
  
 當您完成使用 recordset 物件時，呼叫其[關閉](#close)成員函式，然後終結 querydef 物件。  
  
> [!TIP]
>  若要建立儲存的查詢最簡單方式是建立它們，並將它們儲存在使用 Microsoft Access 資料庫中。 然後您可以開啟，並在您的 MFC 程式碼中使用它們。  
  
## <a name="purposes"></a>用途  
 您可以使用 querydef 物件的任何下列用途：  
  
-   若要建立`CDaoRecordset`物件  
  
-   若要呼叫物件的`Execute`成員函式來直接執行的動作查詢或 SQL 傳遞查詢  
  
 您可以使用任何類型的查詢，包括 select、 動作、 交叉、 delete、 update recordset 物件、 附加、 建立資料表、 資料定義、 SQL 傳遞、 union、 和大量查詢。 查詢的類型取決於您所提供的 SQL 陳述式的內容。 查詢類型的相關資訊，請參閱`Execute`和[GetType](#gettype)成員函式。 資料錄集通常用於傳回資料列的查詢，通常使用**選取...從**關鍵字。 `Execute` 最常用的大量作業。 如需詳細資訊，請參閱[Execute](#execute)和[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)。  
  
## <a name="querydefs-and-recordsets"></a>Querydefs 和資料錄集  
 要用來建立 querydef 物件`CDaoRecordset`物件，您通常建立或開啟 querydef，如上面所述。 然後建構資料錄集物件，當您呼叫時，就將指標傳遞至 querydef 物件[cdaorecordset:: Open](../../mfc/reference/cdaorecordset-class.md#open)。 您傳遞 querydef 必須處於開啟狀態。 如需詳細資訊，請參閱類別[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)。  
  
 您無法使用 querydef 來建立資料錄集 （recordset 最常見用途），除非它是處於開啟狀態。 Querydef 放開啟狀態，藉由呼叫`Open`或`Create`。  
  
## <a name="external-databases"></a>外部資料庫  
 Recordset 物件是使用原生 SQL 用語的外部資料庫引擎的慣用的方式。 例如，您可以建立 Transact SQL 查詢 （如 Microsoft SQL Server 上使用），並將它儲存 recordset 物件中。 當您需要使用不根據 Microsoft Jet 資料庫引擎的 SQL 查詢時，您必須提供指向外部資料來源的連接字串。 查詢具有有效的連接字串會略過資料庫引擎，並查詢將直接傳遞至外部資料庫伺服器的處理。  
  
> [!TIP]
>  使用 ODBC 資料表的較佳的方式是將它們附加至 Microsoft Jet (。MDB) 資料庫。  
  
 如需相關資訊，請參閱 「 Recordset 物件 」、 「 QueryDefs 集合 」 和 「 CdbDatabase 物件 」 DAO SDK 中的主題。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDaoQueryDef`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxdao.h  
  
##  <a name="append"></a>  CDaoQueryDef::Append  
 呼叫此成員函式之後您呼叫,[建立](#create)建立新的 recordset 物件。  
  
```  
virtual void Append();
```  
  
### <a name="remarks"></a>備註  
 `Append` 將 querydef 儲存在資料庫中，將物件附加至資料庫的 QueryDefs 集合。 您可以使用 querydef 作為暫存物件不會附加，但如果您想要保存，您必須呼叫`Append`。  
  
 如果您嘗試新增暫存 recordset 物件，MFC 會擲回例外狀況型別的[CDaoException](../../mfc/reference/cdaoexception-class.md)。  
  
##  <a name="canupdate"></a>  CDaoQueryDef::CanUpdate  
 呼叫此成員函式，以判斷您是否可以修改 querydef — 例如變更其名稱或 SQL 字串。  
  
```  
BOOL CanUpdate();
```  
  
### <a name="return-value"></a>傳回值  
 為非零，如果您允許修改 querydef;否則便是 0。  
  
### <a name="remarks"></a>備註  
 您可以修改 querydef 如果：  
  
-   它不基礎資料庫已經開啟為唯讀。  
  
-   您有更新資料庫的權限。  
  
     這取決於您是否有實作安全性功能。 MFC 不提供支援的安全性;您必須實作它自己藉由呼叫 DAO 直接或使用 Microsoft Access。 請參閱主題 DAO [說明] 中的 < 權限屬性 >。  
  
##  <a name="cdaoquerydef"></a>  CDaoQueryDef::CDaoQueryDef  
 建構 `CDaoQueryDef` 物件。  
  
```  
CDaoQueryDef(CDaoDatabase* pDatabase);
```  
  
### <a name="parameters"></a>參數  
 *pDatabase*  
 開啟指標[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)物件。  
  
### <a name="remarks"></a>備註  
 物件可代表儲存在資料庫的 QueryDefs 集合、 新的查詢儲存在集合中或暫時查詢，不是要儲存現有 querydef。 下一步 querydef 類型而定：  
  
-   如果現有的 querydef 所代表的物件，呼叫物件的[開啟](#open)成員函式來初始化執行個體。  
  
-   如果要儲存新 querydef 所代表的物件，呼叫物件的[建立](#create)成員函式。 這會將物件加入至資料庫的 QueryDefs 集合中。 然後呼叫`CDaoQueryDef`成員函式來設定物件的屬性。 最後，呼叫[附加](#append)。  
  
-   如果暫存 querydef （不要儲存在資料庫中） 所代表的物件，呼叫`Create`，傳遞查詢的名稱為空字串。 在呼叫`Create`，初始化 querydef 藉由直接設定其屬性。 請不要呼叫 `Append`。  
  
 若要設定的 querydef 屬性，您可以使用[SetName](#setname)， [SetSQL](#setsql)， [SetConnect](#setconnect)， [SetODBCTimeout](#setodbctimeout)，和[SetReturnsRecords](#setreturnsrecords)成員函式。  
  
 當您完成 recordset 物件時，呼叫其[關閉](#close)成員函式。 如果您有 querydef 的指標，使用**刪除**終結 c + + 物件的運算子。  
  
##  <a name="close"></a>  CDaoQueryDef::Close  
 當您完成使用 recordset 物件時，請呼叫此成員函式。  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>備註  
 關閉 querydef 釋放基礎的 DAO 物件但不會終結儲存的 DAO recordset 物件或 c + +`CDaoQueryDef`物件。 這不是相同[CDaoDatabase::DeleteQueryDef](../../mfc/reference/cdaodatabase-class.md#deletequerydef)，會刪除 querydef 資料庫 QueryDefs 集合中 DAO （如果沒有暫存 querydef）。  
  
##  <a name="create"></a>  CDaoQueryDef::Create  
 呼叫此成員函式，以建立新儲存的查詢或新的暫時查詢。  
  
```  
virtual void Create(
    LPCTSTR lpszName = NULL,  
    LPCTSTR lpszSQL = NULL);
```  
  
### <a name="parameters"></a>參數  
 *lpszName*  
 儲存在資料庫中查詢的唯一名稱。 如需字串的詳細資訊，請參閱主題 < CreateQueryDef 方法 >，DAO [說明] 中。 如果您接受預設值為空字串，會建立暫存的 recordset。 QueryDefs 集合中不會儲存這類查詢。  
  
 *lpszSQL*  
 定義查詢的 SQL 字串。 如果您接受預設值的**NULL**，您必須稍後呼叫[SetSQL](#setsql)設定字串。 之前，查詢是未定義。 不過，您可以使用未定義的查詢開啟資料錄集。如需詳細資訊，請參閱 < 備註 >。 您可以新增 querydef 至 QueryDefs 集合之前，必須定義 SQL 陳述式。  
  
### <a name="remarks"></a>備註  
 如果您要傳入的名稱在*lpszName*，您就可以呼叫[附加](#append)querydef 儲存資料庫的 QueryDefs 集合中。 否則，物件是暫存 querydef，而且不會儲存。 在任一情況下，querydef 處於開啟狀態，且您可以使用它來建立[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)物件或呼叫 querydef [Execute](#execute)成員函式。  
  
 如果您未提供 SQL 陳述式中的*lpszSQL*，您無法執行與查詢`Execute`但您可以使用它來建立資料錄集。 在此情況下，MFC 會使用資料錄集的預設 SQL 陳述式。  
  
##  <a name="execute"></a>  CDaoQueryDef::Execute  
 呼叫此成員函式，以執行查詢的 recordset 物件所定義。  
  
```  
virtual void Execute(int nOptions = dbFailOnError);
```  
  
### <a name="parameters"></a>參數  
 *nOptions*  
 整數，會決定查詢的特性。 如需相關資訊，請參閱主題 DAO [說明] 中的 < 執行方法 >。 您可以使用位元 OR 運算子 ( **&#124;**) 來結合這個引數的下列常數：  
  
- **dbDenyWrite**拒絕其他使用者的寫入權限。  
  
- **dbInconsistent**不一致的更新。  
  
- **dbConsistent**一致更新。  
  
- **dbSQLPassThrough** SQL 傳遞。 會進行處理傳遞至 ODBC 資料庫的 SQL 陳述式。  
  
- **dbFailOnError**預設值。 回復更新發生錯誤與錯誤報表給使用者。  
  
- **dbSeeChanges**產生執行階段錯誤，如果另一位使用者正在變更您正在編輯的資料。  
  
> [!NOTE]
>  術語的說明 「 不一致 」 和 「 一致性 」，請參閱主題 DAO [說明] 中的 < 執行方法 >。  
  
### <a name="remarks"></a>備註  
 以這種方式執行時使用的 Recordset 物件只能表示下列一種查詢類型：  
  
-   動作的查詢  
  
-   SQL 傳遞查詢  
  
 `Execute` 不適用於傳回記錄，例如 select 查詢的查詢。 `Execute` 通常用於大量作業的查詢，例如**更新**，**插入**，或**SELECT INTO**，或針對資料定義語言 (DDL) 作業。  
  
> [!TIP]
>  使用 ODBC 資料來源的慣用的方法是將資料表附加至 Microsoft Jet (。MDB) 資料庫。 如需詳細資訊，請參閱主題 < 存取外部資料庫使用 DAO"DAO [說明] 中。  
  
 呼叫[GetRecordsAffected](#getrecordsaffected)成員函式來判斷受影響的最新的記錄數目的 recordset 物件`Execute`呼叫。 例如，`GetRecordsAffected`傳回的刪除、 更新或插入動作查詢執行時的記錄數目的相關資訊。 傳回的計數不會反映 cascade 更新或刪除時的相關資料表中的變更才會生效。  
  
 如果您同時包含**dbInconsistent**和**dbConsistent**或如果您包含兩者皆非，結果將是預設值， **dbInconsistent**。  
  
 `Execute` 不會傳回一個資料錄集。 使用`Execute`選取記錄的查詢會使 MFC 擲回例外狀況型別的[CDaoException](../../mfc/reference/cdaoexception-class.md)。  
  
##  <a name="getconnect"></a>  CDaoQueryDef::GetConnect  
 呼叫此成員函式可取得 querydef 的資料來源相關聯的連接字串。  
  
```  
CString GetConnect();
```  
  
### <a name="return-value"></a>傳回值  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md)包含 querydef 的連接字串。  
  
### <a name="remarks"></a>備註  
 此函數只能搭配 ODBC 資料來源和某些 ISAM 驅動程式。 它不適用於 Microsoft Jet (。MDB) 資料庫;在此情況下，`GetConnect`會傳回空字串。 如需詳細資訊，請參閱[SetConnect](#setconnect)。  
  
> [!TIP]
>  若要使用的 ODBC 資料表的慣用的方法為將其連接至。MDB 的資料庫。 如需詳細資訊，請參閱主題 < 存取外部資料庫使用 DAO"DAO [說明] 中。  
  
 如需連接字串資訊，請參閱主題 DAO [說明] 中的 < 連接屬性 >。  
  
##  <a name="getdatecreated"></a>  CDaoQueryDef::GetDateCreated  
 呼叫此成員函式可取得 querydef 物件的建立的日期。  
  
```  
COleDateTime GetDateCreated();
```  
  
### <a name="return-value"></a>傳回值  
 A [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)物件，其中包含的日期和時間 querydef 所建立。  
  
### <a name="remarks"></a>備註  
 如需相關資訊，請參閱 DAO 說明主題 「 DateCreated LastUpdated 屬性 」。  
  
##  <a name="getdatelastupdated"></a>  CDaoQueryDef::GetDateLastUpdated  
 呼叫此成員函式，取得日期 querydef 物件上次更新 — 當其任何屬性已變更，例如其名稱、 其 SQL 字串或其連接字串。  
  
```  
COleDateTime GetDateLastUpdated();
```  
  
### <a name="return-value"></a>傳回值  
 A [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)物件，其中包含的日期和 querydef 上次更新的時間。  
  
### <a name="remarks"></a>備註  
 如需相關資訊，請參閱 DAO 說明主題 「 DateCreated LastUpdated 屬性 」。  
  
##  <a name="getfieldcount"></a>  CDaoQueryDef::GetFieldCount  
 呼叫此成員函式可擷取查詢中的欄位數目。  
  
```  
short GetFieldCount();
```  
  
### <a name="return-value"></a>傳回值  
 查詢中定義的欄位數目。  
  
### <a name="remarks"></a>備註  
 `GetFieldCount` 適用於迴圈 querydef 中的所有欄位。 基於這個目的，使用`GetFieldCount`搭配[GetFieldInfo](#getfieldinfo)。  
  
##  <a name="getfieldinfo"></a>  CDaoQueryDef::GetFieldInfo  
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
 *nIndex*  
 所要的欄位的索引查閱為 querydef 的欄位集合中以零為起始的索引。  
  
 *fieldinfo*  
 若要參考`CDaoFieldInfo`物件，傳回要求的資訊。  
  
 *dwInfoOptions*  
 指定要擷取的欄位有關的資訊的選項。 以下列出可用的選項以及它們會導致此函數傳回：  
  
- `AFX_DAO_PRIMARY_INFO` （預設值）名稱、 類型、 大小屬性  
  
- `AFX_DAO_SECONDARY_INFO` 加上的主要資訊： 所需的序數位置，允許長度為零、 來源欄位、 外部索引名稱、 來源資料表、 定序順序  
  
- `AFX_DAO_ALL_INFO` 主要和次要資訊加上： 預設值，驗證文字驗證規則  
  
 *lpszName*  
 字串，包含依名稱查閱所需的欄位名稱。 您可以使用[CString](../../atl-mfc-shared/reference/cstringt-class.md)。  
  
### <a name="remarks"></a>備註  
 如需在傳回的資訊的說明*fieldinfo*，請參閱[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)結構。 此結構已對應至底下的描述性資訊的成員*dwInfoOptions*上方。 如果您要求的資訊的一個層級，您會取得任何先前的層級的資訊。  
  
##  <a name="getname"></a>  CDaoQueryDef::GetName  
 呼叫此成員函式可擷取 querydef 所表示的查詢名稱。  
  
```  
CString GetName();
```  
  
### <a name="return-value"></a>傳回值  
 查詢的名稱。  
  
### <a name="remarks"></a>備註  
 Querydef 名稱是唯一的使用者定義名稱。 如需 querydef 名稱的詳細資訊，請參閱主題 DAO [說明] 中的 「 名稱屬性 」。  
  
##  <a name="getodbctimeout"></a>  CDaoQueryDef::GetODBCTimeout  
 呼叫此成員函式，ODBC 資料來源的查詢逾時之前，擷取目前的時間限制。  
  
```  
short GetODBCTimeout();
```  
  
### <a name="return-value"></a>傳回值  
 逾時查詢之前的秒數。  
  
### <a name="remarks"></a>備註  
 這個時間限制的相關資訊，請參閱主題 DAO [說明] 中的 「 odbc 逾時屬性 」。  
  
> [!TIP]
>  使用 ODBC 資料表的較佳的方式是將它們附加至 Microsoft Jet (。MDB) 資料庫。 如需詳細資訊，請參閱主題 < 存取外部資料庫使用 DAO"DAO [說明] 中。  
  
##  <a name="getparametercount"></a>  CDaoQueryDef::GetParameterCount  
 呼叫此成員函式可擷取已儲存的查詢中的參數數目。  
  
```  
short GetParameterCount();
```  
  
### <a name="return-value"></a>傳回值  
 查詢中定義的參數數目。  
  
### <a name="remarks"></a>備註  
 `GetParameterCount` 適用於迴圈 querydef 中的所有參數。 基於這個目的，使用`GetParameterCount`搭配[GetParameterInfo](#getparameterinfo)。  
  
 如需相關資訊，請參閱 「 參數物件 」、 「 參數集合 」 和 「 參數宣告 (SQL)"DAO [說明] 中的主題。  
  
##  <a name="getparameterinfo"></a>  CDaoQueryDef::GetParameterInfo  
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
 *nIndex*  
 在 querydef 參數集合中，依索引查閱所需的參數以零為起始的索引。  
  
 *paraminfo 曲線等等*  
 若要參考[CDaoParameterInfo](../../mfc/reference/cdaoparameterinfo-structure.md)物件，傳回要求的資訊。  
  
 *dwInfoOptions*  
 指定要擷取之參數的相關資訊的選項。 可用的選項為以及它會導致此函數傳回此處所列：  
  
- `AFX_DAO_PRIMARY_INFO` （預設值）名稱、 類型  
  
 *lpszName*  
 字串，包含依名稱查閱所需的參數名稱。 您可以使用[CString](../../atl-mfc-shared/reference/cstringt-class.md)。  
  
### <a name="remarks"></a>備註  
 如需在傳回的資訊的說明*paraminfo 曲線等等*，請參閱[CDaoParameterInfo](../../mfc/reference/cdaoparameterinfo-structure.md)結構。 此結構已對應至底下的描述性資訊的成員*dwInfoOptions*上方。  
  
 如需相關資訊，請參閱"參數宣告 (SQL)"DAO [說明] 中的主題。  
  
##  <a name="getparamvalue"></a>  CDaoQueryDef::GetParamValue  
 呼叫此成員函式可擷取目前儲存在 querydef 參數集合中的指定參數的值。  
  
```  
virtual COleVariant GetParamValue(LPCTSTR lpszName);  
virtual COleVariant GetParamValue(int nIndex);
```  
  
### <a name="parameters"></a>參數  
 *lpszName*  
 您想依名稱查閱其值的參數名稱。  
  
 *nIndex*  
 依索引查閱 querydef 參數集合中的參數以零為起始的索引。 您可以取得此值與呼叫[GetParameterCount](#getparametercount)和[GetParameterInfo](#getparameterinfo)。  
  
### <a name="return-value"></a>傳回值  
 類別的物件[COleVariant](../../mfc/reference/colevariant-class.md) ，其中包含參數的值。  
  
### <a name="remarks"></a>備註  
 您可以依名稱或集合中的序數位置來存取參數。  
  
 如需相關資訊，請參閱"參數宣告 (SQL)"DAO [說明] 中的主題。  
  
##  <a name="getrecordsaffected"></a>  CDaoQueryDef::GetRecordsAffected  
 呼叫此成員函式，來判斷的多少筆記錄不受影響的最後一次呼叫[Execute](#execute)。  
  
```  
long GetRecordsAffected();
```  
  
### <a name="return-value"></a>傳回值  
 受影響的記錄數目。  
  
### <a name="remarks"></a>備註  
 傳回的計數不會反映 cascade 更新或刪除時的相關資料表中的變更才會生效。  
  
 如需相關資訊，請參閱主題 DAO [說明] 中的 < RecordsAffected 屬性 >。  
  
##  <a name="getreturnsrecords"></a>  CDaoQueryDef::GetReturnsRecords  
 呼叫此成員函式可判斷 querydef 為基礎的查詢，傳回記錄。  
  
```  
BOOL GetReturnsRecords();
```  
  
### <a name="return-value"></a>傳回值  
 如果 querydef 根據查詢非零，傳回記錄。否則便是 0。  
  
### <a name="remarks"></a>備註  
 此成員函式只用於 SQL 傳遞查詢。 如需 SQL 查詢的詳細資訊，請參閱[Execute](#execute)成員函式。 如需有關使用 SQL 傳遞查詢的詳細資訊，請參閱[SetReturnsRecords](#setreturnsrecords)成員函式。  
  
 如需相關資訊，請參閱主題 DAO [說明] 中的 「 傳回記錄屬性 」。  
  
##  <a name="getsql"></a>  CDaoQueryDef::GetSQL  
 呼叫此成員函式可擷取定義 querydef 為基礎的查詢的 SQL 陳述式。  
  
```  
CString GetSQL();
```  
  
### <a name="return-value"></a>傳回值  
 定義 querydef 為基礎的查詢的 SQL 陳述式。  
  
### <a name="remarks"></a>備註  
 您接著會將可能剖析關鍵字、 資料表名稱等的字串。  
  
 如需相關資訊，請參閱 「 SQL 屬性 」、 「 比較 Microsoft Jet 資料庫引擎 SQL 和 ANSI SQL"和 「 查詢資料庫與 SQL 增益集程式碼 」 DAO 說明主題。  
  
##  <a name="gettype"></a>  CDaoQueryDef::GetType  
 呼叫此成員函式可判斷 querydef 的查詢類型。  
  
```  
short GetType();
```  
  
### <a name="return-value"></a>傳回值  
 查詢 querydef 所定義的類型。 值，請參閱 < 備註 >。  
  
### <a name="remarks"></a>備註  
 查詢類型由您所指定 querydef SQL 字串中當您建立 querydef 或呼叫現有 querydef 設定[SetSQL](#setsql)成員函式。 此函式所傳回的查詢類型可以是下列值之一：  
  
- **dbQSelect**選取  
  
- **dbQAction**動作  
  
- **dbQCrosstab**交叉資料表  
  
- **dbQDelete**刪除  
  
- **dbQUpdate**更新  
  
- **dbQAppend**附加  
  
- **dbQMakeTable**製成資料表  
  
- **dbQDDL**資料定義  
  
- **dbQSQLPassThrough**傳遞  
  
- **dbQSetOperation**等位  
  
- **dbQSPTBulk**搭配**dbQSQLPassThrough**指定不會傳回記錄的查詢。  
  
> [!NOTE]
>  若要建立 SQL 的通過查詢，不需要設定**dbSQLPassThrough**常數。 這會自動設定由 Microsoft Jet 資料庫引擎時建立 recordset 物件，並設定連接字串。  
  
 如需 SQL 字串的相關資訊，請參閱[GetSQL](#getsql)。 查詢類型的相關資訊，請參閱[Execute](#execute)。  
  
##  <a name="isopen"></a>  CDaoQueryDef::IsOpen  
 呼叫此成員函式，以判斷是否`CDaoQueryDef`物件目前是否開啟。  
  
```  
BOOL IsOpen() const;  
```  
  
### <a name="return-value"></a>傳回值  
 為非零，如果`CDaoQueryDef`物件是目前開啟; 否則為 0。  
  
### <a name="remarks"></a>備註  
 Querydef 必須是處於開啟狀態，才使用它來呼叫[Execute](#execute)或建立[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)物件。 可能是處於開啟狀態呼叫的 querydef[建立](#create)（適用於新的 querydef) 或[開啟](#open)（適用於現有的 querydef)。  
  
##  <a name="m_pdatabase"></a>  CDaoQueryDef::m_pDatabase  
 包含的指標[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) querydef 物件相關聯的物件。  
  
### <a name="remarks"></a>備註  
 如果您需要直接存取資料庫，請使用這個指標 — 比方說，若要取得其他 querydef 或資料錄集的指標物件的資料庫集合中。  
  
##  <a name="m_pdaoquerydef"></a>  CDaoQueryDef::m_pDAOQueryDef  
 包含基礎 DAO recordset 物件的 OLE 介面的指標。  
  
### <a name="remarks"></a>備註  
 此指標提供完整性和一致性與其他類別。 不過，由於 MFC 而不是完整封裝 DAO querydefs，您不太可能需要它。 如果您使用它，這樣請多加留意，尤其是，除非您知道您所進行的作業再變更指標的值。  
  
##  <a name="open"></a>  CDaoQueryDef::Open  
 呼叫此成員函式可開啟先前儲存在資料庫的 QueryDefs 集合 querydef。  
  
```  
virtual void Open(LPCTSTR lpszName = NULL);
```  
  
### <a name="parameters"></a>參數  
 *lpszName*  
 字串，其中包含以開啟已儲存的 querydef 名稱。 您可以使用[CString](../../atl-mfc-shared/reference/cstringt-class.md)。  
  
### <a name="remarks"></a>備註  
 Querydef 一旦開啟，您可以呼叫其[Execute](#execute)成員函式或使用建立 querydef [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)物件。  
  
##  <a name="setconnect"></a>  CDaoQueryDef::SetConnect  
 呼叫此成員函式設定 recordset 物件的連接字串。  
  
```  
void SetConnect(LPCTSTR lpszConnect);
```  
  
### <a name="parameters"></a>參數  
 *lpszConnect*  
 字串，包含相關聯的連接字串[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)物件。  
  
### <a name="remarks"></a>備註  
 連接字串用來將額外的資訊傳遞給 ODBC 和視需要某些 ISAM 驅動程式。 它不會使用 Microsoft Jet (。MDB) 資料庫。  
  
> [!TIP]
>  若要使用的 ODBC 資料表的慣用的方法為將其連接至。MDB 的資料庫。  
  
 在執行之前加入 ODBC 資料來源代表 SQL 的通過查詢 querydef，設定連接字串與`SetConnect`並呼叫[SetReturnsRecords](#setreturnsrecords)來指定查詢是否傳回記錄。  
  
 如需有關連接字串的結構和範例連接字串元件的詳細資訊，請參閱 DAO [說明] 中的 < 連接屬性 > 主題。  
  
##  <a name="setname"></a>  CDaoQueryDef::SetName  
 如果您想要變更不是暫時性 querydef 的名稱，請呼叫此成員函式。  
  
```  
void SetName(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>參數  
 *lpszName*  
 字串，包含新的名稱相關聯的暫時性查詢[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)物件。  
  
### <a name="remarks"></a>備註  
 Querydef 名稱是唯一的使用者定義的名稱。 您可以呼叫`SetName`之前 recordset 物件會附加至 QueryDefs 集合。  
  
##  <a name="setodbctimeout"></a>  CDaoQueryDef::SetODBCTimeout  
 呼叫此成員函式來設定 ODBC 資料來源的查詢逾時之前的時間限制。  
  
```  
void SetODBCTimeout(short nODBCTimeout);
```  
  
### <a name="parameters"></a>參數  
 *nODBCTimeout*  
 逾時查詢之前的秒數。  
  
### <a name="remarks"></a>備註  
 此成員函式可讓您覆寫預設連接的資料來源 」 逾時。 」 上的後續作業之前的秒數 由於網路存取問題、 過多的查詢處理時間，以及其他作業可能會逾時。 呼叫`SetODBCTimeout`之前執行具有這個 querydef 的查詢，如果您想要變更查詢逾時值。 （如 ODBC 會重複使用的連接，逾時值是相同的連接上的所有用戶端相同。）  
  
 查詢逾時的預設值為 60 秒。  
  
##  <a name="setparamvalue"></a>  CDaoQueryDef::SetParamValue  
 呼叫此成員函式在執行階段 querydef 中設定參數的值。  
  
```  
virtual void SetParamValue(
    LPCTSTR lpszName,  
    const COleVariant& varValue);

 
virtual void SetParamValue(
    int nIndex,  
    const COleVariant& varValue);
```  
  
### <a name="parameters"></a>參數  
 *lpszName*  
 您想要設定其值的參數名稱。  
  
 *varValue*  
 要設定; 的值請參閱 < 備註 >。  
  
 *nIndex*  
 參數的 recordset 參數集合中的序數位置。 您可以取得此值與呼叫[GetParameterCount](#getparametercount)和[GetParameterInfo](#getparameterinfo)。  
  
### <a name="remarks"></a>備註  
 參數必須有已建立為 querydef SQL 字串的一部分。 您可以依名稱或集合中的序數位置來存取參數。  
  
 指定要設定為值`COleVariant`物件。 如需設定的所需的值和類型資訊您`COleVariant`物件，請參閱類別[COleVariant](../../mfc/reference/colevariant-class.md)。  
  
##  <a name="setreturnsrecords"></a>  CDaoQueryDef::SetReturnsRecords  
 呼叫此成員函式，設定至外部資料庫的 SQL 傳遞查詢的程序的一部分。  
  
```  
void SetReturnsRecords(BOOL bReturnsRecords);
```  
  
### <a name="parameters"></a>參數  
 *bReturnsRecords*  
 傳遞**TRUE**如果在外部資料庫查詢傳回的記錄; 否則**FALSE**。  
  
### <a name="remarks"></a>備註  
 在這種情況下，您必須建立 querydef，並設定其屬性，使用其他`CDaoQueryDef`成員函式。 如需外部資料庫的說明，請參閱[SetConnect](#setconnect)。  
  
##  <a name="setsql"></a>  CDaoQueryDef::SetSQL  
 呼叫此成員函式設定 querydef 執行的 SQL 陳述式。  
  
```  
void SetSQL(LPCTSTR lpszSQL);
```  
  
### <a name="parameters"></a>參數  
 *lpszSQL*  
 字串，包含完整 SQL 陳述式，適用於執行。 這個字串的語法取決於 DBMS 的查詢目標。 如需使用 Microsoft Jet 資料庫引擎之語法的討論，請參閱 「 建置 SQL 陳述式中程式碼 」 DAO [說明] 中的主題。  
  
### <a name="remarks"></a>備註  
 典型用法`SetSQL`是 SQL 傳遞查詢中使用的 recordset 物件設定。 （如需針對目標 DBMS SQL 傳遞查詢的語法，請參閱 DBMS 的文件）。  
  
## <a name="see-also"></a>另請參閱  
 [CObject 類別](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CDaoRecordset 類別](../../mfc/reference/cdaorecordset-class.md)   
 [CDaoDatabase 類別](../../mfc/reference/cdaodatabase-class.md)   
 [CDaoTableDef 類別](../../mfc/reference/cdaotabledef-class.md)   
 [CDaoException 類別](../../mfc/reference/cdaoexception-class.md)
