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
ms.openlocfilehash: af402b532b3aba28bdfefea5afa67331765db4c5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81351821"
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
|[CHTTP連接::CHTTP連接](#chttpconnection)|建立 `CHttpConnection` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CHttpConnection::OpenRequest](#openrequest)|打開 HTTP 請求。|

## <a name="remarks"></a>備註

HTTP 是 MFC WinInet 類實現的三個 Internet 伺服器協定之一。

該類`CHttpConnection`包含一個建構函數和一個成員函數[OpenRequest](#openrequest),用於管理與具有 HTTP 協定的伺服器的連接。

要與 HTTP 伺服器通訊,必須首先創建[CInternetSession](../../mfc/reference/cinternetsession-class.md)的實例,然後創建[CHTTPConnect](#chttpconnection)物件。 您從不直接創建`CHttpConnection`物件;相反,調用[CInternetSession::GetHTTPConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection)`CHttpConnection`,它 創建物件並返回指向它的指標。

要瞭解有關如何`CHttpConnection`與其他 MFC Internet 類合作,請參閱[WinInet](../../mfc/win32-internet-extensions-wininet.md)的 Internet 程式設計文章。 有關使用其他兩個受支援的 Internet 協定(gopher 和 FTP)連接到伺服器的詳細資訊,請參閱[CGopherConnection](../../mfc/reference/cgopherconnection-class.md)和[CFtpConnection](../../mfc/reference/cftpconnection-class.md)的類。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)

`CHttpConnection`

## <a name="requirements"></a>需求

**標題:** afxinet.h

## <a name="chttpconnectionchttpconnection"></a><a name="chttpconnection"></a>CHTTP連接::CHTTP連接

呼叫此成員函數以建構物件`CHttpConnection`。

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

*p 工作階段*<br/>
指向[CInternetSession](../../mfc/reference/cinternetsession-class.md)物件的指標。

*h 連線*<br/>
互聯網連接的句柄。

*pstrServer*<br/>
指向包含伺服器名稱的字串的指標。

*dwContext*<br/>
`CInternetConnection`物件的上下文標識碼。 有關*dwContext*的詳細資訊,請參閱**備註**部分。

*n波特*<br/>
標識此連接的 Internet 連接埠的數位。

*pstrUser 名稱*<br/>
指向 null 終止字串的指標,該字串指定要登錄的使用者的名稱。 如果為 NULL,則預設值為匿名。

*pstr密碼*<br/>
指向 null 終止字串的指標,用於指定用於登入的密碼。 如果*pstrPassword*和*pstrUserName*均為 NULL,則預設的匿名密碼是使用者的電子郵件名稱。 如果*pstrPassword*為 NULL 或空字串,但*pstrUserName*不是 NULL,則使用空白密碼。 下表描述了*pstrUserName*和*pstrPassword*的四種可能設定的行為:

|*pstrUser 名稱*|*pstr密碼*|傳送 FTP 伺服器的使用者名稱|傳送 FTP 伺服器的密碼|
|--------------------|--------------------|---------------------------------|---------------------------------|
|NULL 或""|NULL 或""|"匿名"|使用者的電子郵件名稱|
|NULL 字串|NULL 或""|*pstrUser 名稱*|" "|
|NULL |NULL 字串|ERROR|ERROR|
|NULL 字串|NULL 字串|*pstrUser 名稱*|*pstr密碼*|

*dwFlags*<br/>
標誌的`INTERNET_FLAG_*`任意組合。 請參閱[CHTTPConnection::打開請求的備](#openrequest)**註**部分中的表,瞭解*dwFlags*值的說明。

### <a name="remarks"></a>備註

您從不直接建立`CHttpConnection`。 相反,您可以通過調用[CInternetSession::getHTTPConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection)來創建物件。

## <a name="chttpconnectionopenrequest"></a><a name="openrequest"></a>CHTTP連接::開啟請求

調用此成員函數以打開 HTTP 連接。

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

*普斯特維爾布*<br/>
指向包含要在請求中使用的謂詞的字串的指標。 如果為 NULL,則使用"GET"

*pstrObject 名稱*<br/>
指向包含指定謂詞的目標物件的字串的指標。 此字串通常是檔名、可執行模組或搜索指定器。

*普斯特克弗*<br/>
指向字串的指標,用於指定從中獲取*請求中的*URL 的文件的位址 (URL) 的指標。 如果 NULL,則未指定 HTTP 標頭。

*dwContext*<br/>
操作的`OpenRequest`上下文標識碼。 有關*dwContext*的詳細資訊,請參閱備註部分。

*ppstr 接受類型*<br/>
指向 LPCTSTR 的 null 端結束的陣列的指標指向指示用戶端接受的內容類型的字串。 如果*ppstrAcceptType*為 NULL,則伺服器將解釋用戶端僅接受類型為「文本/*」的文件(即,僅接受文本文檔,而不是圖片或其他二進位檔案)。 內容類型等效於 CGI 變數CONTENT_TYPE,該變數標識具有附加資訊的查詢(如 HTTP POST 和 PUT)的數據類型。

*普斯特裡斯特*<br/>
指向定義 HTTP 版本的字串的指標。 如果為 NULL,則使用" HTTP/1.0"

*dwFlags*<br/>
INTERNET_FLAG_* 標誌的任意組合。 有關可能的*dwFlags*值的說明,請參閱備註部分。

*nVerb*<br/>
與 HTTP 請求類型關聯的數位。 可以是下列其中一項：

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

請求的指向[CHttpFile](../../mfc/reference/chttpfile-class.md)物件的指標。

### <a name="remarks"></a>備註

*dwFlags*可以是以下原因之一:

|網際網路標誌|描述|
|-------------------|-----------------|
|INTERNET_FLAG_RELOAD|強制從源伺服器而不是從快取下載請求的檔案、物件或目錄清單。|
|INTERNET_FLAG_DONT_CACHE|不會將返回的實體添加到緩存中。|
|INTERNET_FLAG_MAKE_PERSISTENT|將返回的實體作為持久實體添加到緩存中。 這意味著標準快取清理、一致性檢查或垃圾回收無法從緩存中刪除此項。|
|INTERNET_FLAG_SECURE|使用安全事務語義。 它轉換為使用 SSL/PCT,僅在 HTTP 請求中有意義|
|INTERNET_FLAG_NO_AUTO_REDIRECT|只與 HTTP 一起使用,指定不應在[CHttpFile 中自動處理重定向::寄送請求](../../mfc/reference/chttpfile-class.md#sendrequest)。|

覆蓋`dwContext`預設值,將上下文識別碼設定為您選擇的值。 上下文識別碼`CHttpConnection`[與其 CInternetSession](../../mfc/reference/cinternetsession-class.md)對象創建的物件的此特定操作相關聯。 該值將返回到[CInternetSession::onStatusBack,](../../mfc/reference/cinternetsession-class.md#onstatuscallback)以提供標識該值的操作的狀態。 有關上下文標識符的詳細資訊[,請參閱"Internet 第一步:WinInet"](../../mfc/wininet-basics.md)一文。

此函數可能會引發異常。

## <a name="see-also"></a>另請參閱

[CInternetConnection 類別](../../mfc/reference/cinternetconnection-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CInternetConnection 類別](../../mfc/reference/cinternetconnection-class.md)<br/>
[CHttpFile 類別](../../mfc/reference/chttpfile-class.md)
