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
ms.openlocfilehash: e89293d7b7803cf661bce7a91ea6df72b9a06122
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50531569"
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
|[CInternetException::CInternetException](#cinternetexception)|建構 `CInternetException` 物件。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CInternetException::m_dwContext](#m_dwcontext)|造成例外狀況的作業相關聯的內容值。|
|[CInternetException::m_dwError](#m_dwerror)|造成例外狀況時發生錯誤。|

## <a name="remarks"></a>備註

`CInternetException`類別包含兩個公用資料成員： 其中保留例外狀況相關聯的錯誤碼，而其他則會保留與錯誤相關聯的網際網路應用程式的內容識別碼。

如需詳細的網際網路應用程式的內容識別碼的詳細資訊，請參閱文章[網際網路程式設計 WinInet](../../mfc/win32-internet-extensions-wininet.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CInternetException`

## <a name="requirements"></a>需求

**標頭：** afxinet.h

##  <a name="cinternetexception"></a>  CInternetException::CInternetException

此成員函式時，會呼叫`CInternetException`建立物件。

```
CInternetException(DWORD dwError);
```

### <a name="parameters"></a>參數

*dwError*<br/>
造成例外狀況時發生錯誤。

### <a name="remarks"></a>備註

擲回 CInternetException，呼叫 MFC 的全域函式[AfxThrowInternetException](internet-url-parsing-globals.md#afxthrowinternetexception)。

##  <a name="m_dwcontext"></a>  CInternetException::m_dwContext

與相關的網際網路作業相關聯的內容值。

```
DWORD_PTR m_dwContext;
```

### <a name="remarks"></a>備註

中原本指定的內容識別項[CInternetSession](../../mfc/reference/cinternetsession-class.md) ，並傳遞到 mfc [CInternetConnection](../../mfc/reference/cinternetconnection-class.md)-並[CInternetFile](../../mfc/reference/cinternetfile-class.md)-衍生的類別。 您可以覆寫此預設值，並指派任何*dwContext*參數您選擇的值。 *dwContext*與指定任何的物件作業相關聯。 *dwContext*識別傳回作業的狀態資訊[CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)。

##  <a name="m_dwerror"></a>  CInternetException::m_dwError

造成例外狀況時發生錯誤。

```
DWORD m_dwError;
```

### <a name="remarks"></a>備註

此錯誤的值可能是系統 WINERROR 中找到的錯誤碼。H 或從 WININET 錯誤值。H.

如需 Win32 錯誤碼的清單，請參閱 <<c0> [ 錯誤碼](/windows/desktop/Debug/system-error-codes)。 如需網際網路特定錯誤訊息的清單，請參閱。 這兩個主題位於 Windows SDK 中。

## <a name="see-also"></a>另請參閱

[CException 類別](../../mfc/reference/cexception-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CException 類別](../../mfc/reference/cexception-class.md)
