---
title: COleException 類別
ms.date: 11/04/2016
f1_keywords:
- COleException
- AFXDISP/COleException
- AFXDISP/COleException::Process
- AFXDISP/COleException::m_sc
helpviewer_keywords:
- COleException [MFC], Process
- COleException [MFC], m_sc
ms.assetid: 2571e9fe-26cc-42f0-9ad9-8ad5b4311ec1
ms.openlocfilehash: 737c9e669990f4de6ae18cdc7662c131ad61516f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375005"
---
# <a name="coleexception-class"></a>COleException 類別

表示與 OLE 作業相關的例外狀況。

## <a name="syntax"></a>語法

```
class COleException : public CException
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COle 例外::P](#process)|將捕獲的異常轉換為 OLE 返回代碼。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[COle 例外:m_sc](#m_sc)|包含指示異常原因的狀態代碼。|

## <a name="remarks"></a>備註

類`COleException`包括一個公共數據成員,該成員持有指示異常原因的狀態代碼。

通常,不應直接創建`COleException`物件,而應直接創建物件。相反,你應該調用[AfxThrowOleexception。](exception-processing.md#afxthrowoleexception)

有關異常的詳細資訊,請參閱[異常處理 (MFC)](../../mfc/exception-handling-in-mfc.md)和[異常:OLE 異常](../../mfc/exceptions-ole-exceptions.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[C 例外](../../mfc/reference/cexception-class.md)

`COleException`

## <a name="requirements"></a>需求

**標頭：** afxdisp.h

## <a name="coleexceptionm_sc"></a><a name="m_sc"></a>COle 例外:m_sc

此數據成員持有指示異常原因的 OLE 狀態代碼。

```
SCODE m_sc;
```

### <a name="remarks"></a>備註

此變數的值由[AfxThrowOleException](exception-processing.md#afxthrowoleexception)設置。

有關 SCODE 的詳細資訊,請參閱 Windows SDK 中的[COM 錯誤代碼結構](/windows/win32/com/structure-of-com-error-codes)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#22](../../mfc/codesnippet/cpp/coleexception-class_1.cpp)]

## <a name="coleexceptionprocess"></a><a name="process"></a>COle 例外::P

調用**Process**成員函數將捕獲的異常轉換為 OLE 狀態代碼。

```
static SCODE PASCAL Process(const CException* pAnyException);
```

### <a name="parameters"></a>參數

*pAnyException*<br/>
指向捕獲的異常的指標。

### <a name="return-value"></a>傳回值

OLE 狀態代碼。

### <a name="remarks"></a>備註

> [!NOTE]
> 此函數是**靜態**的。

有關 SCODE 的詳細資訊,請參閱 Windows SDK 中的[COM 錯誤代碼結構](/windows/win32/com/structure-of-com-error-codes)。

### <a name="example"></a>範例

  請參閱 [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch)的範例。

## <a name="see-also"></a>另請參閱

[MFC 樣品 CALCDRIV](../../overview/visual-cpp-samples.md)<br/>
[CException 類別](../../mfc/reference/cexception-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
