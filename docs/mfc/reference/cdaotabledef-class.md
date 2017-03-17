---
title: "CDaoTableDef 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDaoTableDef
- AFXDAO/CDaoTableDef
- AFXDAO/CDaoTableDef::CDaoTableDef
- AFXDAO/CDaoTableDef::Append
- AFXDAO/CDaoTableDef::CanUpdate
- AFXDAO/CDaoTableDef::Close
- AFXDAO/CDaoTableDef::Create
- AFXDAO/CDaoTableDef::CreateField
- AFXDAO/CDaoTableDef::CreateIndex
- AFXDAO/CDaoTableDef::DeleteField
- AFXDAO/CDaoTableDef::DeleteIndex
- AFXDAO/CDaoTableDef::GetAttributes
- AFXDAO/CDaoTableDef::GetConnect
- AFXDAO/CDaoTableDef::GetDateCreated
- AFXDAO/CDaoTableDef::GetDateLastUpdated
- AFXDAO/CDaoTableDef::GetFieldCount
- AFXDAO/CDaoTableDef::GetFieldInfo
- AFXDAO/CDaoTableDef::GetIndexCount
- AFXDAO/CDaoTableDef::GetIndexInfo
- AFXDAO/CDaoTableDef::GetName
- AFXDAO/CDaoTableDef::GetRecordCount
- AFXDAO/CDaoTableDef::GetSourceTableName
- AFXDAO/CDaoTableDef::GetValidationRule
- AFXDAO/CDaoTableDef::GetValidationText
- AFXDAO/CDaoTableDef::IsOpen
- AFXDAO/CDaoTableDef::Open
- AFXDAO/CDaoTableDef::RefreshLink
- AFXDAO/CDaoTableDef::SetAttributes
- AFXDAO/CDaoTableDef::SetConnect
- AFXDAO/CDaoTableDef::SetName
- AFXDAO/CDaoTableDef::SetSourceTableName
- AFXDAO/CDaoTableDef::SetValidationRule
- AFXDAO/CDaoTableDef::SetValidationText
- AFXDAO/CDaoTableDef::m_pDAOTableDef
- AFXDAO/CDaoTableDef::m_pDatabase
dev_langs:
- C++
helpviewer_keywords:
- database classes [C++], DAO
- tabledefs [C++]
- CDaoTableDef class
- database tables [C++], attached table definition
- database tables [C++], base table definition
ms.assetid: 7c5d2254-8475-43c4-8a6c-2d32ead194c9
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
ms.openlocfilehash: 8bfd0ef3c63c243cabb0a4f841ba278fbeed4ae8
ms.lasthandoff: 02/24/2017

---
# <a name="cdaotabledef-class"></a>CDaoTableDef 類別
表示儲存的基底資料表或附加資料表定義。  
  
## <a name="syntax"></a>語法  
  
```  
class CDaoTableDef : public CObject  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CDaoTableDef::CDaoTableDef](#cdaotabledef)|建構**CDaoTableDef**物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CDaoTableDef::Append](#append)|將新的資料表加入至資料庫。|  
|[CDaoTableDef::CanUpdate](#canupdate)|傳回非零值，如果可以更新資料表 （您可以修改欄位或資料表屬性的定義）。|  
|[CDaoTableDef::Close](#close)|關閉開啟的 tabledef。|  
|[CDaoTableDef::Create](#create)|建立可加入到資料庫時使用這些資料表[附加](#append)。|  
|[CDaoTableDef::CreateField](#createfield)|呼叫來建立資料表的欄位。|  
|[CDaoTableDef::CreateIndex](#createindex)|呼叫來建立資料表的索引。|  
|[CDaoTableDef::DeleteField](#deletefield)|呼叫以從資料表中刪除欄位。|  
|[CDaoTableDef::DeleteIndex](#deleteindex)|呼叫以從資料表中刪除索引。|  
|[CDaoTableDef::GetAttributes](#getattributes)|傳回值，這個值表示的一或多個特性`CDaoTableDef`物件。|  
|[CDaoTableDef::GetConnect](#getconnect)|傳回值，可提供來源資料表的相關資訊。|  
|[CDaoTableDef::GetDateCreated](#getdatecreated)|傳回的日期和時間的基礎基底資料表`CDaoTableDef`建立物件。|  
|[CDaoTableDef::GetDateLastUpdated](#getdatelastupdated)|傳回的日期和時間的基底資料表的設計所做的最新變更。|  
|[CDaoTableDef::GetFieldCount](#getfieldcount)|傳回值，表示資料表中的欄位數目。|  
|[CDaoTableDef::GetFieldInfo](#getfieldinfo)|傳回資料表中的特定類型的欄位資訊。|  
|[CDaoTableDef::GetIndexCount](#getindexcount)|傳回資料表的索引數目。|  
|[CDaoTableDef::GetIndexInfo](#getindexinfo)|傳回特定種類的資料表索引的相關資訊。|  
|[CDaoTableDef::GetName](#getname)|傳回使用者定義資料表的名稱。|  
|[CDaoTableDef::GetRecordCount](#getrecordcount)|傳回資料表中的記錄數目。|  
|[CDaoTableDef::GetSourceTableName](#getsourcetablename)|傳回值，指定來源資料庫中的連結資料表的名稱。|  
|[CDaoTableDef::GetValidationRule](#getvalidationrule)|傳回值，驗證欄位中的資料，因為它已變更或加入至資料表。|  
|[CDaoTableDef::GetValidationText](#getvalidationtext)|傳回值，指定如果欄位物件的值不符合指定的驗證規則，會顯示您的應用程式之訊息的文字。|  
|[CDaoTableDef::IsOpen](#isopen)|傳回非零，如果資料表是開啟。|  
|[CDaoTableDef::Open](#open)|開啟儲存在資料庫中現有的 tabledef 的 TableDef 的集合。|  
|[CDaoTableDef::RefreshLink](#refreshlink)|更新附加資料表的連接資訊。|  
|[CDaoTableDef::SetAttributes](#setattributes)|設定值，這個值表示的一或多個特性`CDaoTableDef`物件。|  
|[CDaoTableDef::SetConnect](#setconnect)|設定值，這個值會提供來源資料表的相關資訊。|  
|[CDaoTableDef::SetName](#setname)|設定資料表的名稱。|  
|[CDaoTableDef::SetSourceTableName](#setsourcetablename)|設定值，指定來源資料庫中的連結資料表的名稱。|  
|[CDaoTableDef::SetValidationRule](#setvalidationrule)|設定驗證欄位中的資料，因為它已變更或加入至資料表的值。|  
|[CDaoTableDef::SetValidationText](#setvalidationtext)|設定值，指定如果欄位物件的值不符合指定的驗證規則，會顯示您的應用程式之訊息的文字。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CDaoTableDef::m_pDAOTableDef](#m_pdaotabledef)|基礎 tabledef 物件 DAO 介面的指標。|  
|[CDaoTableDef::m_pDatabase](#m_pdatabase)|這份資料表的來源資料庫。|  
  
## <a name="remarks"></a>備註  
 每個 DAO 資料庫物件會維護名為 TableDefs，其中包含所有已儲存的 DAO tabledef 物件的集合。  
  
 您操作資料表定義，使用`CDaoTableDef`物件。 例如，您可以：  
  
-   檢查有任何本機、 附加，或外部資料庫資料表中的欄位和索引結構。  
  
-   呼叫`SetConnect`和`SetSourceTableName`成員函式，以附加的資料表，並使用`RefreshLink`成員函式來更新連接來連接資料表。  
  
-   呼叫`CanUpdate`成員函式來判斷是否您可以編輯資料表中的欄位定義。  
  
-   取得或設定使用的驗證條件`GetValidationRule`和`SetValidationRule`，而`GetValidationText`和`SetValidationText`成員函式。  
  
-   使用**開啟**成員函式來建立資料表類型、 動態集或快照集類型`CDaoRecordset`物件。  
  
    > [!NOTE]
    >  DAO 資料庫類別所基礎開放式資料庫連接 (ODBC) 之 MFC 資料庫類別不同。 所有的 DAO 資料庫類別名稱有"CDao"前置詞。 您仍然可以使用 DAO 類別; 存取 ODBC 資料來源DAO 類別通常提供卓越的功能，因為它們專屬於 Microsoft Jet 資料庫引擎。  
  
### <a name="to-use-tabledef-objects-either-to-work-with-an-existing-table-or-to-create-a-new-table"></a>若要使用 tabledef 物件，使用現有的資料表，或建立新的資料表  
  
1.  在所有情況下，第一次建構`CDaoTableDef`物件，提供一個指向[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)資料表所屬的物件。  
  
2.  然後執行下列作業，按照您的需求︰  
  
    -   若要使用現有的儲存資料表，呼叫 tabledef 物件[開啟](#open)成員函式，提供儲存資料表的名稱。  
  
    -   若要建立新的資料表，呼叫 tabledef 物件[建立](#create)成員函式，提供資料表的名稱。 呼叫[CreateField](#createfield)和[CreateIndex](#createindex)將欄位和索引加入至資料表。  
  
    -   呼叫[附加](#append)藉由附加資料庫的 TableDefs 集合來儲存資料表。 **建立**tabledef 放在開啟狀態，因此在呼叫**建立**沒有呼叫**開啟**。  
  
        > [!TIP]
        >  建立已儲存的資料表最簡單的作法是建立它們，然後將它們儲存在使用 Microsoft Access 資料庫中。 然後您可以開啟，並在您的 MFC 程式碼中使用它們。  
  
 若要使用您已開啟或建立 tabledef 物件，建立並開啟`CDaoRecordset`物件，指定的名稱與 tabledef **dbOpenTable**值`nOpenType`參數。  
  
 若要使用 tabledef 物件來建立`CDaoRecordset`物件，您通常建立或開啟 tabledef （如上所述），然後建構資料錄集物件，將指標傳遞至 tabledef 物件，當您呼叫[cdaorecordset:: Open](../../mfc/reference/cdaorecordset-class.md#open)。 您傳遞 tabledef 必須處於開啟狀態。 如需詳細資訊，請參閱類別[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)。  
  
 當您完成使用 tabledef 物件時，呼叫其[關閉](../../mfc/reference/cdaorecordset-class.md#close)成員函式，然後損毀 tabledef 物件。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDaoTableDef`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxdao.h  
  
##  <a name="append"></a>CDaoTableDef::Append  
 呼叫此成員函式之後您呼叫,[建立](#create)來建立新的 tabledef 物件 tabledef 儲存在資料庫中。  
  
```  
virtual void Append();
```  
  
### <a name="remarks"></a>備註  
 函式會將物件附加至資料庫的 TableDefs 集合。 您可以使用 tabledef 作為暫存物件時定義，不加上它，但是如果您想要儲存並使用它，您必須呼叫**附加**。  
  
> [!NOTE]
>  如果您嘗試附加未命名的 tabledef （包含 null 或空字串），MFC 會擲回例外狀況。  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 附加方法 」。  
  
##  <a name="canupdate"></a>CDaoTableDef::CanUpdate  
 呼叫此成員函式，以判斷是否將基礎資料表的定義`CDaoTableDef`物件已變更。  
  
```  
BOOL CanUpdate();
```  
  
### <a name="return-value"></a>傳回值  
 如果可以修改資料表結構 （結構描述） 為非零 （新增或刪除的欄位和索引），否則為 0。  
  
### <a name="remarks"></a>備註  
 根據預設，新建立的資料表，基礎`CDaoTableDef`物件可以更新，並附加的資料表基準`CDaoTableDef`無法更新物件。 A`CDaoTableDef`物件可以是可更新，即使產生的資料錄集並不是可更新。  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 可更新屬性 」。  
  
##  <a name="cdaotabledef"></a>CDaoTableDef::CDaoTableDef  
 建構**CDaoTableDef**物件。  
  
```  
CDaoTableDef(CDaoDatabase* pDatabase);
```  
  
### <a name="parameters"></a>參數  
 `pDatabase`  
 指標[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)物件。  
  
### <a name="remarks"></a>備註  
 之後建構物件，您必須呼叫[建立](#create)或[開啟](#open)成員函式。 當您完成物件時，您必須呼叫其[關閉](#close)成員函式，並摧毀`CDaoTableDef`物件。  
  
##  <a name="close"></a>CDaoTableDef::Close  
 呼叫此成員函式，以關閉及釋放 tabledef 物件。  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>備註  
 通常在呼叫**關閉**，如果它已配置，刪除 tabledef 物件**新**。  
  
 您可以呼叫[開啟](#open)，然後再次呼叫**關閉**。 這可讓您重複使用 tabledef 物件。  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 關閉方法 」。  
  
##  <a name="create"></a>CDaoTableDef::Create  
 呼叫此成員函式，來建立新儲存的資料表。  
  
```  
virtual void Create(
    LPCTSTR lpszName,  
    long lAttributes = 0,  
    LPCTSTR lpszSrcTable = NULL,  
    LPCTSTR lpszConnect = NULL);
```  
  
### <a name="parameters"></a>參數  
 `lpszName`  
 包含的資料表名稱的字串指標。  
  
 `lAttributes`  
 Tabledef 物件所表示的資料表的特性對應值。 您可以使用位元 OR 結合任何下列常數︰  
  
|常數|說明|  
|--------------|-----------------|  
|**dbAttachExclusive**|使用 Microsoft Jet 資料庫引擎的資料庫，表示資料表是以獨佔開啟附加的資料表。|  
|**dbAttachSavePWD**|使用 Microsoft Jet 資料庫引擎的資料庫，表示使用者識別碼和密碼附加的資料表會儲存連接資訊。|  
|**dbSystemObject**|表示資料表是由 Microsoft Jet 資料庫引擎所提供的系統資料表。|  
|**dbHiddenObject**|表示資料表是由 Microsoft Jet 資料庫引擎所提供的隱藏的資料表。|  
  
 *lpszSrcTable*  
 包含來源資料表名稱的字串指標。 依預設，這個值會初始化為**NULL**。  
  
 `lpszConnect`  
 字串，包含預設的連接字串的指標。 依預設，這個值會初始化為**NULL**。  
  
### <a name="remarks"></a>備註  
 一旦您擁有名為 tabledef，您就可以呼叫[附加](#append)tabledef 儲存資料庫的 TableDefs 集合中。 在呼叫**附加**、 tabledef 處於開啟狀態，以及您可以使用它來建立[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)物件。  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 CreateTableDef 方法 」。  
  
##  <a name="createfield"></a>CDaoTableDef::CreateField  
 呼叫此成員函式，將欄位加入至資料表。  
  
```  
void CreateField(
    LPCTSTR lpszName,  
    short nType,  
    long lSize,  
    long lAttributes = 0);  
  
void CreateField(CDaoFieldInfo& fieldinfo);
```  
  
### <a name="parameters"></a>參數  
 `lpszName`  
 指標，指定這個欄位的名稱的字串運算式。  
  
 `nType`  
 值，指出欄位的資料型別。 設定可以是下列值之一︰  
  
|類型|大小 (位元組)|說明|  
|----------|--------------------|-----------------|  
|**dbBoolean**|1 個位元組|BOOL|  
|**dbByte**|1|BYTE|  
|**dbInteger**|2|int|  
|**dbLong**|4|long|  
|**dbCurrency**|8|貨幣 ( [COleCurrency](../../mfc/reference/colecurrency-class.md))|  
|**dbSingle**|4|浮動|  
|**dbDouble**|8|double|  
|**dbDate**|8|日期/時間 ( [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md))|  
|**dbText**|1 – 255|文字 ( [CString](../../atl-mfc-shared/reference/cstringt-class.md))|  
|**dbLongBinary**|0|長度的二進位檔 （OLE 物件）， [CLongBinary](../../mfc/reference/clongbinary-class.md)或[CByteArray](../../mfc/reference/cbytearray-class.md)|  
|**dbMemo**|0|附註 ( [CString](../../atl-mfc-shared/reference/cstringt-class.md))|  
  
 `lSize`  
 值，指出最大大小 （位元組） 的欄位，包含文字或包含文字或數值的欄位的固定的大小。 `lSize`文字欄位以外，所有的參數會被忽略。  
  
 `lAttributes`  
 可以使用位元 OR 結合的欄位，並且特性對應的值。  
  
|常數|描述|  
|--------------|-----------------|  
|**dbFixedField**|欄位大小被固定的 （數值欄位的預設值）。|  
|**dbVariableField**|欄位大小是變數 （文字欄位）。|  
|**dbAutoIncrField**|新記錄的欄位值不能變更的唯一長整數，會自動遞增。 僅支援 Microsoft Jet 資料庫資料表。|  
|**dbUpdatableField**|可以變更欄位值。|  
|**dbDescending**|欄位以遞減排序 (Z – A 或 100-0) （僅適用於索引物件的欄位集合中的欄位物件） 的順序。 如果您省略這個常數，以遞增排序的欄位 (A – Z 或 0-100) 順序 （預設值）。|  
  
 `fieldinfo`  
 參考[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)結構。  
  
### <a name="remarks"></a>備註  
 A **DAOField**會建立並附加至的欄位集合 (OLE) 物件**DAOTableDef** (OLE) 物件。 除了用來檢查物件屬性，您也可以使用`CDaoFieldInfo`來建構在 tabledef 中建立新欄位的輸入的參數。 第一版`CreateField`會更容易使用，但如果您想要較細微的控制，您可以使用第二版`CreateField`，這個方法會接受`CDaoFieldInfo`參數。  
  
 如果您使用的版本`CreateField`採用`CDaoFieldInfo`，您必須仔細設定參數的下列成員的每個`CDaoFieldInfo`結構︰  
  
- **m_strName**  
  
- `m_nType`  
  
- **m_lSize**  
  
- **m_lAttributes**  
  
- **m_bAllowZeroLength**  
  
 其餘成員`CDaoFieldInfo`應設為**0**， **FALSE**，則為空字串，視您的成員，或`CDaoException`可能會發生。  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 CreateField 方法 」。  
  
##  <a name="createindex"></a>CDaoTableDef::CreateIndex  
 呼叫此函式可新增至資料表的索引。  
  
```  
void CreateIndex(CDaoIndexInfo& indexinfo);
```  
  
### <a name="parameters"></a>參數  
 `indexinfo`  
 參考[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)結構。  
  
### <a name="remarks"></a>備註  
 索引會指定從資料庫資料表，及接受重複的記錄存取記錄的順序。 索引也會提供有效率的方式存取資料。  
  
 您不需要建立索引的資料表，但在大型、 未編製索引的資料表中，存取特定的記錄或建立資料錄集可能需要很長的時間。 相反地，建立太多索引降低更新、 附加及刪除作業，因為所有的索引會自動更新。 當您決定建立哪些索引，請考慮這些因素。  
  
 下列成員的`CDaoIndexInfo`結構必須設定︰  
  
- **m_strName**必須提供名稱。  
  
- `m_pFieldInfos`陣列必須指向`CDaoIndexFieldInfo`結構。  
  
- `m_nFields`必須指定陣列中的欄位數目`CDaoFieldInfo`結構。  
  
 剩餘的成員將會忽略的如果設定為**FALSE**。 此外， **m_lDistinctCount**成員會在建立索引期間忽略。  
  
##  <a name="deletefield"></a>CDaoTableDef::DeleteField  
 呼叫此成員函式，若要移除欄位，並使其無法存取。  
  
```  
void DeleteField(LPCTSTR lpszName);  
void DeleteField(int nIndex);
```  
  
### <a name="parameters"></a>參數  
 `lpszName`  
 指標是與現有欄位名稱的字串運算式。  
  
 `nIndex`  
 資料表的以零為起始欄位集合中，依索引查閱欄位的索引。  
  
### <a name="remarks"></a>備註  
 您可以不附加到資料庫的新物件上使用此成員函式或當[CanUpdate](#canupdate)傳回非零值。  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 刪除方法 」。  
  
##  <a name="deleteindex"></a>CDaoTableDef::DeleteIndex  
 呼叫此成員函式來刪除基礎資料表中的索引。  
  
```  
void DeleteIndex(LPCTSTR lpszName);  
void DeleteIndex(int nIndex);
```  
  
### <a name="parameters"></a>參數  
 `lpszName`  
 指標是現有的索引名稱的字串運算式。  
  
 `nIndex`  
 資料庫的以零為起始 TableDefs 集合中，依索引查閱的索引物件的陣列索引。  
  
### <a name="remarks"></a>備註  
 您可以使用此成員函式在新的物件尚未附加到資料庫，或當[CanUpdate](#canupdate)傳回非零值。  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 刪除方法 」。  
  
##  <a name="getattributes"></a>CDaoTableDef::GetAttributes  
 如`CDaoTableDef`物件，傳回的值會指定所表示的資料表的特性`CDaoTableDef`物件，而且可以是加總兩個常數︰  
  
```  
long GetAttributes();
```  
  
### <a name="return-value"></a>傳回值  
 傳回值，這個值表示的一或多個特性`CDaoTableDef`物件。  
  
### <a name="remarks"></a>備註  
  
|常數|說明|  
|--------------|-----------------|  
|**dbAttachExclusive**|使用 Microsoft Jet 資料庫引擎的資料庫，表示資料表是以獨佔開啟附加的資料表。|  
|**dbAttachSavePWD**|使用 Microsoft Jet 資料庫引擎的資料庫，表示使用者識別碼和密碼附加的資料表會儲存連接資訊。|  
|**dbSystemObject**|表示資料表是由 Microsoft Jet 資料庫引擎所提供的系統資料表。|  
|**dbHiddenObject**|表示資料表是由 Microsoft Jet 資料庫引擎所提供的隱藏的資料表。|  
|**dbAttachedTable**|表示資料表是從非 ODBC 資料庫，例如 Paradox 資料庫連接的資料表。|  
|**dbAttachedODBC**|指出資料表附加從 ODBC 資料庫，例如 Microsoft SQL Server 資料表。|  
  
 系統資料表是由 Microsoft Jet 資料庫引擎，以包含各種不同的內部資訊的資料表。  
  
 隱藏的資料表是由 Microsoft Jet 資料庫引擎建立暫時使用的資料表。  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 屬性屬性 」。  
  
##  <a name="getconnect"></a>CDaoTableDef::GetConnect  
 呼叫此成員函式，以取得資料來源的連接字串。  
  
```  
CString GetConnect();
```  
  
### <a name="return-value"></a>傳回值  
 A`CString`物件，其中包含資料表的路徑及資料庫類型。  
  
### <a name="remarks"></a>備註  
 如`CDaoTableDef`物件，表示附加的資料表，`CString`物件包含的一或兩個部分 （資料庫類型指定名稱和資料庫的路徑）。  
  
 下表所示的路徑是包含資料庫檔案的目錄的完整路徑和前面必須有識別碼 」 資料庫 = 」。 在某些情況下 （如 Microsoft Excel 與 Microsoft Jet 資料庫） 中的資料庫路徑引數中包含特定的檔案名稱。  
  
 中的資料表[CDaoTableDef::SetConnect](#setconnect)顯示可能的資料庫類型及其對應的資料庫指定名稱和路徑︰  
  
 Microsoft Jet 資料庫基底資料表的規範，空字串 ("")。  
  
 如果需要密碼但未提供，ODBC 驅動程式就會顯示登入對話方塊第一次資料表存取時，另一次如果連線已關閉並重新開啟。 如果附加的資料表有**dbAttachSavePWD**屬性，登入提示不會重新開啟資料表時。  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 連接屬性 」。  
  
##  <a name="getdatecreated"></a>CDaoTableDef::GetDateCreated  
 呼叫此函式可決定日期和時間資料表基礎`CDaoTableDef`建立物件。  
  
```  
COleDateTime GetDateCreated();
```  
  
### <a name="return-value"></a>傳回值  
 值，其中包含日期和時間的基礎資料表建立`CDaoTableDef`物件。  
  
### <a name="remarks"></a>備註  
 日期和時間設定被衍生自的基底資料表建立或上次更新的電腦。 在多使用者環境中，使用者應該直接從檔案伺服器，以避免不一致的地方，取得這些設定也就是說，所有用戶端應該使用 「 標準 」 的時間來源，可能是從一部伺服器。  
  
 如需相關資訊，請參閱 DAO 說明主題 「 DateCreated LastUpdated 屬性 」。  
  
##  <a name="getdatelastupdated"></a>CDaoTableDef::GetDateLastUpdated  
 呼叫此函式可決定日期和時間資料表基礎**CDaoTableDef**上次更新物件。  
  
```  
COleDateTime GetDateLastUpdated();
```  
  
### <a name="return-value"></a>傳回值  
 包含基礎資料表的日期和時間的值**CDaoTableDef**上次更新物件。  
  
### <a name="remarks"></a>備註  
 日期和時間設定被衍生自的基底資料表建立或上次更新的電腦。 在多使用者環境中，使用者應該直接從檔案伺服器，以避免不一致的地方，取得這些設定也就是說，所有用戶端應該使用 「 標準 」 的時間來源，可能是從一部伺服器。  
  
 如需相關資訊，請參閱 DAO 說明主題 「 DateCreated LastUpdated 屬性 」。  
  
##  <a name="getfieldcount"></a>CDaoTableDef::GetFieldCount  
 呼叫此成員函式擷取資料表中定義的欄位數目。  
  
```  
short GetFieldCount();
```  
  
### <a name="return-value"></a>傳回值  
 資料表中的欄位數目。  
  
### <a name="remarks"></a>備註  
 如果其值為 0，則沒有物件儲存在集合上。  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 計數屬性 」。  
  
##  <a name="getfieldinfo"></a>CDaoTableDef::GetFieldInfo  
 呼叫此成員函式，以取得各種 tabledef 中定義欄位的相關資訊。  
  
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
 資料表的以零為起始欄位集合中，依索引查閱欄位物件的索引。  
  
 `fieldinfo`  
 參考[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)結構。  
  
 `dwInfoOptions`  
 指定要擷取之欄位的相關資訊的選項。 此處列出可用的選項以及它們會導致函式傳回︰  
  
- `AFX_DAO_PRIMARY_INFO`（預設值）屬性名稱、 類型、 大小。 使用此選項以最快的效能。  
  
- `AFX_DAO_SECONDARY_INFO`主要的資訊，加上︰ 序數位置，必要時，允許零長度、 定序順序，外部索引名稱、 來源欄位中，來源資料表  
  
- `AFX_DAO_ALL_INFO`主要和次要的資訊，加上︰ 驗證規則，驗證文字，預設值  
  
 `lpszName`  
 依名稱查閱欄位物件的名稱指標。 最多 64 個字元的唯一名稱欄位的字串名稱。  
  
### <a name="remarks"></a>備註  
 一個版本的函式可讓您查詢索引欄位。 另一個版本可讓您依名稱查閱欄位。  
  
 傳回資訊的說明，請參閱[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)結構。 此結構具有成員資訊的描述中列出的項目所對應`dwInfoOptions`。 當您要求一個層級的資訊時，您會取得任何先前的層資訊。  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 屬性屬性 」。  
  
##  <a name="getindexcount"></a>CDaoTableDef::GetIndexCount  
 呼叫此成員函式來取得資料表的索引編號。  
  
```  
short GetIndexCount();
```  
  
### <a name="return-value"></a>傳回值  
 資料表的索引數目。  
  
### <a name="remarks"></a>備註  
 如果其值為 0，則沒有索引儲存在集合上。  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 計數屬性 」。  
  
##  <a name="getindexinfo"></a>CDaoTableDef::GetIndexInfo  
 呼叫此成員函式，以取得各種 tabledef 中定義索引的相關資訊。  
  
```  
void GetIndexInfo(
    int nIndex,  
    CDaoIndexInfo& indexinfo,  
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

 
void GetIndexInfo(
    LPCTSTR lpszName,  
    CDaoIndexInfo& indexinfo,  
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 在資料表的以零為起始的索引集合中，查閱的集合中位置的索引物件之數字索引。  
  
 `indexinfo`  
 參考[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)結構。  
  
 `dwInfoOptions`  
 指定要擷取索引的相關資訊的選項。 此處列出可用的選項以及它們會導致函式傳回︰  
  
- `AFX_DAO_PRIMARY_INFO`名稱、 欄位資訊欄位。 使用此選項以最快的效能。  
  
- `AFX_DAO_SECONDARY_INFO`主要的資訊，加上︰ 主要、 唯一、 叢集、 忽略 null 值，需要外部  
  
- `AFX_DAO_ALL_INFO`主要和次要的資訊，加上︰ 相異計數  
  
 `lpszName`  
 依名稱查閱的索引物件的名稱指標。  
  
### <a name="remarks"></a>備註  
 一個版本的函式可讓您查詢的集合中位置的索引。 另一個版本可讓您依名稱查閱索引。  
  
 傳回資訊的說明，請參閱[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)結構。 此結構具有成員資訊的描述中列出的項目所對應`dwInfoOptions`。 當您要求一個層級的資訊時，您會取得任何先前的層資訊。  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 屬性屬性 」。  
  
##  <a name="getname"></a>CDaoTableDef::GetName  
 呼叫此成員函式，以取得基礎資料表的使用者定義名稱。  
  
```  
CString GetName();
```  
  
### <a name="return-value"></a>傳回值  
 使用者定義資料表的名稱。  
  
### <a name="remarks"></a>備註  
 這個名稱以字母為開頭，而且可以包含最多 64 個字元。 它可以包含數字和底線字元，但不能包含標點符號或空格。  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 名稱屬性 」。  
  
##  <a name="getrecordcount"></a>CDaoTableDef::GetRecordCount  
 呼叫此成員函式，以找出幾筆記錄的在`CDaoTableDef`物件。  
  
```  
long GetRecordCount();
```  
  
### <a name="return-value"></a>傳回值  
 存取 tabledef 物件中的記錄數目。  
  
### <a name="remarks"></a>備註  
 呼叫`GetRecordCount`資料表類型`CDaoTableDef`物件會反映出資料表中記錄的近似數目及加入和刪除資料表記錄時立即影響。 回復交易會出現的記錄計數的一部分，直到您呼叫[CDaoWorkSpace::CompactDatabase](../../mfc/reference/cdaoworkspace-class.md#compactdatabase)。 A`CDaoTableDef`物件沒有記錄已記錄計數 屬性設定為 0。 使用附加的資料表或 ODBC 資料庫時`GetRecordCount`一律會傳回 –&1;。  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 RecordCount 屬性 」。  
  
##  <a name="getsourcetablename"></a>CDaoTableDef::GetSourceTableName  
 呼叫此成員函式，以擷取附加來源資料庫中資料表的名稱。  
  
```  
CString GetSourceTableName();
```  
  
### <a name="return-value"></a>傳回值  
 A`CString`物件，指定附加的資料表，則為空字串的來源名稱，如果原生資料的資料表。  
  
### <a name="remarks"></a>備註  
 附加的資料表是連結至 Microsoft Jet 資料庫的另一個資料庫中的資料表。 連結資料表的資料會保留在外部資料庫，其中由其他應用程式操作。  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 SourceTableName 屬性 」。  
  
##  <a name="getvalidationrule"></a>CDaoTableDef::GetValidationRule  
 呼叫此成員函式擷取 tabledef 的驗證規則。  
  
```  
CString GetValidationRule();
```  
  
### <a name="return-value"></a>傳回值  
 A **CString**驗證欄位中的資料，因為它已變更或加入至資料表的物件。  
  
### <a name="remarks"></a>備註  
 與更新作業所使用的驗證規則。 如果 tabledef 包含驗證規則，更新該 tabledef 必須符合預先決定的準則，才能在資料變更。 如果變更不符合準則，其中包含的值的例外狀況[GetValidationText](#getvalidationtext)就會擲回。 如`CDaoTableDef`物件，這`CString`是唯讀的附加的資料表，以及在基底資料表的讀取/寫入。  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 ValidationRule 屬性 」。  
  
##  <a name="getvalidationtext"></a>CDaoTableDef::GetValidationText  
 呼叫此函式可擷取使用者輸入的資料不符合驗證規則時要顯示的字串。  
  
```  
CString GetValidationText();
```  
  
### <a name="return-value"></a>傳回值  
 A`CString`物件，指定如果使用者輸入不符合驗證規則的資料顯示的文字。  
  
### <a name="remarks"></a>備註  
 如`CDaoTableDef`物件，這`CString`是唯讀的附加的資料表，以及在基底資料表的讀取/寫入。  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 驗證屬性 」。  
  
##  <a name="isopen"></a>CDaoTableDef::IsOpen  
 呼叫此成員函式，以判斷是否`CDaoTableDef`物件目前已開啟。  
  
```  
BOOL IsOpen() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果為非零`CDaoTableDef`物件為開放型別，否則為 0。  
  
### <a name="remarks"></a>備註  
  
##  <a name="m_pdatabase"></a>CDaoTableDef::m_pDatabase  
 包含一個指向[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)這份資料表的物件。  
  
### <a name="remarks"></a>備註  
  
##  <a name="m_pdaotabledef"></a>CDaoTableDef::m_pDAOTableDef  
 包含 DAO tabledef 物件基礎的 OLE 介面的指標`CDaoTableDef`物件。  
  
### <a name="remarks"></a>備註  
 如果您需要直接存取 DAO 介面，請使用這個指標。  
  
##  <a name="open"></a>CDaoTableDef::Open  
 呼叫此成員函式，以開啟 tabledef 先前儲存在資料庫中的 TableDef 的集合。  
  
```  
virtual void Open(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>參數  
 `lpszName`  
 指定資料表名稱的字串指標。  
  
### <a name="remarks"></a>備註  
  
##  <a name="refreshlink"></a>CDaoTableDef::RefreshLink  
 呼叫此成員函式，來更新附加資料表的連接資訊。  
  
```  
void RefreshLink();
```  
  
### <a name="remarks"></a>備註  
 藉著呼叫更改附加資料表的連接資訊[SetConnect](#setconnect)對應`CDaoTableDef`物件，然後使用`RefreshLink`成員函式可更新的資訊。 當您呼叫`RefreshLink`，附加的資料表內容不會變更。  
  
 若要強制修改連接資訊才會生效，所有已開啟[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)必須關閉此 tabledef 為基礎的物件。  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 RefreshLink 方法 」。  
  
##  <a name="setattributes"></a>CDaoTableDef::SetAttributes  
 設定值，這個值表示的一或多個特性`CDaoTableDef`物件。  
  
```  
void SetAttributes(long lAttributes);
```  
  
### <a name="parameters"></a>參數  
 `lAttributes`  
 所表示的資料表的特性`CDaoTableDef`物件，而且可以是加總兩個常數︰  
  
|常數|說明|  
|--------------|-----------------|  
|**dbAttachExclusive**|使用 Microsoft Jet 資料庫引擎的資料庫，表示資料表是以獨佔開啟附加的資料表。|  
|**dbAttachSavePWD**|使用 Microsoft Jet 資料庫引擎的資料庫，表示使用者識別碼和密碼附加的資料表會儲存連接資訊。|  
|**dbSystemObject**|表示資料表是由 Microsoft Jet 資料庫引擎所提供的系統資料表。|  
|**dbHiddenObject**|表示資料表是由 Microsoft Jet 資料庫引擎所提供的隱藏的資料表。|  
  
### <a name="remarks"></a>備註  
 當設定多個屬性，您可以結合它們可以加總適當使用位元 OR 運算子的常數。 設定**dbAttachExclusive**未附加的資料表上會產生例外狀況。 結合下列的值也產生的例外狀況︰  
  
- **dbAttachExclusive |dbAttachedODBC**  
  
- **dbAttachSavePWD |dbAttachedTable**  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 屬性屬性 」。  
  
##  <a name="setconnect"></a>CDaoTableDef::SetConnect  
 如`CDaoTableDef`物件，表示附加的資料表，string 物件 （資料庫類型指定名稱和資料庫的路徑） 的一或兩個部分所組成。  
  
```  
void SetConnect(LPCTSTR lpszConnect);
```  
  
### <a name="parameters"></a>參數  
 `lpszConnect`  
 指標，指定要傳遞給 ODBC 或可安裝的 ISAM 驅動程式的其他參數的字串運算式。  
  
### <a name="remarks"></a>備註  
 下表所示的路徑是包含資料庫檔案的目錄的完整路徑和前面必須有識別碼 」 資料庫 = 」。 在某些情況下 （如 Microsoft Excel 與 Microsoft Jet 資料庫） 中的資料庫路徑引數中包含特定的檔案名稱。  
  
> [!NOTE]
>  在表單的路徑陳述式中不包含等號前後的空白字元 」 資料庫 = 磁碟機︰\\\path 」。 這會導致擲回例外狀況和連線失敗。  
  
 下表顯示可能的資料庫類型及其對應的資料庫指定名稱和路徑︰  
  
|資料庫類型|指定名稱|路徑|  
|-------------------|---------------|----------|  
|使用 Jet 資料庫引擎的資料庫|"[ `database`];"|" `drive`:\\\ *path*\\\ *filename*.MDB 」|  
|dBASE III|「 dBASE III;"|" `drive`:\\\ *path*"|  
|dBASE IV|「 dBASE IV;"|" `drive`:\\\ *path*"|  
|dBASE 5|「 dBASE 5.0;"|" `drive`:\\\ *path*"|  
|Paradox 3.x|「 Paradox 3.x;"|" `drive`:\\\ *path*"|  
|Paradox 4.x|「 Paradox 4.x;"|" `drive`:\\\ *path*"|  
|Paradox 5.x|「 Paradox 5.x;"|" `drive`:\\\ *path*"|  
|Excel 3.0|「 Excel 3.0 」;|" `drive`:\\\ *path*\\\ *filename*.XLS 」|  
|Excel 4.0|「 Excel 4.0"。|" `drive`:\\\ *path*\\\ *filename*.XLS 」|  
|Excel 5.0 或 Excel 95|「 Excel 5.0 」;|" `drive`:\\\ *path*\\\ *filename*.XLS 」|  
|Excel 97|「 Excel 8.0 」;|" `drive`:\\\ *path*\ *filename*.XLS 」|  
|HTML 匯入|「 HTML 匯入 」。|" `drive`:\\\ *path*\ *filename*"|  
|HTML 匯出|「 HTML 匯出 」。|" `drive`:\\\ *path*"|  
|Text|「 文字 」。|「 磁碟機︰\\\path"|  
|ODBC|「 ODBC。資料庫 = `database`;UID= *user*;PWD =*密碼*;DSN = *datasourcename;*LOGINTIMEOUT =*秒;*」（這可能不是所有伺服器的完整連接字串，它只是一個範例。 它是非常重要不具有參數之間的空格。）|無|  
|Exchange|「 交換;<br /><br /> MAPILEVEL = *folderpath*;<br /><br /> [TABLETYPE = {0 | 1};]<br /><br /> [設定檔 =*設定檔*;]<br /><br /> [PWD =*密碼*;]<br /><br /> [DATABASE = `database`;] 」|*"drive*:\\\ *path*\\\ *filename*.MDB 」|  
  
> [!NOTE]
>  從 DAO 3.5 開始，已不再支援 Btrieve。  
  
 您必須使用雙反斜線 (\\\\) 中的連接字串。 如果您已修改現有的連接使用的屬性`SetConnect`，接下來必須呼叫[RefreshLink](#refreshlink)。 如果您要初始化使用的連接屬性`SetConnect`，您需要不呼叫`RefreshLink`，但您應該選擇這樣做，首先會附加 tabledef。  
  
 如果需要密碼但未提供，ODBC 驅動程式就會顯示登入對話方塊第一次資料表存取時，另一次如果連線已關閉並重新開啟。  
  
 您可以設定的連接字串`CDaoTableDef`所提供的來源引數物件**建立**成員函式。 您可以檢查以判斷型別、 路徑、 使用者識別碼、 密碼或資料庫的 ODBC 資料來源的設定。 如需詳細資訊，請參閱特定的驅動程式的文件。  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 連接屬性 」。  
  
##  <a name="setname"></a>CDaoTableDef::SetName  
 呼叫此成員函式設定使用者定義資料表的名稱。  
  
```  
void SetName(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>參數  
 `lpszName`  
 指標指定的資料表名稱的字串運算式。  
  
### <a name="remarks"></a>備註  
 名稱必須以字母開頭，並可以包含最多 64 個字元。 它可以包含數字和底線字元，但不能包含標點符號或空格。  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 名稱屬性 」。  
  
##  <a name="setsourcetablename"></a>CDaoTableDef::SetSourceTableName  
 呼叫此成員函式，來指定連接的資料表名稱或基底資料表的名稱在其上`CDaoTableDef`物件為基礎，存在於資料的原始來源。  
  
```  
void SetSourceTableName(LPCTSTR lpszSrcTableName);
```  
  
### <a name="parameters"></a>參數  
 *lpszSrcTableName*  
 指標，指定外部資料庫中的資料表名稱的字串運算式。 基底資料表中，設定為空字串 ("")。  
  
### <a name="remarks"></a>備註  
 然後您必須呼叫[RefreshLink](#refreshlink)。 此屬性設定值是空的基底資料表和讀取/寫入附加的資料表或未附加至集合的物件。  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 SourceTableName 屬性 」。  
  
##  <a name="setvalidationrule"></a>CDaoTableDef::SetValidationRule  
 呼叫此成員函式設定 tabledef 的驗證規則。  
  
```  
void SetValidationRule(LPCTSTR lpszValidationRule);
```  
  
### <a name="parameters"></a>參數  
 *lpszValidationRule*  
 驗證作業的字串運算式的指標。  
  
### <a name="remarks"></a>備註  
 與更新作業所使用的驗證規則。 如果 tabledef 包含驗證規則，更新該 tabledef 必須符合預先決定的準則，才能在資料變更。 如果變更不符合準則，包含文字的例外狀況[GetValidationText](#getvalidationtext)隨即出現。  
  
 使用 Microsoft Jet 資料庫引擎的資料庫支援驗證。 運算式不能參考使用者定義函式、 網域彙總函式、 SQL 彙總函式或查詢。 驗證規則`CDaoTableDef`物件可以參考該物件中的多個欄位。  
  
 例如，針對名為欄位`hire_date`和`termination_date`，驗證規則可能是︰  
  
 [!code-cpp[NVC_MFCDatabase #&34;](../../mfc/codesnippet/cpp/cdaotabledef-class_1.cpp)]  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 ValidationRule 屬性 」。  
  
##  <a name="setvalidationtext"></a>CDaoTableDef::SetValidationText  
 呼叫此成員函式設定的驗證規則的例外狀況文字`CDaoTableDef`支援 Microsoft Jet 資料庫引擎的基礎基底資料表的物件。  
  
```  
void SetValidationText(LPCTSTR lpszValidationText);
```  
  
### <a name="parameters"></a>參數  
 *lpszValidationText*  
 指定如果輸入資料顯示的文字的字串運算式的指標無效。  
  
### <a name="remarks"></a>備註  
 您無法設定驗證的文字附加的資料表。  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 驗證屬性 」。  
  
## <a name="see-also"></a>另請參閱  
 [CObject 類別](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CDaoDatabase 類別](../../mfc/reference/cdaodatabase-class.md)   
 [CDaoRecordset 類別](../../mfc/reference/cdaorecordset-class.md)

