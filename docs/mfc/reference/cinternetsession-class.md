---
title: CInternetSession 類別
ms.date: 06/20/2018
f1_keywords:
- CInternetSession
- AFXINET/CInternetSession
- AFXINET/CInternetSession::CInternetSession
- AFXINET/CInternetSession::Close
- AFXINET/CInternetSession::EnableStatusCallback
- AFXINET/CInternetSession::GetContext
- AFXINET/CInternetSession::GetCookie
- AFXINET/CInternetSession::GetCookieLength
- AFXINET/CInternetSession::GetFtpConnection
- AFXINET/CInternetSession::GetGopherConnection
- AFXINET/CInternetSession::GetHttpConnection
- AFXINET/CInternetSession::OnStatusCallback
- AFXINET/CInternetSession::OpenURL
- AFXINET/CInternetSession::SetCookie
- AFXINET/CInternetSession::SetOption
helpviewer_keywords:
- CInternetSession [MFC], CInternetSession
- CInternetSession [MFC], Close
- CInternetSession [MFC], EnableStatusCallback
- CInternetSession [MFC], GetContext
- CInternetSession [MFC], GetCookie
- CInternetSession [MFC], GetCookieLength
- CInternetSession [MFC], GetFtpConnection
- CInternetSession [MFC], GetGopherConnection
- CInternetSession [MFC], GetHttpConnection
- CInternetSession [MFC], OnStatusCallback
- CInternetSession [MFC], OpenURL
- CInternetSession [MFC], SetCookie
- CInternetSession [MFC], SetOption
ms.assetid: ef54feb4-9d0f-4e65-a45d-7a4cf6c40e51
ms.openlocfilehash: ddd7ca6676805e6de1b7afb5ebc77733701dfef9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372385"
---
# <a name="cinternetsession-class"></a>CInternetSession 類別

建立和初始化單一或多個同時網際網路工作階段，並視需要描述您與 Proxy 伺服器的連接。

## <a name="syntax"></a>語法

```cpp
class CInternetSession : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[C 互聯網會話::C 互聯網會話](#cinternetsession)|建構 `CInternetSession` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[C 網際網路工作階段:關閉](#close)|終止 Internet 作業階段時關閉 Internet 連接。|
|[CInternet 工作階段::啟用狀態回調](#enablestatuscallback)|建立狀態回調例程。|
|[C 網際網路工作階段:取得上下文](#getcontext)|終止 Internet 作業階段時關閉 Internet 連接。|
|[C 網路工作階段::取得 Cookie](#getcookie)|返回指定 URL 及其所有父 URL 的 Cookie。|
|[C 網際網路會話::取得 Cookie 長度](#getcookielength)|檢索指定存儲在緩衝區中的 Cookie 長度的變數。|
|[C 網際網路工作階段::取得Ftp連接](#getftpconnection)|打開與伺服器的 FTP 工作階段。 在使用者上登錄。|
|[C 網路工作階段::取得 Gopher 連接](#getgopherconnection)|為嘗試打開連接的應用程式打開gopher伺服器。|
|[C 網際網路工作階段::取得HTTP連接](#gethttpconnection)|為嘗試打開連接的應用程式打開 HTTP 伺服器。|
|[CInternet 工作階段::打開狀態回撥](#onstatuscallback)|啟用狀態回調時更新操作的狀態。|
|[C 網際網路工作階段::開啟網址](#openurl)|分析並打開 URL。|
|[C 網際網路工作階段::SetCookie](#setcookie)|為指定的網址設置 Cookie。|
|[C 網際網路工作階段::設定選項](#setoption)|設置 Internet 工作階段的選項。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[C 網路工作階段::操作員 HINTERNET](#operator_hinternet)|當前 Internet 作業階段的句柄。|

## <a name="remarks"></a>備註

如果必須在應用程式的持續時間內維護 Internet 連接,則可以`CInternetSession`創建類[CWinApp](../../mfc/reference/cwinapp-class.md)的成員。

建立網際網路工作階段後,可以呼叫[OpenURL](#openurl)。 `CInternetSession`然後通過調用全域函數[AfxParseURL](internet-url-parsing-globals.md#afxparseurl)來分析 URL。 無論協定類型如何,`CInternetSession`都解釋 URL 並為您管理它。 它可以處理使用 URL 資源"file://"標識的本地檔的請求。 `OpenURL`如果傳遞的名稱是本地檔,則返回指向[CStdioFile](../../mfc/reference/cstdiofile-class.md)物件的指標。

如果使用 在 Internet`OpenURL`伺服器上打開 URL,則可以從網站讀取資訊。 如果要對伺服器上的檔執行特定於服務的操作(例如 HTTP、FTP 或 gopher)操作,則必須與該伺服器建立適當的連接。 要直接開啟與特定服務的特定類型的連接,請使用以下成員函數之一:

- [獲取 Gopher 連接](#getgopherconnection)以打開到 gopher 服務的連接。

- [獲取 HTTPConnection](#gethttpconnection)以打開與 HTTP 服務的連接。

- [獲取 Ftp 連接](#getftpconnection)以打開與 FTP 服務的連接。

[SetOption](#setoption)允許您設置作業階段的查詢選項,如超時值、重試次數等。

`CInternetSession`成員函數[SetCookie、GetCookie](#setcookie)和[GetCookieLength](#getcookielength)提供了管理 Win32 Cookie 資料庫的方法,通過該資料庫,伺服器和腳本通過該資料庫維護[GetCookie](#getcookie)有關用戶端工作站的狀態資訊。

有關基本 Internet 程式設計任務的詳細資訊,請參閱文章[「互聯網第一步:WinInet](../../mfc/wininet-basics.md)」。 有關使用 MFC WinInet 類別的一般資訊,請參閱[使用 WinInet 進行 Internet 程式設計的文章](../../mfc/win32-internet-extensions-wininet.md)。

> [!NOTE]
> `CInternetSession`將為不支援的服務類型引發[AfxThrow 不支援的例外。](exception-processing.md#afxthrownotsupportedexception) 目前僅支援以下服務類型:FTP、HTTP、gopher 和檔。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;`CInternetSession`

## <a name="requirements"></a>需求

**標題:** afxinet.h

## <a name="cinternetsessioncinternetsession"></a><a name="cinternetsession"></a>C 互聯網會話::C 互聯網會話

創建`CInternetSession`物件時將調用此成員函數。

```cpp
CInternetSession(
    LPCTSTR pstrAgent = NULL,
    DWORD_PTR dwContext = 1,
    DWORD dwAccessType = PRE_CONFIG_INTERNET_ACCESS,
    LPCTSTR pstrProxyName = NULL,
    LPCTSTR pstrProxyBypass = NULL,
    DWORD dwFlags = 0);
```

### <a name="parameters"></a>參數

*普斯特代理*<br/>
指向標識呼叫 Internet 函數的應用程式或實體名稱的字串的指標(例如,"微軟網際網路瀏覽器")。 如果*pstrAgent*為 NULL(預設值),則框架將調用全域函數[AfxGetAppName](application-information-and-management.md#afxgetappname), 該函數傳回包含應用程式名稱的 null 連接連接字串。 某些協定使用此字串向伺服器標識應用程式。

*dwContext*<br/>
操作的上下文標識碼。 *dwContext*識別 CInternetSession 傳回的作業的狀態資訊[::onStatusCallback](#onstatuscallback)。 預設值設定為 1;將預設值設定為 1但是,您可以顯式為操作分配特定的上下文 ID。 物件及其執行的任何工作都將與該上下文 ID 相關聯。

*dwAccess類型*<br/>
所需的訪問類型。 以下是有效的值,其中一個值可能提供:

- INTERNET_OPEN_TYPE_PRECONFIG 使用註冊表中的預配置設置連接。 此存取類型設定為預設值。 要透過 TIS 代理進行連接,請將*dwAccessType*設置為此值;但是,透過 TIS 代理進行連接。然後,您可以適當地設置註冊表。

- INTERNET_OPEN_TYPE_DIRECT直接連接到互聯網。

- INTERNET_OPEN_TYPE_PROXY通過歐洲核子研究中心代理連接。

有關與不同類型的代理連線的資訊,請參閱[典型 FTP 客戶端應用程式中的步驟](../../mfc/steps-in-a-typical-ftp-client-application.md)。

*pstrProxy 名稱*<br/>
如果*dwAccessType*設置為INTERNET_OPEN_TYPE_PROXY,則首選 CERN 代理的名稱。 預設值是 NULL。

*pstrProxy旁路*<br/>
指向包含可選伺服器位址清單的字串的指標。 使用代理訪問時,可能會繞過這些位址。 如果提供了 NULL 值,則從註冊表中讀取繞過清單。 僅當*dwAccessType*設置為INTERNET_OPEN_TYPE_PROXY時,此參數才有意義。

*dwFlags*<br/>
指示各種緩存選項。 默認值設置為 0。 可能的值包括：

- INTERNET_FLAG_DONT_CACHE不要在本地或任何閘道伺服器中快取數據。

- INTERNET_FLAG_OFFLINE僅通過持久緩存滿足下載操作。 如果緩存中不存在該專案,則返回相應的錯誤代碼。 此標誌可與位**或** **(&#124;**) 運算子組合。

### <a name="remarks"></a>備註

`CInternetSession`是應用程式調用的第一個 Internet 函數。 它初始化內部數據結構,並為將來從應用程式調用做好準備。

如果沒有網路連線可以開啟,`CInternetSession`拋出一個[AfxThrow 互聯網例外](internet-url-parsing-globals.md#afxthrowinternetexception)。

### <a name="example"></a>範例

請參考[CFtpFileFind 的範例](../../mfc/reference/cftpfilefind-class.md)。

## <a name="cinternetsessionclose"></a><a name="close"></a>C 網際網路工作階段:關閉

當應用程式完成使用物件後,`CInternetSession`調用此成員函數。

```cpp
virtual void Close();
```

### <a name="example"></a>範例

請參考[CFtpFileFind 的範例](../../mfc/reference/cftpfilefind-class.md)。

## <a name="cinternetsessionenablestatuscallback"></a><a name="enablestatuscallback"></a>CInternet 工作階段::啟用狀態回調

調用此成員函數以啟用狀態回調。

```cpp
BOOL EnableStatusCallback(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>參數

*b 啟用*<br/>
指定回調是啟用還是禁用。 預設值是 TRUE。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。 如果調用失敗,請通過檢查引發的[CInternetException](../../mfc/reference/cinternetexception-class.md)物件來確定失敗的原因。

### <a name="remarks"></a>備註

處理狀態回調時,可以在應用程式的狀態列中提供有關操作進度(如解析名稱、連接到伺服器等)的狀態。 在長期操作期間,顯示操作狀態特別可取。

由於回調發生在請求處理期間,因此應用程式應在回調中花費盡可能少的時間,以防止對網路的數據輸送量下降。 例如,在回調中放置對話框可能是一個冗長的操作,以至於伺服器終止了請求。

只要任何回調是掛起的,則無法刪除狀態回調。

要非操作,必須建立自己的線程或使用沒有 MFC 的 WinInet 函數。

## <a name="cinternetsessiongetcontext"></a><a name="getcontext"></a>C 網際網路工作階段:取得上下文

調用此成員函數獲取特定應用程式會話的上下文值。

```cpp
DWORD_PTR GetContext() const;
```

### <a name="return-value"></a>傳回值

應用程式定義的上下文標識碼。

### <a name="remarks"></a>備註

[OnStatusCallback](#onstatuscallback)使用`GetContext`傳回的上下文 ID 來報告特定應用程式的狀態。 例如,當使用者啟動涉及返回狀態資訊的 Internet 請求時,狀態回調將使用上下文 ID 報告該特定請求的狀態。 如果使用者啟動兩個涉及返回狀態資訊的單獨 Internet`OnStatusCallback`請求, 則使用上下文標識符返回其相應請求的狀態。 因此,上下文標識符用於所有狀態回調操作,並且它與會話關聯,直到會話結束。

有關非同步操作的詳細資訊,請參閱文章[「Internet 第一步:WinInet」。。](../../mfc/wininet-basics.md)

## <a name="cinternetsessiongetcookie"></a><a name="getcookie"></a>C 網路工作階段::取得 Cookie

此成員函數實現 Win32 函數[InternetGetCookie](/windows/win32/api/wininet/nf-wininet-internetgetcookiew)的行為,如 Windows SDK 中所述。

```cpp
static BOOL GetCookie(
    LPCTSTR pstrUrl,
    LPCTSTR pstrCookieName,
    LPTSTR pstrCookieData,
    DWORD dwBufLen);

static BOOL GetCookie(
    LPCTSTR pstrUrl,
    LPCTSTR pstrCookieName,
    CString& strCookieData);
```

### <a name="parameters"></a>參數

*pstr網址*<br/>
指向包含 URL 的字串的指標。

*普斯特庫奇名稱*<br/>
指向包含 Cookie 名稱的字串的指標,用於獲取指定 URL 的名稱。

*普斯特庫奇資料*<br/>
在第一個重載中,指向包含接收 Cookie 數據的緩衝區位址的字串的指標。 此值可以是 NULL。 在第二個重載中,對[CString](../../atl-mfc-shared/reference/cstringt-class.md)物件的引用以接收Cookie資料。

*德布夫倫*<br/>
指定*pstrCookieData*緩衝區大小的變數。 如果函數成功,緩衝區將收到複製到*pstrCookieData*緩衝區的數據量。 如果*pstrCookieData*為 NULL,則此參數將接收指定複製所有 Cookie 資料所需的緩衝區大小的值。

### <a name="return-value"></a>傳回值

如果成功,則返回 TRUE,否則返回 FALSE。 如果呼叫失敗,請致電 Win32 函數[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)以確定錯誤的原因。 套用以下錯誤值:

- ERROR_NO_MORE_ITEMS指定 URL 及其所有父 URL 沒有 Cookie。

- ERROR_INSUFFICIENT_BUFFER *dwBufLen*中傳遞的值不足以複製所有 Cookie 數據。 *在 dwBufLen*中傳回的值是獲取所有資料所需的緩衝區的大小。

### <a name="remarks"></a>備註

在第二個重載中,MFC 將 Cookie 數據`CString`檢索到提供的物件中。

## <a name="cinternetsessiongetcookielength"></a><a name="getcookielength"></a>C 網際網路會話::取得 Cookie 長度

調用此成員函數獲取存儲在緩衝區中的 Cookie 的長度。

```cpp
static DWORD GetCookieLength(
    LPCTSTR pstrUrl,
    LPCTSTR pstrCookieName);
```

### <a name="parameters"></a>參數

*pstr網址*<br/>
包含網址的字串的指標

*普斯特庫奇名稱*<br/>
指向包含 Cookie 名稱的字串的指標。

### <a name="return-value"></a>傳回值

DWORD 值,指示存儲在緩衝區中的 Cookie 的長度。 如果存在帶有*pstrCookieName*指示的名稱的 Cookie,則為零。

### <a name="remarks"></a>備註

此值由[GetCookie](#getcookie)使用。

## <a name="cinternetsessiongetftpconnection"></a><a name="getftpconnection"></a>C 網際網路工作階段::取得Ftp連接

呼叫此成員函數以建立 FTP 連接並`CFtpConnection`獲取指向 物件的指標。

```cpp
CFtpConnection* GetFtpConnection(
    LPCTSTR pstrServer,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    BOOL bPassive = FALSE);
```

### <a name="parameters"></a>參數

*pstrServer*<br/>
指向包含 FTP 伺服器名稱的字串的指標。

*pstrUser 名稱*<br/>
指向 null 終止字串的指標,該字串指定要登錄的使用者的名稱。 如果為 NULL,則預設值為匿名。

*pstr密碼*<br/>
指向 null 終止字串的指標,用於指定用於登入的密碼。 如果*pstrPassword*和*pstrUserName*均為 NULL,則預設的匿名密碼是使用者的電子郵件名稱。 如果*pstrPassword*為 NULL(或空字串),但*pstrUserName*不是 NULL,則使用空白密碼。 下表描述了*pstrUserName*和*pstrPassword*的四種可能設定的行為:

| *pstrUser 名稱*  | *pstr密碼*  | 傳送 FTP 伺服器的使用者名稱 | 傳送 FTP 伺服器的密碼 |
|-----------------|-----------------|-----------------------------|-----------------------------|
|   NULL 或""   |   NULL 或""   |         "匿名"         |      使用者的電子郵件名稱      |
| NULL 字串 |   NULL 或""   |       *pstrUser 名稱*        |             " "             |
|      NULL       | NULL 字串 |            ERROR            |            ERROR            |
| NULL 字串 | NULL 字串 |       *pstrUser 名稱*        |       *pstr密碼*        |

*n波特*<br/>
標識要在伺服器上使用的 TCP/IP 連接埠的數位。

*b被動*<br/>
為此 FTP 會話指定被動或主動模式。 如果設置為 TRUE,它將 Win32`dwFlag`API 設置為INTERNET_FLAG_PASSIVE。

### <a name="return-value"></a>傳回值

指向[CFtpConnect](../../mfc/reference/cftpconnection-class.md)物件的指標。 如果調用失敗,請通過檢查引發的[CInternetException](../../mfc/reference/cinternetexception-class.md)物件來確定失敗的原因。

### <a name="remarks"></a>備註

`GetFtpConnection`連接到 FTP 伺服器,並創建並`CFTPConnection`返回指向 物件的指標。 它不在伺服器上執行任何特定操作。 例如,如果要讀取或寫入檔,則必須將這些操作作為單獨的步驟執行。 有關搜索檔、打開檔以及讀取或寫入檔的資訊,請參閱[CFtpConnect](../../mfc/reference/cftpconnection-class.md)和[CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)類。 有關執行常見 FTP 連接任務的步驟,請參閱[使用 WinInet 進行 Internet 編程](../../mfc/win32-internet-extensions-wininet.md)的文章。

### <a name="example"></a>範例

請參考[CFtpFileFind 的範例](../../mfc/reference/cftpfilefind-class.md)。

## <a name="cinternetsessiongetgopherconnection"></a><a name="getgopherconnection"></a>C 網路工作階段::取得 Gopher 連接

呼叫此成員函數以建立新的 gopher 連接,並`CGopherConnection`獲取指向 物件的指標。

```cpp
CGopherConnection* GetGopherConnection(
    LPCTSTR pstrServer,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER);
```

### <a name="parameters"></a>參數

*pstrServer*<br/>
指向包含 gopher 伺服器名稱的字串的指標。

*pstrUser 名稱*<br/>
指向包含使用者名的字串的指標。

*pstr密碼*<br/>
指向包含存取密碼的字串的指標。

*n波特*<br/>
標識要在伺服器上使用的 TCP/IP 連接埠的數位。

### <a name="return-value"></a>傳回值

指向[Gopher 連接](../../mfc/reference/cgopherconnection-class.md)物件的指標。 如果調用失敗,請通過檢查引發的[CInternetException](../../mfc/reference/cinternetexception-class.md)物件來確定失敗的原因。

### <a name="remarks"></a>備註

`GetGopherConnection`連接到 gopher 伺服器,並建立並`CGopherConnection`返回指向 物件的指標。 它不在伺服器上執行任何特定操作。 例如,如果要讀取或寫入數據,則必須將這些操作作為單獨的步驟執行。 有關搜索檔、打開檔、讀取或寫入檔的資訊,請參閱類[CGopherConnection、CGopherFile](../../mfc/reference/cgopherconnection-class.md)和[CGopherFileFind。](../../mfc/reference/cgopherfilefind-class.md) [CGopherFile](../../mfc/reference/cgopherfile-class.md) 有關流覽 FTP 網站的資訊,請參閱成員函數[OpenURL](#openurl)。 有關執行常見 gopher 連接任務的步驟,請參閱[使用 WinInet 進行 Internet 程式設計](../../mfc/win32-internet-extensions-wininet.md)的文章。

## <a name="cinternetsessiongethttpconnection"></a><a name="gethttpconnection"></a>C 網際網路工作階段::取得HTTP連接

呼叫此成員函數以建立 HTTP 連接並`CHttpConnection`獲取指向 物件的指標。

```cpp
CHttpConnection* GetHttpConnection(
    LPCTSTR pstrServer,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL);

CHttpConnection* GetHttpConnection(
    LPCTSTR pstrServer,
    DWORD dwFlags,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL);
```

### <a name="parameters"></a>參數

*pstrServer*<br/>
指向包含 HTTP 伺服器名稱的字串的指標。

*n波特*<br/>
標識要在伺服器上使用的 TCP/IP 連接埠的數位。

*pstrUser 名稱*<br/>
指向包含使用者名的字串的指標。

*pstr密碼*<br/>
指向包含存取密碼的字串的指標。

*dwflags*<br/>
標誌的`INTERNET_FLAG_*`任意組合。 請參閱[CHTTPConnection::打開請求的備](../../mfc/reference/chttpconnection-class.md#openrequest)**註**部分中的表,瞭解*dwFlags*值的說明。

### <a name="return-value"></a>傳回值

指向[CHTTPConnect](../../mfc/reference/chttpconnection-class.md)物件的指標。 如果調用失敗,請通過檢查引發的[CInternetException](../../mfc/reference/cinternetexception-class.md)物件來確定失敗的原因。

### <a name="remarks"></a>備註

`GetHttpConnection`連接到 HTTP 伺服器,並建立並`CHttpConnection`返回指向 物件的指標。 它不在伺服器上執行任何特定操作。 例如,如果要查詢 HTTP 標頭,則必須作為單獨的步驟執行此操作。 有關可以使用連接到 HTTP 伺服器可以執行的操作的資訊,請參閱類[CHttpConnection](../../mfc/reference/chttpconnection-class.md)和[CHttpFile。](../../mfc/reference/chttpfile-class.md) 有關瀏覽 HTTP 網站的資訊,請參閱成員函數[OpenURL](#openurl)。 有關執行常見 HTTP 連接任務的步驟,請參閱[使用 WinInet 進行 Internet 程式設計](../../mfc/win32-internet-extensions-wininet.md)的文章。

## <a name="cinternetsessiononstatuscallback"></a><a name="onstatuscallback"></a>CInternet 工作階段::打開狀態回撥

框架將調用此成員函數,以在啟用狀態回調且操作掛起時更新狀態。

```cpp
virtual void OnStatusCallback(
    DWORD_PTR dwContext,
    DWORD dwInternetStatus,
    LPVOID lpvStatusInformation,
    DWORD dwStatusInformationLength);
```

### <a name="parameters"></a>參數

*dwContext*<br/>
應用程式提供的上下文值。

*dw網際網路狀態*<br/>
指示進行回調的原因的狀態代碼。 有關可能值的表,請參閱**備註**。

*lpv 狀態資訊*<br/>
指向緩衝區的指標,其中包含與此回調相關的資訊。

*dwStatus 資訊長度*<br/>
*lpv 狀態資訊的大小*。

### <a name="remarks"></a>備註

您必須首先調用[啟用狀態回調](#enablestatuscallback)以利用狀態回調。

*dwInternetStatus*參數指示正在執行的操作,並確定*lpvStatus資訊*的內容。 *dwStatus資訊長度*表示*lpvStatus 資訊*中包含的數據的長度。 *dwInternetStatus*的以下狀態值定義如下:

|值|意義|
|-----------|-------------|
|INTERNET_STATUS_RESOLVING_NAME|尋找*lpvStatus 資訊*中包含的名稱的 IP 位址。|
|INTERNET_STATUS_NAME_RESOLVED|已成功找到*lpvStatus 資訊*中包含的名稱的 IP 位址。|
|INTERNET_STATUS_CONNECTING_TO_SERVER|連線到以*lpvStatus 資訊*指向的通訊通訊地址 ([SOCKADDR](/windows/win32/winsock/sockaddr-2)) 。|
|INTERNET_STATUS_CONNECTED_TO_SERVER|成功連接到*lpvStatus 資訊*指向的套接字位址 (SOCKADDR)。|
|INTERNET_STATUS_SENDING_REQUEST|將資訊請求發送到伺服器。 *lpv 狀態資訊*參數為 NULL。|
|INTERNET_STATUS_REQUEST_SENT|已成功將資訊請求發送到伺服器。 *lpv 狀態資訊*參數為 NULL。|
|INTERNET_STATUS_RECEIVING_RESPONSE|正在等待伺服器回應請求。 *lpv 狀態資訊*參數為 NULL。|
|INTERNET_STATUS_RESPONSE_RECEIVED|已成功收到來自伺服器的回應。 *lpv 狀態資訊*參數為 NULL。|
|INTERNET_STATUS_CLOSING_CONNECTION|關閉與伺服器的連接。 *lpv 狀態資訊*參數為 NULL。|
|INTERNET_STATUS_CONNECTION_CLOSED|成功關閉與伺服器的連接。 *lpv 狀態資訊*參數為 NULL。|
|INTERNET_STATUS_HANDLE_CREATED|Win32 API 函數[InternetConnect](/windows/win32/api/wininet/nf-wininet-internetconnectw)用於指示它已創建新句柄。 這允許應用程式調用 Win32 函數[InternetCloseHandle](/windows/win32/api/wininet/nf-wininet-internetclosehandle)從另一個線程,如果連接時間過長。 有關這些功能的詳細資訊,請參閱 Windows SDK。|
|INTERNET_STATUS_HANDLE_CLOSING|已成功終止此句柄值。|

重寫此成員函數,以執行狀態回調例程之前需要一些操作。

> [!NOTE]
> 狀態回調需要線程狀態保護。 如果在共用庫中使用 MFC,請向重寫的開頭添加以下行:

[!code-cpp[NVC_MFCHtmlHttp#8](../../mfc/reference/codesnippet/cpp/cinternetsession-class_1.cpp)]

有關非同步操作的詳細資訊,請參閱文章[「Internet 第一步:WinInet」。。](../../mfc/wininet-basics.md)

## <a name="cinternetsessionopenurl"></a><a name="openurl"></a>C 網際網路工作階段::開啟網址

呼叫此成員函數將指定的請求發送到 HTTP 伺服器,並允許用戶端指定與請求一起發送的其他 RFC822、MIME 或 HTTP 標頭。

```cpp
CStdioFile* OpenURL(
    LPCTSTR pstrURL,
    DWORD_PTR dwContext = 1,
    DWORD dwFlags = INTERNET_FLAG_TRANSFER_ASCII,
    LPCTSTR pstrHeaders = NULL,
    DWORD dwHeadersLength = 0);
```

### <a name="parameters"></a>參數

*pstrURL*<br/>
指向開始讀取 URL 名稱的指標。 僅支援以檔:、ftp:、gopher:或 http: 開頭的 URL。 斷言如果*pstrURL*為 NULL。

*dwContext*<br/>
使用回調中返回的句柄傳遞的應用程式定義值。

*dwFlags*<br/>
描述如何處理此連接的標誌。 有關有效標誌的詳細資訊,請參閱**備註**。 有效標誌包括:

- INTERNET_FLAG_TRANSFER_ASCII 預設值。 將文件作為 ASCII 文字傳輸。

- INTERNET_FLAG_TRANSFER_BINARY將文件作為二進位檔案傳輸。

- INTERNET_FLAG_RELOAD從導線中獲取數據,即使它是本地快取的。

- INTERNET_FLAG_DONT_CACHE不要在本地或任何閘道中快取資料。

- INTERNET_FLAG_SECURE此標誌僅適用於 HTTP 請求。 它要求使用安全套接字層或 PCT 在電線上進行安全交易。

- INTERNET_OPEN_FLAG_USE_EXISTING_CONNECT 如果可能,請重用與伺服器的現有連接,以造`OpenUrl`訪生成的新請求,而不是為每個連接請求創建新會話。

- INTERNET_FLAG_PASSIVE用於 FTP 網站。 使用被動 FTP 語義。 與的`OpenURL` [CInternet 連接](../../mfc/reference/cinternetconnection-class.md)一起使用。

*pstrHeaders*<br/>
指向包含要發送到 HTTP 伺服器的標頭的字串的指標。

*dwHeaders 長度*<br/>
附加標頭的長度(以字元表示)。 如果為 -1L,並且*pstrHeader*是非 NULL,則假定*pstrHeader*為零端接,並計算長度。

### <a name="return-value"></a>傳回值

僅返回 FTP、GOPHER、HTTP 和 FILE 類型的 Internet 服務的檔句柄。 如果分析不成功,則返回 NULL。

返回的`OpenURL`指標取決於*pstrURL*的服務類型。 下表說明了可以返回的可能指標`OpenURL`。

|網址型態|傳回值|
|--------------|-------------|
|`file://`|`CStdioFile*`|
|`http://`|`CHttpFile*`|
|`gopher://`|`CGopherFile*`|
|`ftp://`|`CInternetFile*`|

### <a name="remarks"></a>備註

參數*dwFlags*必須包括INTERNET_FLAG_TRANSFER_ASCII或INTERNET_FLAG_TRANSFER_BINARY,但不能同時包含這兩個參數。 其餘標誌可以與位**或**運算符 **(&#124;**) 組合。

`OpenURL`,它包裝 Win32`InternetOpenURL`函數 ,只允許從 Internet 伺服器下載、檢索和讀取數據。 `OpenURL`不允許對遠端位置進行檔操作,因此不需要[CInternetConnect](../../mfc/reference/cinternetconnection-class.md)物件。

要使用特定於連接(即特定於協定的)函數(如寫入檔),必須打開會話,然後打開特定類型的連接,然後使用該連接以所需模式打開檔。 有關`CInternetConnection`特定於連接的功能的詳細資訊,請參閱。

## <a name="cinternetsessionoperator-hinternet"></a><a name="operator_hinternet"></a>C 網路工作階段::操作員 HINTERNET

使用此運算元獲取當前 Internet 工作階段的 Windows 句柄。

```cpp
operator HINTERNET() const;
```

## <a name="cinternetsessionsetcookie"></a><a name="setcookie"></a>C 網際網路工作階段::SetCookie

為指定的網址設置 Cookie。

```cpp
static BOOL SetCookie(
    LPCTSTR pstrUrl,
    LPCTSTR pstrCookieName,
    LPCTSTR pstrCookieData);
```

### <a name="parameters"></a>參數

*pstr網址*<br/>
指向 null 連接字串的指標,用於指定應為其設定 Cookie 的 URL。

*普斯特庫奇名稱*<br/>
指向包含 Cookie 名稱的字串的指標。

*普斯特庫奇資料*<br/>
指向包含要與 URL 關聯的實際字串數據的指標。

### <a name="return-value"></a>傳回值

如果成功,則返回 TRUE,否則返回 FALSE。 要取得特定的錯誤代碼,請呼叫`GetLastError.`

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[InternetSetCookie](/windows/win32/api/wininet/nf-wininet-internetsetcookiew)的行為,如 Windows SDK 中所述。

## <a name="cinternetsessionsetoption"></a><a name="setoption"></a>C 網際網路工作階段::設定選項

呼叫此成員函數以設置 Internet 工作階段的選項。

```cpp
BOOL SetOption(
    DWORD dwOption,
    LPVOID lpBuffer,
    DWORD dwBufferLength,
    DWORD dwFlags = 0);

BOOL SetOption(
    DWORD dwOption,
    DWORD dwValue,
    DWORD dwFlags = 0);
```

### <a name="parameters"></a>參數

*dwOption*<br/>
要設置的 Internet 選項。 有關可能的選項的清單,請參閱 Windows SDK[中的選項旗標](/windows/win32/WinInet/option-flags)。

*lpBuffer*<br/>
包含選項設置的緩衝區。

*dwBuffer 長度*<br/>
*lpBuffer*的長度或*dwValue*的大小。

*dwValue*<br/>
包含選項設定的 DWORD。

*dwFlags*<br/>
指示各種緩存選項。 默認值設置為 0。 可能的值包括：

- INTERNET_FLAG_DONT_CACHE不要在本地或任何閘道伺服器中快取數據。

- INTERNET_FLAG_OFFLINE僅通過持久緩存滿足下載操作。 如果緩存中不存在該專案,則返回相應的錯誤代碼。 此標誌可與位**或** **(&#124;**) 運算子組合。

### <a name="return-value"></a>傳回值

如果操作成功,則返回 TRUE 的值。 如果發生錯誤,則返回 FALSE 的值。 如果調用失敗,可能會調用 Win32 函數[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)以確定錯誤的原因。

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CInternetConnection 類別](../../mfc/reference/cinternetconnection-class.md)<br/>
[CHttpConnection 類別](../../mfc/reference/chttpconnection-class.md)<br/>
[CFtpConnection 類別](../../mfc/reference/cftpconnection-class.md)<br/>
[CGopherConnection 類別](../../mfc/reference/cgopherconnection-class.md)
