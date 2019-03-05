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
ms.openlocfilehash: 3c701f933d622adc5f3d8b1eb2371406e5b45e6f
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57283731"
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
|[CHttpFile::CHttpFile](#chttpfile)|建立 `CHttpFile` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CHttpFile::AddRequestHeaders](#addrequestheaders)|將傳送至 HTTP 伺服器的要求標頭。|
|[CHttpFile::EndRequest](#endrequest)|結束要求，傳送至 HTTP 伺服器[SendRequestEx](#sendrequestex)成員函式。|
|[CHttpFile::GetFileURL](#getfileurl)|取得指定的檔案的 URL。|
|[CHttpFile::GetObject](#getobject)|取得動詞命令的目標物件在要求中，HTTP 伺服器。|
|[CHttpFile::GetVerb](#getverb)|取得 HTTP 伺服器要求所使用的動詞命令。|
|[CHttpFile::QueryInfo](#queryinfo)|從 HTTP 伺服器傳回的回應或要求標頭。|
|[CHttpFile::QueryInfoStatusCode](#queryinfostatuscode)|擷取 HTTP 要求相關聯的狀態碼，並將它放在提供`dwStatusCode`參數。|
|[CHttpFile::SendRequest](#sendrequest)|將要求傳送至 HTTP 伺服器。|
|[CHttpFile::SendRequestEx](#sendrequestex)|將要求傳送至 HTTP 伺服器使用[撰寫](../../mfc/reference/cinternetfile-class.md#write)或是[WriteString](../../mfc/reference/cinternetfile-class.md#writestring)方法`CInternetFile`。|

## <a name="remarks"></a>備註

如果您的網際網路工作階段會讀取 HTTP 伺服器中的資料，您必須建立的執行個體`CHttpFile`。

若要進一步了解如何`CHttpFile`運作方式與其他 MFC 網際網路類別，請參閱文章[網際網路程式設計 WinInet](../../mfc/win32-internet-extensions-wininet.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[CStdioFile](../../mfc/reference/cstdiofile-class.md)

[CInternetFile](../../mfc/reference/cinternetfile-class.md)

`CHttpFile`

## <a name="requirements"></a>需求

**標頭：** afxinet.h

##  <a name="addrequestheaders"></a>  CHttpFile::AddRequestHeaders

呼叫此成員函式，將一或多個 HTTP 要求的 HTTP 要求標頭處理。

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
包含標頭或要附加至要求的標頭的字串指標。 每個標頭必須結束 CR/LF 組。

*dwFlags*<br/>
修改新的標頭的語意。 可以是下列其中一項：

- 相同的名稱，並使用旗標新增至後續的標頭中找到的第一個標頭的 HTTP_ADDREQ_FLAG_COALESCE 合併的標頭。 比方說，「 接受： 文字 /\*"後面接著"接受： 音訊 /\*"的單一標頭會導致"接受： 文字 /\*、 音訊 /\*"。 這是由呼叫的應用程式，以確保一致的結構描述方面與聯合或個別的標頭一起傳送的要求所接收的資料。

- HTTP_ADDREQ_FLAG_REPLACE 執行移除，並將取代目前的標頭。 標頭名稱會用來移除目前的標頭，以及完整的值將用來新增新的標頭。 如果標頭值是空的且找到標頭，則會將它移除。 如果不是空的標頭值會取代。

- 如果不存在，只 HTTP_ADDREQ_FLAG_ADD_IF_NEW 加入標頭。 如果有的話，則會傳回錯誤。

- HTTP_ADDREQ_FLAG_ADD 與取代搭配使用。 如果不存在，請加入標頭。

*dwHeadersLen*<br/>
長度，以字元為單位的*pstrHeaders*。 如果這是則為-1l *pstrHeaders*假設為零結束，而且長度會計算。

*str*<br/>
參考[CString](../../atl-mfc-shared/reference/cstringt-class.md)物件，其中包含要加入的標頭的要求標頭。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。 如果呼叫失敗，Win32 函式[GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360)可能會呼叫以判斷錯誤的原因。

### <a name="remarks"></a>備註

`AddRequestHeaders` 將其他的自由格式的標頭附加至 HTTP 要求控制代碼。 它被適用於複雜的用戶端需要細微地控制傳送至 HTTP 伺服器的實際要求。

> [!NOTE]
>  應用程式可以將多個標頭中的傳遞*pstrHeaders*或是*str*如`AddRequestHeaders`使用 HTTP_ADDREQ_FLAG_ADD 或 HTTP_ADDREQ_FLAG_ADD_IF_NEW 呼叫。 如果應用程式會嘗試移除或取代使用 HTTP_ADDREQ_FLAG_REMOVE 或 HTTP_ADDREQ_FLAG_REPLACE 標頭，只有一個標頭可以提供*lpszHeaders*。

##  <a name="chttpfile"></a>  CHttpFile::CHttpFile

此成員函式呼叫來建構`CHttpFile`物件。

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
網際網路檔案控制代碼。

*hSession*<br/>
網際網路工作階段控制代碼。

*pstrObject*<br/>
字串，包含一個指向`CHttpFile`物件。

*pstrServer*<br/>
包含伺服器名稱的字串指標。

*pstrVerb*<br/>
指向的字串，包含要傳送要求時使用的方法。 可以 POST、 HEAD 或 GET。

*dwContext*<br/>
內容識別碼`CHttpFile`物件。 請參閱**備註**如需有關此參數。

*pConnection*<br/>
指標[CHttpConnection](../../mfc/reference/chttpconnection-class.md)物件。

### <a name="remarks"></a>備註

您永遠不會建構`CHttpFile`直接物件; 而是呼叫[cinternetsession:: Openurl](../../mfc/reference/cinternetsession-class.md#openurl)或是[chttpconnection::](../../mfc/reference/chttpconnection-class.md#openrequest)改。

預設值`dwContext`傳送至 mfc`CHttpFile`物件[CInternetSession](../../mfc/reference/cinternetsession-class.md)物件建立`CHttpFile`物件。 當您呼叫`CInternetSession::OpenURL`或是`CHttpConnection`建構`CHttpFile`物件時，您可以覆寫預設值可設定的內容識別碼以您選擇的值。 內容識別碼會傳回到[CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)來提供，它識別之物件的狀態。 請參閱文章[網際網路前幾個步驟：WinInet](../../mfc/wininet-basics.md)取得的內容識別碼的詳細資訊。

##  <a name="endrequest"></a>  CHttpFile::EndRequest

呼叫來結束要求，傳送至 HTTP 伺服器與此成員函式[SendRequestEx](#sendrequestex)成員函式。

```
BOOL EndRequest(
    DWORD dwFlags = 0,
    LPINTERNET_BUFFERS lpBuffIn = NULL,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>參數

*dwFlags*<br/>
描述作業的旗標。 如需適當的旗標的清單，請參閱 < [HttpEndRequest](/windows/desktop/api/wininet/nf-wininet-httpendrequesta) Windows SDK 中。

*lpBuffIn*<br/>
初始化的指標[INTERNET_BUFFERS](/windows/desktop/api/wininet/ns-wininet-_internet_buffersa)描述用於作業的輸入的緩衝區。

*dwContext*<br/>
內容識別碼`CHttpFile`作業。 如需這個參數的詳細資訊，請參閱 < 備註 >。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。 如果呼叫失敗，判斷失敗的原因，藉由檢查擲回[CInternetException](../../mfc/reference/cinternetexception-class.md)物件。

### <a name="remarks"></a>備註

預設值*dwContext* MFC，以便傳送`CHttpFile`物件[CInternetSession](../../mfc/reference/cinternetsession-class.md)物件建立`CHttpFile`物件。 當您呼叫[cinternetsession:: Openurl](../../mfc/reference/cinternetsession-class.md#openurl)或是[CHttpConnection](../../mfc/reference/chttpconnection-class.md)建構`CHttpFile`物件時，您可以覆寫預設值可設定的內容識別碼以您選擇的值。 內容識別碼會傳回到[CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)來提供，它識別之物件的狀態。 請參閱文件[網際網路前幾個步驟：WinInet](../../mfc/wininet-basics.md)取得的內容識別碼的詳細資訊。

##  <a name="getfileurl"></a>  CHttpFile::GetFileURL

呼叫此成員函式，以取得做為 URL 的 HTTP 檔案的名稱。

```
virtual CString GetFileURL() const;
```

### <a name="return-value"></a>傳回值

A [CString](../../atl-mfc-shared/reference/cstringt-class.md)物件，包含 URL 以參考與此檔案相關聯的資源。

### <a name="remarks"></a>備註

使用此成員函式只有在成功呼叫之後[SendRequest](#sendrequest)或在`CHttpFile`已成功建立的物件[OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)。

##  <a name="getobject"></a>  CHttpFile::GetObject

呼叫此成員函式，以取得與此相關聯的物件名稱`CHttpFile`。

```
CString GetObject() const;
```

### <a name="return-value"></a>傳回值

A [CString](../../atl-mfc-shared/reference/cstringt-class.md)物件，包含物件的名稱。

### <a name="remarks"></a>備註

使用此成員函式只有在成功呼叫之後[SendRequest](#sendrequest)或在`CHttpFile`已成功建立的物件[OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)。

##  <a name="getverb"></a>  CHttpFile::GetVerb

呼叫此成員函式，若要取得的 HTTP 動詞命令 （或方法） 與此相關聯`CHttpFile`。

```
CString GetVerb() const;
```

### <a name="return-value"></a>傳回值

A [CString](../../atl-mfc-shared/reference/cstringt-class.md)物件，其中包含 HTTP 動詞命令 （或方法） 的名稱。

### <a name="remarks"></a>備註

使用此成員函式只有在成功呼叫之後[SendRequest](#sendrequest)或在`CHttpFile`已成功建立的物件[OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)。

##  <a name="queryinfo"></a>  CHttpFile::QueryInfo

呼叫此成員函式來傳回回應，或要求的 HTTP 要求標頭。

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
要查詢和下列旗標會指定要求的資訊類型的屬性組合：

- HTTP_QUERY_CUSTOM 尋找標頭名稱，並傳回此值*lpvBuffer*輸出上。 如果找不到標頭，則 HTTP_QUERY_CUSTOM 會擲回判斷提示。

- 應用程式通常 HTTP_QUERY_FLAG_REQUEST_HEADERS，查詢的回應標頭，但應用程式也可以使用這個旗標來查詢要求標頭。

- 這些標頭，其值是日期/時間字串，例如 「 上次修改時間，「 HTTP_QUERY_FLAG_SYSTEMTIME 這個旗標傳回標頭值做為標準的 Win32 [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)不需要應用程式的結構剖析資料。 如果您使用這個旗標時，您可能想要使用`SYSTEMTIME`函式的覆寫。

- 其值是數字，例如狀態的程式碼，這些標頭的 HTTP_QUERY_FLAG_NUMBER 這個旗標的 32 位元數字傳回的資料。

請參閱**備註**的可能值清單一節。

*lpvBuffer*<br/>
接收資訊之緩衝區的指標。

*lpdwBufferLength*<br/>
項目，這會指向包含資料緩衝區的字元或位元組數的長度的值。 請參閱**備註**區段如需詳細資訊，有關此參數。

*lpdwIndex*<br/>
以零為起始的標頭索引指標。 可以是 NULL。 您可以使用這個旗標來列舉具有相同名稱的多個標頭。 輸入時， *lpdwIndex*表示傳回指定的標頭的索引。 在輸出時， *lpdwIndex*指出下一步 標頭的索引。 如果找不到下一個索引，則會傳回 ERROR_HTTP_HEADER_NOT_FOUND。

*str*<br/>
參考[CString](../../atl-mfc-shared/reference/cstringt-class.md)接收傳回的資訊的物件。

*dwIndex*<br/>
索引值。 請參閱*lpdwIndex*。

*pSysTime*<br/>
指標，Win32 [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)結構。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。 如果呼叫失敗，Win32 函式[GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360)可能會呼叫以判斷錯誤的原因。

### <a name="remarks"></a>備註

使用此成員函式只有在成功呼叫之後[SendRequest](#sendrequest)或在`CHttpFile`已成功建立的物件[OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)。

您可以擷取下列類型的資料從`QueryInfo`:

- 字串 （預設值）

- `SYSTEMTIME` (如 「 資料:""Expires:"等等，標頭)

- DWORD （適用於 STATUS_CODE CONTENT_LENGTH 等。）

當字串會寫入至緩衝區，而此成員函式成功，`lpdwBufferLength`包含減 1 結束的 NULL 字元的字元字串的長度。

可能*dwInfoLevel*值包括：

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

##  <a name="queryinfostatuscode"></a>  CHttpFile::QueryInfoStatusCode

呼叫此成員函式，以取得與 HTTP 要求相關聯的狀態碼，並將它放在所提供*dwStatusCode*參數。

```
BOOL QueryInfoStatusCode(DWORD& dwStatusCode) const;
```

### <a name="parameters"></a>參數

*dwStatusCode*<br/>
狀態碼的參考。 狀態代碼表示成功或失敗的要求的事件。 請參閱**備註**的狀態碼描述選取範圍。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。 如果呼叫失敗，Win32 函式[GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360)可能會呼叫以判斷錯誤的原因。

### <a name="remarks"></a>備註

使用此成員函式只有在成功呼叫之後[SendRequest](#sendrequest)或在`CHttpFile`已成功建立的物件[OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)。

HTTP 狀態碼分為指出成功或失敗的要求的群組。 下表概述狀態程式碼群組和最常見的 HTTP 狀態碼。

|群組|意義|
|-----------|-------------|
|200-299|成功|
|300-399|資訊|
|400-499|要求錯誤|
|500-599|伺服器錯誤|

常見的 HTTP 狀態碼：

|狀態碼|意義|
|-----------------|-------------|
|200|找到 URL，接著進行傳輸|
|400|難以理解的要求|
|404|找不到要求的 URL|
|405|伺服器不支援所要求的方法|
|500|未知的伺服器錯誤|
|503|已到達伺服器容量|

##  <a name="sendrequest"></a>  CHttpFile::SendRequest

呼叫此成員函式，將要求傳送至 HTTP 伺服器。

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
包含要傳送的標頭名稱的字串指標。

*dwHeadersLen*<br/>
所識別的標頭的長度*pstrHeaders*。

*lpOptional*<br/>
立即之後的要求標頭傳送的任何選擇性資料。 這通常用於 POST 和 PUT 作業。 如果沒有要傳送的選擇性資料，這可以是 NULL。

*dwOptionalLen*<br/>
長度*lpOptional*。

*strHeaders*<br/>
字串，包含所傳送的要求標頭的名稱。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。 如果呼叫失敗，判斷失敗的原因，藉由檢查擲回[CInternetException](../../mfc/reference/cinternetexception-class.md)物件。

##  <a name="sendrequestex"></a>  CHttpFile::SendRequestEx

呼叫此成員函式，將要求傳送至 HTTP 伺服器。

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
若要在要求中傳送的位元組數目。

*dwFlags*<br/>
描述作業的旗標。 如需適當的旗標的清單，請參閱 < [HttpSendRequestEx](/windows/desktop/api/wininet/nf-wininet-httpsendrequestexa) Windows SDK 中。

*dwContext*<br/>
內容識別碼`CHttpFile`作業。 如需這個參數的詳細資訊，請參閱 < 備註 >。

*lpBuffIn*<br/>
初始化的指標[INTERNET_BUFFERS](/windows/desktop/api/wininet/ns-wininet-_internet_buffersa)描述用於作業的輸入的緩衝區。

*lpBuffOut*<br/>
初始化 INTERNET_BUFFERS 描述用於作業的輸出緩衝區的指標。

### <a name="return-value"></a>傳回值

如果成功，非零值。 如果呼叫失敗，判斷失敗的原因，藉由檢查擲回[CInternetException](../../mfc/reference/cinternetexception-class.md)物件。

### <a name="remarks"></a>備註

此函式可讓您的應用程式將使用的資料傳送[撰寫](../../mfc/reference/cinternetfile-class.md#write)並[WriteString](../../mfc/reference/cinternetfile-class.md#writestring)方法`CInternetFile`。 您必須知道要呼叫此函式的其中一個覆寫之前傳送的資料長度。 第一個覆寫可讓您指定您想要傳送的資料長度。 第二個覆寫會接受 INTERNET_BUFFERS 結構，可以用來描述中，有詳細的緩衝區的指標。

內容寫入至檔案之後，呼叫[EndRequest](#endrequest)結束作業。

預設值*dwContext* MFC，以便傳送`CHttpFile`物件[CInternetSession](../../mfc/reference/cinternetsession-class.md)物件建立`CHttpFile`物件。 當您呼叫[cinternetsession:: Openurl](../../mfc/reference/cinternetsession-class.md#openurl)或是[CHttpConnection](../../mfc/reference/chttpconnection-class.md)建構`CHttpFile`物件時，您可以覆寫預設值可設定的內容識別碼以您選擇的值。 內容識別碼會傳回到[CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)來提供，它識別之物件的狀態。 請參閱文章[網際網路前幾個步驟：WinInet](../../mfc/wininet-basics.md)取得的內容識別碼的詳細資訊。

### <a name="example"></a>範例

此程式碼片段會將字串的內容傳送至名為 MFCISAPI 的 DLL。本機主機伺服器上的 DLL。 雖然這個範例使用只有一個呼叫`WriteString`，將資料傳送區塊中使用多個呼叫可接受。

[!code-cpp[NVC_MFCWinInet#9](../../mfc/codesnippet/cpp/chttpfile-class_1.cpp)]

## <a name="see-also"></a>另請參閱

[CInternetFile 類別](../../mfc/reference/cinternetfile-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CInternetFile 類別](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherFile 類別](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttpConnection 類別](../../mfc/reference/chttpconnection-class.md)
