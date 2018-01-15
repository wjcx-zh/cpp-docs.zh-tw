---
title: "CDaoException 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDaoException
- AFXDAO/CDaoException
- AFXDAO/CDaoException::CDaoException
- AFXDAO/CDaoException::GetErrorCount
- AFXDAO/CDaoException::GetErrorInfo
- AFXDAO/CDaoException::m_nAfxDaoError
- AFXDAO/CDaoException::m_pErrorInfo
- AFXDAO/CDaoException::m_scode
dev_langs: C++
helpviewer_keywords:
- CDaoException [MFC], CDaoException
- CDaoException [MFC], GetErrorCount
- CDaoException [MFC], GetErrorInfo
- CDaoException [MFC], m_nAfxDaoError
- CDaoException [MFC], m_pErrorInfo
- CDaoException [MFC], m_scode
ms.assetid: b2b01fa9-7ce2-42a1-842e-40f13dc50da4
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5295a63a968162f5a891def06206eb50485ab1a5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cdaoexception-class"></a>CDaoException 類別
表示以資料存取物件 (DAO) 為基礎之 MFC 資料庫類別所引發的例外狀況。  
  
## <a name="syntax"></a>語法  
  
```  
class CDaoException : public CException  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CDaoException::CDaoException](#cdaoexception)|建構 `CDaoException` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CDaoException::GetErrorCount](#geterrorcount)|Database engine 錯誤的集合中傳回錯誤的數目。|  
|[CDaoException::GetErrorInfo](#geterrorinfo)|傳回有關特定錯誤物件資訊時發生錯誤至錯誤集合。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CDaoException::m_nAfxDaoError](#m_nafxdaoerror)|包含 MFC DAO 類別中的任何錯誤的延伸的錯誤碼。|  
|[CDaoException::m_pErrorInfo](#m_perrorinfo)|指標[CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md)物件，其中包含一個 DAO 錯誤物件的相關資訊。|  
|[CDaoException::m_scode](#m_scode)|[SCODE](#m_scode)與錯誤相關聯的值。|  
  
## <a name="remarks"></a>備註  
 類別包含您可用來判斷造成例外狀況的公用資料成員。 `CDaoException`物件是建構，而且 DAO 資料庫類別的成員函式所擲回。  
  
> [!NOTE]
>  DAO 資料庫類別是不同的基礎上開放式資料庫連接 (ODBC) 之 MFC 資料庫類別。 所有的 DAO 資料庫類別名稱有"CDao"前置詞。 您仍然可以使用 DAO 類別存取 ODBC 資料來源。 一般情況下，根據 DAO MFC 類別會更能夠比 ODBC; 為基礎的 MFC 類別DAO 類別都可以存取資料，包括透過 ODBC 驅動程式，透過它們自己的資料庫引擎。 DAO 類別也支援資料定義語言 (DDL) 作業，例如新增而不需要直接呼叫 DAO 類別，透過資料表。 如需 ODBC 類別所擲回的例外狀況的資訊，請參閱[CDBException](../../mfc/reference/cdbexception-class.md)。  
  
 您可以存取的範圍內的例外狀況物件[攔截](../../mfc/reference/exception-processing.md#catch)運算式。 您也可以擲回`CDaoException`物件從自己的程式碼與[AfxThrowDaoException](../../mfc/reference/exception-processing.md#afxthrowdaoexception)全域函式。  
  
 在 MFC 中，所有的 DAO 錯誤會表示為類型的例外狀況`CDaoException`。 當您攔截這類型的例外狀況時，您可以使用`CDaoException`成員函式來擷取儲存在資料庫引擎的錯誤集合中任何 DAO 錯誤物件資訊。 每個錯誤發生時，會置於一或多個錯誤物件中的錯誤集合。 （通常集合包含只有一個物件時發生錯誤; 如果您使用 ODBC 資料來源，您能更容易取得多個錯誤物件）。當另一個 DAO 作業會產生錯誤時，錯誤集合會進行清除，和新的 error 物件放在錯誤集合。 不會產生錯誤的 DAO 作業有不會影響的錯誤集合。  
  
 DAO 的錯誤碼，請參閱 DAOERR 的檔案。H. 如需相關資訊，請參閱 「 可截獲資料存取錯誤 」 DAO [說明] 中的主題。  
  
 如需有關的一般情況下，或將例外狀況處理`CDaoException`物件，請參閱文章[例外狀況處理 (MFC)](../../mfc/exception-handling-in-mfc.md)和[例外狀況： 資料庫例外狀況](../../mfc/exceptions-database-exceptions.md)。 第二個發行項包含說明例外狀況處理在 DAO 中的範例程式碼。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `CDaoException`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxdao.h  
  
##  <a name="cdaoexception"></a>CDaoException::CDaoException  
 建構 `CDaoException` 物件。  
  
```  
CDaoException();
```  
  
### <a name="remarks"></a>備註  
 一般情況下，架構建立例外狀況物件，其程式碼擲回例外狀況時。 您很少需要明確建構例外狀況物件。 如果您想要擲回`CDaoException`從自己的程式碼呼叫全域函式[AfxThrowDaoException](../../mfc/reference/exception-processing.md#afxthrowdaoexception)。  
  
 不過，您可能想要明確建立例外狀況物件，如果您要進行直接呼叫 DAO 透過 MFC 類別會封裝 DAO 介面指標。 在此情況下，您可能需要從 DAO 擷取資訊時發生錯誤。 假設當您透過加入工作區的資料庫集合 DAODatabases 介面呼叫 DAO 方法在 DAO 中發生錯誤。  
  
##### <a name="to-retrieve-the-dao-error-information"></a>若要擷取 DAO 資訊時發生錯誤  
  
1.  建構`CDaoException`物件。  
  
2.  呼叫例外狀況物件的[GetErrorCount](#geterrorcount)成員函式來判斷在資料庫引擎的錯誤集合中有多少錯誤物件。 (一般而言，只有一個，除非您將使用 ODBC 資料來源。)  
  
3.  呼叫例外狀況物件的[GetErrorInfo](#geterrorinfo)成員函式來一次擷取一個特定的錯誤物件在集合中，透過例外狀況物件的索引。 例外狀況物件視為一個 DAO 錯誤物件的 proxy。  
  
4.  檢查目前[CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md)結構`GetErrorInfo`中傳回[m_pErrorInfo](#m_perrorinfo)資料成員。 其成員提供 DAO 錯誤的相關資訊。  
  
5.  在 ODBC 資料來源，重複步驟 3 和 4，如有需要針對多個錯誤的物件。  
  
6.  如果您建構在堆積上的例外狀況物件，其與刪除**刪除**運算子，當您完成時。  
  
 如需在 MFC DAO 類別中的錯誤處理的詳細資訊，請參閱文章[例外狀況： 資料庫例外狀況](../../mfc/exceptions-database-exceptions.md)。  
  
##  <a name="geterrorcount"></a>CDaoException::GetErrorCount  
 呼叫此成員函式可擷取的 DAO 資料庫引擎的錯誤集合中的錯誤物件數目。  
  
```  
short GetErrorCount();
```  
  
### <a name="return-value"></a>傳回值  
 DAO 資料庫引擎的錯誤集合中的錯誤物件數目。  
  
### <a name="remarks"></a>備註  
 這項資訊可用於擷取每一個或多個 DAO 錯誤物件的集合中的錯誤集合執行迴圈。 若要依索引或 DAO 錯誤編號擷取錯誤物件，呼叫[GetErrorInfo](#geterrorinfo)成員函式。  
  
> [!NOTE]
>  一般的錯誤集合中沒有只有一個物件時發生錯誤。 如果您正在使用的 ODBC 資料來源，不過，可能有多個。  
  
##  <a name="geterrorinfo"></a>CDaoException::GetErrorInfo  
 傳回有關特定錯誤物件資訊時發生錯誤至錯誤集合。  
  
```  
void GetErrorInfo(int nIndex);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 Database engine 錯誤集合，依索引查閱中的錯誤資訊的索引。  
  
### <a name="remarks"></a>備註  
 呼叫此成員函式可取得下列類型的例外狀況的相關資訊：  
  
-   錯誤碼  
  
-   原始程式檔  
  
-   描述  
  
-   說明檔案  
  
-   說明內容  
  
 `GetErrorInfo`例外狀況物件中儲存的資訊`m_pErrorInfo`資料成員。 傳回的資訊的簡短描述，請參閱[m_pErrorInfo](#m_perrorinfo)。 如果您攔截例外狀況型別的`CDaoException`MFC，所擲回`m_pErrorInfo`成員就會自動填入。 如果您選擇直接呼叫 DAO，您必須呼叫例外狀況物件的`GetErrorInfo`成員函式自行填滿`m_pErrorInfo`。 如需更詳細的說明，請參閱[CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md)結構。  
  
 如需 DAO 例外狀況和範例程式碼，請參閱文章[例外狀況： 資料庫例外狀況](../../mfc/exceptions-database-exceptions.md)。  
  
##  <a name="m_nafxdaoerror"></a>CDaoException::m_nAfxDaoError  
 包含 MFC 延伸錯誤碼。  
  
### <a name="remarks"></a>備註  
 此程式碼會在其中具有 erred MFC DAO 類別中的特定元件的情況下提供。  
  
 可能的值為：  
  
- **NO_AFX_DAO_ERROR**最新的作業不會造成擴充錯誤 MFC。 不過，操作無法已產生其他錯誤，DAO 或 OLE，因此您應該檢查[m_pErrorInfo](#m_perrorinfo) ，甚至[m_scode](#m_scode)。  
  
- **AFX_DAO_ERROR_ENGINE_INITIALIZATION** MFC 無法初始化 Microsoft Jet 資料庫引擎。 OLE 可能無法初始化，或者它可能已被可能建立 DAO 資料庫引擎物件的執行個體。 這些問題通常會建議 DAO 或 OLE 的不正確安裝。  
  
- **AFX_DAO_ERROR_DFX_BIND** DAO 資料錄欄位交換 (DFX) 函式呼叫中使用的位址不存在或無效 （地址已不會用來將資料繫結）。 您可能會在 DFX 呼叫中，傳遞不正確的位址或位址可能已經變成 DFX 作業之間無效。  
  
- **AFX_DAO_ERROR_OBJECT_NOT_OPEN**您嘗試開啟資料錄集根據 querydef 或 tabledef 物件未處於開啟狀態。  
  
##  <a name="m_perrorinfo"></a>CDaoException::m_pErrorInfo  
 包含的指標`CDaoErrorInfo`提供藉由呼叫最後擷取的 DAO 錯誤物件的相關資訊的結構[GetErrorInfo](#geterrorinfo)。  
  
### <a name="remarks"></a>備註  
 這個物件包含下列資訊：  
  
|CDaoErrorInfo 成員|資訊|意義|  
|--------------------------|-----------------|-------------|  
|**m_lErrorCode**|錯誤碼|DAO 錯誤程式碼|  
|`m_strSource`|原始程式檔|物件或最初產生錯誤的應用程式的名稱|  
|`m_strDescription`|描述|與錯誤相關聯的描述性字串|  
|`m_strHelpFile`|說明檔|Windows 說明的檔案，使用者可以在其中取得問題的相關資訊的路徑|  
|**m_lHelpContext**|說明內容|DAO [說明] 檔案中的主題，內容識別碼|  
  
 如需中所包含的資訊的完整詳細資料`CDaoErrorInfo`物件，請參閱[CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md)結構。  
  
##  <a name="m_scode"></a>CDaoException::m_scode  
 包含型別的值`SCODE`描述錯誤。  
  
### <a name="remarks"></a>備註  
 這是 OLE 程式碼。 您很少需要使用此值，因為在幾乎所有的情況下，會提供其他更特定的 MFC 或 DAO 錯誤資訊`CDaoException`資料成員。  
  
 如需有關資訊`SCODE`，請參閱主題[錯誤碼的結構 OLE](http://msdn.microsoft.com/library/windows/desktop/ms690088) Windows SDK 中。 `SCODE`資料類型會對應至`HRESULT`資料型別。  
  
## <a name="see-also"></a>請參閱  
 [CException 類別](../../mfc/reference/cexception-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CException 類別](../../mfc/reference/cexception-class.md)
