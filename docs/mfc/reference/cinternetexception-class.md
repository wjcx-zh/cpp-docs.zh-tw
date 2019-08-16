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
ms.openlocfilehash: c4f4c7a5b7594270aff9dfbc224e9a66ba09be3f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505912"
---
# <a name="cinternetexception-class"></a>CInternetException 類別

表示與網際網路作業相關的例外狀況。

## <a name="syntax"></a>語法

```
class CInternetException : public CException
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CInternetException::CInternetException](#cinternetexception)|建構 `CInternetException` 物件。|

### <a name="public-data-members"></a>公用資料成員

|名稱|說明|
|----------|-----------------|
|[CInternetException::m_dwContext](#m_dwcontext)|與造成例外狀況之作業相關聯的內容值。|
|[CInternetException::m_dwError](#m_dwerror)|造成例外狀況的錯誤。|

## <a name="remarks"></a>備註

`CInternetException`類別包含兩個公用資料成員: 一個保存與例外狀況相關聯的錯誤碼, 另一個則保存與錯誤相關聯之網際網路應用程式的內容識別碼。

如需有關網際網路應用程式內容識別碼的詳細資訊, 請參閱[使用 WinInet 進行網際網路程式設計](../../mfc/win32-internet-extensions-wininet.md)一文。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CInternetException`

## <a name="requirements"></a>需求

**標頭:** afxinet.h。h

##  <a name="cinternetexception"></a>CInternetException:: CInternetException

建立`CInternetException`物件時, 會呼叫這個成員函式。

```
CInternetException(DWORD dwError);
```

### <a name="parameters"></a>參數

*dwError*<br/>
造成例外狀況的錯誤。

### <a name="remarks"></a>備註

若要擲回 CInternetException, 請呼叫 MFC 全域函數[AfxThrowInternetException](internet-url-parsing-globals.md#afxthrowinternetexception)。

##  <a name="m_dwcontext"></a>  CInternetException::m_dwContext

與相關網際網路作業相關聯的內容值。

```
DWORD_PTR m_dwContext;
```

### <a name="remarks"></a>備註

內容識別碼最初是在[CInternetSession](../../mfc/reference/cinternetsession-class.md)中指定, 並由 MFC 傳遞至[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)和[CInternetFile](../../mfc/reference/cinternetfile-class.md)衍生的類別。 您可以覆寫此預設值, 並為任何*dwCoNtext*參數指派您所選擇的值。 *dwCoNtext*與指定物件的任何作業相關聯。 *dwCoNtext*會識別[CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)傳回的作業狀態資訊。

##  <a name="m_dwerror"></a>  CInternetException::m_dwError

造成例外狀況的錯誤。

```
DWORD m_dwError;
```

### <a name="remarks"></a>備註

這個錯誤值可能是系統錯誤碼, 可在 WINERROR.H 中找到。H, 或來自 WININET 的錯誤值。H.

如需 Win32 錯誤碼的清單, 請參閱[錯誤碼](/windows/win32/Debug/system-error-codes)。 如需網際網路特定的錯誤訊息清單, 請參閱。 這兩個主題都在 Windows SDK 中。

## <a name="see-also"></a>另請參閱

[CException 類別](../../mfc/reference/cexception-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CException 類別](../../mfc/reference/cexception-class.md)
