---
title: CDaoException 類別
ms.date: 11/04/2016
f1_keywords:
- CDaoException
- AFXDAO/CDaoException
- AFXDAO/CDaoException::CDaoException
- AFXDAO/CDaoException::GetErrorCount
- AFXDAO/CDaoException::GetErrorInfo
- AFXDAO/CDaoException::m_nAfxDaoError
- AFXDAO/CDaoException::m_pErrorInfo
- AFXDAO/CDaoException::m_scode
helpviewer_keywords:
- CDaoException [MFC], CDaoException
- CDaoException [MFC], GetErrorCount
- CDaoException [MFC], GetErrorInfo
- CDaoException [MFC], m_nAfxDaoError
- CDaoException [MFC], m_pErrorInfo
- CDaoException [MFC], m_scode
ms.assetid: b2b01fa9-7ce2-42a1-842e-40f13dc50da4
ms.openlocfilehash: e5f28b8896fc9e7e5c6a656a64b938cd7af39f42
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507067"
---
# <a name="cdaoexception-class"></a>CDaoException 類別

表示以資料存取物件 (DAO) 為基礎之 MFC 資料庫類別所引發的例外狀況。

## <a name="syntax"></a>語法

```
class CDaoException : public CException
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CDaoException::CDaoException](#cdaoexception)|建構 `CDaoException` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CDaoException::GetErrorCount](#geterrorcount)|傳回資料庫引擎的錯誤集合中的錯誤數目。|
|[CDaoException::GetErrorInfo](#geterrorinfo)|傳回錯誤集合中特定錯誤物件的相關錯誤資訊。|

### <a name="public-data-members"></a>公用資料成員

|名稱|說明|
|----------|-----------------|
|[CDaoException::m_nAfxDaoError](#m_nafxdaoerror)|包含 MFC DAO 類別中任何錯誤的擴充錯誤碼。|
|[CDaoException::m_pErrorInfo](#m_perrorinfo)|[CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md)物件的指標, 其中包含一個 DAO 錯誤物件的相關資訊。|
|[CDaoException::m_scode](#m_scode)|與錯誤相關聯的[SCODE](#m_scode)值。|

## <a name="remarks"></a>備註

類別包含可用來判斷例外狀況原因的公用資料成員。 `CDaoException`物件是由 DAO 資料庫類別的成員函式所結構化和擲回。

> [!NOTE]
>  DAO 資料庫類別與以開放式資料庫連接 (ODBC) 為基礎的 MFC 資料庫類別不同。 所有的 DAO 資料庫類別名稱都具有 "CDao" 前置詞。 您仍然可以使用 DAO 類別來存取 ODBC 資料來源。 一般而言, 以 DAO 為基礎的 MFC 類別比以 ODBC 為基礎的 MFC 類別更有能力;以 DAO 為基礎的類別可以透過自己的資料庫引擎來存取資料, 包括透過 ODBC 驅動程式。 以 DAO 為基礎的類別也支援資料定義語言 (DDL) 作業, 例如透過類別加入資料表, 而不需要直接呼叫 DAO。 如需 ODBC 類別所擲回之例外狀況的詳細資訊, 請參閱[CDBException](../../mfc/reference/cdbexception-class.md)。

您可以存取[CATCH](../../mfc/reference/exception-processing.md#catch)運算式範圍內的例外狀況物件。 您也可以使用`CDaoException` [AfxThrowDaoException](../../mfc/reference/exception-processing.md#afxthrowdaoexception)全域函式, 從您自己的程式碼擲回物件。

在 MFC 中, 所有 DAO 錯誤都會表示為類型`CDaoException`的例外狀況。 當您攔截這個類型的例外狀況時, 您可以`CDaoException`使用成員函式, 從儲存在 database engine 的錯誤集合中的任何 DAO 錯誤物件中抓取資訊。 當發生每個錯誤時, 會將一或多個錯誤物件放在 Errors 集合中。 (通常集合只會包含一個錯誤物件; 如果您使用的是 ODBC 資料來源, 則較可能會取得多個錯誤物件)。當另一個 DAO 作業產生錯誤時, 會清除錯誤集合, 而新的錯誤物件會放在 Errors 集合中。 不會產生錯誤的 DAO 作業不會影響錯誤集合。

如需 DAO 錯誤碼, 請參閱檔案 DAOERR。H. 如需相關資訊, 請參閱 DAO 說明中的「可捕獲的資料存取錯誤」主題。

如需一般或關於`CDaoException`物件的例外狀況處理的詳細資訊, 請參閱[例外狀況處理 (MFC)](../../mfc/exception-handling-in-mfc.md)和[例外狀況:資料庫例外](../../mfc/exceptions-database-exceptions.md)狀況。 第二篇文章包含示範 DAO 中例外狀況處理的範例程式碼。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CDaoException`

## <a name="requirements"></a>需求

**標頭:** afxdao。h

##  <a name="cdaoexception"></a>CDaoException::CDaoException

建構 `CDaoException` 物件。

```
CDaoException();
```

### <a name="remarks"></a>備註

一般來說, 架構會在其程式碼擲回例外狀況時建立例外狀況物件。 您很少需要明確地建立例外狀況物件。 如果您想要`CDaoException`從自己的程式碼擲回, 請呼叫全域函式[AfxThrowDaoException](../../mfc/reference/exception-processing.md#afxthrowdaoexception)。

不過, 如果您要透過 MFC 類別所封裝的 DAO 介面指標直接呼叫 DAO, 您可能會想要明確建立例外狀況物件。 在這種情況下, 您可能需要從 DAO 取出錯誤資訊。 假設當您透過 DAODatabases 介面, 透過工作區的資料庫集合呼叫 DAO 方法時, DAO 會發生錯誤。

##### <a name="to-retrieve-the-dao-error-information"></a>若要取得 DAO 錯誤資訊

1. `CDaoException`建立物件。

1. 呼叫 exception 物件的[GetErrorCount](#geterrorcount)成員函式, 以判斷資料庫引擎的錯誤集合中有多少個錯誤物件。 (通常只有一個, 除非您使用的是 ODBC 資料來源)。

1. 呼叫 exception 物件的[GetErrorInfo](#geterrorinfo)成員函式, 透過例外狀況物件, 在集合中一次取出一個特定的錯誤物件。 將例外狀況物件視為一個 DAO 錯誤物件的 proxy。

1. 檢查在[m_pErrorInfo](#m_perrorinfo)資料成員中`GetErrorInfo`傳回的目前[CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md)結構。 其成員會提供 DAO 錯誤的相關資訊。

1. 如果是 ODBC 資料來源, 請視需要重複步驟3和 4, 以取得更多錯誤物件。

1. 如果您在堆積上建立了例外狀況物件, 當您完成時, 請使用**delete**運算子將它刪除。

如需有關在 MFC DAO 類別中處理錯誤的詳細資訊, 請[參閱例外狀況:資料庫例外](../../mfc/exceptions-database-exceptions.md)狀況。

##  <a name="geterrorcount"></a>CDaoException::GetErrorCount

呼叫這個成員函式, 以抓取資料庫引擎的錯誤集合中的 DAO 錯誤物件數目。

```
short GetErrorCount();
```

### <a name="return-value"></a>傳回值

資料庫引擎的錯誤集合中的 DAO 錯誤物件數目。

### <a name="remarks"></a>備註

這項資訊可用於迴圈處理錯誤集合, 以取得集合中的一個或多個 DAO 錯誤物件。 若要依索引或 DAO 錯誤號碼抓取錯誤物件, 請呼叫[GetErrorInfo](#geterrorinfo)成員函式。

> [!NOTE]
>  一般來說, Errors 集合中只有一個錯誤物件。 不過, 如果您使用的是 ODBC 資料來源, 可能會有一個以上的。

##  <a name="geterrorinfo"></a>CDaoException:: GetErrorInfo

傳回錯誤集合中特定錯誤物件的相關錯誤資訊。

```
void GetErrorInfo(int nIndex);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
資料庫引擎的錯誤集合中, 用於依索引查閱的錯誤資訊索引。

### <a name="remarks"></a>備註

呼叫這個成員函式以取得下列有關例外狀況的資訊類型:

- 錯誤碼

- Source

- 說明

- 說明檔案

- 說明內容

`GetErrorInfo`將資訊儲存在例外狀況物件的`m_pErrorInfo`資料成員中。 如需所傳回信息的簡短描述, 請參閱[m_pErrorInfo](#m_perrorinfo)。 如果您攔截 MFC 所擲回`CDaoException`的類型例外狀況, `m_pErrorInfo`該成員將已填入。 如果您選擇直接呼叫 DAO, 您必須自行呼叫例外狀況物件的`GetErrorInfo`成員函式來填`m_pErrorInfo`滿。 如需更詳細的描述, 請參閱[CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md)結構。

如需 DAO 例外狀況和範例程式碼的相關資訊, [請參閱例外狀況:資料庫例外](../../mfc/exceptions-database-exceptions.md)狀況。

##  <a name="m_nafxdaoerror"></a>  CDaoException::m_nAfxDaoError

包含 MFC 擴充的錯誤碼。

### <a name="remarks"></a>備註

在 MFC DAO 類別的特定元件具有大錯特錯人的情況下, 會提供此程式碼。

可能的值為：

- NO_AFX_DAO_ERROR 最近的作業未導致 MFC 擴充錯誤。 不過, 此作業可能會從 DAO 或 OLE 產生其他錯誤, 因此您應該檢查[m_pErrorInfo](#m_perrorinfo)和可能的[m_scode](#m_scode)。

- AFX_DAO_ERROR_ENGINE_INITIALIZATION MFC 無法初始化 Microsoft Jet 資料庫引擎。 OLE 可能無法初始化, 或可能無法建立 DAO 資料庫引擎物件的實例。 這些問題通常會建議使用不正確的 DAO 或 OLE 安裝。

- AFX_DAO_ERROR_DFX_BIND DAO 記錄欄位交換 (DFX) 函數呼叫中所使用的位址不存在或無效 (位址不是用來系結資料)。 您可能在 DFX 呼叫中傳遞了不正確的位址, 或是 DFX 作業之間的位址可能變成無效。

- AFX_DAO_ERROR_OBJECT_NOT_OPEN 您嘗試根據未處於開啟狀態的 querydef 或 tabledef 物件開啟記錄集。

##  <a name="m_perrorinfo"></a>CDaoException::m_pErrorInfo

包含`CDaoErrorInfo`結構的指標, 它會提供您上次透過呼叫[GetErrorInfo](#geterrorinfo)所抓取之 DAO 錯誤物件的相關資訊。

### <a name="remarks"></a>備註

此物件包含下列資訊:

|CDaoErrorInfo 成員|內容|意義|
|--------------------------|-----------------|-------------|
|`m_lErrorCode`|錯誤碼|DAO 錯誤碼|
|`m_strSource`|Source|原先產生錯誤之物件或應用程式的名稱|
|`m_strDescription`|描述|與錯誤相關聯的描述性字串|
|`m_strHelpFile`|說明檔|Windows 說明檔的路徑, 使用者可以在其中取得問題的相關資訊|
|`m_lHelpContext`|說明內容|DAO 說明檔中主題的內容識別碼|

如需`CDaoErrorInfo`物件中所包含資訊的完整詳細資訊, 請參閱[CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md)結構。

##  <a name="m_scode"></a>CDaoException::m_scode

包含描述錯誤之類型`SCODE`的值。

### <a name="remarks"></a>備註

這是 OLE 程式碼。 您很少需要使用這個值, 因為在幾乎所有情況下, 其他`CDaoException`資料成員中都可以使用更特定的 MFC 或 DAO 錯誤資訊。

如需 SCODE 的詳細資訊, 請參閱 Windows SDK 中的[OLE 錯誤碼](/windows/win32/com/structure-of-com-error-codes)的主題結構。 SCODE 資料類型會對應至 HRESULT 資料類型。

## <a name="see-also"></a>另請參閱

[CException 類別](../../mfc/reference/cexception-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CException 類別](../../mfc/reference/cexception-class.md)
