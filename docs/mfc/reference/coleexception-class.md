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
ms.openlocfilehash: 96061f704d9df6cd788e362652b6ed22a7ffa999
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503953"
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
|[COleException::Process](#process)|將攔截到的例外狀況轉譯為 OLE 傳回碼。|

### <a name="public-data-members"></a>公用資料成員

|名稱|說明|
|----------|-----------------|
|[COleException::m_sc](#m_sc)|包含指出例外狀況原因的狀態碼。|

## <a name="remarks"></a>備註

`COleException`類別包含的公用資料成員會保存狀態碼, 指出例外狀況的原因。

一般來說, 您不應該直接建立`COleException`物件, 而應呼叫[AfxThrowOleException](exception-processing.md#afxthrowoleexception)。

如需例外狀況的詳細資訊, 請參閱[例外狀況處理 (MFC)](../../mfc/exception-handling-in-mfc.md)和[例外狀況:OLE 例外](../../mfc/exceptions-ole-exceptions.md)狀況。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`COleException`

## <a name="requirements"></a>需求

**標頭：** afxdisp.h

##  <a name="m_sc"></a>  COleException::m_sc

此資料成員會保存表示例外狀況原因的 OLE 狀態碼。

```
SCODE m_sc;
```

### <a name="remarks"></a>備註

這個變數的值是由[AfxThrowOleException](exception-processing.md#afxthrowoleexception)所設定。

如需 SCODE 的詳細資訊, 請參閱 Windows SDK 中[COM 錯誤碼的結構](/windows/win32/com/structure-of-com-error-codes)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#22](../../mfc/codesnippet/cpp/coleexception-class_1.cpp)]

##  <a name="process"></a>  COleException::Process

呼叫**進程**成員函式, 將攔截到的例外狀況轉譯為 OLE 狀態碼。

```
static SCODE PASCAL Process(const CException* pAnyException);
```

### <a name="parameters"></a>參數

*pAnyException*<br/>
攔截到的例外狀況指標。

### <a name="return-value"></a>傳回值

OLE 狀態碼。

### <a name="remarks"></a>備註

> [!NOTE]
>  這是**靜態**函式。

如需 SCODE 的詳細資訊, 請參閱 Windows SDK 中[COM 錯誤碼的結構](/windows/win32/com/structure-of-com-error-codes)。

### <a name="example"></a>範例

  請參閱 [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch)的範例。

## <a name="see-also"></a>另請參閱

[MFC 範例 CALCDRIV:](../../overview/visual-cpp-samples.md)<br/>
[CException 類別](../../mfc/reference/cexception-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
