---
title: CGopherConnection 類別
ms.date: 11/04/2016
f1_keywords:
- CGopherConnection
- AFXINET/CGopherConnection
- AFXINET/CGopherConnection::CGopherConnection
- AFXINET/CGopherConnection::CreateLocator
- AFXINET/CGopherConnection::GetAttribute
- AFXINET/CGopherConnection::OpenFile
helpviewer_keywords:
- CGopherConnection [MFC], CGopherConnection
- CGopherConnection [MFC], CreateLocator
- CGopherConnection [MFC], GetAttribute
- CGopherConnection [MFC], OpenFile
ms.assetid: b5b96aea-ac99-430e-bd84-d1372b43f78f
ms.openlocfilehash: eade1a82b674d5ad2e91146559139445ef017180
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373705"
---
# <a name="cgopherconnection-class"></a>CGopherConnection 類別

管理您與 Gopher 網際網路伺服器的連接。

> [!NOTE]
> 類`CGopherConnection``CGopherFile` `CGopherFileFind`、`CGopherLocator`、 及其成員已被棄用,因為它們在 Windows XP 平臺上不工作,但它們將繼續在較早的平臺上工作。

## <a name="syntax"></a>語法

```
class CGopherConnection : public CInternetConnection
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[Gopher 連接::Cgopher 連接](#cgopherconnection)|建構 `CGopherConnection` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[Gopher 連線:建立定位器](#createlocator)|創建一個[CGopherLocator 物件](../../mfc/reference/cgopherlocator-class.md)來查找 gopher 伺服器上的檔。|
|[Gopher 連線:抓取屬性](#getattribute)|檢索有關 gopher 物件的屬性資訊。|
|[Gopher 連線::開啟檔案](#openfile)|打開一個 gopher 檔。|

## <a name="remarks"></a>備註

gopher 服務是 MFC WinInet 類認可的三種互聯網服務之一。

這個類別`CGopherConnection`包含一個建構函數和三個管理 gopher 服務的附加成員函數[:OpenFile、CreateLocator](#openfile)和[CreateLocator](#createlocator)[GetAttribute](#getattribute)。

要與 gopher Internet 伺服器通訊,必須首先建立[CInternetSession](../../mfc/reference/cinternetsession-class.md)的實例,然後調用[CInternetSession::getGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection),`CGopherConnection`它建立物件並傳回指向它的指標。 您從不直接創建`CGopherConnection`物件。

要瞭解有關如何`CGopherConnection`與其他 MFC Internet 類合作,請參閱[WinInet](../../mfc/win32-internet-extensions-wininet.md)的 Internet 程式設計文章。 有關使用其他兩個受支援的 Internet 服務的詳細資訊,FTP 和 HTTP 請參閱[類別 CHttpConnection](../../mfc/reference/chttpconnection-class.md)和[CFtpConnection](../../mfc/reference/cftpconnection-class.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)

`CGopherConnection`

## <a name="requirements"></a>需求

**標題:** afxinet.h

## <a name="cgopherconnectioncgopherconnection"></a><a name="cgopherconnection"></a>Gopher 連接::Cgopher 連接

呼叫此成員函數以建構物件`CGopherConnection`。

```
CGopherConnection(
    CInternetSession* pSession,
    HINTERNET hConnected,
    LPCTSTR pstrServer,
    DWORD_PTR dwContext);

CGopherConnection(
    CInternetSession* pSession,
    LPCTSTR pstrServer,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL,
    DWORD_PTR dwContext = 0,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER);
```

### <a name="parameters"></a>參數

*p 工作階段*<br/>
指向相關[CInternetSession](../../mfc/reference/cinternetsession-class.md)物件的指標。

*h 連線*<br/>
當前 Internet 作業階段的 Windows 句柄。

*pstrServer*<br/>
指向包含 FTP 伺服器名稱的字串的指標。

*dwContext*<br/>
操作的上下文標識碼。 *dwContext*識別 CInternetSession 傳回的作業的狀態資訊[::onStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)。 預設值設定為 1;將預設值設定為 1但是,您可以顯式為操作分配特定的上下文 ID。 物件及其執行的任何工作都將與該上下文 ID 相關聯。

*pstrUser 名稱*<br/>
指向 null 終止字串的指標,該字串指定要登錄的使用者的名稱。 如果為 NULL,則預設值為匿名。

*pstr密碼*<br/>
指向 null 終止字串的指標,用於指定用於登入的密碼。 如果*pstrPassword*和*pstrUserName*均為 NULL,則預設的匿名密碼是使用者的電子郵件名稱。 如果*pstrPassword*為 NULL(或空字串),但*pstrUserName*不是 NULL,則使用空白密碼。 下表描述了*pstrUserName*和*pstrPassword*的四種可能設定的行為:

|*pstrUser 名稱*|*pstr密碼*|傳送 FTP 伺服器的使用者名稱|傳送 FTP 伺服器的密碼|
|--------------------|--------------------|---------------------------------|---------------------------------|
|NULL 或""|NULL 或""|"匿名"|使用者的電子郵件名稱|
|NULL 字串|NULL 或""|*pstrUser 名稱*|" "|
|NULL 非 NULL 字串|ERROR|ERROR||
|NULL 字串|NULL 字串|*pstrUser 名稱*|*pstr密碼*|

*n波特*<br/>
標識要在伺服器上使用的 TCP/IP 連接埠的數位。

### <a name="remarks"></a>備註

您從不直接建立`CGopherConnection`。 相反,調用[CInternetSession::GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection)`CGopherConnection`,它 創建一個物件並返回指向它的指標。

## <a name="cgopherconnectioncreatelocator"></a><a name="createlocator"></a>Gopher 連線:建立定位器

呼叫此成員函數以創建 gopher 定位器以查找或識別 gopher 伺服器上的檔案。

```
CGopherLocator CreateLocator(
    LPCTSTR pstrDisplayString,
    LPCTSTR pstrSelectorString,
    DWORD dwGopherType);

static CGopherLocator CreateLocator(LPCTSTR pstrLocator);

static CGopherLocator CreateLocator(
    LPCTSTR pstrServerName,
    LPCTSTR pstrDisplayString,
    LPCTSTR pstrSelectorString,
    DWORD dwGopherType,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER);
```

### <a name="parameters"></a>參數

*pstrDisplayString*<br/>
指向要檢索的 gopher 文件或目錄名稱的字串的指標。 如果*pstrDisplayString*參數為 NULL,則傳回 gopher 伺服器的預設目錄。

*pstrSelectorString*<br/>
指向要發送到 gopher 伺服器以檢索項的選擇器字串的指標。 *pstrSelectorString*可以是 NULL。

*dwGopher 類型*<br/>
這指定*pstrSelectorString*是否引用目錄或文檔,以及請求是 gopher 還是 gopher*。 請參閱 Windows SDK 中[結構GOPHER_FIND_DATA](/windows/win32/api/wininet/ns-wininet-gopher_find_dataw)的屬性。

*pstrLocator*<br/>
指向標識要打開的檔的字串的指標。 通常,此字串是從呼叫[CGopherFileFind 傳回:getLocator](../../mfc/reference/cgopherfilefind-class.md#getlocator)。

*pstrServer 名稱*<br/>
指向包含 gopher 伺服器名稱的字串的指標。

*n波特*<br/>
標識此連接的 Internet 埠的編號。

### <a name="return-value"></a>傳回值

[Gopher 定位器](../../mfc/reference/cgopherlocator-class.md)物件。

### <a name="remarks"></a>備註

成員函數的靜態版本要求您指定伺服器,而非靜態版本使用連接對象的伺服器名稱。

為了從 gopher 伺服器檢索資訊,應用程式必須首先獲取 gopher 定位器。 然後,應用程式必須將定位器視為不透明權杖(即,應用程式可以使用定位器,但不能直接操作或比較它)。 通常,應用程式使用定位器調用[CGopherFileFind::FindFile](../../mfc/reference/cgopherfilefind-class.md#findfile)成員函數來檢索特定資訊。

## <a name="cgopherconnectiongetattribute"></a><a name="getattribute"></a>Gopher 連線:抓取屬性

調用此成員函數從 gopher 伺服器檢索有關專案的特定屬性資訊。

```
BOOL GetAttribute(
    CGopherLocator& refLocator    CString strRequestedAttributes,
    CString& strResult,);
```

### <a name="parameters"></a>參數

*參考定位器*<br/>
對[CGopher 定位器物件的參考](../../mfc/reference/cgopherlocator-class.md)。

*str 被要求屬性*<br/>
指定要求屬性名稱的空間分隔字串。

*strResult*<br/>
對接收定位器類型的[CString](../../atl-mfc-shared/reference/cstringt-class.md)的引用。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。 如果調用失敗,可能會調用 Win32 函數[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)以確定錯誤的原因。

## <a name="cgopherconnectionopenfile"></a><a name="openfile"></a>Gopher 連線::開啟檔案

呼叫此成員函數以在 gopher 伺服器上打開檔。

```
CGopherFile* OpenFile(
    CGopherLocator& refLocator,
    DWORD dwFlags = 0,
    LPCTSTR pstrView = NULL,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>參數

*參考定位器*<br/>
對[CGopher 定位器物件的參考](../../mfc/reference/cgopherlocator-class.md)。

*dwFlags*<br/>
INTERNET_FLAG_* 標誌的任意組合。 有關INTERNET_FLAG_\*標誌的詳細資訊,請參閱[CInternetSession::OpenUrl。](../../mfc/reference/cinternetsession-class.md#openurl)

*pstrView*<br/>
指向檔檢視字串的指標。 如果伺服器中存在該檔的多個檢視,則此參數指定要打開的文件檢視。 如果*pstrView*為 NULL,則使用預設檔案檢視。

*dwContext*<br/>
正在打開的檔的上下文 ID。 關於*dwContext*的詳細資訊,請參閱**備註**。

### <a name="return-value"></a>傳回值

指向要打開[的 CGopherFile](../../mfc/reference/cgopherfile-class.md)物件的指標。

### <a name="remarks"></a>備註

覆寫*dwContext*預設值,將上下文識別子設定為您選擇的值。 上下文識別碼`CGopherConnection`[與其 CInternetSession](../../mfc/reference/cinternetsession-class.md)對象創建的物件的此特定操作相關聯。 該值將返回到[CInternetSession::onStatusBack](../../mfc/reference/cinternetsession-class.md#onstatuscallback)以提供標識該值的操作的狀態。 有關上下文標識符的詳細資訊[,請參閱"Internet 第一步:WinInet"](../../mfc/wininet-basics.md)一文。

## <a name="see-also"></a>另請參閱

[CInternetConnection 類別](../../mfc/reference/cinternetconnection-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CFtpConnection 類別](../../mfc/reference/cftpconnection-class.md)<br/>
[CHttpConnection 類別](../../mfc/reference/chttpconnection-class.md)<br/>
[CInternetConnection 類別](../../mfc/reference/cinternetconnection-class.md)<br/>
[CGopherLocator 類別](../../mfc/reference/cgopherlocator-class.md)<br/>
[CGopherFile 類別](../../mfc/reference/cgopherfile-class.md)<br/>
[CInternetSession 類別](../../mfc/reference/cinternetsession-class.md)
