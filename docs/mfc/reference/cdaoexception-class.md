---
title: "CDaoException 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDaoException
dev_langs:
- C++
helpviewer_keywords:
- errors [C++], DAO
- CDaoException class
- DAO (Data Access Objects), exceptions
- exceptions, in MFC DAO classes
- Errors collection, DAO
- collections, DAO errors
ms.assetid: b2b01fa9-7ce2-42a1-842e-40f13dc50da4
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: d1cb1c6dbe50d383981af03cc97d1977be12a5f6
ms.lasthandoff: 02/24/2017

---
# <a name="cdaoexception-class"></a>CDaoException 類別
表示以資料存取物件 (DAO) 為基礎之 MFC 資料庫類別所引發的例外狀況。  
  
## <a name="syntax"></a>語法  
  
```  
class CDaoException : public CException  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CDaoException::CDaoException](#cdaoexception)|建構 `CDaoException` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CDaoException::GetErrorCount](#geterrorcount)|資料庫引擎的錯誤集合中傳回錯誤的數目。|  
|[CDaoException::GetErrorInfo](#geterrorinfo)|錯誤集合中傳回特定的錯誤物件的相關資訊時發生錯誤。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CDaoException::m_nAfxDaoError](#m_nafxdaoerror)|包含 MFC DAO 類別中的任何錯誤的延伸的錯誤碼。|  
|[CDaoException::m_pErrorInfo](#m_perrorinfo)|指標[CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md)物件，其中包含一個 DAO 錯誤物件的相關資訊。|  
|[CDaoException::m_scode](#m_scode)|[SCODE](#m_scode)與錯誤相關聯的值。|  
  
## <a name="remarks"></a>備註  
 類別包含可用來判斷造成例外狀況的公用資料成員。 `CDaoException`物件的建構與 DAO 資料庫類別的成員函式所擲回。  
  
> [!NOTE]
>  DAO 資料庫類別所基礎開放式資料庫連接 (ODBC) 之 MFC 資料庫類別不同。 所有的 DAO 資料庫類別名稱有"CDao"前置詞。 您仍然可以使用 DAO 類別存取 ODBC 資料來源。 一般情況下，根據 DAO MFC 類別會更有能力比 ODBC; 架構的 MFC 類別DAO 架構類別可以存取資料，包括透過 ODBC 驅動程式，透過自己的資料庫引擎。 DAO 架構類別也支援資料定義語言 (DDL) 作業，例如加入資料表透過類別，而不需要直接呼叫 DAO。 在 ODBC 類別所擲回的例外狀況的資訊，請參閱[CDBException](../../mfc/reference/cdbexception-class.md)。  
  
 您可以存取的範圍內的例外狀況物件[攔截](../../mfc/reference/exception-processing.md#catch)運算式。 您也可以擲回`CDaoException`物件從自己的程式碼與[AfxThrowDaoException](../../mfc/reference/exception-processing.md#afxthrowdaoexception)全域函式。  
  
 在 MFC 中，所有的 DAO 錯誤會以類型的例外狀況表示`CDaoException`。 當您攔截這類型的例外狀況時，您可以使用`CDaoException`成員函式來擷取儲存在資料庫引擎的錯誤集合中任何 DAO 錯誤物件的資訊。 每個錯誤發生時，一或多個錯誤物件會放置在錯誤集合。 （通常集合只包含一個錯誤物件; 如果您使用 ODBC 資料來源，您會得到的多個錯誤物件）。當另一個 DAO 作業會產生錯誤時，錯誤集合會進行清除，和新的 error 物件放在錯誤集合。 不會產生錯誤的 DAO 作業有不會影響錯誤集合。  
  
 DAO 錯誤代碼，請參閱 DAOERR 的檔案。H. 如需相關資訊，請參閱 「 可截獲資料存取錯誤 」 DAO 說明中的主題。  
  
 如需有關的一般情況下，或將例外狀況處理`CDaoException`物件，請參閱文章[例外狀況處理 (MFC)](../../mfc/exception-handling-in-mfc.md)和[例外狀況︰ 資料庫例外狀況](../../mfc/exceptions-database-exceptions.md)。 第二篇文章包含說明例外狀況處理在 DAO 中的範例程式碼。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `CDaoException`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxdao.h  
  
##  <a name="a-namecdaoexceptiona--cdaoexceptioncdaoexception"></a><a name="cdaoexception"></a>CDaoException::CDaoException  
 建構 `CDaoException` 物件。  
  
```  
CDaoException();
```  
  
### <a name="remarks"></a>備註  
 一般來說，架構建立例外狀況物件，其程式碼擲回例外狀況時。 您很少需要明確建構例外狀況物件。 如果您想要擲回`CDaoException`從自己的程式碼呼叫全域函式[AfxThrowDaoException](../../mfc/reference/exception-processing.md#afxthrowdaoexception)。  
  
 不過，您可能要明確地建立例外狀況物件，如果您要進行直接呼叫 DAO 透過 MFC 類別會封裝 DAO 介面指標。 在此情況下，您可能需要從 DAO 擷取資訊時發生錯誤。 假設當您透過工作區的資料庫集合的 DAODatabases 介面呼叫 DAO 方法在 DAO 中發生錯誤。  
  
##### <a name="to-retrieve-the-dao-error-information"></a>若要擷取 DAO 資訊時發生錯誤  
  
1.  建構`CDaoException`物件。  
  
2.  呼叫例外狀況物件的[GetErrorCount](#geterrorcount)成員函式來判斷在資料庫引擎的錯誤集合中有多少錯誤物件。 (一般而言，只有一個，除非您使用 ODBC 資料來源。)  
  
3.  呼叫例外狀況物件的[GetErrorInfo](#geterrorinfo)成員函式一次擷取一個特定的錯誤物件，在集合中，透過例外狀況物件的索引。 例外狀況物件視為一個 DAO 錯誤物件的 proxy。  
  
4.  檢查目前[CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md)結構`GetErrorInfo`傳回[m_pErrorInfo](#m_perrorinfo)資料成員。 其成員提供 DAO 錯誤的相關資訊。  
  
5.  在 ODBC 資料來源，重複步驟 3 和 4，如有需要如需詳細的錯誤物件。  
  
6.  如果您建構在堆積上的例外狀況物件，將它與刪除**刪除**完成後的運算子。  
  
 如需 MFC DAO 類別中的錯誤處理的詳細資訊，請參閱文章[例外狀況︰ 資料庫例外狀況](../../mfc/exceptions-database-exceptions.md)。  
  
##  <a name="a-namegeterrorcounta--cdaoexceptiongeterrorcount"></a><a name="geterrorcount"></a>CDaoException::GetErrorCount  
 呼叫此成員函式擷取的 DAO 資料庫引擎的錯誤集合中的錯誤物件數目。  
  
```  
short GetErrorCount();
```  
  
### <a name="return-value"></a>傳回值  
 DAO 資料庫引擎的錯誤集合中的錯誤物件數目。  
  
### <a name="remarks"></a>備註  
 這項資訊可用於擷取每一個或多個 DAO 錯誤物件在集合中的錯誤集合執行迴圈。 若要依索引或 DAO 錯誤編號擷取物件時發生錯誤，請呼叫[GetErrorInfo](#geterrorinfo)成員函式。  
  
> [!NOTE]
>  通常會只有一個錯誤物件中的錯誤集合。 如果您正在使用的 ODBC 資料來源，不過，可能有多個。  
  
##  <a name="a-namegeterrorinfoa--cdaoexceptiongeterrorinfo"></a><a name="geterrorinfo"></a>CDaoException::GetErrorInfo  
 錯誤集合中傳回特定的錯誤物件的相關資訊時發生錯誤。  
  
```  
void GetErrorInfo(int nIndex);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 錯誤的資訊在資料庫引擎的錯誤集合中，依索引查閱索引。  
  
### <a name="remarks"></a>備註  
 呼叫此成員函式，以取得下列類型的例外狀況的相關資訊︰  
  
-   錯誤碼  
  
-   來源  
  
-   描述  
  
-   說明檔案  
  
-   說明內容  
  
 `GetErrorInfo`將資訊儲存在例外狀況物件的`m_pErrorInfo`資料成員。 傳回資訊的簡短說明，請參閱[m_pErrorInfo](#m_perrorinfo)。 如果您攔截例外狀況型別`CDaoException`MFC 中，所擲回`m_pErrorInfo`成員就會自動填入。 如果您選擇直接呼叫 DAO，您必須呼叫例外狀況物件的`GetErrorInfo`成員函式自行填入`m_pErrorInfo`。 如需更詳細的說明，請參閱[CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md)結構。  
  
 如需 DAO 例外狀況和範例程式碼，請參閱文章[例外狀況︰ 資料庫例外狀況](../../mfc/exceptions-database-exceptions.md)。  
  
##  <a name="a-namemnafxdaoerrora--cdaoexceptionmnafxdaoerror"></a><a name="m_nafxdaoerror"></a>CDaoException::m_nAfxDaoError  
 包含 MFC 延伸錯誤碼。  
  
### <a name="remarks"></a>備註  
 其中有 erred MFC DAO 類別中的特定元件的情況下會提供此程式碼。  
  
 可能的值為：  
  
- **NO_AFX_DAO_ERROR**最新的作業不會造成 MFC 擴充錯誤。 不過，作業可能都產生其他錯誤從 DAO 或 OLE，所以您應該檢查[m_pErrorInfo](#m_perrorinfo) ，甚至[m_scode](#m_scode)。  
  
- **AFX_DAO_ERROR_ENGINE_INITIALIZATION** MFC 無法初始化 Microsoft Jet 資料庫引擎。 OLE 可能無法初始化，或者它可能已被可能建立 DAO 資料庫引擎物件的執行個體。 這些問題通常會建議 DAO 或 OLE 的不正確安裝。  
  
- **AFX_DAO_ERROR_DFX_BIND** DAO 資料錄欄位交換 (DFX) 函式呼叫中使用的位址不存在或不正確 （地址不用來將資料繫結）。 您可能已在 DFX 呼叫中，傳送不正確的位址或位址可能已經變成無效 DFX 作業之間。  
  
- **AFX_DAO_ERROR_OBJECT_NOT_OPEN**您嘗試開啟資料錄集根據 querydef 或 tabledef 物件未處於開啟狀態。  
  
##  <a name="a-namemperrorinfoa--cdaoexceptionmperrorinfo"></a><a name="m_perrorinfo"></a>CDaoException::m_pErrorInfo  
 包含一個指向`CDaoErrorInfo`提供上次擷取藉由呼叫 DAO 錯誤物件的相關資訊的結構[GetErrorInfo](#geterrorinfo)。  
  
### <a name="remarks"></a>備註  
 這個物件包含下列資訊︰  
  
|CDaoErrorInfo 成員|資訊|意義|  
|--------------------------|-----------------|-------------|  
|**m_lErrorCode**|錯誤碼|DAO 錯誤程式碼|  
|`m_strSource`|來源|物件或最初產生錯誤的應用程式的名稱|  
|`m_strDescription`|說明|與錯誤相關聯的描述性字串|  
|`m_strHelpFile`|說明檔|Windows 說明的檔案，使用者可以在其中取得問題的相關資訊的路徑|  
|**m_lHelpContext**|說明內容|DAO 說明檔中主題的內容識別碼|  
  
 完整詳細資料中包含的資訊`CDaoErrorInfo`物件，請參閱[CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md)結構。  
  
##  <a name="a-namemscodea--cdaoexceptionmscode"></a><a name="m_scode"></a>CDaoException::m_scode  
 包含型別的值`SCODE`描述錯誤。  
  
### <a name="remarks"></a>備註  
 這是 OLE 的程式碼。 您將不常需要使用此值，因為在大多數情況下，會提供其他更明確的 MFC 或 DAO 錯誤資訊`CDaoException`資料成員。  
  
 如需有關資訊`SCODE`，請參閱主題[結構的 OLE 錯誤碼](http://msdn.microsoft.com/library/windows/desktop/ms690088)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 `SCODE`資料類型會對應到`HRESULT`資料型別。  
  
## <a name="see-also"></a>另請參閱  
 [CException 類別](../../mfc/reference/cexception-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CException 類別](../../mfc/reference/cexception-class.md)

