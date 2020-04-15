---
title: CDaoException 類別
ms.date: 09/17/2019
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
ms.openlocfilehash: a8a789f4dba06ffe376d8a8e955b026bb23af924
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369004"
---
# <a name="cdaoexception-class"></a>CDaoException 類別

表示以資料存取物件 (DAO) 為基礎之 MFC 資料庫類別所引發的例外狀況。 DAO 3.6 是最終版本,它被視為過時版本。

## <a name="syntax"></a>語法

```
class CDaoException : public CException
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[道例外::CDao例外](#cdaoexception)|建構 `CDaoException` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDao 例外:取得錯誤計數](#geterrorcount)|返回資料庫引擎的錯誤集合中的錯誤數。|
|[CDao 例外:取得錯誤資訊](#geterrorinfo)|傳回錯誤集合中有關特定錯誤物件的錯誤資訊。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[道例外:m_nAfxDaoError](#m_nafxdaoerror)|包含 MFC DAO 類別錯誤的擴充錯誤程式碼。|
|[道例外:m_pErrorInfo](#m_perrorinfo)|指向包含有關一個 DAO 錯誤物件的資訊的[CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md)物件的指標。|
|[道例外:m_scode](#m_scode)|與錯誤關聯的[SCODE](#m_scode)值。|

## <a name="remarks"></a>備註

該類包括可用於確定異常原因的公共數據成員。 `CDaoException`物件由 DAO 資料庫類的成員函數構造和引發。

> [!NOTE]
> DAO 資料庫類不同於基於開放資料庫連接 (ODBC) 的 MFC 資料庫類。 所有 DAO 資料庫類名稱都有「CDao」首碼。 您仍可以使用 DAO 類存取 ODBC 資料來源。 一般來說,基於 DAO 的 MFC 類比基於 ODBC 的 MFC 類更有能力;基於 DAO 的類可以通過自己的資料庫引擎訪問數據,包括透過 ODBC 驅動程式。 基於 DAO 的類還支援數據定義語言 (DDL) 操作,例如透過類添加表,而無需直接呼叫 DAO。 有關 ODBC 類別引發的資訊,請參考[CDBException](../../mfc/reference/cdbexception-class.md)。

您可以造[訪 CATCH](../../mfc/reference/exception-processing.md#catch)表示式範圍內的異常物件。 您還可以使用`CDaoException`[AfxThrowDaoException](../../mfc/reference/exception-processing.md#afxthrowdaoexception)全域函數從您自己的代碼中引發物件。

在 MFC 中,所有 DAO`CDaoException`錯誤都表示為異常,類型為 。 捕獲此類型的異常時,可以使用`CDaoException`成員函數從資料庫引擎的錯誤集合中存儲的任何 DAO 錯誤物件中檢索資訊。 當發生每個錯誤時,一個或多個錯誤物件將放置在錯誤集合中。 (通常集合只包含一個錯誤物件;如果使用 ODBC 數據源,則更有可能獲取多個錯誤物件。當另一個 DAO 操作生成錯誤時,將清除錯誤集合,並將新的錯誤物件放置在錯誤集合中。 不生成錯誤的 DAO 操作對錯誤集合沒有影響。

有關DAO錯誤代碼,請參閱檔DAOERR。H。 有關相關信息,請參閱 DAO 説明中的主題"可捕獲的數據訪問錯誤」。。

有關常規異常處理或`CDaoException`對象的詳細資訊,請參閱[文章"異常處理 "(MFC)](../../mfc/exception-handling-in-mfc.md)和["例外:資料庫例外](../../mfc/exceptions-database-exceptions.md)"。 第二篇文章包含示例代碼,這些代碼說明瞭 DAO 中的異常處理。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[C 例外](../../mfc/reference/cexception-class.md)

`CDaoException`

## <a name="requirements"></a>需求

**標題:** afxdao.h

## <a name="cdaoexceptioncdaoexception"></a><a name="cdaoexception"></a>道例外::CDao例外

建構 `CDaoException` 物件。

```
CDaoException();
```

### <a name="remarks"></a>備註

通常,當框架的代碼引發異常時,將創建異常物件。 您很少需要顯式構造異常物件。 如果要從自己的代碼中引發`CDaoException`,請呼叫全域函數[AfxThrowDaoException](../../mfc/reference/exception-processing.md#afxthrowdaoexception)。

但是,如果要通過 MFC 類封裝的 DAO 介面指標直接調用 DAO,則可能需要顯式創建異常物件。 在這種情況下,您可能需要從 DAO 檢索錯誤資訊。 假設當您透過 DAO 資料庫介面將 DAO 方法呼叫工作區的資料庫集合時,DAO 中會發生錯誤。

##### <a name="to-retrieve-the-dao-error-information"></a>檢索 DAO 錯誤資訊

1. 構造`CDaoException`物件。

1. 調用異常物件的[GetErrorCount](#geterrorcount)成員函數,以確定資料庫引擎的錯誤集合中有多少錯誤物件。 (通常只有一個,除非您使用的是 ODBC 數據源。

1. 調用異常物件的[GetErrorInfo](#geterrorinfo)成員函數,通過異常物件,通過異常物件,通過集合中的索引,一次檢索一個特定的錯誤物件。 將異常物件視為一個 DAO 錯誤物件的代理。

1. 檢查在資料成員中`GetErrorInfo`返回的當前[CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md)結構[m_pErrorInfo。](#m_perrorinfo) 其成員提供有關 DAO 錯誤的資訊。

1. 對於 ODBC 數據源,根據需要重複步驟 3 和 4,以查找更多錯誤物件。

1. 如果在堆上構造了異常物件,則在完成時使用**delete**運算符將其刪除。

有關在 MFC DAO 類中處理錯誤的詳細資訊,請參閱文章[「例外:資料庫例外](../../mfc/exceptions-database-exceptions.md)」。

## <a name="cdaoexceptiongeterrorcount"></a><a name="geterrorcount"></a>CDao 例外:取得錯誤計數

呼叫此成員函數以檢索資料庫引擎錯誤集合中的 DAO 錯誤物件數。

```
short GetErrorCount();
```

### <a name="return-value"></a>傳回值

資料庫引擎錯誤集合中的 DAO 錯誤物件數。

### <a name="remarks"></a>備註

此資訊可用於迴圈流覽錯誤集合,以檢索集合中的每個一個或多個 DAO 錯誤物件。 若要按索引或 DAO 錯誤編號檢索錯誤物件,請調用[GetErrorInfo](#geterrorinfo)成員函數。

> [!NOTE]
> 通常,"錯誤"集合中只有一個錯誤物件。 但是,如果您正在使用 ODBC 數據源,則可能有多個數據源。

## <a name="cdaoexceptiongeterrorinfo"></a><a name="geterrorinfo"></a>CDao 例外:取得錯誤資訊

傳回錯誤集合中有關特定錯誤物件的錯誤資訊。

```
void GetErrorInfo(int nIndex);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
資料庫引擎的錯誤集合中錯誤資訊的索引,用於按索引查找。

### <a name="remarks"></a>備註

呼叫此成員函數以取得有關異常的以下類型資訊:

- 錯誤碼

- 來源

- 描述

- 說明檔案

- 說明內容文

`GetErrorInfo`將資訊存儲在異常對`m_pErrorInfo`象 的數據成員中。 有關傳回的簡要說明,請參閱[m_pErrorInfo](#m_perrorinfo)。 如果捕獲 MFC`CDaoException`引發的類型異常`m_pErrorInfo`,則成員將被填充。 如果選擇直接呼叫 DAO,則必須自己呼叫異常`GetErrorInfo`物件的成員函數以填`m_pErrorInfo`充 。 有關更詳細的說明,請參閱[CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md)結構。

有關 DAO 異常和範例代碼的資訊,請參閱文章[「例外:資料庫例外](../../mfc/exceptions-database-exceptions.md)」。

## <a name="cdaoexceptionm_nafxdaoerror"></a><a name="m_nafxdaoerror"></a>道例外:m_nAfxDaoError

包含 MFC 擴展錯誤代碼。

### <a name="remarks"></a>備註

在 MFC DAO 類的特定元件出現問題的情況下,提供此代碼。

可能的值包括：

- NO_AFX_DAO_ERROR 最近的操作未導致 MFC 擴展錯誤。 但是,該操作可能會產生 DAO 或 OLE 的其他錯誤,因此您應該檢查[m_pErrorInfo](#m_perrorinfo)並可能[m_scode](#m_scode)。

- AFX_DAO_ERROR_ENGINE_INITIALIZATION MFC 無法初始化 Microsoft Jet 資料庫引擎。 OLE 可能無法初始化,或者可能無法建立 DAO 資料庫引擎物件的實例。 這些問題通常表明 DAO 或 OLE 的安裝錯誤。

- AFX_DAO_ERROR_DFX_BIND DAO 記錄欄位交換 (DFX) 函數調用中使用的位址不存在或無效(該位址未用於綁定數據)。 您可能在 DFX 調用中傳遞了一個壞位址,或者該位址在 DFX 操作之間可能已失效。

- AFX_DAO_ERROR_OBJECT_NOT_OPEN 您嘗試基於查詢def或未處於打開狀態的 tabledef 物件打開記錄集。

## <a name="cdaoexceptionm_perrorinfo"></a><a name="m_perrorinfo"></a>道例外:m_pErrorInfo

包含指向結構的`CDaoErrorInfo`指標,該結構提供有關上次通過調用[GetErrorInfo](#geterrorinfo)檢索的 DAO 錯誤物件的資訊。

### <a name="remarks"></a>備註

此物件包含以下資訊:

|CDaoErrorInfo 成員|資訊|意義|
|--------------------------|-----------------|-------------|
|`m_lErrorCode`|錯誤碼|DAO 錯誤代碼|
|`m_strSource`|來源|最初產生錯誤的物件或應用程式名稱|
|`m_strDescription`|描述|與錯誤關聯的描述性字串|
|`m_strHelpFile`|說明檔案|Windows 說明檔案的路徑,使用者可以在其中取得有關問題的資訊|
|`m_lHelpContext`|說明內容文|DAO 說明檔案主題的內容內容|

有關`CDaoErrorInfo`物件中包含的資訊完整詳細資訊,請參閱[CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md)結構。

## <a name="cdaoexceptionm_scode"></a><a name="m_scode"></a>道例外:m_scode

包含描述錯誤的類型`SCODE`值。

### <a name="remarks"></a>備註

這是一個 OLE 代碼。 您很少需要使用此值,因為在幾乎所有情況下,其他`CDaoException`數據成員中都有更具體的 MFC 或 DAO 錯誤資訊。

有關 SCODE 的資訊,請參閱 Windows SDK 中[有關 OLE 錯誤代碼的結構](/windows/win32/com/structure-of-com-error-codes)的主題。 SCODE 資料類型映射到 HRESULT 資料類型。

## <a name="see-also"></a>另請參閱

[CException 類別](../../mfc/reference/cexception-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CException 類別](../../mfc/reference/cexception-class.md)
