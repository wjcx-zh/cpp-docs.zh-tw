---
title: 剖析 Globals 和 helper 的網際網路 URL
ms.date: 04/03/2017
helpviewer_keywords:
- parsing, URLs
- URLs, parsing
ms.assetid: 46c6384f-e4a6-4dbd-9196-219c19040ec5
ms.openlocfilehash: 310e4ffb3fc207d874e97ba1fac65f6f8cb41a31
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79421300"
---
# <a name="internet-url-parsing-globals-and-helpers"></a>剖析 Globals 和 helper 的網際網路 URL

當用戶端將查詢傳送至網際網路伺服器時，您可以使用其中一個 URL 剖析全域來擷取用戶端的相關資訊。 Helper 函式提供其他網際網路功能。

## <a name="internet-url-parsing-globals"></a>網際網路 URL 剖析全域

|||
|-|-|
|[AfxParseURL](#afxparseurl)|剖析 URL 字串並傳回服務類型及其元件。|
|[AfxParseURLEx](#afxparseurlex)|剖析 URL 字串並傳回服務類型及其元件，並提供使用者名稱和密碼。|

## <a name="other-internet-helpers"></a>其他網際網路協助程式

|||
|-|-|
|[AfxThrowInternetException](#afxthrowinternetexception)|會擲回與網際網路連接相關的例外狀況。|
|[AfxGetInternetHandleType](#afxgetinternethandletype)|決定網際網路控制碼的類型。|

##  <a name="afxparseurl"></a>AfxParseURL

此全域用於[CInternetSession：： OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)。

```
BOOL AFXAPI AfxParseURL(
    LPCTSTR pstrURL,
    DWORD& dwServiceType,
    CString& strServer,
    CString& strObject,
    INTERNET_PORT& nPort);
```

### <a name="parameters"></a>參數

*pstrURL*<br/>
包含要剖析之 URL 的字串指標。

*dwServiceType*<br/>
表示網際網路服務的類型。 可能的值如下：

- AFX_INET_SERVICE_FTP

- AFX_INET_SERVICE_HTTP

- AFX_INET_SERVICE_HTTPS

- AFX_INET_SERVICE_GOPHER

- AFX_INET_SERVICE_FILE

- AFX_INET_SERVICE_MAILTO

- AFX_INET_SERVICE_NEWS

- AFX_INET_SERVICE_NNTP

- AFX_INET_SERVICE_TELNET

- AFX_INET_SERVICE_WAIS

- AFX_INET_SERVICE_MID

- AFX_INET_SERVICE_CID

- AFX_INET_SERVICE_PROSPERO

- AFX_INET_SERVICE_AFS

- AFX_INET_SERVICE_UNK

*strServer*<br/>
服務類型後面的 URL 的第一個區段。

*strObject*<br/>
URL 所參考的物件（可能是空的）。

*nPort*<br/>
從 URL 的伺服器或物件部分決定（如果有的話）。

### <a name="return-value"></a>傳回值

如果成功剖析 URL，則為非零;否則，如果它是空的或不包含已知的網際網路服務類型，則為0。

### <a name="remarks"></a>備註

它會剖析 URL 字串，並傳回服務類型及其元件。

例如，`AfxParseURL` 會剖析*service://server/dir/dir/object.ext:port*表單的 url，並傳回其儲存的元件，如下所示：

*strServer* = = "server"

*strObject* = = "/dir/dir/object/object.ext"

*nPort* = = #port

*dwServiceType* = = #service

> [!NOTE]
>  若要呼叫此函式，您的專案必須包含 AFXINET.H。H.

### <a name="requirements"></a>需求

  **標頭**afxinet.h。h

##  <a name="afxparseurlex"></a>AfxParseURLEx

此全域函式是[AfxParseURL](#afxparseurl)的擴充版本，可用於[CInternetSession：： OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)。

```
BOOL AFXAPI AfxParseURLEx(
    LPCTSTR pstrURL,
    DWORD& dwServiceType,
    CString& strServer,
    CString& strObject,
    INTERNET_PORT& nPort,
    CString& strUsername,
    CString& strPassword,
    DWORD dwFlags = 0);
```

### <a name="parameters"></a>參數

*pstrURL*<br/>
包含要剖析之 URL 的字串指標。

*dwServiceType*<br/>
表示網際網路服務的類型。 可能的值如下：

- AFX_INET_SERVICE_FTP

- AFX_INET_SERVICE_HTTP

- AFX_INET_SERVICE_HTTPS

- AFX_INET_SERVICE_GOPHER

- AFX_INET_SERVICE_FILE

- AFX_INET_SERVICE_MAILTO

- AFX_INET_SERVICE_NEWS

- AFX_INET_SERVICE_NNTP

- AFX_INET_SERVICE_TELNET

- AFX_INET_SERVICE_WAIS

- AFX_INET_SERVICE_MID

- AFX_INET_SERVICE_CID

- AFX_INET_SERVICE_PROSPERO

- AFX_INET_SERVICE_AFS

- AFX_INET_SERVICE_UNK

*strServer*<br/>
服務類型後面的 URL 的第一個區段。

*strObject*<br/>
URL 所參考的物件（可能是空的）。

*nPort*<br/>
從 URL 的伺服器或物件部分決定（如果有的話）。

*strUsername*<br/>
包含使用者名稱之 `CString` 物件的參考。

*strPassword*<br/>
`CString` 物件的參考，其中包含使用者的密碼。

*dwFlags*<br/>
控制如何剖析 URL 的旗標。 可以是下列值的組合：

|值|意義|
|-----------|-------------|
|ICU_DECODE|將% XX escape 序列轉換成字元。|
|ICU_NO_ENCODE|請勿將 unsafe 字元轉換成 escape 序列。|
|ICU_NO_META|請勿移除中繼序列（例如 "\."）。 和 "\.."）從 URL。|
|ICU_ENCODE_SPACES_ONLY|只將空格編碼。|
|ICU_BROWSER_MODE|不要編碼或解碼 ' # ' 或 ' ' 之後的字元，也不要移除 ' ' 後面的尾端空白字元。 如果未指定此值，則會編碼整個 URL，並移除尾端空白字元。|

如果您使用 MFC 預設值，這不是旗標，則函式會將所有不安全的字元和中繼序列（例如 \\.、\. 和 \\...）轉換成 escape 序列。

### <a name="return-value"></a>傳回值

如果成功剖析 URL，則為非零;否則，如果它是空的或不包含已知的網際網路服務類型，則為0。

### <a name="remarks"></a>備註

它會剖析 URL 字串並傳回服務類型及其元件，以及提供使用者的名稱和密碼。 旗標指出如何處理不安全的字元。

> [!NOTE]
>  若要呼叫此函式，您的專案必須包含 AFXINET.H。H.

### <a name="requirements"></a>需求

  **標頭**afxinet.h。h

## <a name="afxgetinternethandletype"></a>AfxGetInternetHandleType

使用此全域函式來判斷網際網路控制碼的類型。

### <a name="syntax"></a>語法

  ```
DWORD AFXAPI AfxGetInternetHandleType(  HINTERNET hQuery );
```

### <a name="parameters"></a>參數

*hQuery*<br/>
網際網路查詢的控制碼。

### <a name="return-value"></a>傳回值

WININET 所定義的任何網際網路服務類型。H. 如需這些網際網路服務的清單，請參閱備註一節。 如果控制碼為 Null 或無法辨識，此函數會傳回 AFX_INET_SERVICE_UNK。

### <a name="remarks"></a>備註

下列清單包含 `AfxGetInternetHandleType`傳回的可能網際網路類型。

- INTERNET_HANDLE_TYPE_INTERNET

- INTERNET_HANDLE_TYPE_CONNECT_FTP

- INTERNET_HANDLE_TYPE_CONNECT_GOPHER

- INTERNET_HANDLE_TYPE_CONNECT_HTTP

- INTERNET_HANDLE_TYPE_FTP_FIND

- INTERNET_HANDLE_TYPE_FTP_FIND_HTML

- INTERNET_HANDLE_TYPE_FTP_FILE

- INTERNET_HANDLE_TYPE_FTP_FILE_HTML

- INTERNET_HANDLE_TYPE_GOPHER_FIND

- INTERNET_HANDLE_TYPE_GOPHER_FIND_HTML

- INTERNET_HANDLE_TYPE_GOPHER_FILE

- INTERNET_HANDLE_TYPE_GOPHER_FILE_HTML

- INTERNET_HANDLE_TYPE_HTTP_REQUEST

> [!NOTE]
>  您的專案必須包含 AFXINET.H，才能呼叫此函式。H.

### <a name="requirements"></a>需求

**標頭：** afxinet.h。h

## <a name="afxthrowinternetexception"></a>AfxThrowInternetException

擲回網際網路例外狀況。

### <a name="syntax"></a>語法

```
   void AFXAPI AfxThrowInternetException(  DWORD dwContext,  DWORD dwError = 0 );
```

### <a name="parameters"></a>參數

*dwCoNtext*<br/>
造成錯誤之作業的內容識別碼。 *DwCoNtext*的預設值原本是在[CInternetSession](cinternetsession-class.md)中指定，並且會傳遞給[CInternetConnection](cinternetconnection-class.md)和[CInternetFile](cinternetfile-class.md)衍生的類別。 對於在連接或檔案上執行的特定作業，您通常會使用自己的*dwCoNtext*來覆寫預設值。 然後，此值會傳回給[CInternetSession：： OnStatusCallback](cinternetsession-class.md#onstatuscallback) ，以識別特定作業的狀態。

*dwError*<br/>
例外狀況產生的錯誤訊息。

### <a name="remarks"></a>備註

您必須負責根據作業系統錯誤碼來判斷原因。

> [!NOTE]
>  若要呼叫此函式，您的專案必須包含 AFXINET.H。H.

### <a name="requirements"></a>需求

**標頭：** afxinet.h。h

## <a name="see-also"></a>另請參閱

[宏和全域](mfc-macros-and-globals.md)<br/>
[CInternetException 類別](cinternetexception-class.md)<br/>
[AfxParseURL](internet-url-parsing-globals.md#afxparseurl)
