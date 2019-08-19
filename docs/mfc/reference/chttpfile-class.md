---
title: CHttpFile 類別
ms.date: 11/04/2016
f1_keywords:
- CHttpFile
- AFXINET/CHttpFile
- AFXINET/CHttpFile::CHttpFile
- AFXINET/CHttpFile::AddRequestHeaders
- AFXINET/CHttpFile::EndRequest
- AFXINET/CHttpFile::GetFileURL
- AFXINET/CHttpFile::GetObject
- AFXINET/CHttpFile::GetVerb
- AFXINET/CHttpFile::QueryInfo
- AFXINET/CHttpFile::QueryInfoStatusCode
- AFXINET/CHttpFile::SendRequest
- AFXINET/CHttpFile::SendRequestEx
helpviewer_keywords:
- CHttpFile [MFC], CHttpFile
- CHttpFile [MFC], AddRequestHeaders
- CHttpFile [MFC], EndRequest
- CHttpFile [MFC], GetFileURL
- CHttpFile [MFC], GetObject
- CHttpFile [MFC], GetVerb
- CHttpFile [MFC], QueryInfo
- CHttpFile [MFC], QueryInfoStatusCode
- CHttpFile [MFC], SendRequest
- CHttpFile [MFC], SendRequestEx
ms.assetid: 399e7c68-bbce-4374-8c55-206e9c7baac6
ms.openlocfilehash: ff050a89a10c68c639c141891dd51b1b2d58e105
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916003"
---
# <a name="chttpfile-class"></a>CHttpFile 類別

提供在 HTTP 伺服器上要求和讀取檔案的功能。

## <a name="syntax"></a>語法

```
class CHttpFile : public CInternetFile
```

## <a name="members"></a>成員

### <a name="protected-constructors"></a>受保護的建構函式

|名稱|描述|
|----------|-----------------|
|[CHttpFile:: CHttpFile](#chttpfile)|建立 `CHttpFile` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CHttpFile::AddRequestHeaders](#addrequestheaders)|將標頭新增至傳送至 HTTP 伺服器的要求。|
|[CHttpFile::EndRequest](#endrequest)|結束使用[SendRequestEx](#sendrequestex)成員函式傳送至 HTTP 伺服器的要求。|
|[CHttpFile::GetFileURL](#getfileurl)|取得指定檔案的 URL。|
|[CHttpFile::GetObject](#getobject)|取得 HTTP 伺服器要求中動詞命令的目標物件。|
|[CHttpFile::GetVerb](#getverb)|取得在 HTTP 伺服器的要求中使用的動詞。|
|[CHttpFile::QueryInfo](#queryinfo)|傳回 HTTP 伺服器的回應或要求標頭。|
|[CHttpFile::QueryInfoStatusCode](#queryinfostatuscode)|抓取與 HTTP 要求相關聯的狀態碼, 並將它放在`dwStatusCode`提供的參數中。|
|[CHttpFile::SendRequest](#sendrequest)|將要求傳送至 HTTP 伺服器。|
|[CHttpFile::SendRequestEx](#sendrequestex)|使用的[Write](../../mfc/reference/cinternetfile-class.md#write)或[WriteString](../../mfc/reference/cinternetfile-class.md#writestring)方法`CInternetFile`, 將要求傳送至 HTTP 伺服器。|

## <a name="remarks"></a>備註

如果您的網際網路會話會從 HTTP 伺服器讀取資料, 您必須建立的`CHttpFile`實例。

若要深入瞭解如何`CHttpFile`與其他 MFC 網際網路類別搭配運作, 請參閱[使用 WinInet 進行網際網路程式設計](../../mfc/win32-internet-extensions-wininet.md)一文。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[CStdioFile](../../mfc/reference/cstdiofile-class.md)

[CInternetFile](../../mfc/reference/cinternetfile-class.md)

`CHttpFile`

## <a name="requirements"></a>需求

**標頭:** afxinet.h。h

##  <a name="addrequestheaders"></a>CHttpFile:: AddRequestHeaders

呼叫這個成員函式, 將一或多個 HTTP 要求標頭新增至 HTTP 要求控制碼。

```
BOOL AddRequestHeaders(
    LPCTSTR pstrHeaders,
    DWORD dwFlags = HTTP_ADDREQ_FLAG_ADD_IF_NEW,
    int dwHeadersLen = -1);

BOOL AddRequestHeaders(
    CString& str,
    DWORD dwFlags = HTTP_ADDREQ_FLAG_ADD_IF_NEW);
```

### <a name="parameters"></a>參數

*pstrHeaders*<br/>
字串的指標, 其中包含要附加至要求的標頭或標頭。 每個標頭都必須以 CR/LF 配對結束。

*dwFlags*<br/>
修改新標頭的語法。 可以是下列其中一項：

- HTTP_ADDREQ_FLAG_COALESCE 會合並相同名稱的標頭, 並使用旗標來新增第一個標頭所找到的標題。 例如, "accept\*: text/" 後面接著 "accept: audio/\*" 會產生單一標頭 "accept: text/\*, audio/\*" 的構成。 呼叫應用程式會負責確保與透過合併或個別標頭傳送的要求所收到的資料具有一致的配置。

- HTTP_ADDREQ_FLAG_REPLACE 會執行 remove 並新增來取代目前的標頭。 標頭名稱將用來移除目前的標頭, 而完整的值將用來加入新的標頭。 如果標頭值是空的, 而且找到標頭, 則會將它移除。 如果不是空的, 則會取代標頭值。

- HTTP_ADDREQ_FLAG_ADD_IF_NEW 只會新增標頭 (如果它不存在)。 如果有的話, 就會傳回錯誤。

- HTTP_ADDREQ_FLAG_ADD 搭配 REPLACE 使用。 新增標頭 (如果不存在)。

*dwHeadersLen*<br/>
*PstrHeaders*的長度 (以字元為單位)。 如果這是-1L, 則會假設*pstrHeaders*以零終止, 並計算長度。

*str*<br/>
[CString](../../atl-mfc-shared/reference/cstringt-class.md)物件的參考, 其中包含要加入的要求標頭或標頭。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。 如果呼叫失敗, 則可以呼叫 Win32 函數[GetLastError](/windows/desktop/api/errhandlingapi/nf-errhandlingapi-getlasterror)來判斷錯誤的原因。

### <a name="remarks"></a>備註

`AddRequestHeaders`將其他的自由格式標頭附加至 HTTP 要求控制碼。 其適用于需要詳細控制傳送至 HTTP 伺服器之確切要求的精密用戶端。

> [!NOTE]
>  應用程式可以傳遞*pstrHeaders*或*str*中的多個標`AddRequestHeaders`頭, 以進行使用 HTTP_ADDREQ_FLAG_ADD 或 HTTP_ADDREQ_FLAG_ADD_IF_NEW 的呼叫。 如果應用程式嘗試使用 HTTP_ADDREQ_FLAG_REMOVE 或 HTTP_ADDREQ_FLAG_REPLACE 來移除或取代標頭, 則*lpszHeaders*中只能提供一個標頭。

##  <a name="chttpfile"></a>CHttpFile:: CHttpFile

呼叫這個成員函式以建立`CHttpFile`物件。

```
CHttpFile(
    HINTERNET hFile,
    HINTERNET hSession,
    LPCTSTR pstrObject,
    LPCTSTR pstrServer,
    LPCTSTR pstrVerb,
    DWORD_PTR dwContext);

CHttpFile(
    HINTERNET hFile,
    LPCTSTR pstrVerb,
    LPCTSTR pstrObject,
    CHttpConnection* pConnection);
```

### <a name="parameters"></a>參數

*hFile*<br/>
網際網路檔案的控制碼。

*hSession*<br/>
網際網路會話的控制碼。

*pstrObject*<br/>
包含`CHttpFile`物件之字串的指標。

*pstrServer*<br/>
包含伺服器名稱之字串的指標。

*pstrVerb*<br/>
字串的指標, 其中包含要在傳送要求時使用的方法。 可以是 POST、HEAD 或 GET。

*dwContext*<br/>
`CHttpFile`物件的內容識別碼。 如需此參數的詳細資訊, 請參閱**備註**。

*pConnection*<br/>
[CHttpConnection](../../mfc/reference/chttpconnection-class.md)物件的指標。

### <a name="remarks"></a>備註

您永遠不會`CHttpFile`直接建立物件, 而是改為呼叫[CInternetSession:: OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)或[CHttpConnection:: OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest) 。

`dwContext`從建立`CHttpFile` 物件的 [CInternetSession](../../mfc/reference/cinternetsession-class.md) 物件, MFC 會將的預設值傳送給物件。 `CHttpFile` 當您呼叫`CInternetSession::OpenURL`或`CHttpConnection`來建立`CHttpFile`物件時, 您可以覆寫預設值, 將內容識別碼設定為您所選擇的值。 內容識別碼會傳回給[CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) , 以在其識別所在的物件上提供狀態。 請參閱網際網路[的第一篇步驟:WinInet](../../mfc/wininet-basics.md)取得內容識別碼的詳細資訊。

##  <a name="endrequest"></a>CHttpFile:: EndRequest

呼叫這個成員函式, 以結束使用[SendRequestEx](#sendrequestex)成員函式傳送至 HTTP 伺服器的要求。

```
BOOL EndRequest(
    DWORD dwFlags = 0,
    LPINTERNET_BUFFERS lpBuffIn = NULL,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>參數

*dwFlags*<br/>
描述作業的旗標。 如需適當旗標的清單, 請參閱 Windows SDK 中的[HttpEndRequest](/windows/desktop/api/wininet/nf-wininet-httpendrequesta) 。

*lpBuffIn*<br/>
已初始化[INTERNET_BUFFERS](/windows/desktop/api/wininet/ns-wininet-internet_buffersa)的指標, 其描述用於作業的輸入緩衝區。

*dwContext*<br/>
作業的內容識別碼`CHttpFile` 。 如需此參數的詳細資訊, 請參閱備註。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。 如果呼叫失敗, 請檢查擲回的[CInternetException](../../mfc/reference/cinternetexception-class.md)物件來判斷失敗的原因。

### <a name="remarks"></a>備註

*DwCoNtext*的預設值是由 MFC 從建立`CHttpFile` `CHttpFile`物件的[CInternetSession](../../mfc/reference/cinternetsession-class.md)物件傳送至物件。 當您呼叫[CInternetSession:: OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)或[CHttpConnection](../../mfc/reference/chttpconnection-class.md) `CHttpFile`來建立物件時, 您可以覆寫預設值, 將內容識別碼設定為您所選擇的值。 內容識別碼會傳回給[CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) , 以在其識別所在的物件上提供狀態。 請參閱[網際網路的第一個步驟:WinInet](../../mfc/wininet-basics.md)取得內容識別碼的詳細資訊。

##  <a name="getfileurl"></a>CHttpFile:: GetFileURL

呼叫這個成員函式以取得 HTTP 檔案的名稱做為 URL。

```
virtual CString GetFileURL() const;
```

### <a name="return-value"></a>傳回值

[CString](../../atl-mfc-shared/reference/cstringt-class.md)物件, 其中包含參考與此檔案相關聯之資源的 URL。

### <a name="remarks"></a>備註

只有在成功呼叫[SendRequest](#sendrequest)或`CHttpFile` [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)成功建立的物件之後, 才使用此成員函式。

##  <a name="getobject"></a>  CHttpFile::GetObject

呼叫這個成員函式, 取得與這個`CHttpFile`相關聯之物件的名稱。

```
CString GetObject() const;
```

### <a name="return-value"></a>傳回值

[CString](../../atl-mfc-shared/reference/cstringt-class.md)物件, 其中包含物件的名稱。

### <a name="remarks"></a>備註

只有在成功呼叫[SendRequest](#sendrequest)或`CHttpFile` [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)成功建立的物件之後, 才使用此成員函式。

##  <a name="getverb"></a>  CHttpFile::GetVerb

呼叫這個成員函式, 取得與這個`CHttpFile`相關聯的 HTTP 動詞命令 (或方法)。

```
CString GetVerb() const;
```

### <a name="return-value"></a>傳回值

[CString](../../atl-mfc-shared/reference/cstringt-class.md)物件, 其中包含 HTTP 動詞命令 (或方法) 的名稱。

### <a name="remarks"></a>備註

只有在成功呼叫[SendRequest](#sendrequest)或`CHttpFile` [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)成功建立的物件之後, 才使用此成員函式。

##  <a name="queryinfo"></a>CHttpFile:: QueryInfo

呼叫這個成員函式, 以從 HTTP 要求傳迴響應或要求標頭。

```
BOOL QueryInfo(
    DWORD dwInfoLevel,
    LPVOID lpvBuffer,
    LPDWORD lpdwBufferLength,
    LPDWORD lpdwIndex = NULL) const;

BOOL QueryInfo(
    DWORD dwInfoLevel,
    CString& str,
    LPDWORD dwIndex = NULL) const;

BOOL QueryInfo(
    DWORD dwInfoLevel,
    SYSTEMTIME* pSysTime,
    LPDWORD dwIndex = NULL) const;
```

### <a name="parameters"></a>參數

*dwInfoLevel*<br/>
要查詢的屬性和下列旗標的組合, 可指定所要求的資訊類型:

- HTTP_QUERY_CUSTOM 會尋找標頭名稱, 並在輸出的*lpvBuffer*中傳回此值。 如果找不到標頭, 則 HTTP_QUERY_CUSTOM 會擲回判斷提示。

- 通常, 應用程式會查詢回應標頭, 但應用程式也可以使用此旗標來查詢要求標頭。

- HTTP_QUERY_FLAG_SYSTEMTIME, 其值為日期/時間字串的標頭 (例如「上次修改時間」), 此旗標會以不需要應用程式剖析資料的標準 Win32 [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)結構傳回標頭值。 如果您使用這個旗標, 您可能會想要`SYSTEMTIME`使用函式的覆寫。

- HTTP_QUERY_FLAG_NUMBER, 其值為數字的標頭 (例如狀態碼), 此旗標會將資料傳回為32位數位。

如需可能值的清單, 請參閱**備註**一節。

*lpvBuffer*<br/>
接收資訊之緩衝區的指標。

*lpdwBufferLength*<br/>
在輸入時, 這會指向包含資料緩衝區長度的值 (以字元或位元組數為單位)。 如需此參數的詳細資訊, 請參閱**備註**一節。

*lpdwIndex*<br/>
以零為基底之標頭索引的指標。 可以是 Null。 使用此旗標來列舉多個具有相同名稱的標頭。 在輸入時, *lpdwIndex*表示要傳回之指定標頭的索引。 在輸出時, *lpdwIndex*表示下一個標頭的索引。 如果找不到下一個索引, 則會傳回 ERROR_HTTP_HEADER_NOT_FOUND。

*str*<br/>
會接收傳回信息之[CString](../../atl-mfc-shared/reference/cstringt-class.md)物件的參考。

*dwIndex*<br/>
索引值。 請參閱*lpdwIndex*。

*pSysTime*<br/>
Win32 [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)結構的指標。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。 如果呼叫失敗, 則可以呼叫 Win32 函數[GetLastError](/windows/desktop/api/errhandlingapi/nf-errhandlingapi-getlasterror)來判斷錯誤的原因。

### <a name="remarks"></a>備註

只有在成功呼叫[SendRequest](#sendrequest)或`CHttpFile` [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)成功建立的物件之後, 才使用此成員函式。

您可以從`QueryInfo`取得下列類型的資料:

- 字串 (預設值)

- `SYSTEMTIME`(針對「資料:」「過期」: "etc, 標頭)

- DWORD (適用于 STATUS_CODE、CONTENT_LENGTH 等)

將字串寫入緩衝區, 且成員函式成功時, 會包含結束`lpdwBufferLength` Null 字元的字串長度 (以字元為單位)。

可能的*dwInfoLevel*值包括:

- HTTP_QUERY_MIME_VERSION

- HTTP_QUERY_CONTENT_TYPE

- HTTP_QUERY_CONTENT_TRANSFER_ENCODING

- HTTP_QUERY_CONTENT_ID

- HTTP_QUERY_CONTENT_DESCRIPTION

- HTTP_QUERY_CONTENT_LENGTH

- HTTP_QUERY_ALLOWED_METHODS

- HTTP_QUERY_PUBLIC_METHODS

- HTTP_QUERY_DATE

- HTTP_QUERY_EXPIRES

- HTTP_QUERY_LAST_MODIFIED

- HTTP_QUERY_MESSAGE_ID

- HTTP_QUERY_URI

- HTTP_QUERY_DERIVED_FROM

- HTTP_QUERY_LANGUAGE

- HTTP_QUERY_COST

- HTTP_QUERY_WWW_LINK

- HTTP_QUERY_PRAGMA

- HTTP_QUERY_VERSION

- HTTP_QUERY_STATUS_CODE

- HTTP_QUERY_STATUS_TEXT

- HTTP_QUERY_RAW_HEADERS

- HTTP_QUERY_RAW_HEADERS_CRLF

##  <a name="queryinfostatuscode"></a>CHttpFile:: QueryInfoStatusCode

呼叫這個成員函式以取得與 HTTP 要求相關聯的狀態碼, 並將它放在提供的*dwStatusCode*參數中。

```
BOOL QueryInfoStatusCode(DWORD& dwStatusCode) const;
```

### <a name="parameters"></a>參數

*dwStatusCode*<br/>
狀態碼的參考。 狀態碼表示要求的事件成功或失敗。 如需狀態碼描述的選項, 請參閱**備註**。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。 如果呼叫失敗, 則可以呼叫 Win32 函數[GetLastError](/windows/desktop/api/errhandlingapi/nf-errhandlingapi-getlasterror)來判斷錯誤的原因。

### <a name="remarks"></a>備註

只有在成功呼叫[SendRequest](#sendrequest)或`CHttpFile` [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)成功建立的物件之後, 才使用此成員函式。

HTTP 狀態碼會分成一個群組, 指出要求成功或失敗。 下表概述狀態碼群組和最常見的 HTTP 狀態碼。

|群組|意義|
|-----------|-------------|
|200-299|Success|
|300-399|資訊|
|400-499|要求錯誤|
|500-599|伺服器錯誤|

一般 HTTP 狀態碼:

|status code|意義|
|-----------------|-------------|
|200|找到 URL，接著進行傳輸|
|400|難以理解的要求|
|404|找不到要求的 URL|
|405|伺服器不支援所要求的方法|
|500|未知的伺服器錯誤|
|503|已達到伺服器容量|

##  <a name="sendrequest"></a>  CHttpFile::SendRequest

呼叫這個成員函式, 將要求傳送至 HTTP 伺服器。

```
BOOL SendRequest(
    LPCTSTR pstrHeaders = NULL,
    DWORD dwHeadersLen = 0,
    LPVOID lpOptional = NULL,
    DWORD dwOptionalLen = 0);

BOOL SendRequest(
    CString& strHeaders,
    LPVOID lpOptional = NULL,
    DWORD dwOptionalLen = 0);
```

### <a name="parameters"></a>參數

*pstrHeaders*<br/>
包含要傳送之標頭名稱的字串指標。

*dwHeadersLen*<br/>
*PstrHeaders*所識別的標頭長度。

*lpOptional*<br/>
要在要求標頭之後立即傳送的任何選擇性資料。 這通常用於 POST 和 PUT 作業。 如果沒有要傳送的選擇性資料, 這可能會是 Null。

*dwOptionalLen*<br/>
*LpOptional*的長度。

*strHeaders*<br/>
字串, 其中包含所傳送之要求的標頭名稱。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。 如果呼叫失敗, 請檢查擲回的[CInternetException](../../mfc/reference/cinternetexception-class.md)物件來判斷失敗的原因。

##  <a name="sendrequestex"></a>CHttpFile:: SendRequestEx

呼叫這個成員函式, 將要求傳送至 HTTP 伺服器。

```
BOOL SendRequestEx(
    DWORD dwTotalLen,
    DWORD dwFlags = HSR_INITIATE,
    DWORD_PTR dwContext = 1);

BOOL SendRequestEx(
    LPINTERNET_BUFFERS lpBuffIn,
    LPINTERNET_BUFFERS lpBuffOut,
    DWORD dwFlags = HSR_INITIATE,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>參數

*dwTotalLen*<br/>
要在要求中傳送的位元組數目。

*dwFlags*<br/>
描述作業的旗標。 如需適當旗標的清單, 請參閱 Windows SDK 中的[HttpSendRequestEx](/windows/desktop/api/wininet/nf-wininet-httpsendrequestexa) 。

*dwContext*<br/>
作業的內容識別碼`CHttpFile` 。 如需此參數的詳細資訊, 請參閱備註。

*lpBuffIn*<br/>
已初始化[INTERNET_BUFFERS](/windows/desktop/api/wininet/ns-wininet-internet_buffersa)的指標, 其描述用於作業的輸入緩衝區。

*lpBuffOut*<br/>
已初始化 INTERNET_BUFFERS 的指標, 其描述用於作業的輸出緩衝區。

### <a name="return-value"></a>傳回值

如果成功, 則為非零值。 如果呼叫失敗, 請檢查擲回的[CInternetException](../../mfc/reference/cinternetexception-class.md)物件來判斷失敗的原因。

### <a name="remarks"></a>備註

此函式可讓您的應用程式使用的[Write](../../mfc/reference/cinternetfile-class.md#write)和[WriteString](../../mfc/reference/cinternetfile-class.md#writestring)方法`CInternetFile`來傳送資料。 呼叫此函式的任一個覆寫之前, 您必須知道要傳送的資料長度。 第一個覆寫可讓您指定您想要傳送的資料長度。 第二個覆寫接受 INTERNET_BUFFERS 結構的指標, 可用來以絕佳的詳細描述緩衝區。

將內容寫入檔案之後, 請呼叫[EndRequest](#endrequest)以結束作業。

*DwCoNtext*的預設值是由 MFC 從建立`CHttpFile` `CHttpFile`物件的[CInternetSession](../../mfc/reference/cinternetsession-class.md)物件傳送至物件。 當您呼叫[CInternetSession:: OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)或[CHttpConnection](../../mfc/reference/chttpconnection-class.md) `CHttpFile`來建立物件時, 您可以覆寫預設值, 將內容識別碼設定為您所選擇的值。 內容識別碼會傳回給[CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) , 以在其識別所在的物件上提供狀態。 請參閱網際網路[的第一篇步驟:WinInet](../../mfc/wininet-basics.md)取得內容識別碼的詳細資訊。

### <a name="example"></a>範例

此程式碼片段會將字串的內容傳送至名為 MFCISAPI 的 DLL。LOCALHOST 伺服器上的 DLL。 雖然此範例只使用一個呼叫`WriteString`, 但使用多個呼叫來傳送區塊中的資料是可接受的。

[!code-cpp[NVC_MFCWinInet#9](../../mfc/codesnippet/cpp/chttpfile-class_1.cpp)]

## <a name="see-also"></a>另請參閱

[CInternetFile 類別](../../mfc/reference/cinternetfile-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CInternetFile 類別](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherFile 類別](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttpConnection 類別](../../mfc/reference/chttpconnection-class.md)
