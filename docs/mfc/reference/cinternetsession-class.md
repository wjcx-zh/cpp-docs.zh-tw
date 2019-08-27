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
ms.openlocfilehash: c9b8eaf51820dfcd08c1390c8645978fa403931d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505851"
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
|[CInternetSession::CInternetSession](#cinternetsession)|建構 `CInternetSession` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CInternetSession::Close](#close)|當網際網路會話終止時, 關閉網際網路連線。|
|[CInternetSession::EnableStatusCallback](#enablestatuscallback)|建立狀態回呼常式。|
|[CInternetSession::GetContext](#getcontext)|當網際網路會話終止時, 關閉網際網路連線。|
|[CInternetSession::GetCookie](#getcookie)|傳回指定 URL 及其所有父 Url 的 cookie。|
|[CInternetSession::GetCookieLength](#getcookielength)|抓取變數, 指定儲存在緩衝區中的 cookie 長度。|
|[CInternetSession::GetFtpConnection](#getftpconnection)|開啟與伺服器的 FTP 會話。 登入使用者。|
|[CInternetSession::GetGopherConnection](#getgopherconnection)|開啟嘗試開啟連接之應用程式的 Gopher 伺服器。|
|[CInternetSession::GetHttpConnection](#gethttpconnection)|為嘗試開啟連接的應用程式開啟 HTTP 伺服器。|
|[CInternetSession::OnStatusCallback](#onstatuscallback)|啟用狀態回撥時, 更新作業的狀態。|
|[CInternetSession::OpenURL](#openurl)|剖析並開啟 URL。|
|[CInternetSession::SetCookie](#setcookie)|為指定的 URL 設定 cookie。|
|[CInternetSession::SetOption](#setoption)|設定網際網路會話的選項。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CInternetSession:: operator HINTERNET](#operator_hinternet)|目前網際網路會話的控制碼。|

## <a name="remarks"></a>備註

如果您的網際網路連線必須在應用程式期間維護, 您可以建立`CInternetSession`類別[CWinApp](../../mfc/reference/cwinapp-class.md)的成員。

建立網際網路會話之後, 您就可以呼叫[OpenURL](#openurl)。 `CInternetSession`然後藉由呼叫全域函數[AfxParseURL](internet-url-parsing-globals.md#afxparseurl), 為您剖析 URL。 不論其通訊協定類型為何`CInternetSession` , 都會解讀 URL 並為您進行管理。 它可以處理以 URL 資源 "file://" 識別之本機檔案的要求。 `OpenURL`如果您傳遞的名稱是本機檔案, 將會傳回[CStdioFile](../../mfc/reference/cstdiofile-class.md)物件的指標。

如果您使用`OpenURL`開啟網際網路伺服器上的 URL, 您可以從網站讀取資訊。 如果您想要對位於伺服器上的檔案執行服務特定 (例如, HTTP、FTP 或 gopher) 動作, 您必須建立與該伺服器的適當連接。 若要將特定類型的連接直接開啟至特定服務, 請使用下列其中一個成員函式:

- [GetGopherConnection](#getgopherconnection)以開啟 gopher 服務的連接。

- [GetHttpConnection](#gethttpconnection)以開啟 HTTP 服務的連接。

- [GetFtpConnection](#getftpconnection)以開啟 FTP 服務的連接。

[SetOption](#setoption)可讓您設定會話的查詢選項, 例如超時值、重試次數等等。

`CInternetSession`成員函式[system.windows.application.setcookie](#setcookie)、 [system.windows.application.getcookie](#getcookie)和[GetCookieLength](#getcookielength)提供管理 Win32 cookie 資料庫的方法, 讓伺服器和腳本維護用戶端工作站的相關狀態資訊。

如需有關基本網際網路程式設計工作的詳細資訊, [請參閱網際網路的第一篇步驟:WinInet](../../mfc/wininet-basics.md)。 如需使用 MFC WinInet 類別的一般資訊, 請參閱[使用 WinInet 進行網際網路程式設計](../../mfc/win32-internet-extensions-wininet.md)一文。

> [!NOTE]
> `CInternetSession`將會擲回不支援之服務類型的[AfxThrowNotSupportedException](exception-processing.md#afxthrownotsupportedexception) 。 目前僅支援下列服務類型:FTP、HTTP、gopher 和 file。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;`CInternetSession`

## <a name="requirements"></a>需求

**標頭:** afxinet.h。h

## <a name="cinternetsession"></a>CInternetSession:: CInternetSession

建立`CInternetSession`物件時, 會呼叫這個成員函式。

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

*pstrAgent*<br/>
字串的指標, 識別呼叫網際網路函式的應用程式或實體的名稱 (例如「Microsoft 網際網路瀏覽器」)。 如果*pstrAgent*為 Null (預設值), 則架構會呼叫全域函式[AfxGetAppName](application-information-and-management.md#afxgetappname), 它會傳回包含應用程式名稱的以 Null 終止的字串。 有些通訊協定會使用此字串來向伺服器識別您的應用程式。

*dwContext*<br/>
作業的內容識別碼。 *dwCoNtext*會識別[CInternetSession:: OnStatusCallback](#onstatuscallback)傳回的作業狀態資訊。 預設值設定為 1;不過, 您可以明確地指派作業的特定內容識別碼。 物件及其執行的任何工作都會與該內容識別碼相關聯。

*dwAccessType*<br/>
所需的存取類型。 下列是有效的值, 其中只有一個可以提供:

- INTERNET_OPEN_TYPE_PRECONFIG 使用登錄中的預先設定設定進行連接。 此存取類型會設定為預設值。 若要透過 TIS proxy 連接, 請將*dwAccessType*設定為此值;然後, 您就可以適當地設定登錄。

- INTERNET_OPEN_TYPE_DIRECT 直接連線到網際網路。

- INTERNET_OPEN_TYPE_PROXY 透過 CERN PROXY 連接。

如需使用不同類型的 proxy 進行連接的相關資訊, 請參閱[一般 FTP 用戶端應用程式中的步驟](../../mfc/steps-in-a-typical-ftp-client-application.md)。

*pstrProxyName*<br/>
如果*dwAccessType*設為 INTERNET_OPEN_TYPE_PROXY, 則慣用的 CERN proxy 的名稱。 預設值為 Null。

*pstrProxyBypass*<br/>
字串的指標, 其中包含選擇性的伺服器地址清單。 使用 proxy 存取時, 可能會略過這些位址。 如果提供 Null 值, 則會從登錄讀取略過清單。 只有在*dwAccessType*設定為 INTERNET_OPEN_TYPE_PROXY 時, 這個參數才有意義。

*dwFlags*<br/>
表示各種快取選項。 預設值是設定為0。 可能的值包括:

- INTERNET_FLAG_DONT_CACHE 不會快取本機或任何閘道伺服器中的資料。

- INTERNET_FLAG_OFFLINE 下載作業只能透過持續性快取來滿足。 如果專案不存在於快取中, 則會傳回適當的錯誤碼。 這個旗標可以與位**or** ( **&#124;** ) 運算子結合。

### <a name="remarks"></a>備註

`CInternetSession`是應用程式所呼叫的第一個網際網路函式。 它會初始化內部資料結構, 並準備未來來自應用程式的呼叫。

如果無法開啟網際網路連線, `CInternetSession`則會擲回[AfxThrowInternetException](internet-url-parsing-globals.md#afxthrowinternetexception)。

### <a name="example"></a>範例

請參閱[CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)的範例。

## <a name="close"></a>  CInternetSession::Close

當您的應用程式完成使用物件時, `CInternetSession`請呼叫這個成員函式。

```cpp
virtual void Close();
```

### <a name="example"></a>範例

請參閱[CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)的範例。

## <a name="enablestatuscallback"></a>  CInternetSession::EnableStatusCallback

呼叫此成員函式以啟用狀態回呼。

```cpp
BOOL EnableStatusCallback(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>參數

*bEnable*<br/>
指定是否啟用或停用回呼。 預設值為 TRUE。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。 如果呼叫失敗, 請檢查擲回的[CInternetException](../../mfc/reference/cinternetexception-class.md)物件來判斷失敗的原因。

### <a name="remarks"></a>備註

處理狀態回呼時, 您可以在應用程式的狀態列中提供作業進度的狀態 (例如解析名稱、連接到伺服器等)。 在長期作業期間, 特別需要顯示作業狀態。

由於回呼是在要求的處理期間發生, 因此應用程式應該盡可能花最少的時間在回呼中, 以防止資料輸送量降低到網路。 例如, 將對話方塊放在回呼中可能是伺服器終止要求的冗長作業。

只要有任何回呼暫止, 就無法移除狀態回呼。

若要以非同步方式處理任何作業, 您必須建立自己的執行緒, 或在沒有 MFC 的情況下使用 WinInet 函數。

## <a name="getcontext"></a>CInternetSession:: GetCoNtext

呼叫這個成員函式, 以取得特定應用程式會話的內容值。

```cpp
DWORD_PTR GetContext() const;
```

### <a name="return-value"></a>傳回值

應用程式定義的內容識別碼。

### <a name="remarks"></a>備註

[OnStatusCallback](#onstatuscallback)會使用所傳回`GetContext`的內容識別碼來報告特定應用程式的狀態。 例如, 當使用者啟動涉及傳回狀態資訊的網際網路要求時, 狀態回呼會使用內容識別碼來報告該特定要求的狀態。 如果使用者啟動兩個與傳回狀態資訊相關的不同網際網路要求, `OnStatusCallback`則會使用內容識別碼來傳回其對應要求的狀態。 因此, 內容識別碼會用於所有狀態回呼作業, 並與會話相關聯, 直到會話結束為止。

如需非同步作業的詳細資訊, 請參閱[網際網路的第一篇步驟:WinInet](../../mfc/wininet-basics.md)。

## <a name="getcookie"></a>  CInternetSession::GetCookie

此成員函式會執行 Win32 函數[InternetGetCookie](/windows/win32/api/wininet/nf-wininet-internetgetcookiew)的行為, 如 Windows SDK 中所述。

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

*pstrUrl*<br/>
包含 URL 之字串的指標。

*pstrCookieName*<br/>
字串的指標, 其中包含要為指定之 URL 取得的 cookie 名稱。

*pstrCookieData*<br/>
在第一個多載中, 包含接收 cookie 資料的緩衝區位址之字串的指標。 這個值可以是 Null。 在第二個多載中, 是用來接收 cookie 資料之[CString](../../atl-mfc-shared/reference/cstringt-class.md)物件的參考。

*dwBufLen*<br/>
指定*pstrCookieData*緩衝區大小的變數。 如果函數成功, 緩衝區會接收復制到*pstrCookieData*緩衝區的資料量。 如果*pstrCookieData*是 Null, 此參數會收到一個值, 指定複製所有 cookie 資料所需的緩衝區大小。

### <a name="return-value"></a>傳回值

如果成功, 則傳回 TRUE, 否則傳回 FALSE。 如果呼叫失敗, 請呼叫 Win32 函數[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)以判斷錯誤的原因。 以下是適用的錯誤值:

- ERROR_NO_MORE_ITEMS 指定的 URL 及其所有父代沒有 cookie。

- ERROR_INSUFFICIENT_BUFFER 在*dwBufLen*中傳遞的值不足以複製所有 cookie 資料。 在*dwBufLen*中傳回的值是取得所有資料所需的緩衝區大小。

### <a name="remarks"></a>備註

在第二個多載中, MFC 會將 cookie 資料`CString`捕獲到提供的物件中。

## <a name="getcookielength"></a>CInternetSession:: GetCookieLength

呼叫這個成員函式, 以取得儲存在緩衝區中的 cookie 長度。

```cpp
static DWORD GetCookieLength(
    LPCTSTR pstrUrl,
    LPCTSTR pstrCookieName);
```

### <a name="parameters"></a>參數

*pstrUrl*<br/>
包含 URL 之字串的指標。

*pstrCookieName*<br/>
包含 cookie 名稱之字串的指標。

### <a name="return-value"></a>傳回值

DWORD 值, 指出儲存在緩衝區中的 cookie 長度。 如果沒有*pstrCookieName*所表示之名稱的 cookie, 則為零。

### <a name="remarks"></a>備註

這個值是由[system.windows.application.getcookie](#getcookie)所使用。

## <a name="getftpconnection"></a>CInternetSession:: GetFtpConnection

呼叫這個成員函式以建立 FTP 連接, 並取得`CFtpConnection`物件的指標。

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
包含 FTP 伺服器名稱之字串的指標。

*pstrUserName*<br/>
以 null 結束的字串指標, 指定要登入之使用者的名稱。 如果是 Null, 則預設值為 anonymous。

*pstrPassword*<br/>
以 null 結束的字串指標, 指定要用來登入的密碼。 如果*pstrPassword*和*PSTRUSERNAME*都是 Null, 則預設的匿名密碼就是使用者的電子郵件名稱。 如果*pstrPassword*為 Null (或空字串), 但*PSTRUSERNAME*不是 null, 則會使用空白密碼。 下表描述*pstrUserName*和*pstrPassword*的四個可能設定的行為:

| *pstrUserName*  | *pstrPassword*  | 傳送到 FTP 伺服器的使用者名稱 | 傳送到 FTP 伺服器的密碼 |
|-----------------|-----------------|-----------------------------|-----------------------------|
|   Null 或 ""   |   Null 或 ""   |         匿名         |      使用者的電子郵件名稱      |
| 非 Null 字串 |   Null 或 ""   |       *pstrUserName*        |             " "             |
|      NULL       | 非 Null 字串 |            錯誤            |            錯誤            |
| 非 Null 字串 | 非 Null 字串 |       *pstrUserName*        |       *pstrPassword*        |

*nPort*<br/>
識別要在伺服器上使用之 TCP/IP 通訊埠的數位。

*bPassive*<br/>
指定此 FTP 會話的被動或主動模式。 如果設定為 TRUE, 則會將 WIN32 API `dwFlag`設定為 INTERNET_FLAG_PASSIVE。

### <a name="return-value"></a>傳回值

[CFtpConnection](../../mfc/reference/cftpconnection-class.md)物件的指標。 如果呼叫失敗, 請檢查擲回的[CInternetException](../../mfc/reference/cinternetexception-class.md)物件來判斷失敗的原因。

### <a name="remarks"></a>備註

`GetFtpConnection`連接到 FTP 伺服器, 並建立並傳回`CFTPConnection`物件的指標。 它不會在伺服器上執行任何特定的作業。 例如, 如果您想要讀取或寫入檔案, 您必須以個別步驟執行這些作業。 如需搜尋檔案、開啟檔案, 以及讀取或寫入檔案的相關資訊, 請參閱 < 類別[CFtpConnection](../../mfc/reference/cftpconnection-class.md)和[CFtpFileFind](../../mfc/reference/cftpfilefind-class.md) 。 如需執行一般 FTP 連接工作的步驟, 請參閱[使用 WinInet 進行網際網路程式設計](../../mfc/win32-internet-extensions-wininet.md)一文。

### <a name="example"></a>範例

請參閱[CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)的範例。

## <a name="getgopherconnection"></a>CInternetSession:: GetGopherConnection

呼叫這個成員函式以建立新的 gopher 連接, 並取得`CGopherConnection`物件的指標。

```cpp
CGopherConnection* GetGopherConnection(
    LPCTSTR pstrServer,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER);
```

### <a name="parameters"></a>參數

*pstrServer*<br/>
包含 Gopher 伺服器名稱之字串的指標。

*pstrUserName*<br/>
包含使用者名稱之字串的指標。

*pstrPassword*<br/>
包含存取密碼之字串的指標。

*nPort*<br/>
識別要在伺服器上使用之 TCP/IP 通訊埠的數位。

### <a name="return-value"></a>傳回值

[CGopherConnection](../../mfc/reference/cgopherconnection-class.md)物件的指標。 如果呼叫失敗, 請檢查擲回的[CInternetException](../../mfc/reference/cinternetexception-class.md)物件來判斷失敗的原因。

### <a name="remarks"></a>備註

`GetGopherConnection`連接到 Gopher 伺服器, 並建立並傳回`CGopherConnection`物件的指標。 它不會在伺服器上執行任何特定的作業。 例如, 如果您想要讀取或寫入資料, 您必須以個別步驟來執行這些作業。 如需搜尋檔案、開啟檔案, 以及讀取或寫入檔案的相關資訊, 請參閱 < 類別[CGopherConnection](../../mfc/reference/cgopherconnection-class.md)、 [CGopherFile](../../mfc/reference/cgopherfile-class.md)和[CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md) 。 如需流覽 FTP 網站的詳細資訊, 請參閱成員函式[OpenURL](#openurl)。 如需執行一般 gopher 連接工作的步驟, 請參閱[使用 WinInet 進行網際網路程式設計](../../mfc/win32-internet-extensions-wininet.md)一文。

## <a name="gethttpconnection"></a>CInternetSession:: GetHttpConnection

呼叫這個成員函式以建立 HTTP 連接, 並取得`CHttpConnection`物件的指標。

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
包含 HTTP 伺服器名稱之字串的指標。

*nPort*<br/>
識別要在伺服器上使用之 TCP/IP 通訊埠的數位。

*pstrUserName*<br/>
包含使用者名稱之字串的指標。

*pstrPassword*<br/>
包含存取密碼之字串的指標。

*dwflags*<br/>
`INTERNET_FLAG_*`旗標的任何組合。 如需*dwFlags*值的說明, 請參閱[CHttpConnection:: OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest)的「**備註**」一節中的表格。

### <a name="return-value"></a>傳回值

[CHttpConnection](../../mfc/reference/chttpconnection-class.md)物件的指標。 如果呼叫失敗, 請檢查擲回的[CInternetException](../../mfc/reference/cinternetexception-class.md)物件來判斷失敗的原因。

### <a name="remarks"></a>備註

`GetHttpConnection`連接至 HTTP 伺服器, 並建立並傳回`CHttpConnection`物件的指標。 它不會在伺服器上執行任何特定的作業。 例如, 如果您想要查詢 HTTP 標頭, 您必須以個別步驟執行此作業。 如需可使用 HTTP 伺服器連接執行之作業的相關資訊, 請參閱 < 類別[CHttpConnection](../../mfc/reference/chttpconnection-class.md)和[CHttpFile](../../mfc/reference/chttpfile-class.md) 。 如需流覽 HTTP 網站的詳細資訊, 請參閱成員函式[OpenURL](#openurl)。 如需執行一般 HTTP 連接工作的步驟, 請參閱[使用 WinInet 進行網際網路程式設計](../../mfc/win32-internet-extensions-wininet.md)一文。

## <a name="onstatuscallback"></a>  CInternetSession::OnStatusCallback

此成員函式會由架構呼叫, 以在啟用狀態回撥和暫止的作業時更新狀態。

```cpp
virtual void OnStatusCallback(
    DWORD_PTR dwContext,
    DWORD dwInternetStatus,
    LPVOID lpvStatusInformation,
    DWORD dwStatusInformationLength);
```

### <a name="parameters"></a>參數

*dwContext*<br/>
應用程式所提供的內容值。

*dwInternetStatus*<br/>
狀態碼, 指出回呼的執行原因。 如需可能值的資料表, 請參閱**備註**。

*lpvStatusInformation*<br/>
緩衝區的指標, 其中包含與此回呼相關的資訊。

*dwStatusInformationLength*<br/>
*LpvStatusInformation*的大小。

### <a name="remarks"></a>備註

您必須先呼叫[EnableStatusCallback](#enablestatuscallback)以利用狀態回呼。

*DwInternetStatus*參數會指出要執行的作業, 並決定*lpvStatusInformation*的內容為何。 *dwStatusInformationLength*指出*lpvStatusInformation*中包含的資料長度。 下列*dwInternetStatus*的狀態值定義如下:

|值|意義|
|-----------|-------------|
|INTERNET_STATUS_RESOLVING_NAME|查閱*lpvStatusInformation*中包含之名稱的 IP 位址。|
|INTERNET_STATUS_NAME_RESOLVED|已成功找到*lpvStatusInformation*中所含名稱的 IP 位址。|
|INTERNET_STATUS_CONNECTING_TO_SERVER|連接到*lpvStatusInformation*所指向的通訊端位址 ([SOCKADDR](/windows/win32/winsock/sockaddr-2))。|
|INTERNET_STATUS_CONNECTED_TO_SERVER|已成功連線到*lpvStatusInformation*所指向的通訊端位址 (SOCKADDR)。|
|INTERNET_STATUS_SENDING_REQUEST|正在將資訊要求傳送至伺服器。 *LpvStatusInformation*參數為 Null。|
|INTERNET_STATUS_ REQUEST_SENT|已成功將資訊要求傳送至伺服器。 *LpvStatusInformation*參數為 Null。|
|INTERNET_STATUS_RECEIVING_RESPONSE|正在等候伺服器回應要求。 *LpvStatusInformation*參數為 Null。|
|INTERNET_STATUS_RESPONSE_RECEIVED|已成功接收來自伺服器的回應。 *LpvStatusInformation*參數為 Null。|
|INTERNET_STATUS_CLOSING_CONNECTION|關閉伺服器的連接。 *LpvStatusInformation*參數為 Null。|
|INTERNET_STATUS_CONNECTION_CLOSED|已成功關閉與伺服器的連接。 *LpvStatusInformation*參數為 Null。|
|INTERNET_STATUS_HANDLE_CREATED|WIN32 API 函式[InternetConnect](/windows/win32/api/wininet/nf-wininet-internetconnectw)用來表示它已建立新的控制碼。 這可讓應用程式從另一個執行緒呼叫 Win32 函數[InternetCloseHandle](/windows/win32/api/wininet/nf-wininet-internetclosehandle) (如果連接花費太長的時間)。 如需這些功能的詳細資訊, 請參閱 Windows SDKfor。|
|INTERNET_STATUS_HANDLE_CLOSING|已成功終止此控制碼值。|

覆寫這個成員函式, 在執行狀態回呼常式之前, 需要採取一些動作。

> [!NOTE]
> 狀態回呼需要執行緒狀態保護。 如果您在共用程式庫中使用 MFC, 請將下列程式程式碼新增至覆寫的開頭:

[!code-cpp[NVC_MFCHtmlHttp#8](../../mfc/reference/codesnippet/cpp/cinternetsession-class_1.cpp)]

如需非同步作業的詳細資訊, 請參閱[網際網路的第一篇步驟:WinInet](../../mfc/wininet-basics.md)。

## <a name="openurl"></a>CInternetSession:: OpenURL

呼叫這個成員函式可將指定的要求傳送至 HTTP 伺服器, 並允許用戶端指定與要求一起傳送的其他 RFC822、MIME 或 HTTP 標頭。

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
要開始讀取之 URL 名稱的指標。 僅支援以 file:、ftp:、gopher: 或 HTTP: 開頭的 Url。 如果*pstrURL*為 Null, 則判斷提示。

*dwContext*<br/>
在回呼中以傳回的控制碼傳遞的應用程式定義值。

*dwFlags*<br/>
描述如何處理此連接的旗標。 如需有效旗標的詳細資訊, 請參閱**備註**。 有效的旗標如下:

- INTERNET_FLAG_TRANSFER_ASCII 預設值。 以 ASCII 文字傳送檔案。

- INTERNET_FLAG_TRANSFER_BINARY 將檔案傳輸為二進位檔案。

- INTERNET_FLAG_RELOAD 從網路取得資料, 即使它是在本機快取的。

- INTERNET_FLAG_DONT_CACHE 不會在本機或任何閘道上快取資料。

- INTERNET_FLAG_SECURE 此旗標僅適用于 HTTP 要求。 它會要求網路上的安全交易, 安全通訊端層或 PCT。

- INTERNET_OPEN_FLAG_USE_EXISTING_CONNECT 可能的話, 針對產生的`OpenUrl`新要求重複使用伺服器的現有連線, 而不是針對每個連線要求建立新的會話。

- 用於 FTP 網站的 INTERNET_FLAG_PASSIVE。 使用被動 FTP 語義。 搭配`OpenURL`的[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)使用。

*pstrHeaders*<br/>
字串的指標, 其中包含要傳送至 HTTP 伺服器的標頭。

*dwHeadersLength*<br/>
其他標頭的長度 (以字元為單位)。 如果此為-1L, 而*pstrHeaders*為非 Null, 則會假設*pstrHeaders*為零終止, 而且長度為。

### <a name="return-value"></a>傳回值

只傳回 FTP、GOPHER、HTTP 和檔案類型網際網路服務的檔案控制代碼。 如果剖析失敗, 則傳回 Null。

傳回的指標`OpenURL`取決於*pstrURL*的服務類型。 下表說明可能的指標`OpenURL`傳回。

|URL 類型|傳回值|
|--------------|-------------|
|file://|`CStdioFile*`|
|http://|`CHttpFile*`|
|gopher://|`CGopherFile*`|
|ftp://|`CInternetFile*`|

### <a name="remarks"></a>備註

參數*dwFlags*必須包括 INTERNET_FLAG_TRANSFER_ASCII 或 INTERNET_FLAG_TRANSFER_BINARY, 但不能同時包含兩者。 其餘的旗標可以與位**or**運算子 ( **&#124;** ) 結合。

`OpenURL`包裝 Win32 `InternetOpenURL`函式的, 只允許從網際網路伺服器下載、抓取和讀取資料。 `OpenURL`不允許在遠端位置上進行檔案操作, 因此不需要任何[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)物件。

若要使用連線特定 (也就是通訊協定特定) 函式 (例如寫入檔案), 您必須開啟會話, 然後開啟特定類型的連接, 然後使用該連接以所需的模式開啟檔案。 如`CInternetConnection`需連接特定功能的詳細資訊, 請參閱。

## <a name="operator_hinternet"></a>CInternetSession:: operator HINTERNET

使用此運算子來取得目前網際網路會話的 Windows 控制碼。

```cpp
operator HINTERNET() const;
```

## <a name="setcookie"></a>  CInternetSession::SetCookie

為指定的 URL 設定 cookie。

```cpp
static BOOL SetCookie(
    LPCTSTR pstrUrl,
    LPCTSTR pstrCookieName,
    LPCTSTR pstrCookieData);
```

### <a name="parameters"></a>參數

*pstrUrl*<br/>
以 null 結束的字串指標, 指定應設定 cookie 的 URL。

*pstrCookieName*<br/>
包含 cookie 名稱之字串的指標。

*pstrCookieData*<br/>
字串的指標, 其中包含要與 URL 建立關聯的實際字串資料。

### <a name="return-value"></a>傳回值

如果成功, 則傳回 TRUE, 否則傳回 FALSE。 若要取得特定的錯誤碼, 請呼叫`GetLastError.`

### <a name="remarks"></a>備註

此成員函式會執行 Win32 message [InternetSetCookie](/windows/win32/api/wininet/nf-wininet-internetsetcookiew)的行為, 如 Windows SDK 中所述。

## <a name="setoption"></a>  CInternetSession::SetOption

呼叫這個成員函式可設定網際網路會話的選項。

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
要設定的網際網路選項。 如需可能的選項清單, 請參閱 Windows SDKfor 中的[選項旗標](/windows/win32/WinInet/option-flags)。

*lpBuffer*<br/>
包含選項設定的緩衝區。

*dwBufferLength*<br/>
*LpBuffer*的長度或*dwValue*的大小。

*dwValue*<br/>
包含選項設定的 DWORD。

*dwFlags*<br/>
表示各種快取選項。 預設值是設定為0。 可能的值包括:

- INTERNET_FLAG_DONT_CACHE 不會快取本機或任何閘道伺服器中的資料。

- INTERNET_FLAG_OFFLINE 下載作業只能透過持續性快取來滿足。 如果專案不存在於快取中, 則會傳回適當的錯誤碼。 這個旗標可以與位**or** ( **&#124;** ) 運算子結合。

### <a name="return-value"></a>傳回值

如果作業成功, 則會傳回 TRUE 值。 如果發生錯誤, 則會傳回 FALSE 值。 如果呼叫失敗, 則可以呼叫 Win32 函數[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)來判斷錯誤的原因。

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CInternetConnection 類別](../../mfc/reference/cinternetconnection-class.md)<br/>
[CHttpConnection 類別](../../mfc/reference/chttpconnection-class.md)<br/>
[CFtpConnection 類別](../../mfc/reference/cftpconnection-class.md)<br/>
[CGopherConnection 類別](../../mfc/reference/cgopherconnection-class.md)
