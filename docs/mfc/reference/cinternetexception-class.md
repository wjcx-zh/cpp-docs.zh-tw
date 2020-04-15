---
title: CInternetException 類別
ms.date: 11/04/2016
f1_keywords:
- CInternetException
- AFXINET/CInternetException
- AFXINET/CInternetException::CInternetException
- AFXINET/CInternetException::m_dwContext
- AFXINET/CInternetException::m_dwError
helpviewer_keywords:
- CInternetException [MFC], CInternetException
- CInternetException [MFC], m_dwContext
- CInternetException [MFC], m_dwError
ms.assetid: 44fb3cbe-523e-4754-8843-a77909990b14
ms.openlocfilehash: b0239afa2b984ccf93d661ec11f11013c89fd912
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372411"
---
# <a name="cinternetexception-class"></a>CInternetException 類別

表示與網際網路作業相關的例外狀況。

## <a name="syntax"></a>語法

```
class CInternetException : public CException
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[C 網際網路例外:C 網際網路例外](#cinternetexception)|建構 `CInternetException` 物件。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[C 網際網路例外:m_dwContext](#m_dwcontext)|與導致異常的操作關聯的上下文值。|
|[C 互聯網例外:m_dwError](#m_dwerror)|導致例外狀況的錯誤。|

## <a name="remarks"></a>備註

該`CInternetException`類包括兩個公共數據成員:一個保存與異常關聯的錯誤代碼,另一個保留與錯誤關聯的 Internet 應用程式的上下文標識符。

有關網際網路應用程式的內容識別碼的詳細資訊,請參閱[使用 WinInet 使用 Internet 撰寫程式的文章](../../mfc/win32-internet-extensions-wininet.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[C 例外](../../mfc/reference/cexception-class.md)

`CInternetException`

## <a name="requirements"></a>需求

**標題:** afxinet.h

## <a name="cinternetexceptioncinternetexception"></a><a name="cinternetexception"></a>C 網際網路例外:C 網際網路例外

創建`CInternetException`物件時將調用此成員函數。

```
CInternetException(DWORD dwError);
```

### <a name="parameters"></a>參數

*dwError*<br/>
導致例外狀況的錯誤。

### <a name="remarks"></a>備註

要引發 CInternetException,請致電 MFC 全域函數[AfxThrow InternetException](internet-url-parsing-globals.md#afxthrowinternetexception)。

## <a name="cinternetexceptionm_dwcontext"></a><a name="m_dwcontext"></a>C 網際網路例外:m_dwContext

與相關 Internet 操作關聯的上下文值。

```
DWORD_PTR m_dwContext;
```

### <a name="remarks"></a>備註

上下文識別碼最初在[CInternetSession](../../mfc/reference/cinternetsession-class.md)中指定,並由 MFC 傳遞給[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)- 和[CInternetFile](../../mfc/reference/cinternetfile-class.md)派生類。 您可以覆寫此預設值,並分配任何*dwContext*參數您選擇的值。 *dwContext*與給定物件的任何操作相關聯。 *dwContext*識別 CInternetSession 傳回的作業的狀態資訊[::onStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)。

## <a name="cinternetexceptionm_dwerror"></a><a name="m_dwerror"></a>C 互聯網例外:m_dwError

導致例外狀況的錯誤。

```
DWORD m_dwError;
```

### <a name="remarks"></a>備註

此錯誤值可能是在 WINERROR 中找到的系統錯誤代碼。H,或 WININET 的錯誤值。H。

有關 Win32 錯誤代碼的清單,請參閱[錯誤代碼](/windows/win32/Debug/system-error-codes)。 有關特定於 Internet 的錯誤消息的清單,請參閱。 這兩個主題都在 Windows SDK 中。

## <a name="see-also"></a>另請參閱

[CException 類別](../../mfc/reference/cexception-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CException 類別](../../mfc/reference/cexception-class.md)
