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
ms.openlocfilehash: 4b5dd2de2924b62dd76d7f16a494566849357de8
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57300358"
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
|[COleException::Process](#process)|將轉譯成 OLE 傳回碼攔截的例外狀況。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[COleException::m_sc](#m_sc)|包含指出例外狀況原因的狀態碼。|

## <a name="remarks"></a>備註

`COleException`類別包含公用資料成員包含例外狀況原因的狀態碼。

一般情況下，您不應建立`COleException`物件直接; 相反地，您應該呼叫[AfxThrowOleException](exception-processing.md#afxthrowoleexception)。

如需有關例外狀況的詳細資訊，請參閱文章[例外狀況處理 (MFC)](../../mfc/exception-handling-in-mfc.md)和[例外狀況：OLE 例外狀況](../../mfc/exceptions-ole-exceptions.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`COleException`

## <a name="requirements"></a>需求

**標頭：** afxdisp.h

##  <a name="m_sc"></a>  COleException::m_sc

此資料成員包含指出例外狀況的原因之 OLE 狀態碼。

```
SCODE m_sc;
```

### <a name="remarks"></a>備註

這個變數的值由設定[AfxThrowOleException](exception-processing.md#afxthrowoleexception)。

如需有關 SCODE 的詳細資訊，請參閱[錯誤碼的結構 COM](/windows/desktop/com/structure-of-com-error-codes) Windows SDK 中。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#22](../../mfc/codesnippet/cpp/coleexception-class_1.cpp)]

##  <a name="process"></a>  COleException::Process

呼叫**程序**成員函式以轉譯 OLE 狀態程式碼攔截的例外狀況。

```
static SCODE PASCAL Process(const CException* pAnyException);
```

### <a name="parameters"></a>參數

*pAnyException*<br/>
若要攔截的例外狀況的指標。

### <a name="return-value"></a>傳回值

OLE 狀態程式碼中。

### <a name="remarks"></a>備註

> [!NOTE]
>  此函式是**靜態**。

如需有關 SCODE 的詳細資訊，請參閱[錯誤碼的結構 COM](/windows/desktop/com/structure-of-com-error-codes) Windows SDK 中。

### <a name="example"></a>範例

  請參閱 [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch)的範例。

## <a name="see-also"></a>另請參閱

[MFC 範例 CALCDRIV](../../visual-cpp-samples.md)<br/>
[CException 類別](../../mfc/reference/cexception-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
