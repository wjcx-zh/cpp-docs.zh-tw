---
title: CInternetConnection 類別
ms.date: 11/04/2016
f1_keywords:
- CInternetConnection
- AFXINET/CInternetConnection
- AFXINET/CInternetConnection::CInternetConnection
- AFXINET/CInternetConnection::GetContext
- AFXINET/CInternetConnection::GetServerName
- AFXINET/CInternetConnection::GetSession
helpviewer_keywords:
- CInternetConnection [MFC], CInternetConnection
- CInternetConnection [MFC], GetContext
- CInternetConnection [MFC], GetServerName
- CInternetConnection [MFC], GetSession
ms.assetid: 62a5d1c3-8471-4e36-a064-48831829b2a7
ms.openlocfilehash: 6649986f279e010a833b31157922cb4fd1ea8613
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372417"
---
# <a name="cinternetconnection-class"></a>CInternetConnection 類別

管理您與網際網路伺服器的連接。

## <a name="syntax"></a>語法

```
class CInternetConnection : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[C 網路連線:C 網連線](#cinternetconnection)|建構 `CInternetConnection` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[C 網路連線:抓取內容](#getcontext)|獲取此連接物件的上下文 ID。|
|[C 網路連線::取得伺服器名稱](#getservername)|獲取與連接關聯的伺服器的名稱。|
|[C 網路連線:抓取工作階段](#getsession)|獲取指向與連接關聯的[CInternetSession](../../mfc/reference/cinternetsession-class.md)物件的指標。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[C網連接::運營商HINTERNET](#operator_hinternet)|互聯網會話的句柄。|

## <a name="remarks"></a>備註

它是 MFC 類[CFtpConnection、CHTTPConnection](../../mfc/reference/cftpconnection-class.md)和[CGopherConnection](../../mfc/reference/cgopherconnection-class.md)的基類。 [CHttpConnection](../../mfc/reference/chttpconnection-class.md) 每個類都提供了與相應的 FTP、HTTP 或 gopher 伺服器通訊的其他功能。

要直接與 Internet 伺服器通訊,您必須具有[CInternetSession](../../mfc/reference/cinternetsession-class.md)物件和`CInternetConnection`物件。

要瞭解有關 WinInet 類別的資訊,請參閱[使用 WinInet 進行 Internet 編程的文章](../../mfc/win32-internet-extensions-wininet.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

`CInternetConnection`

## <a name="requirements"></a>需求

**標題:** afxinet.h

## <a name="cinternetconnectioncinternetconnection"></a><a name="cinternetconnection"></a>C 網路連線:C 網連線

創建`CInternetConnection`物件時將調用此成員函數。

```
CInternetConnection(
    CInternetSession* pSession,
    LPCTSTR pstrServer,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>參數

*p 工作階段*<br/>
指向[CInternetSession](../../mfc/reference/cinternetsession-class.md)物件的指標。

*pstrServer*<br/>
指向包含伺服器名稱的字串的指標。

*n波特*<br/>
標識此連接的 Internet 連接埠的數位。

*dwContext*<br/>
`CInternetConnection`物件的上下文標識碼。 關於*dwContext*的詳細資訊,請參閱**備註**。

### <a name="remarks"></a>備註

你從來不叫`CInternetConnection`自己;相反,請呼叫[CInternetSession](../../mfc/reference/cinternetsession-class.md)成員函數,表示要建立的連線類型:

- [C 網際網路工作階段::取得Ftp連接](../../mfc/reference/cinternetsession-class.md#getftpconnection)

- [C 網際網路工作階段::取得HTTP連接](../../mfc/reference/cinternetsession-class.md#gethttpconnection)

- [C 網路工作階段::取得 Gopher 連接](../../mfc/reference/cinternetsession-class.md#getgopherconnection)

mFC 將*dwContext*的預設值`CInternetConnection`發送到創建**InternetConnection**派生物件的[CInternetSession](../../mfc/reference/cinternetsession-class.md)物件的派生物件。 預設值設定為 1;將預設值設定為 1但是,您可以在連接的[CInternetSession](../../mfc/reference/cinternetsession-class.md#cinternetsession)建構函數中顯式分配特定的上下文標識符。 物件及其執行的任何工作都將與該上下文 ID 相關聯。 上下文標識符返回到[CInternetSession::onStatusBackononononononback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)提供標識它的物件的狀態。 有關上下文標識符的詳細資訊[,請參閱"Internet 第一步:WinInet"](../../mfc/wininet-basics.md)一文。

## <a name="cinternetconnectiongetcontext"></a><a name="getcontext"></a>C 網路連線:抓取內容

調用此成員函數獲取此會話的上下文 ID。

```
DWORD_PTR GetContext() const;
```

### <a name="return-value"></a>傳回值

應用程式分配的上下文 ID。

### <a name="remarks"></a>備註

內容代碼最初在[CInternetSession](../../mfc/reference/cinternetsession-class.md)中指定`CInternetConnection`, 並傳播到 - 和[CInternetFile](../../mfc/reference/cinternetfile-class.md)派生類,除非在調用打開連接的函數時以不同方式指定。 上下文 ID 與給定物件的任何操作相關聯,並標識 CInternetSession 返回的操作的狀態資訊[::onStatusCallback。](../../mfc/reference/cinternetsession-class.md#onstatuscallback)

有關如何使用`GetContext`其他 WinInet 類提供使用者狀態資訊的詳細資訊,請參閱文章[「Internet 第一步:WinInet」](../../mfc/wininet-basics.md)瞭解有關上下文標識符的詳細資訊。

## <a name="cinternetconnectiongetservername"></a><a name="getservername"></a>C 網路連線::取得伺服器名稱

呼叫此成員函數獲取與此 Internet 連接關聯的伺服器的名稱。

```
CString GetServerName() const;
```

### <a name="return-value"></a>傳回值

此連接物件正在使用的伺服器的名稱。

## <a name="cinternetconnectiongetsession"></a><a name="getsession"></a>C 網路連線:抓取工作階段

呼叫此成員函數以獲取指向與此連接關聯的`CInternetSession`物件的指標。

```
CInternetSession* GetSession() const;
```

### <a name="return-value"></a>傳回值

指向與此 Internet 連接物件關聯的[CInternetSession](../../mfc/reference/cinternetsession-class.md)物件的指標。

## <a name="cinternetconnectionoperator-hinternet"></a><a name="operator_hinternet"></a>C網連接::運營商HINTERNET

使用此運算元獲取當前 Internet 會話的 API 級句柄。

```
operator HINTERNET() const;
```

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
