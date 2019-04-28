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
ms.openlocfilehash: 9f17c3ade53ec45ddde654e83c77fe1d817d8495
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62345691"
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
|[CInternetConnection::CInternetConnection](#cinternetconnection)|建構 `CInternetConnection` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CInternetConnection::GetContext](#getcontext)|取得這個連線物件的內容識別碼。|
|[CInternetConnection::GetServerName](#getservername)|取得與連接相關聯的伺服器名稱。|
|[CInternetConnection::GetSession](#getsession)|取得指標[CInternetSession](../../mfc/reference/cinternetsession-class.md)與連接相關聯的物件。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CInternetConnection::operator HINTERNET](#operator_hinternet)|網際網路工作階段控制代碼。|

## <a name="remarks"></a>備註

它是 MFC 類別的基底類別[CFtpConnection](../../mfc/reference/cftpconnection-class.md)， [CHttpConnection](../../mfc/reference/chttpconnection-class.md)，並[CGopherConnection](../../mfc/reference/cgopherconnection-class.md)。 每個類別提供額外的功能與個別的 FTP、 HTTP 或 gopher 伺服器通訊。

若要直接與網際網路伺服器通訊，您必須擁有[CInternetSession](../../mfc/reference/cinternetsession-class.md)物件和`CInternetConnection`物件。

若要深入了解如何 WinInet 類別都能，請參閱文章[網際網路程式設計 WinInet](../../mfc/win32-internet-extensions-wininet.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

`CInternetConnection`

## <a name="requirements"></a>需求

**標頭：** afxinet.h

##  <a name="cinternetconnection"></a>  CInternetConnection::CInternetConnection

此成員函式時，會呼叫`CInternetConnection`建立物件。

```
CInternetConnection(
    CInternetSession* pSession,
    LPCTSTR pstrServer,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>參數

*pSession*<br/>
指標[CInternetSession](../../mfc/reference/cinternetsession-class.md)物件。

*pstrServer*<br/>
包含伺服器名稱的字串指標。

*nPort*<br/>
識別此連線的網際網路連接埠的數字。

*dwContext*<br/>
內容識別碼`CInternetConnection`物件。 請參閱**備註**如需詳細資訊*dwContext*。

### <a name="remarks"></a>備註

您永遠不會呼叫`CInternetConnection`自行; 相反地，呼叫[CInternetSession](../../mfc/reference/cinternetsession-class.md)您想要建立的連線類型的成員函式：

- [CInternetSession::GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection)

- [CInternetSession::GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection)

- [CInternetSession::GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection)

預設值*dwContext* MFC，以便傳送`CInternetConnection`-衍生的物件，從[CInternetSession](../../mfc/reference/cinternetsession-class.md)物件建立**InternetConnection**-在衍生的物件。 預設值設為 1。不過，您可以明確指派的特定內容識別項[CInternetSession](../../mfc/reference/cinternetsession-class.md#cinternetsession)建構函式的連接。 物件，而且它沒有任何工作將會與該內容識別碼相關聯 內容識別碼會傳回到[CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)來提供，它識別之物件的狀態。 請參閱文章[網際網路前幾個步驟：WinInet](../../mfc/wininet-basics.md)取得的內容識別碼的詳細資訊。

##  <a name="getcontext"></a>  CInternetConnection::GetContext

呼叫此成員函式，以取得此工作階段的內容識別碼。

```
DWORD_PTR GetContext() const;
```

### <a name="return-value"></a>傳回值

使用應用程式指派的內容識別碼。

### <a name="remarks"></a>備註

中原本指定的內容 ID [CInternetSession](../../mfc/reference/cinternetsession-class.md)並將傳播到`CInternetConnection`-並[CInternetFile](../../mfc/reference/cinternetfile-class.md)-除非開啟函式呼叫中所指定以不同的方式衍生的類別，連接。 內容識別碼是否與指定任何的物件作業相關聯，以及識別傳回作業的狀態資訊[CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)。

如需有關如何`GetContext`適用於其他 WinInet 類別，以提供使用者的狀態資訊，請參閱文章[網際網路前幾個步驟：WinInet](../../mfc/wininet-basics.md)取得的內容識別碼的詳細資訊。

##  <a name="getservername"></a>  CInternetConnection::GetServerName

呼叫此成員函式，以取得與這個網際網路連接相關聯的伺服器名稱。

```
CString GetServerName() const;
```

### <a name="return-value"></a>傳回值

此連接物件正在使用的伺服器名稱。

##  <a name="getsession"></a>  CInternetConnection::GetSession

呼叫以取得變數的指標，此成員函式`CInternetSession`與此連線相關聯的物件。

```
CInternetSession* GetSession() const;
```

### <a name="return-value"></a>傳回值

指標[CInternetSession](../../mfc/reference/cinternetsession-class.md)這個網際網路連線物件相關聯的物件。

##  <a name="operator_hinternet"></a>  CInternetConnection::operator HINTERNET

您可以使用這個運算子來取得目前的網際網路工作階段的 API 層級控制代碼。

```
operator HINTERNET() const;
```

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
