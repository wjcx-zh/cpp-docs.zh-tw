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
ms.openlocfilehash: cba3ba7d86577703de2bf5709d66bbd5e0298863
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368397"
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
|[CHttpFile:CHttpFile](#chttpfile)|建立 `CHttpFile` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CHttpFile::新增請求標題](#addrequestheaders)|將標頭添加到發送到 HTTP 伺服器的請求。|
|[CHttpFile:結束請求](#endrequest)|使用[SendRequestEx](#sendrequestex)成員功能結束發送到 HTTP 伺服器的請求。|
|[CHttpFile:取得檔案網址](#getfileurl)|取得指定檔案的 URL。|
|[CHttpFile:抓取物件](#getobject)|獲取對 HTTP 伺服器的請求中謂詞的目標物件。|
|[CHttpFile:GetVerb](#getverb)|獲取在請求到 HTTP 伺服器時使用的謂詞。|
|[CHttpFile:查詢資訊](#queryinfo)|從 HTTP 伺服器返回回應或請求標頭。|
|[CHTTP檔::查詢資訊狀態代碼](#queryinfostatuscode)|檢索與 HTTP 請求關聯的狀態代碼,並將其置`dwStatusCode`於提供的 參數中。|
|[CHttpFile:傳送要求](#sendrequest)|向 HTTP 伺服器發送請求。|
|[CHttpFile::傳送請求Ex](#sendrequestex)|使用 的[寫入](../../mfc/reference/cinternetfile-class.md#write)或[寫入字串](../../mfc/reference/cinternetfile-class.md#writestring)方法傳`CInternetFile`送 HTTP 伺服器送出要求 。|

## <a name="remarks"></a>備註

如果 Internet 工作階段從 HTTP 伺服器讀取數據,`CHttpFile`則必須創建的實例。

要瞭解有關如何`CHttpFile`與其他 MFC Internet 類合作,請參閱[WinInet](../../mfc/win32-internet-extensions-wininet.md)的 Internet 程式設計文章。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[CStdioFile](../../mfc/reference/cstdiofile-class.md)

[CInternetFile](../../mfc/reference/cinternetfile-class.md)

`CHttpFile`

## <a name="requirements"></a>需求

**標題:** afxinet.h

## <a name="chttpfileaddrequestheaders"></a><a name="addrequestheaders"></a>CHttpFile::新增請求標題

呼叫此成員函數以向 HTTP 請求句柄添加一個或多個 HTTP 請求標頭。

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
指向包含標頭或標頭的字串的指標,用於追加請求。 每個標頭必須由CR/LF 對終止。

*dwFlags*<br/>
修改新標頭的語義。 可以是下列其中一項：

- HTTP_ADDREQ_FLAG_COALESCE合併同名的標頭,使用標誌將找到的第一個標頭添加到後續標頭。 例如,"接受:文本\*/"後跟"接受:音訊/"\*導致形成單個標題"接受:文本\*/, 音訊\*/"。 調用應用程式由確保與使用合併或單獨標頭髮送的請求接收的數據進行統一方案。

- HTTP_ADDREQ_FLAG_REPLACE 執行刪除並添加以替換當前標頭。 標頭名稱將用於刪除當前標頭,並且完整值將用於添加新標頭。 如果標頭值為空並且找到標頭,則刪除它。 如果未為空,則替換標頭值。

- HTTP_ADDREQ_FLAG_ADD_IF_NEW僅添加標頭(如果標頭不存在)。 如果存在,則返回錯誤。

- HTTP_ADDREQ_FLAG_ADD與 REPLACE 一起使用。 如果標頭不存在,請添加它。

*德海德倫*<br/>
*pstrHeader 的長度*(以字元表示)。 如果為 -1L,則假定*pstrHeader*為零端接,並計算長度。

*Str*<br/>
對包含要添加的請求標頭或標頭的[CString](../../atl-mfc-shared/reference/cstringt-class.md)物件的引用。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。 如果調用失敗,可能會調用 Win32 函數[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)以確定錯誤的原因。

### <a name="remarks"></a>備註

`AddRequestHeaders`將其他自由格式標頭追加到 HTTP 請求句柄。 它供需要詳細控制發送到 HTTP 伺服器的確切請求的先進用戶端使用。

> [!NOTE]
> 應用程式可以使用HTTP_ADDREQ_FLAG_ADD或HTTP_ADDREQ_FLAG_ADD_IF_NEW在*pstrHeader 或* *str*`AddRequestHeaders`中傳遞多個標頭。 如果應用程式嘗試使用HTTP_ADDREQ_FLAG_REMOVE或HTTP_ADDREQ_FLAG_REPLACE刪除或替換標頭,則*lpszHeader*中只能提供一個標頭。

## <a name="chttpfilechttpfile"></a><a name="chttpfile"></a>CHttpFile:CHttpFile

呼叫此成員函數以建構物件`CHttpFile`。

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
互聯網檔的句柄。

*h 工作階段*<br/>
互聯網會話的句柄。

*pstrObject*<br/>
指向包含物件的字串的`CHttpFile`指標。

*pstrServer*<br/>
指向包含伺服器名稱的字串的指標。

*普斯特維爾布*<br/>
指向包含發送請求時要使用的方法的字串的指標。 可以是 POST、頭或 GET。

*dwContext*<br/>
`CHttpFile`物件的上下文標識碼。 有關此參數的詳細資訊,請參閱**備註**。

*pConnection*<br/>
指向[CHTTPConnect](../../mfc/reference/chttpconnection-class.md)物件的指標。

### <a name="remarks"></a>備註

您從不直接構造`CHttpFile`物件;而是呼叫[CInternetSession::開啟 URL](../../mfc/reference/cinternetsession-class.md#openurl)或[CHTTPConnect:開啟請求](../../mfc/reference/chttpconnection-class.md#openrequest)。

MFC`dwContext`的 預設值由`CHttpFile`MFC 從創建`CHttpFile`物件的[CInternetSession](../../mfc/reference/cinternetsession-class.md)物件發送到物件。 呼叫`CInternetSession::OpenURL``CHttpConnection`或 建構`CHttpFile`物件時 ,可以重寫預設值,將上下文識別符設定為您選擇的值。 上下文標識符返回到[CInternetSession::onStatusBackononononononback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)提供標識它的物件的狀態。 有關上下文標識符的詳細資訊[,請參閱"Internet 第一步:WinInet"](../../mfc/wininet-basics.md)一文。

## <a name="chttpfileendrequest"></a><a name="endrequest"></a>CHttpFile:結束請求

呼叫此成員函數以結束使用[SendRequestEx](#sendrequestex)成員函數發送到 HTTP 伺服器的請求。

```
BOOL EndRequest(
    DWORD dwFlags = 0,
    LPINTERNET_BUFFERS lpBuffIn = NULL,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>參數

*dwFlags*<br/>
描述操作的標誌。 有關相應標誌的清單,請參閱 Windows SDK 中的[HttpEndRequest。](/windows/win32/api/wininet/nf-wininet-httpendrequestw)

*lpBuffin*<br/>
指向初始[化INTERNET_BUFFERS,](/windows/win32/api/wininet/ns-wininet-internet_buffersw)用於描述用於操作的輸入緩衝區。

*dwContext*<br/>
操作的`CHttpFile`上下文標識碼。 有關此參數的詳細資訊,請參閱備註。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。 如果調用失敗,請通過檢查引發的[CInternetException](../../mfc/reference/cinternetexception-class.md)物件來確定失敗的原因。

### <a name="remarks"></a>備註

mFC`CHttpFile`從 創建物件的[CInternetSession](../../mfc/reference/cinternetsession-class.md)`CHttpFile`物件向物件發送*dwContext*的預設值。 當您調用[CInternetSession::OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)或[CHTTPConnect](../../mfc/reference/chttpconnection-class.md)`CHttpFile`構造物件時,可以重寫預設值,將上下文標識符設定為您選擇的值。 上下文標識符返回到[CInternetSession::onStatusBackononononononback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)提供標識它的物件的狀態。 有關上下文標識符的詳細資訊[,請參閱文章"Internet 第一步:WinInet"。](../../mfc/wininet-basics.md)

## <a name="chttpfilegetfileurl"></a><a name="getfileurl"></a>CHttpFile:取得檔案網址

呼叫此成員函數以獲取 HTTP 檔的名稱作為網址。

```
virtual CString GetFileURL() const;
```

### <a name="return-value"></a>傳回值

包含參考與此檔關聯的資源的網址的[CString](../../atl-mfc-shared/reference/cstringt-class.md)物件。

### <a name="remarks"></a>備註

僅當成功呼叫[SendRequest](#sendrequest)或`CHttpFile`[OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)成功建立的物件上時,才使用此成員函數。

## <a name="chttpfilegetobject"></a><a name="getobject"></a>CHttpFile:抓取物件

呼叫此成員函式以取得與此關聯的物件`CHttpFile`名稱 。

```
CString GetObject() const;
```

### <a name="return-value"></a>傳回值

包含物件名稱的[CString](../../atl-mfc-shared/reference/cstringt-class.md)物件。

### <a name="remarks"></a>備註

僅當成功呼叫[SendRequest](#sendrequest)或`CHttpFile`[OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)成功建立的物件上時,才使用此成員函數。

## <a name="chttpfilegetverb"></a><a name="getverb"></a>CHttpFile:GetVerb

呼叫此成員函數以取得與此關聯的 HTTP 謂詞(`CHttpFile`或方法 )。

```
CString GetVerb() const;
```

### <a name="return-value"></a>傳回值

包含 HTTP 謂詞(或方法)名稱的[CString](../../atl-mfc-shared/reference/cstringt-class.md)物件。

### <a name="remarks"></a>備註

僅當成功呼叫[SendRequest](#sendrequest)或`CHttpFile`[OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)成功建立的物件上時,才使用此成員函數。

## <a name="chttpfilequeryinfo"></a><a name="queryinfo"></a>CHttpFile:查詢資訊

調用此成員函數以從 HTTP 請求傳回回應或請求標頭。

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
要查詢的屬性與指定要求的資訊型態的以下旗標的組合:

- HTTP_QUERY_CUSTOM 查找標頭名稱並在輸出時在*lpvBuffer*中傳回此值。 如果未找到標頭,HTTP_QUERY_CUSTOM引發斷言。

- HTTP_QUERY_FLAG_REQUEST_HEADERS通常,應用程式查詢響應標頭,但應用程式也可以使用此標誌查詢請求標頭。

- HTTP_QUERY_FLAG_SYSTEMTIME對於值為日期/時間字串(如"上次修改時間")的標頭,此標誌將標頭值作為標準 Win32 [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)結構返回,該結構不需要應用程式來分析數據。 如果使用此標誌,則可能需要使用函數的`SYSTEMTIME`重寫。

- HTTP_QUERY_FLAG_NUMBER 對於值為數字的標頭(如狀態代碼),此標誌將數據作為 32 位元數位返回。

有關可能值的清單,請參閱**備註**部分。

*lpvBuffer*<br/>
指向接收資訊的緩衝區的指標。

*lpdwBuffer 長度*<br/>
在輸入時,這將指向包含數據緩衝區長度(以字元數或位元組數)的值。 有關此參數的詳細資訊,請參閱**備註**部分。

*lpdwIndex*<br/>
指向零基標頭索引的指標。 可以是 NULL。 使用此標誌可以枚舉具有相同名稱的多個標頭。 在輸入時 *,lpdwIndex*指示要返回的指定標頭的索引。 在輸出時 *,lpdwIndex*指示下一個標頭的索引。 如果找不到下一個索引,則返回ERROR_HTTP_HEADER_NOT_FOUND。

*Str*<br/>
對接收返回資訊的[CString](../../atl-mfc-shared/reference/cstringt-class.md)物件的引用。

*dwIndex*<br/>
索引值。 請參考*lpdwIndex*。

*pSysTime*<br/>
指向 Win32[系統時間結構的](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)指標。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。 如果調用失敗,可能會調用 Win32 函數[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)以確定錯誤的原因。

### <a name="remarks"></a>備註

僅當成功呼叫[SendRequest](#sendrequest)或`CHttpFile`[OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)成功建立的物件上時,才使用此成員函數。

可以從中擷取以下型態`QueryInfo`的資料 :

- 字串(預設)

- `SYSTEMTIME`(對於"數據":"過期"等,標題)

- DWORD(用於STATUS_CODE、CONTENT_LENGTH等)

當字串寫入緩衝區並且成員函數成功時,`lpdwBufferLength`字串的長度為字元減去 1 表示終止 NULL 字元。

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

## <a name="chttpfilequeryinfostatuscode"></a><a name="queryinfostatuscode"></a>CHTTP檔::查詢資訊狀態代碼

調用此成員函數獲取與 HTTP 請求關聯的狀態代碼,並將其放置在提供的*dwStatusCode*參數中。

```
BOOL QueryInfoStatusCode(DWORD& dwStatusCode) const;
```

### <a name="parameters"></a>參數

*dwStatusCode*<br/>
對狀態代碼的引用。 狀態代碼指示請求事件的成功或失敗。 關於狀態碼標題的選擇,請參閱**備註**。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。 如果調用失敗,可能會調用 Win32 函數[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)以確定錯誤的原因。

### <a name="remarks"></a>備註

僅當成功呼叫[SendRequest](#sendrequest)或`CHttpFile`[OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)成功建立的物件上時,才使用此成員函數。

HTTP 狀態代碼分為指示請求成功或失敗的組。 下表概述了狀態代碼組和最常見的 HTTP 狀態代碼。

|群組|意義|
|-----------|-------------|
|200-299|Success|
|300-399|資訊|
|400-499|要求錯誤|
|500-599|伺服器錯誤|

常見 HTTP 狀態代碼:

|狀態碼|意義|
|-----------------|-------------|
|200|找到 URL，接著進行傳輸|
|400|難以理解的要求|
|404|找不到要求的 URL|
|405|伺服器不支援所要求的方法|
|500|未知的伺服器錯誤|
|503|已達到伺服器容量|

## <a name="chttpfilesendrequest"></a><a name="sendrequest"></a>CHttpFile:傳送要求

呼叫此成員函數以向 HTTP 伺服器發送請求。

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
指向包含要發送的標頭名稱的字串的指標。

*德海德倫*<br/>
由*pstrHeader*標識的標頭的長度。

*lp 選擇*<br/>
在請求標頭之後立即發送的任何可選數據。 這通常用於 POST 和 PUT 操作。 如果沒有要發送的可選數據,則這可以為 NULL。

*德沃納倫*<br/>
*lp 可選*的長度。

*串標題*<br/>
包含要傳送的請求的標頭名稱的字串。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。 如果調用失敗,請通過檢查引發的[CInternetException](../../mfc/reference/cinternetexception-class.md)物件來確定失敗的原因。

## <a name="chttpfilesendrequestex"></a><a name="sendrequestex"></a>CHttpFile::傳送請求Ex

呼叫此成員函數以向 HTTP 伺服器發送請求。

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

*德·道倫*<br/>
要在請求中發送的位元組數。

*dwFlags*<br/>
描述操作的標誌。 有關適當的標誌清單,請參閱 Windows SDK 中的[HSendRequestEx。](/windows/win32/api/wininet/nf-wininet-httpsendrequestexw)

*dwContext*<br/>
操作的`CHttpFile`上下文標識碼。 有關此參數的詳細資訊,請參閱備註。

*lpBuffin*<br/>
指向初始[化INTERNET_BUFFERS,](/windows/win32/api/wininet/ns-wininet-internet_buffersw)用於描述用於操作的輸入緩衝區。

*lpBuffOut*<br/>
指向初始化INTERNET_BUFFERS的指標,該INTERNET_BUFFERS描述用於操作的輸出緩衝區。

### <a name="return-value"></a>傳回值

如果成功,則為非零。 如果調用失敗,請通過檢查引發的[CInternetException](../../mfc/reference/cinternetexception-class.md)物件來確定失敗的原因。

### <a name="remarks"></a>備註

此函數允許應用程式使用`CInternetFile`的[寫入](../../mfc/reference/cinternetfile-class.md#write)和[寫入String](../../mfc/reference/cinternetfile-class.md#writestring)方法發送數據。 在調用此函數的任一重寫之前,必須知道要發送的數據的長度。 第一個覆蓋允許您指定要發送的數據長度。 第二個重寫接受指向INTERNET_BUFFERS結構的指標,這些結構可用於詳細描述緩衝區。

將內容寫入檔後,呼叫[EndRequest](#endrequest)以結束操作。

mFC`CHttpFile`從 創建物件的[CInternetSession](../../mfc/reference/cinternetsession-class.md)`CHttpFile`物件向物件發送*dwContext*的預設值。 當您調用[CInternetSession::OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)或[CHTTPConnect](../../mfc/reference/chttpconnection-class.md)`CHttpFile`構造物件時,可以重寫預設值,將上下文標識符設定為您選擇的值。 上下文標識符返回到[CInternetSession::onStatusBackononononononback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)提供標識它的物件的狀態。 有關上下文標識符的詳細資訊[,請參閱"Internet 第一步:WinInet"](../../mfc/wininet-basics.md)一文。

### <a name="example"></a>範例

此程式片段將字串的內容發送到名為 MFCISAPI 的 DLL。本地主機上的 DLL。 此示例僅對 使用`WriteString`一個調用,使用多個調用以塊發送數據是可以接受的。

[!code-cpp[NVC_MFCWinInet#9](../../mfc/codesnippet/cpp/chttpfile-class_1.cpp)]

## <a name="see-also"></a>另請參閱

[C 網際網路檔案類別](../../mfc/reference/cinternetfile-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[C 網際網路檔案類別](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherFile 類別](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttpConnection 類別](../../mfc/reference/chttpconnection-class.md)
