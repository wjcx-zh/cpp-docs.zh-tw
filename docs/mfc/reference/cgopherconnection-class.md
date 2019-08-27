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
ms.openlocfilehash: f5d655aa7fd2eb9e41c15c60a71492c24ba43c43
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506187"
---
# <a name="cgopherconnection-class"></a>CGopherConnection 類別

管理您與 Gopher 網際網路伺服器的連接。

> [!NOTE]
>  類別`CGopherConnection`、 `CGopherFile`、和其成員`CGopherLocator`已被取代, 因為它們無法在 Windows XP 平臺上使用, 但它們將繼續在舊版平臺上使用。 `CGopherFileFind`

## <a name="syntax"></a>語法

```
class CGopherConnection : public CInternetConnection
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CGopherConnection::CGopherConnection](#cgopherconnection)|建構 `CGopherConnection` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CGopherConnection::CreateLocator](#createlocator)|建立[CGopherLocator](../../mfc/reference/cgopherlocator-class.md)物件, 以在 Gopher 伺服器上尋找檔案。|
|[CGopherConnection::GetAttribute](#getattribute)|抓取有關 gopher 物件的屬性資訊。|
|[CGopherConnection::OpenFile](#openfile)|開啟 gopher 檔案。|

## <a name="remarks"></a>備註

Gopher 服務是由 MFC WinInet 類別識別的三種網際網路服務之一。

類別`CGopherConnection`包含一個可管理 gopher 服務的函式和三個額外的成員函式:[OpenFile](#openfile)、 [CreateLocator](#createlocator)和[GetAttribute](#getattribute)。

若要與 gopher 網際網路伺服器通訊, 您必須先建立[CInternetSession](../../mfc/reference/cinternetsession-class.md)的實例, 然後呼叫[CInternetSession:: GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection), `CGopherConnection`它會建立物件並傳回它的指標。 您永遠不會`CGopherConnection`直接建立物件。

若要深入瞭解如何`CGopherConnection`與其他 MFC 網際網路類別搭配運作, 請參閱[使用 WinInet 進行網際網路程式設計](../../mfc/win32-internet-extensions-wininet.md)一文。 如需使用其他兩個支援的網際網路服務的詳細資訊, 請參閱 < 類別[CHttpConnection](../../mfc/reference/chttpconnection-class.md)和[CFtpConnection](../../mfc/reference/cftpconnection-class.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)

`CGopherConnection`

## <a name="requirements"></a>需求

**標頭:** afxinet.h。h

##  <a name="cgopherconnection"></a>CGopherConnection::CGopherConnection

呼叫這個成員函式以建立`CGopherConnection`物件。

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

*pSession*<br/>
相關[CInternetSession](../../mfc/reference/cinternetsession-class.md)物件的指標。

*hConnected*<br/>
目前網際網路會話的 Windows 控制碼。

*pstrServer*<br/>
包含 FTP 伺服器名稱之字串的指標。

*dwContext*<br/>
作業的內容識別碼。 *dwCoNtext*會識別[CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)傳回的作業狀態資訊。 預設值設定為 1;不過, 您可以明確地指派作業的特定內容識別碼。 物件及其執行的任何工作都會與該內容識別碼相關聯。

*pstrUserName*<br/>
以 null 結束的字串指標, 指定要登入之使用者的名稱。 如果是 Null, 則預設值為 anonymous。

*pstrPassword*<br/>
以 null 結束的字串指標, 指定要用來登入的密碼。 如果*pstrPassword*和*PSTRUSERNAME*都是 Null, 則預設的匿名密碼就是使用者的電子郵件名稱。 如果*pstrPassword*為 Null (或空字串), 但*PSTRUSERNAME*不是 null, 則會使用空白密碼。 下表描述*pstrUserName*和*pstrPassword*的四個可能設定的行為:

|*pstrUserName*|*pstrPassword*|傳送到 FTP 伺服器的使用者名稱|傳送到 FTP 伺服器的密碼|
|--------------------|--------------------|---------------------------------|---------------------------------|
|Null 或 ""|Null 或 ""|匿名|使用者的電子郵件名稱|
|非 Null 字串|Null 或 ""|*pstrUserName*|" "|
|Null 非 Null 字串|錯誤|錯誤||
|非 Null 字串|非 Null 字串|*pstrUserName*|*pstrPassword*|

*nPort*<br/>
識別要在伺服器上使用之 TCP/IP 通訊埠的數位。

### <a name="remarks"></a>備註

您永遠不會`CGopherConnection`直接建立。 相反地, 呼叫[CInternetSession:: GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection), 它會`CGopherConnection`建立物件, 並傳回其指標。

##  <a name="createlocator"></a>  CGopherConnection::CreateLocator

呼叫這個成員函式以建立 gopher 定位器, 以尋找或識別 Gopher 伺服器上的檔案。

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
字串的指標, 其中包含要抓取的 gopher 檔或目錄的名稱。 如果*pstrDisplayString*參數是 Null, 則會傳回 Gopher 伺服器的預設目錄。

*pstrSelectorString*<br/>
要傳送至 Gopher 伺服器以取得專案的選取器字串指標。 *pstrSelectorString*可以是 Null。

*dwGopherType*<br/>
這會指定*pstrSelectorString*是否指的是目錄或檔, 以及要求是 gopher 還是 gopher +。 請參閱 Windows SDK 中結構[GOPHER_FIND_DATA](/windows/win32/api/wininet/ns-wininet-gopher_find_dataw)的屬性。

*pstrLocator*<br/>
字串的指標, 識別要開啟的檔案。 一般來說, 這個字串是從呼叫[CGopherFileFind:: GetLocator](../../mfc/reference/cgopherfilefind-class.md#getlocator)傳回。

*pstrServerName*<br/>
包含 Gopher 伺服器名稱之字串的指標。

*nPort*<br/>
識別此連線之網際網路埠的編號。

### <a name="return-value"></a>傳回值

[CGopherLocator](../../mfc/reference/cgopherlocator-class.md)物件。

### <a name="remarks"></a>備註

成員函式的靜態版本需要您指定伺服器, 而非靜態版本則使用連線物件中的伺服器名稱。

為了從 Gopher 伺服器取出資訊, 應用程式必須先取得 gopher 定位器。 然後, 應用程式必須將定位器視為不透明的 token (也就是說, 應用程式可以使用定位器, 但不能直接操作或比較)。 一般來說, 應用程式會使用定位器來呼叫[CGopherFileFind:: FindFile](../../mfc/reference/cgopherfilefind-class.md#findfile)成員函式, 以取得特定的資訊片段。

##  <a name="getattribute"></a>  CGopherConnection::GetAttribute

呼叫這個成員函式, 從 Gopher 伺服器抓取專案的特定屬性資訊。

```
BOOL GetAttribute(
    CGopherLocator& refLocator    CString strRequestedAttributes,
    CString& strResult,);
```

### <a name="parameters"></a>參數

*refLocator*<br/>
[CGopherLocator](../../mfc/reference/cgopherlocator-class.md)物件的參考。

*strRequestedAttributes*<br/>
以空格分隔的字串, 指定所要求屬性的名稱。

*strResult*<br/>
可接收定位器類型之[CString](../../atl-mfc-shared/reference/cstringt-class.md)的參考。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。 如果呼叫失敗, 則可以呼叫 Win32 函數[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)來判斷錯誤的原因。

##  <a name="openfile"></a>CGopherConnection:: OpenFile

呼叫這個成員函式, 在 Gopher 伺服器上開啟檔案。

```
CGopherFile* OpenFile(
    CGopherLocator& refLocator,
    DWORD dwFlags = 0,
    LPCTSTR pstrView = NULL,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>參數

*refLocator*<br/>
[CGopherLocator](../../mfc/reference/cgopherlocator-class.md)物件的參考。

*dwFlags*<br/>
INTERNET_FLAG_ * 旗標的任意組合。 如需 INTERNET_FLAG_\*旗標的進一步資訊, 請參閱[CInternetSession:: OpenUrl](../../mfc/reference/cinternetsession-class.md#openurl) 。

*pstrView*<br/>
檔案視圖字串的指標。 如果伺服器上有多個檔案的流覽, 此參數會指定要開啟的檔案。 如果*pstrView*為 Null, 則會使用預設的檔案視圖。

*dwContext*<br/>
要開啟之檔案的內容識別碼。 如需*dwCoNtext*的詳細資訊, 請參閱**備註**。

### <a name="return-value"></a>傳回值

要開啟的[CGopherFile](../../mfc/reference/cgopherfile-class.md)物件指標。

### <a name="remarks"></a>備註

覆寫*dwCoNtext*預設值, 將內容識別碼設定為您選擇的值。 內容識別碼會與其`CGopherConnection` [CInternetSession](../../mfc/reference/cinternetsession-class.md)物件所建立之物件的這個特定作業相關聯。 此值會傳回[CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) , 以提供所識別之作業的狀態。 請參閱網際網路[的第一篇步驟:WinInet](../../mfc/wininet-basics.md)取得內容識別碼的詳細資訊。

## <a name="see-also"></a>另請參閱

[CInternetConnection 類別](../../mfc/reference/cinternetconnection-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CFtpConnection 類別](../../mfc/reference/cftpconnection-class.md)<br/>
[CHttpConnection 類別](../../mfc/reference/chttpconnection-class.md)<br/>
[CInternetConnection 類別](../../mfc/reference/cinternetconnection-class.md)<br/>
[CGopherLocator 類別](../../mfc/reference/cgopherlocator-class.md)<br/>
[CGopherFile 類別](../../mfc/reference/cgopherfile-class.md)<br/>
[CInternetSession 類別](../../mfc/reference/cinternetsession-class.md)
