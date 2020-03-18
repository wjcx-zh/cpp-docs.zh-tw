---
title: CHttpConnection 類別
ms.date: 03/27/2019
f1_keywords:
- CHttpConnection
- AFXINET/CHttpConnection
- AFXINET/CHttpConnection::CHttpConnection
- AFXINET/CHttpConnection::OpenRequest
helpviewer_keywords:
- CHttpConnection [MFC], CHttpConnection
- CHttpConnection [MFC], OpenRequest
ms.assetid: a402b662-c445-4988-800d-c8278551babe
ms.openlocfilehash: 1941af1e16a897235dd90db509d6ed29c2d9a875
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79420397"
---
# <a name="chttpconnection-class"></a>CHttpConnection 類別

管理您與 HTTP 伺服器的連接。

## <a name="syntax"></a>語法

```
class CHttpConnection : public CInternetConnection
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CHttpConnection：： CHttpConnection](#chttpconnection)|建立 `CHttpConnection` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CHttpConnection：： OpenRequest](#openrequest)|開啟 HTTP 要求。|

## <a name="remarks"></a>備註

HTTP 是由 MFC WinInet 類別所實作為的三種網際網路伺服器通訊協定之一。

類別 `CHttpConnection` 包含一個用來管理使用 HTTP 通訊協定之伺服器連接的[OpenRequest](#openrequest)函數和一個成員函式。

若要與 HTTP 伺服器通訊，您必須先建立[CInternetSession](../../mfc/reference/cinternetsession-class.md)的實例，然後建立[CHttpConnection](#chttpconnection)物件。 您永遠不會直接建立 `CHttpConnection` 物件;相反地，請呼叫[CInternetSession：： GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection)，它會建立 `CHttpConnection` 物件，並傳回它的指標。

若要深入瞭解 `CHttpConnection` 如何與其他 MFC 網際網路類別搭配運作，請參閱[使用 WinInet 進行網際網路程式設計](../../mfc/win32-internet-extensions-wininet.md)一文。 如需使用其他兩種支援的網際網路通訊協定（gopher 和 FTP）連接到伺服器的詳細資訊，請參閱類別[CGopherConnection](../../mfc/reference/cgopherconnection-class.md)和[CFtpConnection](../../mfc/reference/cftpconnection-class.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)

`CHttpConnection`

## <a name="requirements"></a>需求

**標頭：** afxinet.h。h

##  <a name="chttpconnection"></a>CHttpConnection：： CHttpConnection

呼叫這個成員函式來建立 `CHttpConnection` 物件。

```
CHttpConnection(
    CInternetSession* pSession,
    HINTERNET hConnected,
    LPCTSTR pstrServer,
    DWORD_PTR dwContext);

CHttpConnection(
    CInternetSession* pSession,
    LPCTSTR pstrServer,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL,
    DWORD_PTR dwContext = 1);

CHttpConnection(
    CInternetSession* pSession,
    LPCTSTR pstrServer,
    DWORD dwFlags,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>參數

*pSession*<br/>
[CInternetSession](../../mfc/reference/cinternetsession-class.md)物件的指標。

*hConnected*<br/>
網際網路連接的控制碼。

*pstrServer*<br/>
包含伺服器名稱之字串的指標。

*dwCoNtext*<br/>
`CInternetConnection` 物件的內容識別碼。 如需*dwCoNtext*的詳細資訊，請參閱**備註**一節。

*nPort*<br/>
識別此連接之網際網路埠的數位。

*pstrUserName*<br/>
以 null 結束的字串指標，指定要登入之使用者的名稱。 如果是 Null，則預設值為 anonymous。

*pstrPassword*<br/>
以 null 結束的字串指標，指定要用來登入的密碼。 如果*pstrPassword*和*PSTRUSERNAME*都是 Null，則預設的匿名密碼就是使用者的電子郵件名稱。 如果*pstrPassword*為 Null 或空字串，但*PSTRUSERNAME*不是 null，則會使用空白密碼。 下表描述*pstrUserName*和*pstrPassword*的四個可能設定的行為：

|*pstrUserName*|*pstrPassword*|傳送到 FTP 伺服器的使用者名稱|傳送到 FTP 伺服器的密碼|
|--------------------|--------------------|---------------------------------|---------------------------------|
|Null 或 ""|Null 或 ""|匿名|使用者的電子郵件名稱|
|非 Null 字串|Null 或 ""|*pstrUserName*|" "|
|NULL |非 Null 字串|ERROR|ERROR|
|非 Null 字串|非 Null 字串|*pstrUserName*|*pstrPassword*|

*dwFlags*<br/>
`INTERNET_FLAG_*` 旗標的任何組合。 如需*dwFlags*值的說明，請參閱[CHttpConnection：： OpenRequest](#openrequest)的「**備註**」一節中的表格。

### <a name="remarks"></a>備註

您永遠不會直接建立 `CHttpConnection`。 相反地，您可以藉由呼叫[CInternetSession：： GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection)來建立物件。

##  <a name="openrequest"></a>CHttpConnection：： OpenRequest

呼叫這個成員函式以開啟 HTTP 連接。

```
CHttpFile* OpenRequest(
    LPCTSTR pstrVerb,
    LPCTSTR pstrObjectName,
    LPCTSTR pstrReferer = NULL,
    DWORD_PTR dwContext = 1,
    LPCTSTR* ppstrAcceptTypes = NULL,
    LPCTSTR pstrVersion = NULL,
    DWORD dwFlags = INTERNET_FLAG_EXISTING_CONNECT);

CHttpFile* OpenRequest(
    int nVerb,
    LPCTSTR pstrObjectName,
    LPCTSTR pstrReferer = NULL,
    DWORD_PTR dwContext = 1,
    LPCTSTR* ppstrAcceptTypes = NULL,
    LPCTSTR pstrVersion = NULL,
    DWORD dwFlags = INTERNET_FLAG_EXISTING_CONNECT);
```

### <a name="parameters"></a>參數

*pstrVerb*<br/>
字串的指標，其中包含要在要求中使用的動詞。 如果是 Null，則會使用 "GET"。

*pstrObjectName*<br/>
字串的指標，其中包含指定之動詞的目標物件。 這個字串通常是檔案名、可執行檔模組或搜尋規範。

*pstrReferer*<br/>
字串的指標，指定取得要求（*pstrObjectName*）中的 URL 之檔的位址（url）。 如果是 Null，則不會指定 HTTP 標頭。

*dwCoNtext*<br/>
`OpenRequest` 作業的內容識別碼。 如需*dwCoNtext*的詳細資訊，請參閱備註一節。

*ppstrAcceptTypes*<br/>
指向字串的 LPCTSTR 指標之 null 結束陣列的指標，表示用戶端接受的內容類型。 如果*ppstrAcceptTypes*為 Null，則伺服器會解讀用戶端只接受 "text/*" 類型的檔（也就是只有文字檔，而不是圖片或其他二進位檔）。 內容類型相當於 CGI 變數 CONTENT_TYPE，它會識別具有附加資訊之查詢的資料類型，例如 HTTP POST 和 PUT。

*pstrVersion*<br/>
定義 HTTP 版本之字串的指標。 如果是 Null，則會使用 "HTTP/1.0"。

*dwFlags*<br/>
INTERNET_ FLAG_ * 旗標的任何組合。 如需可能的*dwFlags*值的說明，請參閱備註一節。

*nVerb*<br/>
與 HTTP 要求類型相關聯的數位。 可以是下列其中一項：

|HTTP 要求類型|*nVerb*值|
|-----------------------|-------------------|
|HTTP_VERB_POST|0|
|HTTP_VERB_GET|1|
|HTTP_VERB_HEAD|2|
|HTTP_VERB_PUT|3|
|HTTP_VERB_LINK|4|
|HTTP_VERB_DELETE|5|
|HTTP_VERB_UNLINK|6|

### <a name="return-value"></a>傳回值

所要求[CHttpFile](../../mfc/reference/chttpfile-class.md)物件的指標。

### <a name="remarks"></a>備註

*dwFlags*可以是下列其中一項：

|網際網路旗標|描述|
|-------------------|-----------------|
|INTERNET_FLAG_RELOAD|強制從源伺服器下載要求的檔案、物件或目錄清單，而不是從快取。|
|INTERNET_FLAG_DONT_CACHE|不會將傳回的實體新增至快取。|
|INTERNET_FLAG_MAKE_PERSISTENT|將傳回的實體新增至快取，做為持續性實體。 這表示標準快取清除、一致性檢查或垃圾收集無法從快取中移除此專案。|
|INTERNET_FLAG_SECURE|會使用安全的交易語義。 它會轉譯為使用 SSL/PCT，而且只有在 HTTP 要求中有意義|
|INTERNET_FLAG_NO_AUTO_REDIRECT|僅搭配 HTTP 使用，指定不應在[CHttpFile：： SendRequest](../../mfc/reference/chttpfile-class.md#sendrequest)中自動處理重新導向。|

覆寫 `dwContext` 預設值，將內容識別碼設定為您所選擇的值。 內容識別碼會與[CInternetSession](../../mfc/reference/cinternetsession-class.md)物件所建立之 `CHttpConnection` 物件的這個特定作業相關聯。 此值會傳回[CInternetSession：： OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) ，以提供其識別之作業的狀態。 如需內容識別碼的詳細資訊，請參閱[網際網路第一個步驟： WinInet 一](../../mfc/wininet-basics.md)文。

使用此函式可能會擲回例外狀況。

## <a name="see-also"></a>另請參閱

[CInternetConnection 類別](../../mfc/reference/cinternetconnection-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CInternetConnection 類別](../../mfc/reference/cinternetconnection-class.md)<br/>
[CHttpFile 類別](../../mfc/reference/chttpfile-class.md)
