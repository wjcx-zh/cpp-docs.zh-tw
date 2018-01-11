---
title: "CInternetSession 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
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
caps.latest.revision: "25"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e7aad2f6ce26fd5ca9ed0ec323a8fcb05ac17f7c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cinternetsession-class"></a>CInternetSession 類別
建立和初始化單一或多個同時網際網路工作階段，並視需要描述您與 Proxy 伺服器的連接。  
  
## <a name="syntax"></a>語法  
  
```  
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
|[CInternetSession::Close](#close)|網際網路工作階段結束時，關閉網際網路連線。|  
|[CInternetSession::EnableStatusCallback](#enablestatuscallback)|建立狀態回呼常式。|  
|[CInternetSession::GetContext](#getcontext)|網際網路工作階段結束時，關閉網際網路連線。|  
|[CInternetSession::GetCookie](#getcookie)|傳回指定的 URL 和所有其父代 Url 的 cookie。|  
|[CInternetSession::GetCookieLength](#getcookielength)|擷取指定的 cookie 儲存在緩衝區長度的變數。|  
|[Cinternetsession:: Getftpconnection](#getftpconnection)|開啟與伺服器的 FTP 工作階段。 使用者登入。|  
|[CInternetSession::GetGopherConnection](#getgopherconnection)|會開啟嘗試開啟連接的應用程式在 gopher 伺服器。|  
|[CInternetSession::GetHttpConnection](#gethttpconnection)|會開啟 HTTP 伺服器正在嘗試開啟連接的應用程式。|  
|[CInternetSession::OnStatusCallback](#onstatuscallback)|啟用狀態回呼時更新作業的狀態。|  
|[Cinternetsession:: Openurl](#openurl)|剖析，並開啟 URL。|  
|[CInternetSession::SetCookie](#setcookie)|設定指定之 url 的 cookie。|  
|[CInternetSession::SetOption](#setoption)|設定網際網路工作階段選項。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CInternetSession::operator HINTERNET](#operator_hinternet)|目前的網際網路工作階段控制代碼。|  
  
## <a name="remarks"></a>備註  
 如果您的網際網路連線必須維護期間的應用程式，您可以建立`CInternetSession`類別成員[CWinApp](../../mfc/reference/cwinapp-class.md)。  
  
 一旦您已建立的網際網路工作階段，您可以呼叫[OpenURL](#openurl)。 `CInternetSession`然後會剖析 URL，讓您藉由呼叫全域函式[AfxParseURL](internet-url-parsing-globals.md#afxparseurl)。 其通訊協定類型，不論`CInternetSession`解譯 URL，並會為您管理它。 它可以處理要求的 URL 資源"file:// 與識別的本機檔案。 `OpenURL`將傳回的指標[Cgopherfile](../../mfc/reference/cstdiofile-class.md)物件名稱您傳遞給它，如果是本機檔案。  
  
 如果您開啟上網際網路伺服器使用的 URL `OpenURL`，您可以從站台讀取資訊。 如果您想要在伺服器上的檔案上執行特定服務 （如 HTTP、 FTP 或 gopher） 動作，您必須建立與該伺服器的適當連線。 若要開啟特定種類的連接直接連接至特定的服務，請使用下列成員函式的其中一個：  
  
- [GetGopherConnection](#getgopherconnection)開啟 gopher 服務的連線。  
  
- [GetHttpConnection](#gethttpconnection)開啟至 HTTP 服務的連接。  
  
- [GetFtpConnection](#getftpconnection)開啟 FTP 服務的連線。  
  
 [SetOption](#setoption)可讓您設定您的工作階段，例如逾時值，重試，次數的查詢選項等等。  
  
 `CInternetSession`成員函式[SetCookie](#setcookie)， [GetCookie](#getcookie)，和[GetCookieLength](#getcookielength)提供管理透過此伺服器和指令碼維護的 Win32 cookie 資料庫的方法用戶端工作站的狀態資訊。  
  
 如需基本網際網路程式設計工作的詳細資訊，請參閱文章[網際網路第一個步驟： WinInet](../../mfc/wininet-basics.md)。 如需使用 MFC WinInet 類別的一般資訊，請參閱文章[網際網路程式設計 WinInet](../../mfc/win32-internet-extensions-wininet.md)。  
  
> [!NOTE]
> `CInternetSession`將會擲回[AfxThrowNotSupportedException](exception-processing.md#afxthrownotsupportedexception)不支援的服務類型。 目前支援下列服務類型： FTP、 HTTP、 gopher 和檔案。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CInternetSession`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxinet.h  
  
##  <a name="cinternetsession"></a>CInternetSession::CInternetSession  
 此成員函式時，會呼叫`CInternetSession`建立物件。  
  
```  
CInternetSession(
    LPCTSTR pstrAgent = NULL,  
    DWORD_PTR dwContext = 1,  
    DWORD dwAccessType = PRE_CONFIG_INTERNET_ACCESS,  
    LPCTSTR pstrProxyName = NULL,  
    LPCTSTR pstrProxyBypass = NULL,  
    DWORD dwFlags = 0);
```  
  
### <a name="parameters"></a>參數  
 `pstrAgent`  
 識別的實體呼叫網際網路函式 （例如，"Microsoft 網際網路瀏覽器 」） 的應用程式名稱的字串指標。 如果`pstrAgent`是**NULL** （預設值），架構會呼叫全域函式[AfxGetAppName](application-information-and-management.md#afxgetappname)，它會傳回 null 結束的字串，包含應用程式的名稱。 某些通訊協定會使用這個字串，識別您的應用程式伺服器。  
  
 `dwContext`  
 作業的內容識別碼。 `dwContext`識別作業的狀態資訊傳回[CInternetSession::OnStatusCallback](#onstatuscallback)。 預設是設為 1。不過，您可以明確指派作業的特定內容識別碼。 物件，且任何工作，它會將相關聯的內容識別碼。  
  
 `dwAccessType`  
 所需的存取類型。 以下是有效的值，可能需要提供其中之一：  
  
- **INTERNET_OPEN_TYPE_PRECONFIG**連接在登錄中使用預先設定的設定。 此存取類型會設為預設值。 若要透過 TIS proxy 連線，將`dwAccessType`為此值; 您再登錄適當地設定。  
  
- `INTERNET_OPEN_TYPE_DIRECT`直接連線到網際網路。  
  
- `INTERNET_OPEN_TYPE_PROXY`透過 CERN proxy 的連線。  
  
 如需使用不同類型 proxy 的連接資訊，請參閱[一般 FTP 用戶端應用程式中的步驟](../../mfc/steps-in-a-typical-ftp-client-application.md)。  
  
 *pstrProxyName*  
 慣用 CERN proxy 名稱如果`dwAccessType`設為`INTERNET_OPEN_TYPE_PROXY`。 預設值是**NULL**。  
  
 *pstrProxyBypass*  
 包含選擇性的伺服器位址清單的字串指標。 使用 proxy 的存取時，可能會略過這些位址。 如果**NULL**提供值時，會從登錄讀取略過清單。 這個參數是有意義才`dwAccessType`設`INTERNET_OPEN_TYPE_PROXY`。  
  
 `dwFlags`  
 表示各種快取選項。 預設值是設為 0。 可能的值包括：  
  
- `INTERNET_FLAG_DONT_CACHE`不會快取資料，在本機或任何閘道伺服器。  
  
- `INTERNET_FLAG_OFFLINE`下載作業透過持續性的快取沒有問題。 如果項目不存在於快取中，會傳回適當的錯誤程式碼。 這個旗標可能會合併使用位元`OR`( **&#124;**) 運算子。  
  
### <a name="remarks"></a>備註  
 **CInternetSession**是在應用程式呼叫的第一個網際網路函式。 它會初始化內部資料結構，並準備進行後續的呼叫，從應用程式。  
  
 如果可以開啟沒有網際網路連線，`CInternetSession`會擲回[AfxThrowInternetException](internet-url-parsing-globals.md#afxthrowinternetexception)。  
  
### <a name="example"></a>範例  
  請參閱範例的[CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)。  
  
##  <a name="close"></a>CInternetSession::Close  
 呼叫此成員函式，當您的應用程式已經完成使用`CInternetSession`物件。  
  
```  
virtual void Close();
```  
  
### <a name="example"></a>範例  
  請參閱範例的[CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)。  
  
##  <a name="enablestatuscallback"></a>CInternetSession::EnableStatusCallback  
 呼叫此成員函式可啟用狀態回呼。  
  
```  
BOOL EnableStatusCallback(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `bEnable`  
 指定回呼是否要啟用或停用。 預設值是**TRUE**。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。 如果呼叫失敗，判斷失敗的原因擲回[CInternetException](../../mfc/reference/cinternetexception-class.md)物件。  
  
### <a name="remarks"></a>備註  
 當處理狀態回呼，您可以提供有關 （例如，名稱解析，以連接到伺服器，依此類推） 作業的進度狀態在應用程式的狀態列中。 顯示作業狀態是特別合理長期作業期間的。  
  
 因為回呼會在要求處理期間，應用程式應該花費中用來防止網路的資料輸送量降低的回呼，盡可能少的時間。 例如，放在回呼中的對話方塊可能是這類長時間作業伺服器終止要求。  
  
 無法移除狀態回撥，只要任何回呼為擱置中。  
  
 若要以非同步方式處理任何作業，您必須建立自己的執行緒，或使用 MFC WinInet 函式。  
  
##  <a name="getcontext"></a>CInternetSession::GetContext  
 呼叫此成員函式可取得特定的應用程式工作階段內容值。  
  
```  
DWORD_PTR GetContext() const;  
```  
  
### <a name="return-value"></a>傳回值  
 應用程式定義的內容識別項。  
  
### <a name="remarks"></a>備註  
 [OnStatusCallback](#onstatuscallback)所傳回的內容識別碼的用法**GetContext**報告特定的應用程式的狀態。 例如，使用者啟動牽涉到傳回狀態資訊的網際網路要求，狀態回呼就會使用報告狀態的內容識別碼上該特定要求。 如果在使用者啟動兩個不同網際網路要求兩者都涉及傳回狀態資訊`OnStatusCallback`使用內容識別項，會傳回有關其相對應的要求的狀態。 因此，內容識別項用於所有回呼作業狀態，而且相關聯的工作階段，直到該工作階段結束為止。  
  
 如需有關非同步作業的詳細資訊，請參閱文章[網際網路第一個步驟： WinInet](../../mfc/wininet-basics.md)。  
  
##  <a name="getcookie"></a>CInternetSession::GetCookie  
 此成員函式實作的 Win32 函式的行為[InternetGetCookie](http://msdn.microsoft.com/library/windows/desktop/aa384710)、 Windows SDK 中所述。  
  
```  
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
 `pstrUrl`  
 包含 URL 的字串指標。  
  
 `pstrCookieName`  
 包含要取得指定之 url 的 cookie 名稱的字串指標。  
  
 `pstrCookieData`  
 在第一個多載中，字串，包含接收的 cookie 資料緩衝區的位址指標。 這個值可以是**NULL**。 在第二個多載的參考[CString](../../atl-mfc-shared/reference/cstringt-class.md)来接收的 cookie 資料物件。  
  
 `dwBufLen`  
 指定大小的變數`pstrCookieData`緩衝區。 如果函式成功時，緩衝區會接收的資料複製到量`pstrCookieData`緩衝區。 如果`pstrCookieData`是**NULL**，這個參數會接收值，指定要複製的所有 cookie 資料所需的緩衝區大小。  
  
### <a name="return-value"></a>傳回值  
 傳回**TRUE**如果成功，或**FALSE**否則。 如果呼叫失敗，會呼叫 Win32 函式[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)以判斷錯誤的原因。 適用於下列的錯誤值：  
  
- **ERROR_NO_MORE_ITEMS**沒有指定之 url 的任何 cookie，而且所有其父系。  
  
- **ERROR_INSUFFICIENT_BUFFER**傳入的值`dwBufLen`不足，無法複製所有的 cookie 資料。 中傳回的值`dwBufLen`才能取得所有資料緩衝區的大小。  
  
### <a name="remarks"></a>備註  
 在第二個多載中，MFC 將 cookie 資料擷取至提供`CString`物件。  
  
##  <a name="getcookielength"></a>CInternetSession::GetCookieLength  
 呼叫此成員函式可取得 cookie 儲存在緩衝區的長度。  
  
```  
static DWORD GetCookieLength(
    LPCTSTR pstrUrl,  
    LPCTSTR pstrCookieName);
```  
  
### <a name="parameters"></a>參數  
 `pstrUrl`  
 字串，包含 URL 的指標  
  
 `pstrCookieName`  
 包含 cookie 名稱的字串指標。  
  
### <a name="return-value"></a>傳回值  
 A`DWORD`值，指出 cookie，儲存在緩衝區的長度。 如果沒有 cookie 零名稱所指示`pstrCookieName`存在。  
  
### <a name="remarks"></a>備註  
 這個值由[GetCookie](#getcookie)。  
  
##  <a name="getftpconnection"></a>Cinternetsession:: Getftpconnection  
 呼叫此成員函式，以建立 FTP 連線，並取得指標`CFtpConnection`物件。  
  
```  
CFtpConnection* GetFtpConnection(
    LPCTSTR pstrServer,  
    LPCTSTR pstrUserName = NULL,  
    LPCTSTR pstrPassword = NULL,  
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,  
    BOOL bPassive = FALSE);
```  
  
### <a name="parameters"></a>參數  
 `pstrServer`  
 包含 FTP 伺服器名稱的字串指標。  
  
 `pstrUserName`  
 以 null 終止的字串，指定使用者登入名稱的指標。 如果**NULL**，預設值是匿名的。  
  
 `pstrPassword`  
 指向以 null 結束的字串，指定要用來登入密碼。 如果兩個`pstrPassword`和`pstrUserName`是**NULL**，預設匿名密碼是使用者的電子郵件名稱。 如果`pstrPassword`是**NULL** （或空字串），但`pstrUserName`不**NULL**，則使用空白密碼。 下表描述四個可能設定的行為`pstrUserName`和`pstrPassword`:  
  
|`pstrUserName`|`pstrPassword`|傳送至 FTP 伺服器的使用者名稱|傳送至 FTP 伺服器的密碼|  
|--------------------|--------------------|---------------------------------|---------------------------------|  
|**NULL**或""|**NULL**或""|「 匿名 」|使用者的電子郵件名稱|  
|非- **NULL**字串|**NULL**或""|`pstrUserName`|" "|  
|**NULL**非**NULL**字串|**錯誤**|**錯誤**||  
|非- **NULL**字串|非- **NULL**字串|`pstrUserName`|`pstrPassword`|  
  
 `nPort`  
 識別要在伺服器上使用的 TCP/IP 連接埠的數字。  
  
 `bPassive`  
 指定此 FTP 工作階段被動還是主動模式。 如果設定為**TRUE**，它會將 Win32 API`dwFlag`至**INTERNET_FLAG_PASSIVE**。  
  
### <a name="return-value"></a>傳回值  
 指標[CFtpConnection](../../mfc/reference/cftpconnection-class.md)物件。 如果呼叫失敗，判斷失敗的原因擲回[CInternetException](../../mfc/reference/cinternetexception-class.md)物件。  
  
### <a name="remarks"></a>備註  
 `GetFtpConnection`連接到 FTP 伺服器，而且建立，但將指標傳回至**CFTPConnection**物件。 它不會執行任何特定伺服器上的作業。 如果您想要讀取或寫入檔案，比方說，您就必須執行這些作業做為個別的步驟。 請參閱 < 類別[CFtpConnection](../../mfc/reference/cftpconnection-class.md)和[CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)有關搜尋檔案，開啟檔案、 和讀取或寫入檔案。 請參閱文章[網際網路程式設計 WinInet](../../mfc/win32-internet-extensions-wininet.md)執行一般 FTP 連線的工作中的步驟。  
  
### <a name="example"></a>範例  
  請參閱範例的[CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)。  
  
##  <a name="getgopherconnection"></a>CInternetSession::GetGopherConnection  
 呼叫此成員函式，以建立新的 gopher 連線並取得指標`CGopherConnection`物件。  
  
```  
CGopherConnection* GetGopherConnection(
    LPCTSTR pstrServer,  
    LPCTSTR pstrUserName = NULL,  
    LPCTSTR pstrPassword = NULL,  
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER);
```  
  
### <a name="parameters"></a>參數  
 `pstrServer`  
 包含 gopher 伺服器名稱的字串指標。  
  
 `pstrUserName`  
 包含使用者名稱的字串指標。  
  
 `pstrPassword`  
 包含存取密碼的字串指標。  
  
 `nPort`  
 識別要在伺服器上使用的 TCP/IP 連接埠的數字。  
  
### <a name="return-value"></a>傳回值  
 指標[CGopherConnection](../../mfc/reference/cgopherconnection-class.md)物件。 如果呼叫失敗，判斷失敗的原因擲回[CInternetException](../../mfc/reference/cinternetexception-class.md)物件。  
  
### <a name="remarks"></a>備註  
 `GetGopherConnection`連接至 gopher 伺服器，而且建立，但將指標傳回至`CGopherConnection`物件。 它不會執行任何特定伺服器上的作業。 如果您想要讀取或寫入資料，例如，您就必須執行這些作業做為個別的步驟。 請參閱 < 類別[CGopherConnection](../../mfc/reference/cgopherconnection-class.md)， [CGopherFile](../../mfc/reference/cgopherfile-class.md)，和[CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md)有關搜尋檔案，開啟檔案、 和讀取或寫入檔案。 瀏覽 FTP 站台的相關資訊，請參閱此成員函式[OpenURL](#openurl)。 請參閱文章[網際網路程式設計 WinInet](../../mfc/win32-internet-extensions-wininet.md)中執行一般 gopher 連接工作的步驟。  
  
##  <a name="gethttpconnection"></a>CInternetSession::GetHttpConnection  
 呼叫此成員函式，以建立 HTTP 連線，並取得指標`CHttpConnection`物件。  
  
```  
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
 `pstrServer`  
 包含 HTTP 伺服器名稱的字串指標。  
  
 `nPort`  
 識別要在伺服器上使用的 TCP/IP 連接埠的數字。  
  
 `pstrUserName`  
 包含使用者名稱的字串指標。  
  
 `pstrPassword`  
 包含存取密碼的字串指標。  
  
 *將 dwflags*  
 任何組合**INTERNET_ FLAG_\*** 旗標。 請參閱表格**備註**區段[chttpconnection::](../../mfc/reference/chttpconnection-class.md#openrequest)的說明`dwFlags`值。  
  
### <a name="return-value"></a>傳回值  
 指標[CHttpConnection](../../mfc/reference/chttpconnection-class.md)物件。 如果呼叫失敗，判斷失敗的原因擲回[CInternetException](../../mfc/reference/cinternetexception-class.md)物件。  
  
### <a name="remarks"></a>備註  
 `GetHttpConnection`連接到 HTTP 伺服器，而且建立，但將指標傳回至`CHttpConnection`物件。 它不會執行任何特定伺服器上的作業。 如果您想要查詢 HTTP 標頭，例如，您必須執行這項作業當做個別的步驟。 請參閱 < 類別[CHttpConnection](../../mfc/reference/chttpconnection-class.md)和[Cinternetfile](../../mfc/reference/chttpfile-class.md)您可以使用 HTTP 伺服器的連接執行作業的相關資訊。 瀏覽 HTTP 站台的相關資訊，請參閱此成員函式[OpenURL](#openurl)。 請參閱文章[網際網路程式設計 WinInet](../../mfc/win32-internet-extensions-wininet.md)中執行一般的 HTTP 連接工作的步驟。  
  
##  <a name="onstatuscallback"></a>CInternetSession::OnStatusCallback  
 此成員函式會呼叫架構，以啟用狀態回呼和作業暫止時，更新的狀態。  
  
```  
virtual void OnStatusCallback(
    DWORD_PTR dwContext,  
    DWORD dwInternetStatus,  
    LPVOID lpvStatusInformation,  
    DWORD dwStatusInformationLength);
```  
  
### <a name="parameters"></a>參數  
 `dwContext`  
 提供應用程式的內容值。  
  
 `dwInternetStatus`  
 狀態碼指出為什麼正在進行回呼。 請參閱**備註**可能值的資料表。  
  
 `lpvStatusInformation`  
 包含這個回呼的相關資訊之緩衝區的指標。  
  
 `dwStatusInformationLength`  
 `lpvStatusInformation` 的大小。  
  
### <a name="remarks"></a>備註  
 您必須先呼叫[EnableStatusCallback](#enablestatuscallback)利用狀態回呼。  
  
 `dwInternetStatus`參數指出正在執行的作業，並決定哪些內容的`lpvStatusInformation`會。 `dwStatusInformationLength`指出中包含的資料長度`lpvStatusInformation`。 下列狀態的值`dwInternetStatus`的定義方式如下：  
  
|值|意義|  
|-----------|-------------|  
|`INTERNET_STATUS_RESOLVING_NAME`|查閱中所包含的名稱的 IP 位址`lpvStatusInformation`。|  
|`INTERNET_STATUS_NAME_RESOLVED`|已成功找到名稱中包含的 IP 位址`lpvStatusInformation`。|  
|`INTERNET_STATUS_CONNECTING_TO_SERVER`|連接到通訊端位址 ( [SOCKADDR](../../mfc/reference/sockaddr-structure.md)) 所指向`lpvStatusInformation`。|  
|`INTERNET_STATUS_CONNECTED_TO_SERVER`|已成功連接到通訊端位址 ( `SOCKADDR`) 所指向`lpvStatusInformation`。|  
|`INTERNET_STATUS_SENDING_REQUEST`|將資訊要求傳送至伺服器。 `lpvStatusInformation`參數是**NULL**。|  
|**INTERNET_STATUS_ REQUEST_SENT**|已成功傳送的資訊要求到伺服器。 `lpvStatusInformation`參數是**NULL**。|  
|`INTERNET_STATUS_RECEIVING_RESPONSE`|等候伺服器回應的要求。 `lpvStatusInformation`參數是**NULL**。|  
|`INTERNET_STATUS_RESPONSE_RECEIVED`|已成功從伺服器收到的回應。 `lpvStatusInformation`參數是**NULL**。|  
|`INTERNET_STATUS_CLOSING_CONNECTION`|關閉連接到伺服器。 `lpvStatusInformation`參數是**NULL**。|  
|`INTERNET_STATUS_CONNECTION_CLOSED`|已成功關閉伺服器的連線。 `lpvStatusInformation`參數是**NULL**。|  
|`INTERNET_STATUS_HANDLE_CREATED`|使用 Win32 API 函式[InternetConnect](http://msdn.microsoft.com/library/windows/desktop/aa384363)表示它已建立新的控制代碼。 這可讓應用程式呼叫 Win32 函式[InternetCloseHandle](http://msdn.microsoft.com/library/windows/desktop/aa384350)從另一個執行緒，如果連線耗費時間過長。 查看 Windows SDKfor 這些函式的詳細資訊。|  
|`INTERNET_STATUS_HANDLE_CLOSING`|已成功終止此控制代碼值。|  
  
 覆寫此成員函式，為狀態回呼常式執行之前，需要某些動作。  
  
> [!NOTE]
>  狀態回呼需要執行緒狀態 」 保護。 如果您使用 MFC 共用文件庫中，請覆寫的開頭加入下列行：  
  
 [!code-cpp[NVC_MFCHtmlHttp#8](../../mfc/reference/codesnippet/cpp/cinternetsession-class_1.cpp)]  
  
 如需有關非同步作業的詳細資訊，請參閱文章[網際網路第一個步驟： WinInet](../../mfc/wininet-basics.md)。  
  
##  <a name="openurl"></a>Cinternetsession:: Openurl  
 呼叫此成員函式將指定的要求傳送至 HTTP 伺服器，並允許用戶端指定其他的 RFC822 MIME 或連同要求一起傳送的 HTTP 標頭。  
  
```  
CStdioFile* OpenURL(
    LPCTSTR pstrURL,  
    DWORD_PTR dwContext = 1,  
    DWORD dwFlags = INTERNET_FLAG_TRANSFER_ASCII,  
    LPCTSTR pstrHeaders = NULL,  
    DWORD dwHeadersLength = 0);
```  
  
### <a name="parameters"></a>參數  
 *pstrURL*  
 若要開始讀取 URL 名稱指標。 只有 Url 開頭檔案:、 ftp:，gopher:、 或 http： 支援。 **ASSERT**如果*pszURL*是**NULL**。  
  
 `dwContext`  
 應用程式定義的值隨回呼中傳回的控制代碼。  
  
 `dwFlags`  
 描述如何處理此連線的旗標。 請參閱**備註**如需有關有效的旗標。 有效的旗標如下：  
  
- **INTERNET_FLAG_TRANSFER_ASCII**預設值。 將檔案傳輸 ASCII 文字。  
  
- **INTERNET_FLAG_TRANSFER_BINARY**成二進位檔案將檔案傳輸。  
  
- `INTERNET_FLAG_RELOAD`即使在本機快取，請從網路取得的資料。  
  
- `INTERNET_FLAG_DONT_CACHE`不會快取資料，在本機或任何閘道。  
  
- `INTERNET_FLAG_SECURE`這個旗標適用於只使用 HTTP 要求。 它會要求使用安全通訊端層或 PCT 網路上的安全交易  
  
- **INTERNET_OPEN_FLAG_USE_EXISTING_CONNECT**的話，請重複使用現有的連接所產生的新要求的伺服器**OpenUrl**而不是建立新的工作階段，針對每個連接要求。  
  
- **INTERNET_FLAG_PASSIVE**用於 FTP 站台。 使用被動 FTP 語意。 搭配[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)的`OpenURL`。  
  
 `pstrHeaders`  
 包含要傳送至 HTTP 伺服器的標頭的字串指標。  
  
 *dwHeadersLength*  
 以字元為單位，其他的標頭的長度。 如果這是-1l; 此時和`pstrHeaders`是非**NULL**，然後`pstrHeaders`會假設為零結束，而且長度會計算。  
  
### <a name="return-value"></a>傳回值  
 傳回 FTP、 GOPHER、 HTTP 和檔案類型的網際網路服務的檔案控制代碼。 傳回**NULL**如果成功剖析。  
  
 指標的`OpenURL`取決於傳回*pszURL*的服務類型。 下表說明可能的指標`OpenURL`可以傳回。  
  
|URL 類型|Returns|  
|--------------|-------------|  
|file://|**Cgopherfile\***|  
|http://|**Cinternetfile\***|  
|gopher://|**CGopherFile\***|  
|ftp: / /|**CInternetFile\***|  
  
### <a name="remarks"></a>備註  
 參數`dwFlags`必須包含**INTERNET_FLAG_TRANSFER_ASCII**或**INTERNET_FLAG_TRANSFER_BINARY**，但非兩者。 剩餘的旗標可以結合的位元`OR`運算子 ( **&#124;**)。  
  
 `OpenURL`其中包裝的 Win32 函式**InternetOpenURL**，允許只下載、 擷取和網際網路伺服器中讀取資料。 `OpenURL`可讓遠端位置，不在檔案操作，因此需要無[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)物件。  
  
 若要使用特定的連接 (也就是通訊協定特有) 函式，例如寫入檔案時，您必須開啟工作階段，然後開啟特定種類的連線，然後使用該連接所需模式中開啟檔案。 請參閱`CInternetConnection`如需有關連接特有的函式。  
  
##  <a name="operator_hinternet"></a>CInternetSession::operator HINTERNET  
 您可以使用這個運算子來取得目前的網際網路工作階段的 Windows 控制代碼。  
  
```  
operator HINTERNET() const;  
```  
  
##  <a name="setcookie"></a>CInternetSession::SetCookie  
 設定指定之 url 的 cookie。  
  
```  
static BOOL SetCookie(
    LPCTSTR pstrUrl,  
    LPCTSTR pstrCookieName,  
    LPCTSTR pstrCookieData);
```  
  
### <a name="parameters"></a>參數  
 `pstrUrl`  
 以 null 終止的字串，指定應該設定 cookie 的 URL 的指標。  
  
 `pstrCookieName`  
 包含 cookie 名稱的字串指標。  
  
 `pstrCookieData`  
 包含實際的字串資料的 url 相關聯的字串指標。  
  
### <a name="return-value"></a>傳回值  
 傳回**TRUE**如果成功，或**FALSE**否則。 若要取得特定錯誤碼，請呼叫**時發生。**  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息行為[InternetSetCookie](http://msdn.microsoft.com/library/windows/desktop/aa385107)、 Windows SDK 中所述。  
  
##  <a name="setoption"></a>CInternetSession::SetOption  
 呼叫此成員函式可設定的網際網路工作階段選項。  
  
```  
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
 `dwOption`  
 若要設定 網際網路選項。 請參閱[選項旗標](http://msdn.microsoft.com/library/windows/desktop/aa385328)Windows SDKfor 個可能的選項清單中。  
  
 `lpBuffer`  
 包含的選項設定的緩衝區。  
  
 *dwBufferLength*  
 長度`lpBuffer`或大小`dwValue`。  
  
 `dwValue`  
 A `DWORD` ，其中包含的選項設定。  
  
 `dwFlags`  
 表示各種快取選項。 預設值是設為 0。 可能的值包括：  
  
- `INTERNET_FLAG_DONT_CACHE`不會快取資料，在本機或任何閘道伺服器。  
  
- `INTERNET_FLAG_OFFLINE`下載作業透過持續性的快取沒有問題。 如果項目不存在於快取中，會傳回適當的錯誤程式碼。 這個旗標可能會合併使用位元`OR`( **&#124;**) 運算子。  
  
### <a name="return-value"></a>傳回值  
 如果作業成功，值為**TRUE**傳回。 如果發生錯誤，值為**FALSE**傳回。 如果呼叫失敗，Win32 函式[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)可能會呼叫以判斷錯誤的原因。  
  
## <a name="see-also"></a>請參閱  
 [CObject 類別](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CInternetConnection 類別](../../mfc/reference/cinternetconnection-class.md)   
 [CHttpConnection 類別](../../mfc/reference/chttpconnection-class.md)   
 [CFtpConnection 類別](../../mfc/reference/cftpconnection-class.md)   
 [CGopherConnection 類別](../../mfc/reference/cgopherconnection-class.md)
