---
title: CHttpConnection 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CHttpConnection
- AFXINET/CHttpConnection
- AFXINET/CHttpConnection::CHttpConnection
- AFXINET/CHttpConnection::OpenRequest
dev_langs:
- C++
helpviewer_keywords:
- CHttpConnection [MFC], CHttpConnection
- CHttpConnection [MFC], OpenRequest
ms.assetid: a402b662-c445-4988-800d-c8278551babe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 18439e33eed4181ebf3f2619226b132721babcc7
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50073563"
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
|[CHttpConnection::CHttpConnection](#chttpconnection)|建立 `CHttpConnection` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[Chttpconnection::](#openrequest)|會開啟 HTTP 要求。|

## <a name="remarks"></a>備註

HTTP 是其中一個 MFC WinInet 類別所實作的三種網際網路伺服器通訊協定。

此類別`CHttpConnection`包含建構函式和一個成員函式[OpenRequest](#openrequest)，可管理使用 HTTP 通訊協定與伺服器連接。

若要與 HTTP 伺服器通訊，您必須先建立的執行個體[CInternetSession](../../mfc/reference/cinternetsession-class.md)，然後建立[CHttpConnection](#_mfc_chttpconnection)物件。 您永遠不會建立`CHttpConnection`直接物件; 而是呼叫[cinternetsession:: Gethttpconnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection)，這會建立`CHttpConnection`物件，並傳回的指標。

若要進一步了解如何`CHttpConnection`運作方式與其他 MFC 網際網路類別，請參閱文章[網際網路程式設計 WinInet](../../mfc/win32-internet-extensions-wininet.md)。 如需連接至使用其他兩個伺服器的詳細資訊支援網際網路通訊協定、 gopher 和 FTP，請參閱類別[CGopherConnection](../../mfc/reference/cgopherconnection-class.md)並[CFtpConnection](../../mfc/reference/cftpconnection-class.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)

`CHttpConnection`

## <a name="requirements"></a>需求

**標頭：** afxinet.h

##  <a name="chttpconnection"></a>  CHttpConnection::CHttpConnection

此成員函式呼叫來建構`CHttpConnection`物件。

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
指標[CInternetSession](../../mfc/reference/cinternetsession-class.md)物件。

*hConnected*<br/>
網際網路連線控制代碼。

*pstrServer*<br/>
包含伺服器名稱的字串指標。

*dwContext*<br/>
內容識別碼`CInternetConnection`物件。 請參閱**備註**如需詳細資訊*dwContext*。

*nPort*<br/>
識別此連線的網際網路連接埠的數字。

*pstrUserName*<br/>
以 null 終止的字串，指定要登入的使用者名稱的指標。 如果是 NULL，則預設會為匿名。

*pstrPassword*<br/>
以 null 終止的字串，指定要用來登入密碼的指標。 如果兩個*pstrPassword*並*pstrUserName*為 NULL 時，預設匿名密碼是使用者的電子郵件名稱。 如果*pstrPassword*是 NULL （或空字串），但*pstrUserName*不是 NULL，則使用空白密碼。 下表描述的四個可能的設定行為*pstrUserName*並*pstrPassword*:

|*pstrUserName*|*pstrPassword*|傳送至 FTP 伺服器的使用者名稱|傳送至 FTP 伺服器的密碼|
|--------------------|--------------------|---------------------------------|---------------------------------|
|NULL 或""|NULL 或""|「 匿名 」|使用者的電子郵件名稱|
|非 NULL 字串|NULL 或""|*pstrUserName*|" "|
|NULL 的非 NULL 字串|錯誤|錯誤||
|非 NULL 字串|非 NULL 字串|*pstrUserName*|*pstrPassword*|

*dwFlags*<br/>
任何組合`INTERNET_FLAG_*`旗標。 請參閱表格**備註**一節[chttpconnection::](#openrequest)的說明*dwFlags*值。

### <a name="remarks"></a>備註

您永遠不會建立`CHttpConnection`直接。 相反地，您藉由呼叫，會在建立物件時[cinternetsession:: Gethttpconnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection)。

##  <a name="openrequest"></a>  Chttpconnection::

呼叫此成員函式可開啟 HTTP 連線。

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
包含要在要求中使用的動詞命令的字串指標。 如果是 NULL，會使用 「 取得 」。

*pstrObjectName*<br/>
字串，包含指定的動詞命令的目標物件的指標。 這通常是檔案名稱、 可執行檔的模組或搜尋規範。

*pstrReferer*<br/>
字串，指定來源文件的位址 (URL) 的指標中要求的 URL ( *pstrObjectName*) 取得。 如果是 NULL，指定沒有 HTTP 標頭。

*dwContext*<br/>
內容識別碼`OpenRequest`作業。 請參閱 < 備註 > 一節的詳細資訊，關於*dwContext*。

*ppstrAcceptTypes*<br/>
以 null 結束陣列 LPCTSTR 指出用戶端接受的內容類型的字串指標的指標。 如果*ppstrAcceptTypes*是 NULL 時，伺服器會解譯，用戶端只接受類型的文件 」 文字 / *"（也就是只有文字文件和未圖片或其他二進位檔）。 內容類型相當於 CGI 變數有效，識別已連接資訊，例如 HTTP POST 和 PUT 的查詢資料的型別。

*pstrVersion*<br/>
定義的 HTTP 版本字串的指標。 如果是 NULL，則會使用 HTTP / 「 1.0 」。

*dwFlags*<br/>
INTERNET_ FLAG_ * 旗標的任意組合。 請參閱 < 備註 > 一節，如需可能的描述*dwFlags*值。

*nVerb*<br/>
與 HTTP 要求類型相關聯的數字。 可以是下列其中一項：

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

指標[CHttpFile](../../mfc/reference/chttpfile-class.md)要求物件。

### <a name="remarks"></a>備註

*dwFlags*可以是下列其中之一：

|網際網路旗標|描述|
|-------------------|-----------------|
|INTERNET_FLAG_RELOAD|從原始伺服器，而不是從快取，請強制的下載要求的檔案、 物件或目錄清單。|
|INTERNET_FLAG_DONT_CACHE|不會新增至快取傳回的實體。|
|INTERNET_FLAG_MAKE_PERSISTENT|將傳回的實體加入至快取中，做為持續性的實體。 這表示，標準版快取清除、 一致性檢查，或回收無法移除此項目從快取。|
|INTERNET_FLAG_SECURE|使用安全的交易語意。 這會轉譯成使用 SSL/百分比，才有意義的 HTTP 要求|
|INTERNET_FLAG_NO_AUTO_REDIRECT|只適用於 HTTP、 指定的重新導向應該不會自動以處理[CHttpFile::SendRequest](../../mfc/reference/chttpfile-class.md#sendrequest)。|

覆寫`dwContext`預設可設定的內容識別碼以您選擇的值。 內容識別碼是與這個特定作業的相關聯`CHttpConnection`所建立的物件及其[CInternetSession](../../mfc/reference/cinternetsession-class.md)物件。 若要傳回的值[CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)來提供與識別此作業的狀態。 請參閱文章[網際網路前幾個步驟： WinInet](../../mfc/wininet-basics.md)取得的內容識別碼的詳細資訊。

此函式可能擲回例外狀況。

## <a name="see-also"></a>另請參閱

[CInternetConnection 類別](../../mfc/reference/cinternetconnection-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CInternetConnection 類別](../../mfc/reference/cinternetconnection-class.md)<br/>
[CHttpFile 類別](../../mfc/reference/chttpfile-class.md)
