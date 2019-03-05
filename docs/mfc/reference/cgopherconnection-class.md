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
ms.openlocfilehash: d960d566a63531af211592a7a8ae8f1cb35c5958
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57300714"
---
# <a name="cgopherconnection-class"></a>CGopherConnection 類別

管理您與 Gopher 網際網路伺服器的連接。

> [!NOTE]
>  類別`CGopherConnection`， `CGopherFile`， `CGopherFileFind`，`CGopherLocator`和其成員已被取代，因為它們不在 Windows XP 平台上運作，但它們會繼續在舊版平台上運作。

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
|[CGopherConnection::CreateLocator](#createlocator)|會建立[CGopherLocator](../../mfc/reference/cgopherlocator-class.md) gopher 伺服器上尋找檔案的物件。|
|[CGopherConnection::GetAttribute](#getattribute)|擷取 gopher 物件的屬性資訊。|
|[CGopherConnection::OpenFile](#openfile)|開啟 gopher 檔案。|

## <a name="remarks"></a>備註

Gopher 服務是其中一個 MFC WinInet 類別可辨識的三個網際網路服務。

此類別`CGopherConnection`包含建構函式和三個管理 gopher 服務的其他成員函式：[OpenFile](#openfile)， [CreateLocator](#createlocator)，以及[GetAttribute](#getattribute)。

若要與 gopher 網際網路伺服器通訊，您必須先建立的執行個體[CInternetSession](../../mfc/reference/cinternetsession-class.md)，然後呼叫[Getgopherconnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection)，這會建立`CGopherConnection`物件，並傳回的指標。 您永遠不會建立`CGopherConnection`直接物件。

若要進一步了解如何`CGopherConnection`運作方式與其他 MFC 網際網路類別，請參閱文章[網際網路程式設計 WinInet](../../mfc/win32-internet-extensions-wininet.md)。 如需有關使用其他兩個支援網際網路服務，FTP 和 HTTP 查看類別[CHttpConnection](../../mfc/reference/chttpconnection-class.md)並[CFtpConnection](../../mfc/reference/cftpconnection-class.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)

`CGopherConnection`

## <a name="requirements"></a>需求

**標頭：** afxinet.h

##  <a name="cgopherconnection"></a>  CGopherConnection::CGopherConnection

此成員函式呼叫來建構`CGopherConnection`物件。

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
相關的指標[CInternetSession](../../mfc/reference/cinternetsession-class.md)物件。

*hConnected*<br/>
目前的網際網路工作階段的 Windows 控制代碼。

*pstrServer*<br/>
包含 FTP 伺服器名稱的字串指標。

*dwContext*<br/>
作業的內容識別碼。 *dwContext*識別傳回作業的狀態資訊[CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)。 預設值設為 1。不過，您可以明確指派作業的特定內容識別碼。 物件，而且它沒有任何工作將會與該內容識別碼相關聯

*pstrUserName*<br/>
以 null 終止的字串，指定要登入的使用者名稱的指標。 如果是 NULL，則預設會為匿名。

*pstrPassword*<br/>
以 null 終止的字串，指定要用來登入密碼的指標。 如果兩個*pstrPassword*並*pstrUserName*為 NULL 時，預設匿名密碼是使用者的電子郵件名稱。 如果*pstrPassword*是 NULL （或空字串），但*pstrUserName*不是 NULL，則使用空白密碼。 下表描述的四個可能的設定行為*pstrUserName*並*pstrPassword*:

|*pstrUserName*|*pstrPassword*|傳送至 FTP 伺服器的使用者名稱|傳送至 FTP 伺服器的密碼|
|--------------------|--------------------|---------------------------------|---------------------------------|
|NULL 或""|NULL 或""|「 匿名 」|使用者的電子郵件名稱|
|非 NULL 字串|NULL 或""|*pstrUserName*|" "|
|NULL 的非 NULL 字串|ERROR|ERROR||
|非 NULL 字串|非 NULL 字串|*pstrUserName*|*pstrPassword*|

*nPort*<br/>
識別要使用的伺服器上的 TCP/IP 連接埠的數字。

### <a name="remarks"></a>備註

您永遠不會建立`CGopherConnection`直接。 相反地，呼叫[Getgopherconnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection)，這會建立`CGopherConnection`物件，並傳回的指標。

##  <a name="createlocator"></a>  CGopherConnection::CreateLocator

呼叫此成員函式來建立 gopher 定位器來尋找，或識別 gopher 伺服器上的檔案。

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
包含 gopher 文件或要擷取的目錄名稱的字串指標。 如果*pstrDisplayString*參數為 NULL，會傳回 gopher 伺服器的預設目錄。

*pstrSelectorString*<br/>
若要傳送至 gopher 伺服器，以擷取項目選取器字串的指標。 *pstrSelectorString*可以是 NULL。

*dwGopherType*<br/>
這會指定是否*pstrSelectorString*指的是目錄或文件，以及要求是否為 gopher +。 請參閱結構的屬性[GOPHER_FIND_DATA](/windows/desktop/api/wininet/ns-wininet-gopher_find_dataa) Windows SDK 中。

*pstrLocator*<br/>
字串，識別要開啟的檔案指標。 一般而言，這個字串會傳回呼叫[CGopherFileFind::GetLocator](../../mfc/reference/cgopherfilefind-class.md#getlocator)。

*pstrServerName*<br/>
包含 gopher 伺服器名稱的字串指標。

*nPort*<br/>
識別此連線的網際網路連接埠號碼。

### <a name="return-value"></a>傳回值

A [CGopherLocator](../../mfc/reference/cgopherlocator-class.md)物件。

### <a name="remarks"></a>備註

靜態成員函式版本會要求您指定伺服器，而非靜態版本使用的連接物件中的伺服器名稱。

若要從 gopher 伺服器擷取資訊，應用程式必須先取得 gopher 定位器。 應用程式必須再將視為不透明的語彙基元的定位器 （也就是應用程式可以使用定位程式，但不是直接操作或比較它）。 一般來說，應用程式的呼叫中使用定位器[CGopherFileFind::FindFile](../../mfc/reference/cgopherfilefind-class.md#findfile)成員函式來擷取特定資訊。

##  <a name="getattribute"></a>  CGopherConnection::GetAttribute

呼叫此成員函式擷取特定的屬性資訊項目從 gopher 伺服器。

```
BOOL GetAttribute(
    CGopherLocator& refLocator    CString strRequestedAttributes,
    CString& strResult,);
```

### <a name="parameters"></a>參數

*refLocator*<br/>
參考[CGopherLocator](../../mfc/reference/cgopherlocator-class.md)物件。

*strRequestedAttributes*<br/>
以空格分隔的字串，指定要求的屬性名稱。

*strResult*<br/>
參考[CString](../../atl-mfc-shared/reference/cstringt-class.md)接收定位器類型。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。 如果呼叫失敗，Win32 函式[GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360)可能會呼叫以判斷錯誤的原因。

##  <a name="openfile"></a>  CGopherConnection::OpenFile

呼叫此成員函式，以開啟 gopher 伺服器上的檔案。

```
CGopherFile* OpenFile(
    CGopherLocator& refLocator,
    DWORD dwFlags = 0,
    LPCTSTR pstrView = NULL,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>參數

*refLocator*<br/>
參考[CGopherLocator](../../mfc/reference/cgopherlocator-class.md)物件。

*dwFlags*<br/>
INTERNET_FLAG_ * 旗標的任意組合。 請參閱[cinternetsession:: Openurl](../../mfc/reference/cinternetsession-class.md#openurl)更多有關 INTERNET_FLAG_\*旗標。

*pstrView*<br/>
檔案檢視字串指標。 如果檔案的幾個檢視存在於伺服器，則此參數會指定要開啟的檔案檢視。 如果*pstrView*是 NULL，會使用預設檔案檢視。

*dwContext*<br/>
正在開啟之檔案的內容識別碼。 請參閱**備註**如需詳細資訊*dwContext*。

### <a name="return-value"></a>傳回值

指標[CGopherFile](../../mfc/reference/cgopherfile-class.md)開啟的物件。

### <a name="remarks"></a>備註

覆寫*dwContext*預設可設定的內容識別碼以您選擇的值。 內容識別碼是與這個特定作業的相關聯`CGopherConnection`所建立的物件及其[CInternetSession](../../mfc/reference/cinternetsession-class.md)物件。 若要傳回的值[CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)來提供與識別此作業的狀態。 請參閱文章[網際網路前幾個步驟：WinInet](../../mfc/wininet-basics.md)取得的內容識別碼的詳細資訊。

## <a name="see-also"></a>另請參閱

[CInternetConnection 類別](../../mfc/reference/cinternetconnection-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CFtpConnection 類別](../../mfc/reference/cftpconnection-class.md)<br/>
[CHttpConnection 類別](../../mfc/reference/chttpconnection-class.md)<br/>
[CInternetConnection 類別](../../mfc/reference/cinternetconnection-class.md)<br/>
[CGopherLocator 類別](../../mfc/reference/cgopherlocator-class.md)<br/>
[CGopherFile 類別](../../mfc/reference/cgopherfile-class.md)<br/>
[CInternetSession 類別](../../mfc/reference/cinternetsession-class.md)
