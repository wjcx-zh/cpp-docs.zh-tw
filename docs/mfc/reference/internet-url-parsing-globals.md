---
title: 網際網路 URL 剖析全域和協助程式
ms.date: 04/03/2017
helpviewer_keywords:
- parsing, URLs
- URLs, parsing
ms.assetid: 46c6384f-e4a6-4dbd-9196-219c19040ec5
ms.openlocfilehash: c7ce6eeee6deb4537d09e102b925a742ada04650
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88837160"
---
# <a name="internet-url-parsing-globals-and-helpers"></a>網際網路 URL 剖析全域和協助程式

當用戶端將查詢傳送至網際網路伺服器時，您可以使用其中一個 URL 剖析全域來擷取用戶端的相關資訊。 Helper 函式提供其他網際網路功能。

## <a name="internet-url-parsing-globals"></a>網際網路 URL 剖析全域

|名稱|描述|
|-|-|
|[AfxParseURL](#afxparseurl)|剖析 URL 字串並傳回服務類型及其元件。|
|[AfxParseURLEx](#afxparseurlex)|剖析 URL 字串並傳回服務類型及其元件，並提供使用者名稱和密碼。|

## <a name="other-internet-helpers"></a>其他網際網路協助程式

|名稱|描述|
|-|-|
|[AfxThrowInternetException](#afxthrowinternetexception)|擲回與網際網路連接相關的例外狀況。|
|[AfxGetInternetHandleType](#afxgetinternethandletype)|決定網際網路控制碼的類型。|

## <a name="afxparseurl"></a><a name="afxparseurl"></a> AfxParseURL

此全域用於 [CInternetSession：： OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)。

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
指出網際網路服務的類型。 可能值如下所示：

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
遵循服務類型之 URL 的第一個區段。

*strObject*<br/>
URL 所參考的物件 (可能是空的) 。

*nPort*<br/>
從 URL 的伺服器或物件部分決定（如果有的話）。

### <a name="return-value"></a>傳回值

如果成功剖析 URL，則為非零;否則，如果是空的或不包含已知的網際網路服務類型，則為0。

### <a name="remarks"></a>備註

它會剖析 URL 字串，並傳回服務類型及其元件。

例如，剖析 `AfxParseURL` *service://server/dir/dir/object.ext:port* 表單的 url，並傳回其儲存的元件，如下所示：

*strServer* = = "server"

*strObject* = = "/dir/dir/object/object.ext"

*nPort* = = #port

*dwServiceType* = = #service

> [!NOTE]
> 若要呼叫此函數，您的專案必須包含 AFXINET.H。H。

### <a name="requirements"></a>規格需求

  **標頭** afxinet.h。h

## <a name="afxparseurlex"></a><a name="afxparseurlex"></a> AfxParseURLEx

此全域函式是 [AfxParseURL](#afxparseurl) 的擴充版本，在 [CInternetSession：： OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)中使用。

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
指出網際網路服務的類型。 可能值如下所示：

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
遵循服務類型之 URL 的第一個區段。

*strObject*<br/>
URL 所參考的物件 (可能是空的) 。

*nPort*<br/>
從 URL 的伺服器或物件部分決定（如果有的話）。

*strUsername*<br/>
物件的參考，該 `CString` 物件包含使用者的名稱。

*strPassword*<br/>
物件的參考，該 `CString` 物件包含使用者的密碼。

*dwFlags*<br/>
控制如何剖析 URL 的旗標。 可以是下列值的組合：

|值|意義|
|-----------|-------------|
|ICU_DECODE|將% XX escape 序列轉換成字元。|
|ICU_NO_ENCODE|請勿將 unsafe 字元轉換成 escape 序列。|
|ICU_NO_META|請勿移除中繼序列 (例如 "\." 和「\ ...」從 URL ) 。|
|ICU_ENCODE_SPACES_ONLY|僅編碼空格。|
|ICU_BROWSER_MODE|請勿在 ' # ' 或 ' ' 之後編碼或解碼字元，而且不要在 ' ' 之後移除尾端空白字元。 如果未指定此值，則會編碼整個 URL，並移除尾端空白字元。|

如果您使用 MFC 預設值（不是旗標），此函式會將所有不安全的字元和中繼序列 (例如 \\ .、\ ... 和 \\ ... ) 以進行 escape。

### <a name="return-value"></a>傳回值

如果成功剖析 URL，則為非零;否則，如果是空的或不包含已知的網際網路服務類型，則為0。

### <a name="remarks"></a>備註

它會剖析 URL 字串，並傳回服務類型及其元件，以及提供使用者的名稱和密碼。 旗標會指出如何處理不安全的字元。

> [!NOTE]
> 若要呼叫此函數，您的專案必須包含 AFXINET.H。H。

### <a name="requirements"></a>規格需求

  **標頭** afxinet.h。h

## <a name="afxgetinternethandletype"></a><a name="afxgetinternethandletype"></a> AfxGetInternetHandleType

您可以使用此全域函式來判斷網際網路控制碼的類型。

### <a name="syntax"></a>語法

  ```
DWORD AFXAPI AfxGetInternetHandleType(  HINTERNET hQuery );
```

### <a name="parameters"></a>參數

*hQuery*<br/>
網際網路查詢的控制碼。

### <a name="return-value"></a>傳回值

WININET 所定義的任何網際網路服務類型。H。 請參閱「備註」一節，以取得這些網際網路服務的清單。 如果控制碼為 Null 或無法辨識，則函數會傳回 AFX_INET_SERVICE_UNK。

### <a name="remarks"></a>備註

下列清單包含所傳回的可能網際網路類型 `AfxGetInternetHandleType` 。

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
> 為了呼叫這個函式，您的專案必須包含 AFXINET.H。H。

### <a name="requirements"></a>規格需求

**標頭：** afxinet.h。h

## <a name="afxthrowinternetexception"></a><a name="afxthrowinternetexception"></a> AfxThrowInternetException

擲回網際網路例外狀況。

### <a name="syntax"></a>語法

```
   void AFXAPI AfxThrowInternetException(  DWORD dwContext,  DWORD dwError = 0 );
```

### <a name="parameters"></a>參數

*dwCoNtext*<br/>
造成錯誤之作業的內容識別碼。 *DwCoNtext*的預設值最初是在[CInternetSession](cinternetsession-class.md)中指定，並傳遞至[CInternetConnection](cinternetconnection-class.md)和[CInternetFile](cinternetfile-class.md)衍生的類別。 針對連接或檔案上執行的特定作業，您通常會以自己的 *dwCoNtext* 覆寫預設值。 然後，此值會傳回給 [CInternetSession：： OnStatusCallback](cinternetsession-class.md#onstatuscallback) ，以識別特定作業的狀態。

*dwError*<br/>
導致例外狀況的錯誤。

### <a name="remarks"></a>備註

您必須負責根據作業系統錯誤碼來判斷原因。

> [!NOTE]
> 若要呼叫此函數，您的專案必須包含 AFXINET.H。H。

### <a name="requirements"></a>規格需求

**標頭：** afxinet.h。h

## <a name="see-also"></a>另請參閱

[巨集和全域](mfc-macros-and-globals.md)<br/>
[CInternetException 類別](cinternetexception-class.md)<br/>
[AfxParseURL](internet-url-parsing-globals.md#afxparseurl)
