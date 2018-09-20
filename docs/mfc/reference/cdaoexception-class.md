---
title: CDaoException 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
dev_langs:
- C++
helpviewer_keywords:
- CDaoException [MFC], CDaoException
- CDaoException [MFC], GetErrorCount
- CDaoException [MFC], GetErrorInfo
- CDaoException [MFC], m_nAfxDaoError
- CDaoException [MFC], m_pErrorInfo
- CDaoException [MFC], m_scode
ms.assetid: b2b01fa9-7ce2-42a1-842e-40f13dc50da4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 38ac86784216fdc81eb73c56f82e8f7b6744941d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46431810"
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
|[CDaoException::GetErrorCount](#geterrorcount)|資料庫引擎的錯誤集合中傳回錯誤的數目。|
|[CDaoException::GetErrorInfo](#geterrorinfo)|傳回錯誤集合中的特定錯誤物件的相關資訊時發生錯誤。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CDaoException::m_nAfxDaoError](#m_nafxdaoerror)|包含 MFC DAO 類別中的任何錯誤的延伸的錯誤碼。|
|[CDaoException::m_pErrorInfo](#m_perrorinfo)|指標[CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md)物件，其中包含一個 DAO 錯誤物件的相關資訊。|
|[CDaoException::m_scode](#m_scode)|[SCODE](#m_scode)與錯誤相關聯的值。|

## <a name="remarks"></a>備註

類別包含公用資料成員，您可以使用它來判斷造成例外狀況。 `CDaoException` 物件的建構及 DAO 資料庫類別的成員函式所擲回。

> [!NOTE]
>  DAO 資料庫類別是開放式資料庫連接 (ODBC) 為基礎的 MFC 資料庫類別有所區別。 所有的 DAO 資料庫類別名稱有"CDao"前置詞。 您仍然可以使用 DAO 類別存取 ODBC 資料來源。 一般情況下，根據 DAO MFC 類別會更有能力比 ODBC; 為基礎的 MFC 類別DAO 類別可以存取資料，包括透過 ODBC 驅動程式，透過自己的資料庫引擎。 DAO 類別也支援資料定義語言 (DDL) 作業，例如加入資料表透過類別，而不必直接呼叫 DAO。 如需 ODBC 類別所擲回的例外狀況的資訊，請參閱 < [CDBException](../../mfc/reference/cdbexception-class.md)。

您可以存取的範圍內的例外狀況物件[攔截](../../mfc/reference/exception-processing.md#catch)運算式。 您也可以擲回`CDaoException`從您自己的程式碼的物件[AfxThrowDaoException](../../mfc/reference/exception-processing.md#afxthrowdaoexception)全域函式。

在 MFC 中，所有的 DAO 錯誤會表示為類型的例外狀況`CDaoException`。 當您攔截此類型的例外狀況時，您可以使用`CDaoException`成員函式來擷取儲存在資料庫引擎的錯誤集合中任何 DAO 錯誤物件中的資訊。 每個錯誤發生時，一或多個錯誤物件置於錯誤的集合。 （通常集合只包含一個錯誤物件，如果您使用 ODBC 資料來源，您會更容易取得多個錯誤物件）。當另一個的 DAO 作業會產生錯誤時，會清除錯誤集合，和新的 error 物件放在錯誤集合。 不會產生錯誤的 DAO 作業有不會影響的錯誤集合。

DAO 錯誤碼，請參閱 DAOERR 的檔案。H. 如需相關資訊，請參閱 「 可截獲資料存取錯誤 」 DAO [說明] 中。

如需詳細資訊，在一般情況下，或將處理的例外狀況的相關`CDaoException`物件，請參閱文章[例外狀況處理 (MFC)](../../mfc/exception-handling-in-mfc.md)並[例外狀況： 資料庫例外狀況](../../mfc/exceptions-database-exceptions.md)。 第二篇文章包含說明如何在 DAO 中的例外狀況處理的範例程式碼。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CDaoException`

## <a name="requirements"></a>需求

**標頭：** afxdao.h

##  <a name="cdaoexception"></a>  CDaoException::CDaoException

建構 `CDaoException` 物件。

```
CDaoException();
```

### <a name="remarks"></a>備註

一般情況下，framework 建立例外狀況物件，其程式碼擲回例外狀況時。 您很少需要明確建構例外狀況物件。 如果您想要擲回`CDaoException`從您自己的程式碼，呼叫全域函式[AfxThrowDaoException](../../mfc/reference/exception-processing.md#afxthrowdaoexception)。

不過，您可能要明確地建立例外狀況物件，如果您要進行直接呼叫 DAO 透過 MFC 類別會封裝的 DAO 介面指標。 在此情況下，您可能需要從 DAO 擷取資訊時發生錯誤。 假設在 DAO 中當您透過工作區的資料庫集合的 DAODatabases 介面呼叫 DAO 方法發生的錯誤。

##### <a name="to-retrieve-the-dao-error-information"></a>若要擷取 DAO 資訊時發生錯誤

1. 建構`CDaoException`物件。

1. 呼叫例外狀況物件的[GetErrorCount](#geterrorcount)成員函式來判斷在資料庫引擎的錯誤集合中有多少錯誤物件。 (通常只有一個，除非您使用 ODBC 資料來源。)

1. 呼叫例外狀況物件的[GetErrorInfo](#geterrorinfo)成員函式來一次擷取一個特定的錯誤物件，以在集合中，透過例外狀況物件的索引。 您可以將例外狀況物件想像成一個 DAO 錯誤物件的 proxy。

1. 檢查目前[CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md)結構`GetErrorInfo`中會傳回[m_pErrorInfo](#m_perrorinfo)資料成員。 其成員提供 DAO 錯誤的相關資訊。

1. 如果是 ODBC 資料來源，重複步驟 3 和 4 依需要針對多個錯誤物件。

1. 如果您建構在堆積上的例外狀況物件，將它與刪除**刪除**運算子，當您完成時。

如需在 MFC DAO 類別中處理錯誤的詳細資訊，請參閱文章[例外狀況： 資料庫例外狀況](../../mfc/exceptions-database-exceptions.md)。

##  <a name="geterrorcount"></a>  CDaoException::GetErrorCount

呼叫此成員函式，以擷取 DAO 資料庫引擎的錯誤集合中的錯誤物件的數目。

```
short GetErrorCount();
```

### <a name="return-value"></a>傳回值

DAO 資料庫引擎的錯誤集合中的錯誤物件的數目。

### <a name="remarks"></a>備註

這項資訊可用於擷取每一或多個 DAO 錯誤物件的集合中的錯誤集合執行迴圈。 若要依索引或 DAO 錯誤編號，請擷取物件時發生錯誤，請呼叫[GetErrorInfo](#geterrorinfo)成員函式。

> [!NOTE]
>  通常沒有只有一個物件時發生錯誤的錯誤集合。 如果您正在使用 ODBC 資料來源，不過，可能有多個。

##  <a name="geterrorinfo"></a>  CDaoException::GetErrorInfo

傳回錯誤集合中的特定錯誤物件的相關資訊時發生錯誤。

```
void GetErrorInfo(int nIndex);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
資料庫引擎的錯誤集合，依索引查閱中的錯誤資訊的索引。

### <a name="remarks"></a>備註

呼叫此成員函式可取得下列類型的例外狀況的相關資訊：

- 錯誤碼

- 原始程式檔

- 描述

- 說明檔案

- 說明內容

`GetErrorInfo` 將資訊儲存在例外狀況物件的`m_pErrorInfo`資料成員。 傳回的資訊的簡短描述，請參閱 < [m_pErrorInfo](#m_perrorinfo)。 如果您攔截例外狀況型別的`CDaoException`MFC 中，所擲回`m_pErrorInfo`成員就會自動填入。 如果您選擇直接呼叫 DAO，您必須呼叫例外狀況物件的`GetErrorInfo`成員函式自行填入`m_pErrorInfo`。 如需更詳細的說明，請參閱[CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md)結構。

如需 DAO 例外狀況和範例程式碼，請參閱文章[例外狀況： 資料庫例外狀況](../../mfc/exceptions-database-exceptions.md)。

##  <a name="m_nafxdaoerror"></a>  CDaoException::m_nAfxDaoError

包含 MFC 延伸錯誤碼。

### <a name="remarks"></a>備註

此程式碼會在 MFC DAO 類別的特定元件具有 erred 其中的情況下提供。

可能的值為：

- 最新的作業不會造成在 MFC 中的 NO_AFX_DAO_ERROR 延伸錯誤。 不過，作業可能已產生其他錯誤從 DAO 或 OLE，因此您應該檢查[m_pErrorInfo](#m_perrorinfo)且可能[m_scode](#m_scode)。

- AFX_DAO_ERROR_ENGINE_INITIALIZATION MFC 無法初始化 Microsoft Jet 資料庫引擎。 OLE 可能無法初始化，或者它可能已被無法建立 DAO 資料庫引擎物件的執行個體。 這些問題通常會建議 DAO 或 OLE 的不正確安裝。

- AFX_DAO_ERROR_DFX_BIND DAO 資料錄欄位交換 (DFX) 函式呼叫中所用的地址不存在或無效 （地址已不會用來將資料繫結）。 您可能會在 DFX 呼叫中，傳遞不正確的位址或位址可能會變得無效 DFX 作業之間。

- AFX_DAO_ERROR_OBJECT_NOT_OPEN 您嘗試開啟資料錄集根據 querydef 或 tabledef 物件未處於開啟狀態。

##  <a name="m_perrorinfo"></a>  CDaoException::m_pErrorInfo

包含的指標`CDaoErrorInfo`提供您上次擷取藉由呼叫 DAO 錯誤物件的相關資訊的結構[GetErrorInfo](#geterrorinfo)。

### <a name="remarks"></a>備註

這個物件包含下列資訊：

|CDaoErrorInfo 成員|資訊|意義|
|--------------------------|-----------------|-------------|
|`m_lErrorCode`|錯誤碼|DAO 錯誤程式碼|
|`m_strSource`|原始程式檔|物件或最初產生錯誤的應用程式的名稱|
|`m_strDescription`|描述|與錯誤相關聯的描述性字串|
|`m_strHelpFile`|說明檔|Windows 說明的檔案，使用者可以在其中取得問題的相關資訊的路徑|
|`m_lHelpContext`|說明內容|DAO [說明] 檔案中的主題內容識別碼|

如需中所包含的資訊的完整詳細資料`CDaoErrorInfo`物件，請參閱 < [CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md)結構。

##  <a name="m_scode"></a>  CDaoException::m_scode

包含型別的值`SCODE`描述錯誤。

### <a name="remarks"></a>備註

這是 OLE 程式碼。 您很少需要使用此值，因為在幾乎所有情況下，更具體的 MFC 或 DAO 錯誤資訊可在其他`CDaoException`資料成員。

SCODE 的相關資訊，請參閱主題[結構的 OLE 錯誤碼](/windows/desktop/com/structure-of-com-error-codes)Windows SDK 中。 SCODE 資料類型會對應到 HRESULT 資料型別。

## <a name="see-also"></a>另請參閱

[CException 類別](../../mfc/reference/cexception-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CException 類別](../../mfc/reference/cexception-class.md)
