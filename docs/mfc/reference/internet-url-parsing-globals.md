---
title: 網際網路網址解析全域與說明器
ms.date: 04/03/2017
helpviewer_keywords:
- parsing, URLs
- URLs, parsing
ms.assetid: 46c6384f-e4a6-4dbd-9196-219c19040ec5
ms.openlocfilehash: 742b381ecb55c433d0f384174b7612fcc21e9716
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81356612"
---
# <a name="internet-url-parsing-globals-and-helpers"></a>網際網路網址解析全域與說明器

當用戶端將查詢傳送至網際網路伺服器時，您可以使用其中一個 URL 剖析全域來擷取用戶端的相關資訊。 幫助器功能提供其他互聯網功能。

## <a name="internet-url-parsing-globals"></a>網際網路 URL 剖析全域

|||
|-|-|
|[AfxParseURL](#afxparseurl)|剖析 URL 字串並傳回服務類型及其元件。|
|[AfxParseURLEx](#afxparseurlex)|剖析 URL 字串並傳回服務類型及其元件，並提供使用者名稱和密碼。|

## <a name="other-internet-helpers"></a>其他網路説明

|||
|-|-|
|[AfxThrowInternetException](#afxthrowinternetexception)|引發與互聯網連接相關的異常。|
|[AfxGetInternetHandleType](#afxgetinternethandletype)|確定 Internet 句柄的類型。|

## <a name="afxparseurl"></a><a name="afxparseurl"></a>AfxParseURL

此全域在[CInternetSession::打開 URL](../../mfc/reference/cinternetsession-class.md#openurl)中使用。

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
指向包含要解析的 URL 的字串的指標。

*dwServiceType*<br/>
指示 Internet 服務的類型。 可能的值如下：

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

*斯特雷伺服器*<br/>
服務類型之後網址的第一個段。

*strObject*<br/>
URL 引用的物件(可能為空)。

*n波特*<br/>
從 URL 的伺服器或物件部分確定(如果存在)。

### <a name="return-value"></a>傳回值

如果 URL 已成功解析,則非零;否則,如果為空或不包含已知的 Internet 服務類型,則為 0。

### <a name="remarks"></a>備註

它分析網址字串並傳回服務類型及其元件。

例如,`AfxParseURL`分析表單*service://server/dir/dir/object.ext:port*的網址 並傳回儲存的元件,如下所示:

*strServer* = "伺服器"

*strObject* = "/dir/dir/dir/物件/物件.ext"

*n波特*= #port

*dwServiceType* = #service

> [!NOTE]
> 要調用此函數,您的項目必須包括 AFXINET。H。

### <a name="requirements"></a>需求

  **標題**afxinet.h

## <a name="afxparseurlex"></a><a name="afxparseurlex"></a>AfxParseURLEx

此全域函數是[AfxParseURL](#afxparseurl)的延伸版本,用於[CInternetSession::openURL](../../mfc/reference/cinternetsession-class.md#openurl)。

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
指向包含要解析的 URL 的字串的指標。

*dwServiceType*<br/>
指示 Internet 服務的類型。 可能的值如下：

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

*斯特雷伺服器*<br/>
服務類型之後網址的第一個段。

*strObject*<br/>
URL 引用的物件(可能為空)。

*n波特*<br/>
從 URL 的伺服器或物件部分確定(如果存在)。

*序列使用者名稱*<br/>
對包含使用者名稱`CString`的物件的引用。

*斯特密碼*<br/>
對包含使用者密碼`CString`的物件的引用。

*dwFlags*<br/>
控制如何分析 URL 的標誌。 可以是以下值的組合:

|值|意義|
|-----------|-------------|
|ICU_DECODE|將 %1 次序列轉換為字元。|
|ICU_NO_ENCODE|不要將不安全的字元轉換為轉義序列。|
|ICU_NO_META|不要刪除元序列(如"*"。 和"*"。從 URL。|
|ICU_ENCODE_SPACES_ONLY|僅對空格進行編碼。|
|ICU_BROWSER_MODE|不要在"+"或"""之後對字元進行編碼或解碼,也不要刪除""之後的尾隨空格。 如果未指定此值,則對整個 URL 進行編碼並刪除尾隨空格。|

如果使用 MFC 預設值(沒有標誌),則函數將轉換所有不安全的字元和元序列\\(如 .、* . 和\\.)以轉義序列。

### <a name="return-value"></a>傳回值

如果 URL 已成功解析,則非零;否則,如果為空或不包含已知的 Internet 服務類型,則為 0。

### <a name="remarks"></a>備註

它解析 URL 字串並傳回服務類型及其元件,並提供使用者的名稱和密碼。 這些標誌指示如何處理不安全的字元。

> [!NOTE]
> 要調用此函數,您的項目必須包括 AFXINET。H。

### <a name="requirements"></a>需求

  **標題**afxinet.h

## <a name="afxgetinternethandletype"></a><a name="afxgetinternethandletype"></a>AfxGet網路處理類型

使用此全域函數確定 Internet 句柄的類型。

### <a name="syntax"></a>語法

  ```
DWORD AFXAPI AfxGetInternetHandleType(  HINTERNET hQuery );
```

### <a name="parameters"></a>參數

*hQuery*<br/>
Internet 查詢的句柄。

### <a name="return-value"></a>傳回值

WININET 定義的任何 Internet 服務類型。H。 有關這些互聯網服務的清單,請參閱備註部分。 如果句柄為 NULL 或無法識別,則函數將返回AFX_INET_SERVICE_UNK。

### <a name="remarks"></a>備註

以下清單包括返回的可能`AfxGetInternetHandleType`Internet 類型。

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
> 為了調用此函數,您的項目必須包括 AFXINET。H。

### <a name="requirements"></a>需求

**標題:** afxinet.h

## <a name="afxthrowinternetexception"></a><a name="afxthrowinternetexception"></a>AfxThrow互聯網例外

引發 Internet 異常。

### <a name="syntax"></a>語法

```
   void AFXAPI AfxThrowInternetException(  DWORD dwContext,  DWORD dwError = 0 );
```

### <a name="parameters"></a>參數

*dwContext*<br/>
導致錯誤的操作的上下文標識符。 *dwContext*的預設值最初在[CInternetSession 中](cinternetsession-class.md)指定,並傳遞給[CInternetConnection](cinternetconnection-class.md)- 和[CInternetFile](cinternetfile-class.md)派生類。 對於對連接或檔執行的特定操作,通常使用您自己的*dwContext*覆蓋預設值。 然後,此值將返回到[CInternetSession::onStatusBack](cinternetsession-class.md#onstatuscallback)以標識特定操作的狀態。

*dwError*<br/>
導致例外狀況的錯誤。

### <a name="remarks"></a>備註

您負責根據作業系統錯誤代碼確定原因。

> [!NOTE]
> 要調用此函數,您的項目必須包括 AFXINET。H。

### <a name="requirements"></a>需求

**標題:** afxinet.h

## <a name="see-also"></a>另請參閱

[巨集和全域](mfc-macros-and-globals.md)<br/>
[CInternetException 類別](cinternetexception-class.md)<br/>
[AfxParseURL](internet-url-parsing-globals.md#afxparseurl)
