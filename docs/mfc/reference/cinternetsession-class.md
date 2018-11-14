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
ms.openlocfilehash: 3b820ea3687fd52947eff48e4814ab4173fd95c7
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2018
ms.locfileid: "51519289"
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
|[CInternetSession::Close](#close)|網際網路工作階段終止時，請關閉網際網路連線。|
|[CInternetSession::EnableStatusCallback](#enablestatuscallback)|建立狀態回呼常式。|
|[CInternetSession::GetContext](#getcontext)|網際網路工作階段終止時，請關閉網際網路連線。|
|[CInternetSession::GetCookie](#getcookie)|傳回指定的 URL 和所有其父代 Url 的 cookie。|
|[CInternetSession::GetCookieLength](#getcookielength)|擷取指定的 cookie 儲存在緩衝區長度的變數。|
|[Cinternetsession:: Getftpconnection](#getftpconnection)|開啟伺服器的 FTP 工作階段。 使用者登入。|
|[Getgopherconnection](#getgopherconnection)|開啟應用程式嘗試開啟連線 gopher 伺服器。|
|[Cinternetsession:: Gethttpconnection](#gethttpconnection)|開啟應用程式嘗試開啟連線的 HTTP 伺服器。|
|[CInternetSession::OnStatusCallback](#onstatuscallback)|啟用狀態回呼時更新作業的狀態。|
|[Cinternetsession:: Openurl](#openurl)|剖析，並開啟的 URL。|
|[CInternetSession::SetCookie](#setcookie)|設定指定之 url 的 cookie。|
|[CInternetSession::SetOption](#setoption)|設定網際網路工作階段選項。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CInternetSession::operator HINTERNET](#operator_hinternet)|目前的網際網路工作階段控制代碼。|

## <a name="remarks"></a>備註

如果要維護您的網際網路連線的應用程式的持續時間，您可以建立`CInternetSession`類別的成員[CWinApp](../../mfc/reference/cwinapp-class.md)。

一旦您已建立的網際網路工作階段，您可以呼叫[OpenURL](#openurl)。 `CInternetSession` 然後會剖析 URL，讓您藉由呼叫全域函式[AfxParseURL](internet-url-parsing-globals.md#afxparseurl)。 不論通訊協定類型，為何`CInternetSession`解譯 URL，並為您管理它。 它可以處理 URL 資源"file:// 與識別的本機檔案的要求。 `OpenURL` 將傳回的指標[CStdioFile](../../mfc/reference/cstdiofile-class.md)如果名稱傳遞給它的物件是本機檔案。

如果您開啟網際網路伺服器使用 URL `OpenURL`，讀取站台的資訊。 如果您想要在位於伺服器上的檔案上執行特定服務 （適用於範例、 HTTP、 FTP 或 gopher） 動作，您必須建立與該伺服器適當的連接。 若要開啟特定種類的直接連線至特定的服務，請使用下列成員函式的其中一個：

- [GetGopherConnection](#getgopherconnection)開啟 gopher 服務的連接。

- [GetHttpConnection](#gethttpconnection)開啟至 HTTP 服務的連接。

- [GetFtpConnection](#getftpconnection)開啟連線到 FTP 服務。

[SetOption](#setoption)可讓您設定您的工作階段，例如逾時值，重試次數的查詢選項等等。

`CInternetSession` 成員函式[SetCookie](#setcookie)， [GetCookie](#getcookie)，並[GetCookieLength](#getcookielength)提供方法來管理透過此伺服器和指令碼維護的 Win32 cookie 資料庫用戶端工作站的狀態資訊。

如需有關基本網際網路程式設計工作的詳細資訊，請參閱[網際網路前幾個步驟： WinInet](../../mfc/wininet-basics.md)。 如需使用 MFC WinInet 類別的一般資訊，請參閱文章[網際網路程式設計 WinInet](../../mfc/win32-internet-extensions-wininet.md)。

> [!NOTE]
> `CInternetSession` 將會擲回[AfxThrowNotSupportedException](exception-processing.md#afxthrownotsupportedexception)不支援的服務類型。 目前支援以下服務類型： FTP、 HTTP、 gopher 和檔案。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;`CInternetSession`

## <a name="requirements"></a>需求

**標頭：** afxinet.h

## <a name="cinternetsession"></a> CInternetSession::CInternetSession

此成員函式時，會呼叫`CInternetSession`建立物件。

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
識別的應用程式或呼叫網際網路函式 （例如，「 Microsoft 網際網路瀏覽器 」） 的實體名稱的字串指標。 如果*pstrAgent*是 NULL （預設值），這個架構會呼叫全域函式[AfxGetAppName](application-information-and-management.md#afxgetappname)，它會傳回 null 終止的字串，包含應用程式的名稱。 某些通訊協定會使用此字串來識別您的應用程式到伺服器。

*dwContext*<br/>
作業的內容識別碼。 *dwContext*識別傳回作業的狀態資訊[CInternetSession::OnStatusCallback](#onstatuscallback)。 預設值設為 1。不過，您可以明確指派作業的特定內容識別碼。 物件，而且它沒有任何工作將會與該內容識別碼相關聯

*dwAccessType*<br/>
所需的存取類型。 以下是有效的值，可能會提供其中之一：

- INTERNET_OPEN_TYPE_PRECONFIG 連接使用預先設定的登錄中的設定。 此存取類型設定為預設值。 若要透過 TIS proxy 連線，將*dwAccessType*為此值; 您再登錄適當地設定。

- INTERNET_OPEN_TYPE_DIRECT 直接連線到網際網路。

- INTERNET_OPEN_TYPE_PROXY 透過 CERN proxy 連線。

如需使用不同類型 proxy 的連接資訊，請參閱[典型的 FTP 用戶端應用程式中的步驟](../../mfc/steps-in-a-typical-ftp-client-application.md)。

*pstrProxyName*<br/>
慣用的 CERN proxy 的名稱如果*dwAccessType*設成 INTERNET_OPEN_TYPE_PROXY。 預設值是 NULL。

*pstrProxyBypass*<br/>
包含選擇性的伺服器位址清單的字串指標。 使用 proxy 的存取時，可能會略過這些位址。 如果提供 NULL 值，則會從登錄讀取略過清單。 此參數才有意義才*dwAccessType*設 INTERNET_OPEN_TYPE_PROXY。

*dwFlags*<br/>
表示各種快取選項。 預設值是設定為 0。 可能值包括：

- 在本機或在任何閘道伺服器，請 INTERNET_FLAG_DONT_CACHE 不要快取的資料。

- 透過持續性的快取滿足 INTERNET_FLAG_OFFLINE 下載作業。 如果項目不存在於快取中，會傳回適當的錯誤碼。 這個旗標可能會結合使用位元**或是**( **&#124;**) 運算子。

### <a name="remarks"></a>備註

`CInternetSession` 第一個網際網路函式會呼叫應用程式。 它會初始化內部資料結構，並準備進行後續的呼叫，從應用程式。

如果可以開啟沒有網際網路連線，請`CInternetSession`會擲回[AfxThrowInternetException](internet-url-parsing-globals.md#afxthrowinternetexception)。

### <a name="example"></a>範例

範例，請參閱[CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)。

## <a name="close"></a>  CInternetSession::Close

呼叫此成員函式，您的應用程式使用完畢`CInternetSession`物件。

```cpp
virtual void Close();
```

### <a name="example"></a>範例

範例，請參閱[CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)。

## <a name="enablestatuscallback"></a>  CInternetSession::EnableStatusCallback

呼叫此成員函式，若要啟用狀態回呼。

```cpp
BOOL EnableStatusCallback(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>參數

*bEnable*<br/>
指定是否啟用或停用回撥。 預設值為 TRUE。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。 如果呼叫失敗，判斷失敗的原因，藉由檢查擲回[CInternetException](../../mfc/reference/cinternetexception-class.md)物件。

### <a name="remarks"></a>備註

處理時狀態回撥，您可以在應用程式的 [狀態] 列中提供有關 （例如名稱解析、 連接到伺服器，並依此類推） 作業的進度狀態。 顯示作業狀態是特別需要長期作業期間。

在 要求處理期間發生的回呼，因為應用程式應該最少的時間，盡可能在回呼中，以防止網路的資料輸送量降低。 比方說，將出現一個對話方塊，在回呼中，可能是這類長時間作業的伺服器會終止要求。

無法移除狀態回撥，只要任何回呼會暫止。

若要以非同步方式處理任何作業，您必須建立自己的執行緒，或使用不以 MFC WinInet 函式。

## <a name="getcontext"></a>  CInternetSession::GetContext

呼叫此成員函式，若要取得特定的應用程式工作階段內容值。

```cpp
DWORD_PTR GetContext() const;
```

### <a name="return-value"></a>傳回值

應用程式定義的內容識別項。

### <a name="remarks"></a>備註

[OnStatusCallback](#onstatuscallback)所傳回的內容識別碼的用法`GetContext`報告特定的應用程式的狀態。 例如，使用者啟動牽涉到傳回狀態資訊的網際網路要求，狀態回呼就會使用報告狀態的內容識別碼針對該特定的要求。 如果使用者啟動兩個不同網際網路要求兩者都涉及傳回狀態資訊`OnStatusCallback`使用內容識別項，傳回有關其相對應的要求的狀態。 因此，內容識別碼使用於所有的狀態回呼作業，而相關聯的工作階段，直到工作階段結束為止。

如需有關非同步作業的詳細資訊，請參閱文章[網際網路前幾個步驟： WinInet](../../mfc/wininet-basics.md)。

## <a name="getcookie"></a>  CInternetSession::GetCookie

此成員函式實作的 Win32 函式行為[InternetGetCookie](/windows/desktop/api/wininet/nf-wininet-internetgetcookiea)、 Windows SDK 中所述。

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
字串，包含 URL 的指標。

*pstrCookieName*<br/>
包含要取得指定之 url 的 cookie 名稱的字串指標。

*pstrCookieData*<br/>
在第一個多載中，字串，包含接收的 cookie 資料緩衝區的位址指標。 這個值可以是 NULL。 在第二個多載的參考[CString](../../atl-mfc-shared/reference/cstringt-class.md)接收的 cookie 資料的物件。

*dwBufLen*<br/>
指定大小的變數*pstrCookieData*緩衝區。 如果函式成功時，緩衝區會接收複製到的資料量*pstrCookieData*緩衝區。 如果*pstrCookieData*是 NULL，此參數會接收值，指定要複製所有 cookie 資料所需的緩衝區大小。

### <a name="return-value"></a>傳回值

否則傳回如果成功，則為 TRUE 或 FALSE。 如果呼叫失敗，會呼叫 Win32 函式[GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360)來判斷錯誤的原因。 適用於下列的錯誤值：

- ERROR_NO_MORE_ITEMS 是指定之 url 的任何 cookie 和所有其父代。

- 傳入的值 ERROR_INSUFFICIENT_BUFFER *dwBufLen*不足以複製所有 cookie 資料。 中傳回的值*dwBufLen*所取得的所有資料緩衝區的大小。

### <a name="remarks"></a>備註

在第二個多載中，MFC，請擷取到所提供的 cookie 資料`CString`物件。

## <a name="getcookielength"></a>  CInternetSession::GetCookieLength

呼叫此成員函式，以取得 cookie 儲存在緩衝區的長度。

```cpp
static DWORD GetCookieLength(
    LPCTSTR pstrUrl,
    LPCTSTR pstrCookieName);
```

### <a name="parameters"></a>參數

*pstrUrl*<br/>
字串，包含 URL 的指標

*pstrCookieName*<br/>
包含 cookie 名稱的字串指標。

### <a name="return-value"></a>傳回值

DWORD 值，指出 cookie，長度會儲存在緩衝區中。 如果沒有 cookie 零名稱所指示*pstrCookieName*存在。

### <a name="remarks"></a>備註

這個值由[GetCookie](#getcookie)。

## <a name="getftpconnection"></a>  Cinternetsession:: Getftpconnection

呼叫此成員函式，以建立 FTP 連線，並取得的指標`CFtpConnection`物件。

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
包含 FTP 伺服器名稱的字串指標。

*pstrUserName*<br/>
以 null 終止的字串，指定要登入的使用者名稱的指標。 如果是 NULL，則預設會為匿名。

*pstrPassword*<br/>
以 null 終止的字串，指定要用來登入密碼的指標。 如果兩個*pstrPassword*並*pstrUserName*為 NULL 時，預設匿名密碼是使用者的電子郵件名稱。 如果*pstrPassword*是 NULL （或空字串），但*pstrUserName*不是 NULL，則使用空白密碼。 下表描述的四個可能的設定行為*pstrUserName*並*pstrPassword*:

| *pstrUserName*  | *pstrPassword*  | 傳送至 FTP 伺服器的使用者名稱 | 傳送至 FTP 伺服器的密碼 |
|-----------------|-----------------|-----------------------------|-----------------------------|
|   NULL 或""   |   NULL 或""   |         「 匿名 」         |      使用者的電子郵件名稱      |
| 非 NULL 字串 |   NULL 或""   |       *pstrUserName*        |             " "             |
|      NULL       | 非 NULL 字串 |            ERROR            |            ERROR            |
| 非 NULL 字串 | 非 NULL 字串 |       *pstrUserName*        |       *pstrPassword*        |

*nPort*<br/>
識別要使用的伺服器上的 TCP/IP 連接埠的數字。

*bPassive*<br/>
指定此 FTP 工作階段的被動還是主動模式。 如果設為 TRUE，會將 Win32 API `dwFlag` INTERNET_FLAG_PASSIVE 到。

### <a name="return-value"></a>傳回值

指標[CFtpConnection](../../mfc/reference/cftpconnection-class.md)物件。 如果呼叫失敗，判斷失敗的原因，藉由檢查擲回[CInternetException](../../mfc/reference/cinternetexception-class.md)物件。

### <a name="remarks"></a>備註

`GetFtpConnection` 連接到 FTP 伺服器，並會建立並將指標傳回至`CFTPConnection`物件。 它不會執行任何伺服器上的特定作業。 如果您想要讀取或寫入檔案，比方說，您就必須執行這些作業分開的步驟。 請參閱類別[CFtpConnection](../../mfc/reference/cftpconnection-class.md)並[CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)有關搜尋檔案，開啟檔案，並讀取或寫入檔案。 請參閱文章[網際網路程式設計 WinInet](../../mfc/win32-internet-extensions-wininet.md)中執行一般的 FTP 連線工作的步驟。

### <a name="example"></a>範例

範例，請參閱[CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)。

## <a name="getgopherconnection"></a>  Getgopherconnection

呼叫此成員函式，以建立新的 gopher 連線並取得的指標`CGopherConnection`物件。

```cpp
CGopherConnection* GetGopherConnection(
    LPCTSTR pstrServer,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER);
```

### <a name="parameters"></a>參數

*pstrServer*<br/>
包含 gopher 伺服器名稱的字串指標。

*pstrUserName*<br/>
包含使用者名稱的字串指標。

*pstrPassword*<br/>
包含的存取密碼的字串指標。

*nPort*<br/>
識別要使用的伺服器上的 TCP/IP 連接埠的數字。

### <a name="return-value"></a>傳回值

指標[CGopherConnection](../../mfc/reference/cgopherconnection-class.md)物件。 如果呼叫失敗，判斷失敗的原因，藉由檢查擲回[CInternetException](../../mfc/reference/cinternetexception-class.md)物件。

### <a name="remarks"></a>備註

`GetGopherConnection` 連線至 gopher 伺服器，並會建立並將指標傳回至`CGopherConnection`物件。 它不會執行任何伺服器上的特定作業。 如果您想要讀取或寫入資料，例如，您就必須執行這些作業分開的步驟。 請參閱類別[CGopherConnection](../../mfc/reference/cgopherconnection-class.md)， [CGopherFile](../../mfc/reference/cgopherfile-class.md)，並[CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md)有關搜尋檔案，開啟檔案，並讀取或寫入檔案。 如需瀏覽 FTP 站台資訊，請參閱成員函式[OpenURL](#openurl)。 請參閱文章[網際網路程式設計 WinInet](../../mfc/win32-internet-extensions-wininet.md)中執行一般 gopher 連接工作的步驟。

## <a name="gethttpconnection"></a>  Cinternetsession:: Gethttpconnection

呼叫此成員函式，以建立 HTTP 連線，並取得的指標`CHttpConnection`物件。

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
包含 HTTP 伺服器名稱的字串指標。

*nPort*<br/>
識別要使用的伺服器上的 TCP/IP 連接埠的數字。

*pstrUserName*<br/>
包含使用者名稱的字串指標。

*pstrPassword*<br/>
包含的存取密碼的字串指標。

*dwflags*<br/>
任何組合`INTERNET_FLAG_*`旗標。 請參閱表格**備註**一節[chttpconnection::](../../mfc/reference/chttpconnection-class.md#openrequest)的說明*dwFlags*值。

### <a name="return-value"></a>傳回值

指標[CHttpConnection](../../mfc/reference/chttpconnection-class.md)物件。 如果呼叫失敗，判斷失敗的原因，藉由檢查擲回[CInternetException](../../mfc/reference/cinternetexception-class.md)物件。

### <a name="remarks"></a>備註

`GetHttpConnection` 連接至 HTTP 伺服器，並會建立並將指標傳回至`CHttpConnection`物件。 它不會執行任何伺服器上的特定作業。 如果您想要查詢 HTTP 標頭，例如，您必須執行此作業，以個別步驟。 請參閱類別[CHttpConnection](../../mfc/reference/chttpconnection-class.md)並[CHttpFile](../../mfc/reference/chttpfile-class.md)您可以使用 HTTP 伺服器的連接執行作業的相關資訊。 如需瀏覽 HTTP 站台資訊，請參閱成員函式[OpenURL](#openurl)。 請參閱文章[網際網路程式設計 WinInet](../../mfc/win32-internet-extensions-wininet.md)中執行一般的 HTTP 連接工作的步驟。

## <a name="onstatuscallback"></a>  CInternetSession::OnStatusCallback

啟用狀態回呼，而且作業已暫止時，更新狀態，架構會呼叫此成員函式。

```cpp
virtual void OnStatusCallback(
    DWORD_PTR dwContext,
    DWORD dwInternetStatus,
    LPVOID lpvStatusInformation,
    DWORD dwStatusInformationLength);
```

### <a name="parameters"></a>參數

*dwContext*<br/>
提供應用程式的內容值。

*dwInternetStatus*<br/>
狀態碼指出為什麼要進行回呼。 請參閱**備註**可能值的資料表。

*lpvStatusInformation*<br/>
包含有關此回呼之緩衝區的指標。

*dwStatusInformationLength*<br/>
大小*lpvStatusInformation*。

### <a name="remarks"></a>備註

您必須先呼叫[EnableStatusCallback](#enablestatuscallback)善用狀態回撥。

*DwInternetStatus*參數指出正在執行的作業，並判斷哪些內容*lpvStatusInformation*會。 *dwStatusInformationLength*指出中包含的資料長度*lpvStatusInformation*。 下列狀態的值*dwInternetStatus*定義如下：

|值|意義|
|-----------|-------------|
|INTERNET_STATUS_RESOLVING_NAME|查閱中所包含的名稱的 IP 位址*lpvStatusInformation*。|
|INTERNET_STATUS_NAME_RESOLVED|已成功找到名稱中包含的 IP 位址*lpvStatusInformation*。|
|INTERNET_STATUS_CONNECTING_TO_SERVER|連接到通訊端位址 ([SOCKADDR](../../mfc/reference/sockaddr-structure.md)) 所指*lpvStatusInformation*。|
|INTERNET_STATUS_CONNECTED_TO_SERVER|已成功連線到通訊端位址 (SOCKADDR)，指向*lpvStatusInformation*。|
|INTERNET_STATUS_SENDING_REQUEST|資訊要求傳送至伺服器。 *LpvStatusInformation*參數為 NULL。|
|INTERNET_STATUS_ REQUEST_SENT|已成功傳送至伺服器的資訊要求。 *LpvStatusInformation*參數為 NULL。|
|INTERNET_STATUS_RECEIVING_RESPONSE|等候伺服器回應要求。 *LpvStatusInformation*參數為 NULL。|
|INTERNET_STATUS_RESPONSE_RECEIVED|已成功從伺服器收到的回應。 *LpvStatusInformation*參數為 NULL。|
|INTERNET_STATUS_CLOSING_CONNECTION|正在關閉伺服器的連線。 *LpvStatusInformation*參數為 NULL。|
|INTERNET_STATUS_CONNECTION_CLOSED|已成功關閉連線到伺服器。 *LpvStatusInformation*參數為 NULL。|
|INTERNET_STATUS_HANDLE_CREATED|使用 Win32 API 函式[InternetConnect](/windows/desktop/api/wininet/nf-wininet-internetconnecta)來指出它已建立新的控制代碼。 這可讓應用程式呼叫 Win32 函式[InternetCloseHandle](/windows/desktop/api/wininet/nf-wininet-internetclosehandle)從另一個執行緒，如果連接的時間太長。 查看 Windows SDKfor 這些函式的詳細資訊。|
|INTERNET_STATUS_HANDLE_CLOSING|已成功終止此控制代碼值。|

覆寫這個成員函式會在執行狀態回呼常式之前，需要某些動作。

> [!NOTE]
> 狀態回呼需要執行緒狀態 」 保護。 如果您使用 MFC 的共用程式庫中，請覆寫的開頭新增下行：

[!code-cpp[NVC_MFCHtmlHttp#8](../../mfc/reference/codesnippet/cpp/cinternetsession-class_1.cpp)]

如需有關非同步作業的詳細資訊，請參閱文章[網際網路前幾個步驟： WinInet](../../mfc/wininet-basics.md)。

## <a name="openurl"></a>  Cinternetsession:: Openurl

呼叫此成員函式將指定的要求傳送至 HTTP 伺服器，並允許用戶端指定其他的 RFC822 MIME 或 HTTP 標頭，連同要求一起傳送。

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
若要開始讀取 URL 的名稱指標。 只有 Url 開頭為檔案:、 ftp:，gopher:，或 http： 支援。 如果判斷提示*pstrURL*是 NULL。

*dwContext*<br/>
應用程式定義的值會隨在回呼中傳回的控制代碼。

*dwFlags*<br/>
描述如何處理此連線的旗標。 請參閱**備註**如需有效的旗標。 有效的旗標如下：

- INTERNET_FLAG_TRANSFER_ASCII 預設值。 將檔案傳送為 ASCII 文字。

- INTERNET_FLAG_TRANSFER_BINARY 傳輸將檔案當作二進位檔案。

- INTERNET_FLAG_RELOAD 從網路取得的資料，即使在本機快取。

- 在本機或在任何閘道，請 INTERNET_FLAG_DONT_CACHE 不要快取的資料。

- INTERNET_FLAG_SECURE 這個旗標適用於僅限 HTTP 要求。 它會要求使用安全通訊端層或 PCT 在網路上安全的交易

- INTERNET_OPEN_FLAG_USE_EXISTING_CONNECT 如果可能的話，請重複使用現有的連線至伺服器，以產生新的要求`OpenUrl`而不是建立新的工作階段，針對每個連接要求。

- INTERNET_FLAG_PASSIVE 用於 FTP 站台。 使用被動 FTP 語意。 搭配[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)的`OpenURL`。

*pstrHeaders*<br/>
包含要傳送至 HTTP 伺服器的標頭的字串指標。

*dwHeadersLength*<br/>
以字元為單位，其他的標頭的長度。 如果這是為-1l 並*pstrHeaders*是不是 NULL，則*pstrHeaders*會假設為零結束，而且長度會計算。

### <a name="return-value"></a>傳回值

傳回 FTP、 GOPHER、 HTTP 和檔案類型的網際網路服務之檔案控制代碼。 如果剖析成功，則傳回 NULL。

指標，`OpenURL`傳回而定*pstrURL*的服務類型。 下表說明可能的指標`OpenURL`可以傳回。

|URL 類型|Returns|
|--------------|-------------|
|file://|`CStdioFile*`|
|http://|`CHttpFile*`|
|gopher://|`CGopherFile*`|
|ftp: / /|`CInternetFile*`|

### <a name="remarks"></a>備註

參數*dwFlags* INTERNET_FLAG_TRANSFER_ASCII 或 INTERNET_FLAG_TRANSFER_BINARY，但不是能兩者都必須包含。 剩餘的旗標可以與位元結合**或是**運算子 ( **&#124;**)。

`OpenURL`其中包裝 Win32 函式`InternetOpenURL`，允許只下載、 擷取和讀取網際網路伺服器中的資料。 `OpenURL` 可讓遠端位置上的沒有檔案操作，因此需要無[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)物件。

若要使用連線特有 (也就是特定通訊協定) 函式，例如寫入檔案時，您必須開啟工作階段，然後開啟特定類型的連線，然後使用該連線所需的模式中開啟檔案。 請參閱`CInternetConnection`如需有關連接特有的函式。

## <a name="operator_hinternet"></a>  CInternetSession::operator HINTERNET

您可以使用這個運算子來取得目前的網際網路工作階段的 Windows 控制代碼。

```cpp
operator HINTERNET() const;
```

## <a name="setcookie"></a>  CInternetSession::SetCookie

設定指定之 url 的 cookie。

```cpp
static BOOL SetCookie(
    LPCTSTR pstrUrl,
    LPCTSTR pstrCookieName,
    LPCTSTR pstrCookieData);
```

### <a name="parameters"></a>參數

*pstrUrl*<br/>
以 null 終止的字串，指定的 URL 應該設定 cookie 的指標。

*pstrCookieName*<br/>
包含 cookie 名稱的字串指標。

*pstrCookieData*<br/>
字串，包含 URL 相關聯的實際的字串資料指標。

### <a name="return-value"></a>傳回值

否則傳回如果成功，則為 TRUE 或 FALSE。 若要取得特定的錯誤碼，請呼叫 `GetLastError.`

### <a name="remarks"></a>備註

此成員函式實作的 Win32 訊息的行為[InternetSetCookie](/windows/desktop/api/wininet/nf-wininet-internetsetcookiea)、 Windows SDK 中所述。

## <a name="setoption"></a>  CInternetSession::SetOption

呼叫此成員函式，若要設定網際網路工作階段選項。

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
若要設定的 [網際網路] 選項。 請參閱[選項旗標](/windows/desktop/WinInet/option-flags)Windows SDKfor 可能選項的清單中。

*lpBuffer*<br/>
這種緩衝區包含選項的設定。

*dwBufferLength*<br/>
長度*lpBuffer*或大小*dwValue*。

*dwValue*<br/>
DWORD，其中包含的選項設定。

*dwFlags*<br/>
表示各種快取選項。 預設值是設定為 0。 可能值包括：

- 在本機或在任何閘道伺服器，請 INTERNET_FLAG_DONT_CACHE 不要快取的資料。

- 透過持續性的快取滿足 INTERNET_FLAG_OFFLINE 下載作業。 如果項目不存在於快取中，會傳回適當的錯誤碼。 這個旗標可能會結合使用位元**或是**( **&#124;**) 運算子。

### <a name="return-value"></a>傳回值

如果作業成功，則會傳回 TRUE 值。 如果發生錯誤，則會傳回 FALSE 值。 如果呼叫失敗，Win32 函式[GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360)可能會呼叫以判斷錯誤的原因。

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CInternetConnection 類別](../../mfc/reference/cinternetconnection-class.md)<br/>
[CHttpConnection 類別](../../mfc/reference/chttpconnection-class.md)<br/>
[CFtpConnection 類別](../../mfc/reference/cftpconnection-class.md)<br/>
[CGopherConnection 類別](../../mfc/reference/cgopherconnection-class.md)
