---
title: COleDispatchException 類別
ms.date: 11/04/2016
f1_keywords:
- COleDispatchException
- AFXDISP/COleDispatchException
- AFXDISP/COleDispatchException::m_dwHelpContext
- AFXDISP/COleDispatchException::m_strDescription
- AFXDISP/COleDispatchException::m_strHelpFile
- AFXDISP/COleDispatchException::m_strSource
- AFXDISP/COleDispatchException::m_wCode
helpviewer_keywords:
- COleDispatchException [MFC], m_dwHelpContext
- COleDispatchException [MFC], m_strDescription
- COleDispatchException [MFC], m_strHelpFile
- COleDispatchException [MFC], m_strSource
- COleDispatchException [MFC], m_wCode
ms.assetid: 0e95c8be-e21a-490c-99ec-181c6a9a26d0
ms.openlocfilehash: 4572b639b757569d8e3cfa731f99c123762f3900
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375055"
---
# <a name="coledispatchexception-class"></a>COleDispatchException 類別

處理 OLE `IDispatch` 介面 (OLE Automation 的主要部分) 特定的例外狀況。

## <a name="syntax"></a>語法

```
class COleDispatchException : public CException
```

## <a name="members"></a>成員

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[COleDispatch例外:m_dwHelpContext](#m_dwhelpcontext)|説明上下文查找錯誤。|
|[COleDispatch例外::m_strDescription](#m_strdescription)|口頭錯誤描述。|
|[COleDispatchException::m_strHelpFile](#m_strhelpfile)|說明檔案與`m_dwHelpContext`使用 。|
|[COleDispatch例外::m_strSource](#m_strsource)|生成異常的應用程式。|
|[COleDispatch例外:m_wCode](#m_wcode)|`IDispatch`-特定於錯誤代碼。|

## <a name="remarks"></a>備註

與從`CException`基類派生的其他異常類一樣`COleDispatchException`, 可以使用 THROW、THROW_LAST、TRY、CATCH、AND_CATCH 和END_CATCH宏。

通常,應呼叫[AfxThrowOleDispatchException](exception-processing.md#afxthrowoledispatchexception)來建立和`COleDispatchException`引發物件 。

有關異常的詳細資訊,請參閱[異常處理 (MFC)](../../mfc/exception-handling-in-mfc.md)和[異常:OLE 異常](../../mfc/exceptions-ole-exceptions.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[C 例外](../../mfc/reference/cexception-class.md)

`COleDispatchException`

## <a name="requirements"></a>需求

**標頭：** afxdisp.h

## <a name="coledispatchexceptionm_dwhelpcontext"></a><a name="m_dwhelpcontext"></a>COleDispatch例外:m_dwHelpContext

在應用程式的説明 (中標識説明上下文。HLP)檔。

```
DWORD m_dwHelpContext;
```

### <a name="remarks"></a>備註

此成員由函數[AfxThrowOleDispatchException](exception-processing.md#afxthrowoledispatchexception)設置,當引發異常時。

### <a name="example"></a>範例

  請參閱 [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch)的範例。

## <a name="coledispatchexceptionm_strdescription"></a><a name="m_strdescription"></a>COleDispatch例外::m_strDescription

包含口頭錯誤描述,如"磁碟已滿"。

```
CString m_strDescription;
```

### <a name="remarks"></a>備註

此成員由函數[AfxThrowOleDispatchException](exception-processing.md#afxthrowoledispatchexception)設置,當引發異常時。

### <a name="example"></a>範例

  請參閱 [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch)的範例。

## <a name="coledispatchexceptionm_strhelpfile"></a><a name="m_strhelpfile"></a>COleDispatchException::m_strHelpFile

框架用應用程式的幫助檔的名稱填充此字串。

```
CString m_strHelpFile;
```

## <a name="coledispatchexceptionm_strsource"></a><a name="m_strsource"></a>COleDispatch例外::m_strSource

框架用生成異常的應用程式的名稱填充此字串。

```
CString m_strSource;
```

### <a name="example"></a>範例

  請參閱 [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch)的範例。

## <a name="coledispatchexceptionm_wcode"></a><a name="m_wcode"></a>COleDispatch例外:m_wCode

包含特定於應用程式的錯誤代碼。

```
WORD m_wCode;
```

### <a name="remarks"></a>備註

此成員由函數[AfxThrowOleDispatchException](exception-processing.md#afxthrowoledispatchexception)設置,當引發異常時。

## <a name="see-also"></a>另請參閱

[MFC 樣品 CALCDRIV](../../overview/visual-cpp-samples.md)<br/>
[CException 類別](../../mfc/reference/cexception-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COle排程驅動程式類別](../../mfc/reference/coledispatchdriver-class.md)<br/>
[COleException 類別](../../mfc/reference/coleexception-class.md)
