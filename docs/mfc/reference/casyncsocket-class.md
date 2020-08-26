---
title: CAsyncSocket 類別
ms.date: 06/25/2020
f1_keywords:
- CAsyncSocket
- AFXSOCK/CAsyncSocket
- AFXSOCK/CAsyncSocket::CAsyncSocket
- AFXSOCK/CAsyncSocket::Accept
- AFXSOCK/CAsyncSocket::AsyncSelect
- AFXSOCK/CAsyncSocket::Attach
- AFXSOCK/CAsyncSocket::Bind
- AFXSOCK/CAsyncSocket::Close
- AFXSOCK/CAsyncSocket::Connect
- AFXSOCK/CAsyncSocket::Create
- AFXSOCK/CAsyncSocket::Detach
- AFXSOCK/CAsyncSocket::FromHandle
- AFXSOCK/CAsyncSocket::GetLastError
- AFXSOCK/CAsyncSocket::GetPeerName
- AFXSOCK/CAsyncSocket::GetPeerNameEx
- AFXSOCK/CAsyncSocket::GetSockName
- AFXSOCK/CAsyncSocket::GetSockNameEx
- AFXSOCK/CAsyncSocket::GetSockOpt
- AFXSOCK/CAsyncSocket::IOCtl
- AFXSOCK/CAsyncSocket::Listen
- AFXSOCK/CAsyncSocket::Receive
- AFXSOCK/CAsyncSocket::ReceiveFrom
- AFXSOCK/CAsyncSocket::ReceiveFromEx
- AFXSOCK/CAsyncSocket::Send
- AFXSOCK/CAsyncSocket::SendTo
- AFXSOCK/CAsyncSocket::SendToEx
- AFXSOCK/CAsyncSocket::SetSockOpt
- AFXSOCK/CAsyncSocket::ShutDown
- AFXSOCK/CASyncSocket::Socket
- AFXSOCK/CAsyncSocket::OnAccept
- AFXSOCK/CAsyncSocket::OnClose
- AFXSOCK/CAsyncSocket::OnConnect
- AFXSOCK/CAsyncSocket::OnOutOfBandData
- AFXSOCK/CAsyncSocket::OnReceive
- AFXSOCK/CAsyncSocket::OnSend
- AFXSOCK/CAsyncSocket::m_hSocket
helpviewer_keywords:
- CAsyncSocket [MFC], CAsyncSocket
- CAsyncSocket [MFC], Accept
- CAsyncSocket [MFC], AsyncSelect
- CAsyncSocket [MFC], Attach
- CAsyncSocket [MFC], Bind
- CAsyncSocket [MFC], Close
- CAsyncSocket [MFC], Connect
- CAsyncSocket [MFC], Create
- CAsyncSocket [MFC], Detach
- CAsyncSocket [MFC], FromHandle
- CAsyncSocket [MFC], GetLastError
- CAsyncSocket [MFC], GetPeerName
- CAsyncSocket [MFC], GetPeerNameEx
- CAsyncSocket [MFC], GetSockName
- CAsyncSocket [MFC], GetSockNameEx
- CAsyncSocket [MFC], GetSockOpt
- CAsyncSocket [MFC], IOCtl
- CAsyncSocket [MFC], Listen
- CAsyncSocket [MFC], Receive
- CAsyncSocket [MFC], ReceiveFrom
- CAsyncSocket [MFC], ReceiveFromEx
- CAsyncSocket [MFC], Send
- CAsyncSocket [MFC], SendTo
- CAsyncSocket [MFC], SendToEx
- CAsyncSocket [MFC], SetSockOpt
- CAsyncSocket [MFC], ShutDown
- CASyncSocket [MFC], Socket
- CAsyncSocket [MFC], OnAccept
- CAsyncSocket [MFC], OnClose
- CAsyncSocket [MFC], OnConnect
- CAsyncSocket [MFC], OnOutOfBandData
- CAsyncSocket [MFC], OnReceive
- CAsyncSocket [MFC], OnSend
- CAsyncSocket [MFC], m_hSocket
ms.assetid: cca4d5a1-aa0f-48bd-843e-ef0e2d7fc00b
ms.openlocfilehash: cac3a95734a60252f241ab3080c05c65a9e04723
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88841645"
---
# <a name="casyncsocket-class"></a>CAsyncSocket 類別

代表 Windows 通訊端，也就是網路通訊的端點。

## <a name="syntax"></a>語法

```
class CAsyncSocket : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CAsyncSocket：： CAsyncSocket](#casyncsocket)|建構 `CAsyncSocket` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAsyncSocket：： Accept](#accept)|接受通訊端上的連接。|
|[CAsyncSocket：： AsyncSelect](#asyncselect)|要求通訊端的事件通知。|
|[CAsyncSocket：： Attach](#attach)|將通訊端控制碼附加至 `CAsyncSocket` 物件。|
|[CAsyncSocket：： Bind](#bind)|將本機位址與通訊端產生關聯。|
|[CAsyncSocket：： Close](#close)|關閉通訊端。|
|[CAsyncSocket：： Connect](#connect)|建立對等通訊端的連接。|
|[CAsyncSocket::Create](#create)|建立通訊端。|
|[CAsyncSocket：： CreateEx](#createex)|建立具有 advanced 選項的通訊端。|
|[CAsyncSocket：:D etach](#detach)|從物件卸離通訊端控制碼 `CAsyncSocket` 。|
|[CAsyncSocket：： FromHandle](#fromhandle)|`CAsyncSocket`傳回物件的指標，指定 socket 控制碼。|
|[CAsyncSocket：： GetLastError](#getlasterror)|取得上次失敗作業的錯誤狀態。|
|[CAsyncSocket：： GetPeerName](#getpeername)|取得通訊端所連接之對等通訊端的位址。|
|[CAsyncSocket：： GetPeerNameEx](#getpeernameex)|取得通訊端所連接之對等通訊端的位址 (處理) 的 IPv6 位址。|
|[CAsyncSocket：： GetSockName](#getsockname)|取得通訊端的本機名稱。|
|[CAsyncSocket：： GetSockNameEx](#getsocknameex)|取得通訊端 (處理 IPv6 位址) 的本機名稱。|
|[CAsyncSocket：： GetSockOpt](#getsockopt)|捕獲通訊端選項。|
|[CAsyncSocket：： IOCtl](#ioctl)|控制通訊端的模式。|
|[CAsyncSocket：：接聽](#listen)|建立通訊端來接聽連入連線要求。|
|[CAsyncSocket：： Receive](#receive)|從通訊端接收資料。|
|[CAsyncSocket：： ReceiveFrom](#receivefrom)|接收資料包並儲存來源位址。|
|[CAsyncSocket：： ReceiveFromEx](#receivefromex)|接收資料包並儲存來源位址， (處理 IPv6 位址) 。|
|[CAsyncSocket：： Send](#send)|將資料傳送到已連線的通訊端。|
|[CAsyncSocket：： SendTo](#sendto)|將資料傳送至特定目的地。|
|[CAsyncSocket：： SendToEx](#sendtoex)|將資料傳送至特定目的地 (處理 IPv6 位址) 。|
|[CAsyncSocket：： SetSockOpt](#setsockopt)|設定通訊端選項。|
|[CAsyncSocket：： ShutDown](#shutdown)|`Send`在通訊端上停用和/或 `Receive` 呼叫。|
|[CASyncSocket：： Socket](#socket)|配置通訊端控制碼。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CAsyncSocket：： OnAccept](#onaccept)|通知接聽通訊端，它可以藉由呼叫來接受擱置的連接要求 `Accept` 。|
|[CAsyncSocket：： OnClose](#onclose)|通知通訊端與其連接的通訊端已關閉。|
|[CAsyncSocket：： OnConnect](#onconnect)|通知連接的通訊端連接嘗試已完成，不論成功或發生錯誤。|
|[CAsyncSocket：： OnOutOfBandData](#onoutofbanddata)|通知接收通訊端有頻外資料在通訊端上讀取，通常是緊急訊息。|
|[CAsyncSocket：： OnReceive](#onreceive)|藉由呼叫來通知接聽通訊端有資料可供取出 `Receive` 。|
|[CAsyncSocket：： OnSend](#onsend)|通知通訊端它可以藉由呼叫來傳送資料 `Send` 。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CAsyncSocket：： operator =](#operator_eq)|將新值指派給 `CAsyncSocket` 物件。|
|[CAsyncSocket：： operator 通訊端](#operator_socket)|使用這個運算子來取得物件的通訊端控制碼 `CAsyncSocket` 。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CAsyncSocket：： m_hSocket](#m_hsocket)|指出附加至此物件的通訊端控制碼 `CAsyncSocket` 。|

## <a name="remarks"></a>備註

類別會 `CAsyncSocket` 封裝 Windows 通訊端函式 API，為想要搭配使用 Windows 通訊端與 MFC 的程式設計人員提供物件導向的抽象概念。

此類別是根據您瞭解網路通訊的假設。 您必須負責處理封鎖、位元組順序的差異，以及 Unicode 和多位元組字元集之間的轉換 (MBCS) 字串。 如果您想要更方便的介面來為您管理這些問題，請參閱類別 [CSocket](../../mfc/reference/csocket-class.md)。

若要使用 `CAsyncSocket` 物件，請呼叫它的函式，然後呼叫 [create](#create) 函式來建立基礎通訊端控制碼 (類型 `SOCKET`) ，但已接受的通訊端除外。 如果是伺服器通訊端，請呼叫 [接聽](#listen) 成員函式，而針對用戶端通訊端，則呼叫 [Connect](#connect) 成員函式。 伺服器通訊端應該在收到連接要求時呼叫 [Accept](#accept) 函數。 使用剩餘的函式 `CAsyncSocket` 來執行通訊端之間的通訊。 完成時， `CAsyncSocket` 如果物件是在堆積上建立，則終結物件; 此函式會自動呼叫 [Close](#close) 函數。 通訊端資料類型會在 [Windows 通訊端：背景](../../mfc/windows-sockets-background.md)一文中說明。

> [!NOTE]
> 在靜態連結的 MFC 應用程式中使用次要執行緒中的 MFC 通訊端時，您必須 `AfxSocketInit` 在使用通訊端的每個執行緒中呼叫，以初始化通訊端程式庫。 根據預設， `AfxSocketInit` 只會在主要執行緒中呼叫。

如需詳細資訊，請參閱 [Windows 通訊端：使用類別 CAsyncSocket](../../mfc/windows-sockets-using-class-casyncsocket.md) 和相關文章，以及 [windows 通訊端 2 API](/windows/win32/WinSock/windows-sockets-start-page-2)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

`CAsyncSocket`

## <a name="requirements"></a>規格需求

**標頭：** afxsock。h

## <a name="casyncsocketaccept"></a><a name="accept"></a> CAsyncSocket：： Accept

呼叫此成員函式以接受通訊端上的連接。

```
virtual BOOL Accept(
    CAsyncSocket& rConnectedSocket,
    SOCKADDR* lpSockAddr = NULL,
    int* lpSockAddrLen = NULL);
```

### <a name="parameters"></a>參數

*rConnectedSocket*<br/>
識別可供連接之新通訊端的參考。

*lpSockAddr*<br/>
[SOCKADDR](/windows/win32/winsock/sockaddr-2)結構的指標，此結構會接收網路上已知的連接通訊端位址。 *LpSockAddr*引數的確切格式取決於建立通訊端時所建立的位址系列。 如果 *lpSockAddr* 和/或 *lpSockAddrLen* 等於 Null，則不會傳回已接受之通訊端遠端位址的相關資訊。

*lpSockAddrLen*<br/>
*LpSockAddr*中位址長度的指標（以位元組為單位）。 *LpSockAddrLen*是值結果參數：它一開始應該包含*lpSockAddr*所指向的空間量;傳回時，會包含所傳回位址的實際長度 (位元組) 。

### <a name="return-value"></a>傳回值

如果函式成功，則為非零;否則為0，而且可以藉由呼叫 [GetLastError](#getlasterror)來取出特定的錯誤碼。 下列錯誤適用于這個成員函式：

- WSANOTINITIALISED 成功的 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) 必須在使用此 API 之前進行。

- WSAENETDOWN Windows 通訊端執行偵測到網路子系統失敗。

- WSAEFAULT *lpSockAddrLen* 引數太小 (小於 [SOCKADDR](/windows/win32/winsock/sockaddr-2) 結構) 的大小。

- WSAEINPROGRESS 封鎖的 Windows 通訊端呼叫正在進行中。

- `Listen`未在接受之前叫用 WSAEINVAL。

- WSAEMFILE 輸入時，佇列是空的，而且沒有可用的描述項。

- WSAENOBUFS 沒有緩衝區空間可用。

- WSAENOTSOCK 描述項不是通訊端。

- WSAEOPNOTSUPP 參考的通訊端不是支援連接導向服務的類型。

- WSAEWOULDBLOCK 通訊端會標示為非封鎖，且不會有任何連線可接受。

### <a name="remarks"></a>備註

此常式會在暫止的連線佇列中，將第一個連接解壓縮，並以與此通訊端相同的屬性建立新的通訊端，並將其附加至 *rConnectedSocket*。 如果佇列中沒有擱置的連接，則會傳回 `Accept` 零，並傳回 `GetLastError` 錯誤。 接受的通訊端 ( *rConnectedSocket) * 不能用來接受更多連接。 原始通訊端會保持開啟並接聽。

引數 *lpSockAddr* 是以連接的通訊端位址填入的結果參數，如同通訊層的已知。 `Accept` 會搭配以連接為基礎的通訊端類型（例如 SOCK_STREAM）使用。

## <a name="casyncsocketasyncselect"></a><a name="asyncselect"></a> CAsyncSocket：： AsyncSelect

呼叫此成員函式以要求通訊端的事件通知。

```
BOOL AsyncSelect(long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```

### <a name="parameters"></a>參數

*lEvent*<br/>
位元遮罩，指定應用程式感興趣的網路事件組合。

- FD_READ 想要接收讀取就緒的通知。

- 當資料可供讀取時，FD_WRITE 想要收到通知。

- FD_OOB 想要接收頻外資料抵達的通知。

- FD_ACCEPT 想要接收連入連線的通知。

- FD_CONNECT 想要接收連接結果的通知。

- FD_CLOSE 想要在對等互連關閉通訊端時接收通知。

### <a name="return-value"></a>傳回值

如果函式成功，則為非零;否則為0，而且可以藉由呼叫 [GetLastError](#getlasterror)來取出特定的錯誤碼。 下列錯誤適用于這個成員函式：

- WSANOTINITIALISED 成功的 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) 必須在使用此 API 之前進行。

- WSAENETDOWN Windows 通訊端執行偵測到網路子系統失敗。

- WSAEINVAL 指出其中一個指定的參數無效。

- WSAEINPROGRESS 封鎖的 Windows 通訊端作業正在進行中。

### <a name="remarks"></a>備註

這個函式是用來指定要為通訊端呼叫哪些 MFC 回呼通知函數。 `AsyncSelect` 自動將此通訊端設定為非封鎖模式。 如需詳細資訊，請參閱 [Windows 通訊端：通訊端通知](../../mfc/windows-sockets-socket-notifications.md)文章。

## <a name="casyncsocketattach"></a><a name="attach"></a> CAsyncSocket：： Attach

呼叫這個成員函式，將 *hSocket* 控制碼附加至 `CAsyncSocket` 物件。

```
BOOL Attach(
    SOCKET hSocket, long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```

### <a name="parameters"></a>參數

*hSocket*<br/>
包含通訊端的控制碼。

*lEvent*<br/>
位元遮罩，指定應用程式感興趣的網路事件組合。

- FD_READ 想要接收讀取就緒的通知。

- 當資料可供讀取時，FD_WRITE 想要收到通知。

- FD_OOB 想要接收頻外資料抵達的通知。

- FD_ACCEPT 想要接收連入連線的通知。

- FD_CONNECT 想要接收連接結果的通知。

- FD_CLOSE 想要在對等互連關閉通訊端時接收通知。

### <a name="return-value"></a>傳回值

如果函式成功，則為非零。

### <a name="remarks"></a>備註

通訊端控制碼會儲存在物件的 [m_hSocket](#m_hsocket) 資料成員中。

## <a name="casyncsocketbind"></a><a name="bind"></a> CAsyncSocket：： Bind

呼叫這個成員函式，將本機位址與通訊端建立關聯。

```
BOOL Bind(
    UINT nSocketPort,
    LPCTSTR lpszSocketAddress = NULL);

BOOL Bind (
    const SOCKADDR* lpSockAddr,
    int nSockAddrLen);
```

### <a name="parameters"></a>參數

*nSocketPort*<br/>
識別通訊端應用程式的埠。

*lpszSocketAddress*<br/>
網路位址、點號，例如 "128.56.22.8"。 傳遞此參數的 Null 字串表示 `CAsyncSocket` 實例應該接聽所有網路介面上的用戶端活動。

*lpSockAddr*<br/>
[SOCKADDR](/windows/win32/winsock/sockaddr-2)結構的指標，其中包含要指派給這個通訊端的位址。

*nSockAddrLen*<br/>
*LpSockAddr*中位址的長度（以位元組為單位）。

### <a name="return-value"></a>傳回值

如果函式成功，則為非零;否則為0，而且可以藉由呼叫 [GetLastError](#getlasterror)來取出特定的錯誤碼。 下列清單涵蓋一些可能會傳回的錯誤。 如需完整清單，請參閱 [Windows 通訊端錯誤碼](/windows/win32/winsock/windows-sockets-error-codes-2)。

- WSANOTINITIALISED 成功的 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) 必須在使用此 API 之前進行。

- WSAENETDOWN Windows 通訊端執行偵測到網路子系統失敗。

- WSAEADDRINUSE 指定的位址已在使用中。  (請參閱 [ [SetSockOpt](#setsockopt)] 底下的 [SO_REUSEADDR 通訊端] 選項。 ) 

- WSAEFAULT *nSockAddrLen* 引數太小 (小於 [SOCKADDR](/windows/win32/winsock/sockaddr-2) 結構) 的大小。

- WSAEINPROGRESS 封鎖的 Windows 通訊端呼叫正在進行中。

- 此埠不支援 WSAEAFNOSUPPORT 指定的位址系列。

- WSAEINVAL 通訊端已系結至位址。

- WSAENOBUFS 沒有足夠的緩衝區可用、太多連接。

- WSAENOTSOCK 描述項不是通訊端。

### <a name="remarks"></a>備註

此常式會在未連線的資料包或串流通訊端上使用，然後再進行後續 `Connect` 或 `Listen` 呼叫。 接聽伺服器通訊端必須先選取埠號碼，並藉由呼叫來讓它知道 Windows 通訊端，才能接受連線要求 `Bind` 。 `Bind` 藉由將本機名稱指派給未命名的通訊端，來建立通訊端 (主機位址/埠號碼) 的本機關聯。

## <a name="casyncsocketcasyncsocket"></a><a name="casyncsocket"></a> CAsyncSocket：： CAsyncSocket

結構空白的通訊端物件。

```
CAsyncSocket();
```

### <a name="remarks"></a>備註

在建立物件之後，您必須呼叫其 `Create` 成員函式來建立通訊端資料結構並系結其位址。  (在 Windows 通訊端通訊的伺服器端，當接聽通訊端建立要在呼叫中使用的通訊端時， `Accept` 就不會呼叫 `Create` 該通訊端。 ) 

## <a name="casyncsocketclose"></a><a name="close"></a> CAsyncSocket：： Close

關閉通訊端。

```
virtual void Close();
```

### <a name="remarks"></a>備註

此函式會釋出通訊端描述項，以便進一步參考它會失敗，並出現錯誤 WSAENOTSOCK。 如果這是基礎通訊端的最後一個參考，則會捨棄相關聯的命名資訊和佇列資料。 通訊端物件的函式 `Close` 會呼叫您。

針對 `CAsyncSocket` （但不適用於 `CSocket` ）的語義 `Close` 會受到通訊端選項 SO_LINGER 和 SO_DONTLINGER 的影響。 如需詳細資訊，請參閱成員函式 `GetSockOpt` 。

## <a name="casyncsocketconnect"></a><a name="connect"></a> CAsyncSocket：： Connect

呼叫這個成員函式，以建立與未連接之資料流程或資料包通訊端的連接。

```
BOOL Connect(
    LPCTSTR lpszHostAddress,
    UINT nHostPort);

BOOL Connect(
    const SOCKADDR* lpSockAddr,
    int nSockAddrLen);
```

### <a name="parameters"></a>參數

*lpszHostAddress*<br/>
此物件所連接之通訊端的網路位址：電腦名稱稱（例如 "ftp.microsoft.com"）或點號（例如 "128.56.22.8"）。

*nHostPort*<br/>
識別通訊端應用程式的埠。

*lpSockAddr*<br/>
[SOCKADDR](/windows/win32/winsock/sockaddr-2)結構的指標，其中包含連接的通訊端位址。

*nSockAddrLen*<br/>
*LpSockAddr*中位址的長度（以位元組為單位）。

### <a name="return-value"></a>傳回值

如果函式成功，則為非零;否則為0，而且可以藉由呼叫 [GetLastError](#getlasterror)來取出特定的錯誤碼。 如果這表示 WSAEWOULDBLOCK 的錯誤碼，而您的應用程式使用可覆寫的回呼，則當連接作業完成時，您的應用程式會收到 `OnConnect` 訊息。 下列錯誤適用于這個成員函式：

- WSANOTINITIALISED 成功的 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) 必須在使用此 API 之前進行。

- WSAENETDOWN Windows 通訊端執行偵測到網路子系統失敗。

- WSAEADDRINUSE 指定的位址已在使用中。

- WSAEINPROGRESS 封鎖的 Windows 通訊端呼叫正在進行中。

- WSAEADDRNOTAVAIL 指定的位址無法在本機電腦上使用。

- 指定系列中的 WSAEAFNOSUPPORT 位址不能與這個通訊端一起使用。

- WSAECONNREFUSED 嘗試連接遭到拒絕。

- 需要 WSAEDESTADDRREQ 目的地位址。

- WSAEFAULT *nSockAddrLen* 引數不正確。

- WSAEINVAL 不正確主機位址。

- WSAEISCONN 通訊端已連線。

- WSAEMFILE 沒有其他可用的檔案描述項。

- WSAENETUNREACH 目前無法從這部主機連線到網路。

- WSAENOBUFS 沒有緩衝區空間可用。 無法連接通訊端。

- WSAENOTSOCK 描述項不是通訊端。

- WSAETIMEDOUT 嘗試連接逾時，而不建立連接。

- WSAEWOULDBLOCK 通訊端標示為非封鎖，且無法立即完成連線。

### <a name="remarks"></a>備註

如果通訊端未系結，系統會將唯一的值指派給本機關聯，而通訊端會標示為已系結。 請注意，如果名稱結構的 [位址] 欄位都是零， `Connect` 將會傳回零。 若要取得延伸錯誤資訊，請呼叫 `GetLastError` 成員函式。

針對 (類型 SOCK_STREAM) 的資料流程通訊端，使用中連接會起始至外部主機。 當通訊端呼叫順利完成時，通訊端就可以開始傳送/接收資料。

若為資料包通訊端 (類型 SOCK_DGRAM) ，則會設定預設目的地，以供後續 `Send` 和 `Receive` 呼叫使用。

## <a name="casyncsocketcreate"></a><a name="create"></a> CAsyncSocket：： Create

`Create`在建立通訊端物件之後呼叫成員函式，以建立 Windows 通訊端並附加它。

```
BOOL Create(
    UINT nSocketPort = 0,
    int nSocketType = SOCK_STREAM,
    long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE,
    LPCTSTR lpszSocketAddress = NULL);
```

### <a name="parameters"></a>參數

*nSocketPort*<br/>
要搭配通訊端使用的知名埠，如果您想要讓 Windows 通訊端選取埠，則為0。

*nSocketType*<br/>
SOCK_STREAM 或 SOCK_DGRAM。

*lEvent*<br/>
位元遮罩，指定應用程式感興趣的網路事件組合。

- FD_READ 想要接收讀取就緒的通知。

- FD_WRITE 想要收到寫入準備就緒的通知。

- FD_OOB 想要接收頻外資料抵達的通知。

- FD_ACCEPT 想要接收連入連線的通知。

- FD_CONNECT 想要接收已完成連接的通知。

- FD_CLOSE 想要接收通訊端關閉的通知。

*lpszSockAddress*<br/>
包含已連接通訊端之網路位址的字串指標，也就是「128.56.22.8」之類的點號。傳遞此參數的 Null 字串表示 `CAsyncSocket` 實例應該接聽所有網路介面上的用戶端活動。

### <a name="return-value"></a>傳回值

如果函式成功，則為非零;否則為0，而且可以藉由呼叫 [GetLastError](#getlasterror)來取出特定的錯誤碼。 下列錯誤適用于這個成員函式：

- WSANOTINITIALISED 成功的 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) 必須在使用此 API 之前進行。

- WSAENETDOWN Windows 通訊端執行偵測到網路子系統失敗。

- 不支援 WSAEAFNOSUPPORT 指定的位址系列。

- WSAEINPROGRESS 封鎖的 Windows 通訊端作業正在進行中。

- WSAEMFILE 沒有其他可用的檔案描述項。

- WSAENOBUFS 沒有緩衝區空間可用。 無法建立通訊端。

- 不支援 WSAEPROTONOSUPPORT 指定的埠。

- WSAEPROTOTYPE 指定的埠是此通訊端的錯誤類型。

- WSAESOCKTNOSUPPORT 此位址系列不支援指定的通訊端類型。

### <a name="remarks"></a>備註

`Create` 呼叫 [通訊端](#socket) ，如果成功，則會呼叫 [bind](#bind) ，將通訊端系結至指定的位址。 以下是支援的通訊端類型：

- SOCK_STREAM 提供已排序、可靠、全雙工、以連接為基礎的位元組資料流程。 使用網際網路位址系列 (TCP) 的傳輸控制通訊協定。

- SOCK_DGRAM 支援不連接的資料包、不可靠的固定 (封包，通常是小) 的最大長度。 針對網際網路位址系列使用使用者資料包協定 (UDP) 。

    > [!NOTE]
    >  成員函式 `Accept` 會接受新的空白物件的參考 `CSocket` 做為其參數。 在呼叫之前，您必須先建立這個物件 `Accept` 。 請記住，如果此通訊端物件超出範圍，連接就會關閉。 請勿呼叫 `Create` 這個新的通訊端物件。

> [!IMPORTANT]
> `Create` 不 **是安全** 執行緒。  如果您在多執行緒環境中呼叫它，以供不同的執行緒同時叫用，請務必使用 mutex 或其他同步處理鎖定來保護每個呼叫。

如需有關串流和資料包通訊端的詳細資訊，請參閱 [Windows 通訊端：背景](../../mfc/windows-sockets-background.md) 和 [windows 通訊端：埠和通訊端位址](../../mfc/windows-sockets-ports-and-socket-addresses.md) 和 [windows 通訊端 2 API](/windows/win32/WinSock/windows-sockets-start-page-2)的文章。

## <a name="casyncsocketcreateex"></a><a name="createex"></a> CAsyncSocket：： CreateEx

`CreateEx`在建立通訊端物件之後呼叫成員函式，以建立 Windows 通訊端並附加它。

當您需要提供先進的選項（例如通訊端類型）時，請使用此函式。

```
BOOL CreateEx(
    ADDRINFOT* pAI,
    long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```

### <a name="parameters"></a>參數

*排*<br/>
[ADDRINFOT](/windows/win32/api/ws2def/ns-ws2def-addrinfoa)的指標，用來保存通訊端資訊，例如家族和通訊端類型。

*lEvent*<br/>
位元遮罩，指定應用程式感興趣的網路事件組合。

- FD_READ 想要接收讀取就緒的通知。

- FD_WRITE 想要收到寫入準備就緒的通知。

- FD_OOB 想要接收頻外資料抵達的通知。

- FD_ACCEPT 想要接收連入連線的通知。

- FD_CONNECT 想要接收已完成連接的通知。

- FD_CLOSE 想要接收通訊端關閉的通知。

### <a name="return-value"></a>傳回值

請參閱 [Create ( # B1 ](#return-value-5)的傳回值。

### <a name="remarks"></a>備註

請參閱 [建立 ( # B1 ](#remarks-8)的備註。

## <a name="casyncsocketdetach"></a><a name="detach"></a> CAsyncSocket：:D etach

呼叫這個成員函式，以從物件卸離 *m_hSocket* 資料成員中的通訊端控制碼 `CAsyncSocket` ，並將 *m_hSocket* 設定為 Null。

```
SOCKET Detach();
```

## <a name="casyncsocketfromhandle"></a><a name="fromhandle"></a> CAsyncSocket：： FromHandle

傳回物件的指標 `CAsyncSocket` 。

```
static CAsyncSocket* PASCAL FromHandle(SOCKET hSocket);
```

### <a name="parameters"></a>參數

*hSocket*<br/>
包含通訊端的控制碼。

### <a name="return-value"></a>傳回值

物件的指標 `CAsyncSocket` ，如果沒有 `CAsyncSocket` 附加至 *hSocket*的物件，則為 Null。

### <a name="remarks"></a>備註

當提供通訊端控制碼時，如果 `CAsyncSocket` 物件未附加至控制碼，則成員函式會傳回 Null。

## <a name="casyncsocketgetlasterror"></a><a name="getlasterror"></a> CAsyncSocket：： GetLastError

呼叫這個成員函式，以取得最後一個失敗作業的錯誤狀態。

```
static int PASCAL GetLastError();
```

### <a name="return-value"></a>傳回值

傳回值會指出這個執行緒所執行之最後一個 Windows 通訊端 API 常式的錯誤碼。

### <a name="remarks"></a>備註

當特定成員函式指出發生錯誤時， `GetLastError` 應該呼叫以取得適當的錯誤碼。 如需適用的錯誤碼清單，請參閱個別成員函數描述。

如需錯誤碼的詳細資訊，請參閱 [Windows 通訊端 2 API](/windows/win32/WinSock/windows-sockets-start-page-2)。

## <a name="casyncsocketgetpeername"></a><a name="getpeername"></a> CAsyncSocket：： GetPeerName

呼叫這個成員函式，以取得這個通訊端所連接之對等通訊端的位址。

```
BOOL GetPeerName(
    CString& rPeerAddress,
    UINT& rPeerPort);

BOOL GetPeerName(
    SOCKADDR* lpSockAddr,
    int* lpSockAddrLen);
```

### <a name="parameters"></a>參數

*rPeerAddress*<br/>
參考 `CString` 接收點數位 IP 位址的物件。

*rPeerPort*<br/>
儲存埠之 UINT 的參考。

*lpSockAddr*<br/>
[SOCKADDR](/windows/win32/winsock/sockaddr-2)結構的指標，此結構會接收對等通訊端的名稱。

*lpSockAddrLen*<br/>
*LpSockAddr*中位址長度的指標（以位元組為單位）。 傳回時， *lpSockAddrLen* 引數會包含實際傳回的 *lpSockAddr* 大小（以位元組為單位）。

### <a name="return-value"></a>傳回值

如果函式成功，則為非零;否則為0，而且可以藉由呼叫 [GetLastError](#getlasterror)來取出特定的錯誤碼。 下列錯誤適用于這個成員函式：

- WSANOTINITIALISED 成功的 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) 必須在使用此 API 之前進行。

- WSAENETDOWN Windows 通訊端執行偵測到網路子系統失敗。

- WSAEFAULT *lpSockAddrLen* 引數不夠大。

- WSAEINPROGRESS 封鎖的 Windows 通訊端呼叫正在進行中。

- WSAENOTCONN 通訊端未連線。

- WSAENOTSOCK 描述項不是通訊端。

### <a name="remarks"></a>備註

若要處理 IPv6 位址，請使用 [CAsyncSocket：： GetPeerNameEx](#getpeernameex)。

## <a name="casyncsocketgetpeernameex"></a><a name="getpeernameex"></a> CAsyncSocket：： GetPeerNameEx

呼叫此成員函式，以取得此通訊端所連接之對等通訊端的位址 (處理) 的 IPv6 位址。

```
BOOL GetPeerNameEx(
    CString& rPeerAddress,
    UINT& rPeerPort);
```

### <a name="parameters"></a>參數

*rPeerAddress*<br/>
參考 `CString` 接收點數位 IP 位址的物件。

*rPeerPort*<br/>
儲存埠之 UINT 的參考。

### <a name="return-value"></a>傳回值

如果函式成功，則為非零;否則為0，而且可以藉由呼叫 [GetLastError](#getlasterror)來取出特定的錯誤碼。 下列錯誤適用于這個成員函式：

- WSANOTINITIALISED 成功的 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) 必須在使用此 API 之前進行。

- WSAENETDOWN Windows 通訊端執行偵測到網路子系統失敗。

- WSAEFAULT *lpSockAddrLen* 引數不夠大。

- WSAEINPROGRESS 封鎖的 Windows 通訊端呼叫正在進行中。

- WSAENOTCONN 通訊端未連線。

- WSAENOTSOCK 描述項不是通訊端。

### <a name="remarks"></a>備註

此函式與 [CAsyncSocket：： GetPeerName](#getpeername) 相同，不同之處在于它會處理 IPv6 位址以及較舊的通訊協定。

## <a name="casyncsocketgetsockname"></a><a name="getsockname"></a> CAsyncSocket：： GetSockName

呼叫此成員函式以取得通訊端的本機名稱。

```
BOOL GetSockName(
    CString& rSocketAddress,
    UINT& rSocketPort);

BOOL GetSockName(
    SOCKADDR* lpSockAddr,
    int* lpSockAddrLen);
```

### <a name="parameters"></a>參數

*rSocketAddress*<br/>
參考 `CString` 接收點數位 IP 位址的物件。

*rSocketPort*<br/>
儲存埠之 UINT 的參考。

*lpSockAddr*<br/>
[SOCKADDR](/windows/win32/winsock/sockaddr-2)結構的指標，此結構會接收通訊端的位址。

*lpSockAddrLen*<br/>
*LpSockAddr*中位址長度的指標（以位元組為單位）。

### <a name="return-value"></a>傳回值

如果函式成功，則為非零;否則為0，而且可以藉由呼叫 [GetLastError](#getlasterror)來取出特定的錯誤碼。 下列錯誤適用于這個成員函式：

- WSANOTINITIALISED 成功的 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) 必須在使用此 API 之前進行。

- WSAENETDOWN Windows 通訊端執行偵測到網路子系統失敗。

- WSAEFAULT *lpSockAddrLen* 引數不夠大。

- WSAEINPROGRESS 封鎖的 Windows 通訊端作業正在進行中。

- WSAENOTSOCK 描述項不是通訊端。

- WSAEINVAL 通訊端尚未系結至的位址 `Bind` 。

### <a name="remarks"></a>備註

當呼叫未先進行呼叫時，這個呼叫會特別有用 `Connect` `Bind` ; 此呼叫提供唯一的方法，您可以判斷系統已設定的本機關聯。

若要處理 IPv6 位址，請使用 [CAsyncSocket：： GetSockNameEx](#getsocknameex)

## <a name="casyncsocketgetsocknameex"></a><a name="getsocknameex"></a> CAsyncSocket：： GetSockNameEx

呼叫此成員函式以取得通訊端的本機名稱， (處理 IPv6 位址) 。

```
BOOL GetSockNameEx(
    CString& rSocketAddress,
    UINT& rSocketPort);
```

### <a name="parameters"></a>參數

*rSocketAddress*<br/>
參考 `CString` 接收點數位 IP 位址的物件。

*rSocketPort*<br/>
儲存埠之 UINT 的參考。

### <a name="return-value"></a>傳回值

如果函式成功，則為非零;否則為0，而且可以藉由呼叫 [GetLastError](#getlasterror)來取出特定的錯誤碼。 下列錯誤適用于這個成員函式：

- WSANOTINITIALISED 成功的 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) 必須在使用此 API 之前進行。

- WSAENETDOWN Windows 通訊端執行偵測到網路子系統失敗。

- WSAEFAULT *lpSockAddrLen* 引數不夠大。

- WSAEINPROGRESS 封鎖的 Windows 通訊端作業正在進行中。

- WSAENOTSOCK 描述項不是通訊端。

- WSAEINVAL 通訊端尚未系結至的位址 `Bind` 。

### <a name="remarks"></a>備註

此呼叫與 [CAsyncSocket：： GetSockName](#getsockname) 相同，不同之處在于它會處理 IPv6 位址以及較舊的通訊協定。

當呼叫未先進行呼叫時，這個呼叫會特別有用 `Connect` `Bind` ; 此呼叫提供唯一的方法，您可以判斷系統已設定的本機關聯。

## <a name="casyncsocketgetsockopt"></a><a name="getsockopt"></a> CAsyncSocket：： GetSockOpt

呼叫此成員函式以抓取通訊端選項。

```
BOOL GetSockOpt(
    int nOptionName,
    void* lpOptionValue,
    int* lpOptionLen,
    int nLevel = SOL_SOCKET);
```

### <a name="parameters"></a>參數

*nOptionName*<br/>
要抓取值的通訊端選項。

*lpOptionValue*<br/>
緩衝區的指標，此緩衝區會傳回所要求選項的值。 與選取的選項相關聯的值會在緩衝區 *lpOptionValue*中傳回。 *LpOptionLen*所指向的整數最初應該包含這個緩衝區的大小（以位元組為單位）。傳回時，它會設定為傳回值的大小。 針對 SO_LINGER，這會是結構的大小 `LINGER` ; 針對所有其他選項，它會是 BOOL 或的大小 **`int`** （視選項而定）。 在 [備註] 區段中，查看選項及其大小的清單。

*lpOptionLen*<br/>
*LpOptionValue*緩衝區大小的指標（以位元組為單位）。

*nLevel*<br/>
定義選項的層級;唯一支援的層級為 SOL_SOCKET 和 IPPROTO_TCP。

### <a name="return-value"></a>傳回值

如果函式成功，則為非零;否則為0，而且可以藉由呼叫 [GetLastError](#getlasterror)來取出特定的錯誤碼。 如果從未使用設定選項 `SetSockOpt` ，則會傳回 `GetSockOpt` 選項的預設值。 下列錯誤適用于這個成員函式：

- WSANOTINITIALISED 成功的 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) 必須在使用此 API 之前進行。

- WSAENETDOWN Windows 通訊端執行偵測到網路子系統失敗。

- WSAEFAULT *lpOptionLen* 引數無效。

- WSAEINPROGRESS 封鎖的 Windows 通訊端作業正在進行中。

- WSAENOPROTOOPT 選項未知或不受支援。 尤其是在類型為 SOCK_STREAM 的通訊端上，不支援 SO_BROADCAST，但 SO_ACCEPTCONN、SO_DONTLINGER、SO_KEEPALIVE、SO_LINGER 和 SO_OOBINLINE 在類型 SOCK_DGRAM 的通訊端上不受支援。

- WSAENOTSOCK 描述項不是通訊端。

### <a name="remarks"></a>備註

`GetSockOpt` 抓取與任何類型之通訊端（處於任何狀態）相關聯之通訊端選項的目前值，並將結果儲存在 *lpOptionValue*中。 選項會影響通訊端作業，例如封包的路由、頻外資料傳輸等等。

支援下列選項 `GetSockOpt` 。 此類型會識別 *lpOptionValue*所定址的資料類型。 TCP_NODELAY 選項使用層級 IPPROTO_TCP;所有其他選項都會使用層級 SOL_SOCKET。

|值|類型|意義|
|-----------|----------|-------------|
|SO_ACCEPTCONN|BOOL|通訊端正在接聽。|
|SO_BROADCAST|BOOL|通訊端是針對廣播訊息的傳輸而設定。|
|SO_DEBUG|BOOL|已啟用偵錯工具。|
|SO_DONTLINGER|BOOL|若為 true，則會停用 SO_LINGER 選項。|
|SO_DONTROUTE|BOOL|路由已停用。|
|SO_ERROR|**`int`**|取得錯誤狀態並清除。|
|SO_KEEPALIVE|BOOL|正在傳送 keep-alive。|
|SO_LINGER|`struct LINGER`|傳回目前的延遲選項。|
|SO_OOBINLINE|BOOL|標準資料流程中正在接收頻外資料。|
|SO_RCVBUF|int|接收的緩衝區大小。|
|SO_REUSEADDR|BOOL|通訊端可以系結至已在使用中的位址。|
|SO_SNDBUF|**`int`**|傳送的緩衝區大小。|
|SO_TYPE|**`int`**|通訊端的型別 (例如 SOCK_STREAM) 。|
|TCP_NODELAY|BOOL|停用用於傳送聯合的 Nagle 演算法。|

不支援的 Berkeley Software 散發 (BSD) 選項 `GetSockOpt` 如下：

|值|類型|意義|
|-----------|----------|-------------|
|SO_RCVLOWAT|**`int`**|接收下限標準。|
|SO_RCVTIMEO|**`int`**|接收時間。|
|SO_SNDLOWAT|**`int`**|傳送低水位線。|
|SO_SNDTIMEO|**`int`**|傳送超時。|
|IP_OPTIONS||取得 IP 標頭中的選項。|
|TCP_MAXSEG|**`int`**|取得 TCP 區段大小上限。|

`GetSockOpt`使用不支援的選項進行呼叫，將會導致從傳回的 WSAENOPROTOOPT 錯誤碼 `GetLastError` 。

## <a name="casyncsocketioctl"></a><a name="ioctl"></a> CAsyncSocket：： IOCtl

呼叫此成員函式來控制通訊端的模式。

```
BOOL IOCtl(
    long lCommand,
    DWORD* lpArgument);
```

### <a name="parameters"></a>參數

*lCommand*<br/>
要在通訊端上執行的命令。

*lpArgument*<br/>
*LCommand*參數的指標。

### <a name="return-value"></a>傳回值

如果函式成功，則為非零;否則為0，而且可以藉由呼叫 [GetLastError](#getlasterror)來取出特定的錯誤碼。 下列錯誤適用于這個成員函式：

- WSANOTINITIALISED 成功的 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) 必須在使用此 API 之前進行。

- WSAENETDOWN Windows 通訊端執行偵測到網路子系統失敗。

- WSAEINVAL *lCommand* 不是有效的命令，或 *lpArgument* 不是可接受的 *lCommand*參數，或命令不適用於提供的通訊端類型。

- WSAEINPROGRESS 封鎖的 Windows 通訊端作業正在進行中。

- WSAENOTSOCK 描述項不是通訊端。

### <a name="remarks"></a>備註

此常式可用於任何狀態的任何通訊端。 它是用來取得或取得與通訊端相關聯的作業參數，與通訊協定和通訊子系統無關。 支援的命令如下：

- FIONBIO 啟用或停用通訊端上的非封鎖模式。 *LpArgument*參數會指向 `DWORD` ，如果要啟用非封鎖模式則為非零，如果要停用，則為零。 如果已 `AsyncSelect` 在通訊端上發出，則任何嘗試使用將 `IOCtl` 通訊端設定回封鎖模式的嘗試都會失敗，並出現 WSAEINVAL。 若要將通訊端設定回封鎖模式並防止 WSAEINVAL 錯誤，應用程式必須先 `AsyncSelect` `AsyncSelect` 使用等於0的 *lEvent* 參數呼叫來停用，然後再呼叫 `IOCtl` 。

- FIONREAD 會決定可以使用此通訊端的一個呼叫來讀取的最大位元組數目 `Receive` 。 *LpArgument*參數會指向， `DWORD` 其中會 `IOCtl` 儲存結果。 如果這個通訊端屬於 SOCK_STREAM 類型，FIONREAD 會傳回可在單一資料中讀取的總數據量， `Receive` 這通常與通訊端上佇列的資料總量相同。 如果這個通訊端屬於 SOCK_DGRAM 類型，FIONREAD 會傳回在通訊端上排入佇列的第一個資料包的大小。

- SIOCATMARK 判斷是否已讀取所有頻外資料。 這僅適用于類型為 SOCK_STREAM 的通訊端，而此通訊端已設定為可在任何頻外接收任何頻外的資料 ( SO_OOBINLINE) 。 如果沒有任何頻外資料正在等候讀取，則作業會傳回非零值。 否則，它會傳回0，而且下一次 `Receive` 或 `ReceiveFrom` 在通訊端上執行時，將會抓取 "mark" 前面的部分或所有資料; 應用程式應該使用 SIOCATMARK 作業來判斷是否有任何資料存在。 如果「緊急」 (頻外) 資料前面有任何一般資料，則會依序接收。  (請注意， `Receive` 或 `ReceiveFrom` 永遠不會在相同的呼叫中混合頻外和一般資料。 ) *lpArgument* 參數點會 `DWORD` `IOCtl` 儲存結果。

此函式是 `ioctl()` Berkeley 通訊端中所使用的子集。 尤其是，沒有與 FIOASYNC 相同的命令，而 SIOCATMARK 是唯一支援的通訊端層級命令。

## <a name="casyncsocketlisten"></a><a name="listen"></a> CAsyncSocket：：接聽

呼叫這個成員函式來接聽連入連線要求。

```
BOOL Listen(int nConnectionBacklog = 5);
```

### <a name="parameters"></a>參數

*nConnectionBacklog*<br/>
暫止連接佇列可以成長的最大長度。 有效範圍是從1到5。

### <a name="return-value"></a>傳回值

如果函式成功，則為非零;否則為0，而且可以藉由呼叫 [GetLastError](#getlasterror)來取出特定的錯誤碼。 下列錯誤適用于這個成員函式：

- WSANOTINITIALISED 成功的 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) 必須在使用此 API 之前進行。

- WSAENETDOWN Windows 通訊端執行偵測到網路子系統失敗。

- WSAEADDRINUSE 嘗試在使用中的位址上進行接聽。

- WSAEINPROGRESS 封鎖的 Windows 通訊端作業正在進行中。

- WSAEINVAL 通訊端未系結或已 `Bind` 連線。

- WSAEISCONN 通訊端已連線。

- WSAEMFILE 沒有其他可用的檔案描述項。

- WSAENOBUFS 沒有緩衝區空間可用。

- WSAENOTSOCK 描述項不是通訊端。

- WSAEOPNOTSUPP 參考的通訊端不是支援作業的型別 `Listen` 。

### <a name="remarks"></a>備註

若要接受連接，則會先使用建立通訊端 `Create` 、使用指定的連入連線待處理專案 `Listen` ，然後接受連接 `Accept` 。 `Listen` 只適用于支援連接的通訊端，也就是類型 SOCK_STREAM 的通訊端。 此通訊端會置於「被動」模式，在此模式中，會確認傳入連線，並將進程排入佇列。

這項功能通常是由伺服器 (或任何想要接受連接的應用程式所使用) 可能一次有一個以上的連線要求：如果連接要求抵達佇列已滿，用戶端會收到錯誤，指出 WSAECONNREFUSED。

`Listen` 當沒有可用的埠 (描述項) 時，會嘗試繼續運作等理性判斷。 它會接受連接，直到佇列清空為止。 如果埠變成可用，稍後對或的 `Listen` 呼叫 `Accept` 會將佇列重填至目前或最近的「待處理專案」（如果可能），並繼續接聽連入連接。

## <a name="casyncsocketm_hsocket"></a><a name="m_hsocket"></a> CAsyncSocket：： m_hSocket

包含此物件所封裝之通訊端的通訊端控制碼 `CAsyncSocket` 。

```
SOCKET m_hSocket;
```

## <a name="casyncsocketonaccept"></a><a name="onaccept"></a> CAsyncSocket：： OnAccept

由架構呼叫，以通知接聽通訊端，藉由呼叫 [accept](#accept) 成員函式來接受擱置的連接要求。

```
virtual void OnAccept(int nErrorCode);
```

### <a name="parameters"></a>參數

*nErrorCode*<br/>
通訊端的最新錯誤。 下列錯誤碼適用于成員函式 `OnAccept` ：

- **0** 函式已成功執行。

- WSAENETDOWN Windows 通訊端執行偵測到網路子系統失敗。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [Windows 通訊端：通訊端通知](../../mfc/windows-sockets-socket-notifications.md)。

## <a name="casyncsocketonclose"></a><a name="onclose"></a> CAsyncSocket：： OnClose

由架構呼叫，以通知這個通訊端，連接的通訊端由其進程關閉。

```
virtual void OnClose(int nErrorCode);
```

### <a name="parameters"></a>參數

*nErrorCode*<br/>
通訊端的最新錯誤。 下列錯誤碼適用于成員函式 `OnClose` ：

- **0** 函式已成功執行。

- WSAENETDOWN Windows 通訊端執行偵測到網路子系統失敗。

- WSAECONNRESET 連接已由遠端重設。

- WSAECONNABORTED 連接已因為超時或其他失敗而中止。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [Windows 通訊端：通訊端通知](../../mfc/windows-sockets-socket-notifications.md)。

## <a name="casyncsocketonconnect"></a><a name="onconnect"></a> CAsyncSocket：： OnConnect

由架構呼叫，以通知這個連接的通訊端其連接嘗試已完成，不論成功或發生錯誤。

```
virtual void OnConnect(int nErrorCode);
```

### <a name="parameters"></a>參數

*nErrorCode*<br/>
通訊端的最新錯誤。 下列錯誤碼適用于成員函式 `OnConnect` ：

- **0** 函式已成功執行。

- WSAEADDRINUSE 指定的位址已在使用中。

- WSAEADDRNOTAVAIL 指定的位址無法在本機電腦上使用。

- 指定系列中的 WSAEAFNOSUPPORT 位址不能與這個通訊端一起使用。

- WSAECONNREFUSED 已強制拒絕連接嘗試。

- 需要 WSAEDESTADDRREQ 目的地位址。

- WSAEFAULT *lpSockAddrLen* 引數不正確。

- WSAEINVAL 通訊端已系結至位址。

- WSAEISCONN 通訊端已連線。

- WSAEMFILE 沒有其他可用的檔案描述項。

- WSAENETUNREACH 目前無法從這部主機連線到網路。

- WSAENOBUFS 沒有緩衝區空間可用。 無法連接通訊端。

- WSAENOTCONN 通訊端未連線。

- WSAENOTSOCK 描述項是檔案，而不是通訊端。

- WSAETIMEDOUT 嘗試連接逾時，而不建立連接。

### <a name="remarks"></a>備註

> [!NOTE]
> 在 [CSocket](../../mfc/reference/csocket-class.md)中， `OnConnect` 永遠不會呼叫通知函數。 若是連接，您只要呼叫 `Connect` ，就會在連接完成 (成功或) 錯誤時傳回。 連接通知的處理方式是 MFC 的執行詳細資料。

如需詳細資訊，請參閱 [Windows 通訊端：通訊端通知](../../mfc/windows-sockets-socket-notifications.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCAsyncSocket#1](../../mfc/reference/codesnippet/cpp/casyncsocket-class_1.cpp)]

## <a name="casyncsocketonoutofbanddata"></a><a name="onoutofbanddata"></a> CAsyncSocket：： OnOutOfBandData

由架構呼叫，以通知接收通訊端傳送的通訊端有頻外資料要傳送。

```
virtual void OnOutOfBandData(int nErrorCode);
```

### <a name="parameters"></a>參數

*nErrorCode*<br/>
通訊端的最新錯誤。 下列錯誤碼適用于成員函式 `OnOutOfBandData` ：

- **0** 函式已成功執行。

- WSAENETDOWN Windows 通訊端執行偵測到網路子系統失敗。

### <a name="remarks"></a>備註

頻外資料是邏輯上獨立的通道，與類型 SOCK_STREAM 的每一對連接通訊端相關聯。 通道通常用來傳送緊急資料。

MFC 支援頻外資料，但不建議使用類別的使用者 `CAsyncSocket` 。 更簡單的方式是建立第二個通訊端來傳遞這類資料。 如需頻外資料的詳細資訊，請參閱 [Windows 通訊端：通訊端通知](../../mfc/windows-sockets-socket-notifications.md)。

## <a name="casyncsocketonreceive"></a><a name="onreceive"></a> CAsyncSocket：： OnReceive

由架構呼叫，以通知這個通訊端，緩衝區中有資料可透過呼叫成員函式來取出 `Receive` 。

```
virtual void OnReceive(int nErrorCode);
```

### <a name="parameters"></a>參數

*nErrorCode*<br/>
通訊端的最新錯誤。 下列錯誤碼適用于成員函式 `OnReceive` ：

- **0** 函式已成功執行。

- WSAENETDOWN Windows 通訊端執行偵測到網路子系統失敗。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [Windows 通訊端：通訊端通知](../../mfc/windows-sockets-socket-notifications.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCAsyncSocket#2](../../mfc/reference/codesnippet/cpp/casyncsocket-class_2.cpp)]

## <a name="casyncsocketonsend"></a><a name="onsend"></a> CAsyncSocket：： OnSend

由架構呼叫，以通知通訊端它現在可以藉由呼叫成員函式來傳送資料 `Send` 。

```
virtual void OnSend(int nErrorCode);
```

### <a name="parameters"></a>參數

*nErrorCode*<br/>
通訊端的最新錯誤。 下列錯誤碼適用于成員函式 `OnSend` ：

- **0** 函式已成功執行。

- WSAENETDOWN Windows 通訊端執行偵測到網路子系統失敗。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [Windows 通訊端：通訊端通知](../../mfc/windows-sockets-socket-notifications.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCAsyncSocket#3](../../mfc/reference/codesnippet/cpp/casyncsocket-class_3.cpp)]

## <a name="casyncsocketoperator-"></a><a name="operator_eq"></a> CAsyncSocket：： operator =

將新值指派給 `CAsyncSocket` 物件。

```cpp
void operator=(const CAsyncSocket& rSrc);
```

### <a name="parameters"></a>參數

*.Rsrc*<br/>
現有物件的參考 `CAsyncSocket` 。

### <a name="remarks"></a>備註

呼叫此函式可將現有的 `CAsyncSocket` 物件複製到另一個 `CAsyncSocket` 物件。

## <a name="casyncsocketoperator-socket"></a><a name="operator_socket"></a> CAsyncSocket：： operator 通訊端

使用這個運算子來取得物件的通訊端控制碼 `CAsyncSocket` 。

```
operator SOCKET() const;
```

### <a name="return-value"></a>傳回值

如果成功，則為通訊端物件的控制碼;否則為 Null。

### <a name="remarks"></a>備註

您可以使用控制碼直接呼叫 Windows Api。

## <a name="casyncsocketreceive"></a><a name="receive"></a> CAsyncSocket：： Receive

呼叫此成員函式以接收來自通訊端的資料。

```
virtual int Receive(
    void* lpBuf,
    int nBufLen,
    int nFlags = 0);
```

### <a name="parameters"></a>參數

*lpBuf*<br/>
傳入資料的緩衝區。

*nBufLen*<br/>
*LpBuf*的長度（以位元組為單位）。

*nFlags*<br/>
指定進行呼叫的方式。 此函數的語法取決於通訊端選項和 *nFlags* 參數。 後者的構成方式是將下列任何值與 c + + **或** 運算子結合：

- MSG_PEEK 查看傳入資料。 資料會複製到緩衝區中，但不會從輸入佇列中移除。

- MSG_OOB 處理頻外資料。

### <a name="return-value"></a>傳回值

如果未發生錯誤，則會傳回 `Receive` 所接收的位元組數目。 如果連接已關閉，則會傳回0。 否則會傳回 SOCKET_ERROR 的值，而且可以藉由呼叫 [GetLastError](#getlasterror)來抓取特定的錯誤碼。 下列錯誤適用于這個成員函式：

- WSANOTINITIALISED 成功的 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) 必須在使用此 API 之前進行。

- WSAENETDOWN Windows 通訊端執行偵測到網路子系統失敗。

- WSAENOTCONN 通訊端未連線。

- WSAEINPROGRESS 封鎖的 Windows 通訊端作業正在進行中。

- WSAENOTSOCK 描述項不是通訊端。

- 指定了 WSAEOPNOTSUPP MSG_OOB，但通訊端不是 SOCK_STREAM 類型。

- WSAESHUTDOWN 通訊端已關機; `Receive` 當 `ShutDown` *nHow* 設定為0或2的情況下叫用之後，就無法在通訊端上呼叫。

- WSAEWOULDBLOCK 通訊端會標示為非封鎖，而作業 `Receive` 會封鎖。

- WSAEMSGSIZE 資料包太大，無法放入指定的緩衝區，且已被截斷。

- WSAEINVAL 通訊端尚未與系結 `Bind` 。

- WSAECONNABORTED 虛擬電路因為超時或其他失敗而中止。

- WSAECONNRESET 虛擬電路已由遠端重設。

### <a name="remarks"></a>備註

這個函式會用於連接的資料流程或資料包通訊端，並用來讀取傳入的資料。

針對 SOCK_STREAM 類型的通訊端，會傳回目前所提供的緩衝區大小所提供的最多資訊。 如果通訊端已設定為以串聯方式接收頻外資料 (通訊端選項 SO_OOBINLINE) 和頻外資料未讀取，則只會傳回頻外資料。 應用程式可以使用 `IOCtlSIOCATMARK` 選項或 [OnOutOfBandData](#onoutofbanddata) ，判斷是否有任何其他頻外資料仍在讀取。

針對資料包通訊端，資料會從第一個排入佇列的資料包中解壓縮，最多可達提供的緩衝區大小。 如果資料包大於提供的緩衝區，緩衝區就會填入資料包的第一個部分，而多餘的資料會遺失，並傳回 SOCKET_ERROR 的值，並將 `Receive` 錯誤碼設為 WSAEMSGSIZE。 如果通訊端沒有內送資料可供使用，則會傳回 SOCKET_ERROR 的值，並將錯誤碼設定為 WSAEWOULDBLOCK。 您可以使用 [OnReceive](#onreceive) 回呼函式來判斷何時會有更多資料抵達。

如果通訊端是 SOCK_STREAM 類型，而遠端端已正常關閉連線，則 `Receive` 會立即完成，並收到0個位元組。 如果連接已重設，則 `Receive` 會失敗，並出現錯誤 WSAECONNRESET。

`Receive` 每次呼叫 [CAsyncSocket：： OnReceive](#onreceive) 時，只能呼叫一次。

### <a name="example"></a>範例

  請參閱 [CAsyncSocket：： OnReceive](#onreceive)的範例。

## <a name="casyncsocketreceivefrom"></a><a name="receivefrom"></a> CAsyncSocket：： ReceiveFrom

呼叫此成員函式以接收資料包，並將來源位址儲存在 [SOCKADDR](/windows/win32/winsock/sockaddr-2) 結構或 *rSocketAddress*中。

```
int ReceiveFrom(
    void* lpBuf,
    int nBufLen,
    CString& rSocketAddress,
    UINT& rSocketPort,
    int nFlags = 0);

int ReceiveFrom(
    void* lpBuf,
    int nBufLen,
    SOCKADDR* lpSockAddr,
    int* lpSockAddrLen,
    int nFlags = 0);
```

### <a name="parameters"></a>參數

*lpBuf*<br/>
傳入資料的緩衝區。

*nBufLen*<br/>
*LpBuf*的長度（以位元組為單位）。

*rSocketAddress*<br/>
參考 `CString` 接收點數位 IP 位址的物件。

*rSocketPort*<br/>
儲存埠之 UINT 的參考。

*lpSockAddr*<br/>
[SOCKADDR](/windows/win32/winsock/sockaddr-2)結構的指標，此結構會在傳回時保存來源位址。

*lpSockAddrLen*<br/>
*LpSockAddr*中來源位址長度的指標（以位元組為單位）。

*nFlags*<br/>
指定進行呼叫的方式。 此函數的語法取決於通訊端選項和 *nFlags* 參數。 後者的構成方式是將下列任何值與 c + + **或** 運算子結合：

- MSG_PEEK 查看傳入資料。 資料會複製到緩衝區中，但不會從輸入佇列中移除。

- MSG_OOB 處理頻外資料。

### <a name="return-value"></a>傳回值

如果未發生錯誤，則會傳回 `ReceiveFrom` 所接收的位元組數目。 如果連接已關閉，則會傳回0。 否則會傳回 SOCKET_ERROR 的值，而且可以藉由呼叫來取出特定的錯誤碼 `GetLastError` 。 下列錯誤適用于這個成員函式：

- WSANOTINITIALISED 成功的 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) 必須在使用此 API 之前進行。

- WSAENETDOWN Windows 通訊端執行偵測到網路子系統失敗。

- WSAEFAULT *lpSockAddrLen* 引數無效： *lpSockAddr* 緩衝區太小，無法容納對等位址。

- WSAEINPROGRESS 封鎖的 Windows 通訊端作業正在進行中。

- WSAEINVAL 通訊端尚未與系結 `Bind` 。

- WSAENOTCONN 通訊端未連線 ( 只 SOCK_STREAM) 。

- WSAENOTSOCK 描述項不是通訊端。

- 指定了 WSAEOPNOTSUPP MSG_OOB，但通訊端不是 SOCK_STREAM 類型。

- WSAESHUTDOWN 通訊端已關機; `ReceiveFrom` 當 `ShutDown` *nHow* 設定為0或2的情況下叫用之後，就無法在通訊端上呼叫。

- WSAEWOULDBLOCK 通訊端會標示為非封鎖，而作業 `ReceiveFrom` 會封鎖。

- WSAEMSGSIZE 資料包太大，無法放入指定的緩衝區，且已被截斷。

- WSAECONNABORTED 虛擬電路因為超時或其他失敗而中止。

- WSAECONNRESET 虛擬電路已由遠端重設。

### <a name="remarks"></a>備註

此函數是用來讀取 (可能已連線) 通訊端上的傳入資料，並捕捉傳送資料的來源位址。

若要處理 IPv6 位址，請使用 [CAsyncSocket：： ReceiveFromEx](#receivefromex)。

針對 SOCK_STREAM 類型的通訊端，會傳回目前所提供的緩衝區大小所提供的最多資訊。 如果通訊端已設定為以串聯方式接收頻外資料 (通訊端選項 SO_OOBINLINE) 和頻外資料未讀取，則只會傳回頻外資料。 應用程式可以使用 `IOCtlSIOCATMARK` 選項，或 `OnOutOfBandData` 判斷是否有任何其他頻外資料仍在讀取。 SOCK_STREAM 通訊端會忽略 *lpSockAddr* 和 *lpSockAddrLen* 參數。

針對資料包通訊端，資料會從第一個排入佇列的資料包中解壓縮，最多可達提供的緩衝區大小。 如果資料包大於提供的緩衝區，緩衝區就會填入訊息的第一個部分，而多餘的資料會遺失，並傳回 SOCKET_ERROR 的值，並將 `ReceiveFrom` 錯誤碼設為 WSAEMSGSIZE。

如果 *lpSockAddr* 為非零值，且通訊端的類型為 SOCK_DGRAM，則傳送資料之通訊端的網路位址會複製到對應的 [SOCKADDR](/windows/win32/winsock/sockaddr-2) 結構。 *LpSockAddrLen*所指向的值會初始化為此結構的大小，並在傳回時修改，以指出儲存在該處的實際位址大小。 如果通訊端沒有內送資料可供使用， `ReceiveFrom` 除非通訊端為非封鎖，否則呼叫會等待資料抵達。 在此情況下，會傳回 SOCKET_ERROR 的值，並將錯誤碼設定為 WSAEWOULDBLOCK。 `OnReceive`回呼可以用來判斷何時會有更多資料抵達。

如果通訊端是 SOCK_STREAM 類型，而遠端端已正常關閉連線，則 `ReceiveFrom` 會立即完成，並收到0個位元組。

## <a name="casyncsocketreceivefromex"></a><a name="receivefromex"></a> CAsyncSocket：： ReceiveFromEx

呼叫此成員函式以接收資料包，然後將來源位址儲存在 [SOCKADDR](/windows/win32/winsock/sockaddr-2) 結構或 *RSocketAddress* (處理 IPv6 位址) 。

```
int ReceiveFromEx(
    void* lpBuf,
    int nBufLen,
    CString& rSocketAddress,
    UINT& rSocketPort,
    int nFlags = 0);
```

### <a name="parameters"></a>參數

*lpBuf*<br/>
傳入資料的緩衝區。

*nBufLen*<br/>
*LpBuf*的長度（以位元組為單位）。

*rSocketAddress*<br/>
參考 `CString` 接收點數位 IP 位址的物件。

*rSocketPort*<br/>
儲存埠之 UINT 的參考。

*nFlags*<br/>
指定進行呼叫的方式。 此函數的語法取決於通訊端選項和 *nFlags* 參數。 後者的構成方式是將下列任何值與 c + + **或** 運算子結合：

- MSG_PEEK 查看傳入資料。 資料會複製到緩衝區中，但不會從輸入佇列中移除。

- MSG_OOB 處理頻外資料。

### <a name="return-value"></a>傳回值

如果未發生錯誤，則會傳回 `ReceiveFromEx` 所接收的位元組數目。 如果連接已關閉，則會傳回0。 否則會傳回 SOCKET_ERROR 的值，而且可以藉由呼叫來取出特定的錯誤碼 `GetLastError` 。 下列錯誤適用于這個成員函式：

- WSANOTINITIALISED 成功的 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) 必須在使用此 API 之前進行。

- WSAENETDOWN Windows 通訊端執行偵測到網路子系統失敗。

- WSAEFAULT *lpSockAddrLen* 引數無效： *lpSockAddr* 緩衝區太小，無法容納對等位址。

- WSAEINPROGRESS 封鎖的 Windows 通訊端作業正在進行中。

- WSAEINVAL 通訊端尚未與系結 `Bind` 。

- WSAENOTCONN 通訊端未連線 ( 只 SOCK_STREAM) 。

- WSAENOTSOCK 描述項不是通訊端。

- 指定了 WSAEOPNOTSUPP MSG_OOB，但通訊端不是 SOCK_STREAM 類型。

- WSAESHUTDOWN 通訊端已關機; `ReceiveFromEx` 當 `ShutDown` *nHow* 設定為0或2的情況下叫用之後，就無法在通訊端上呼叫。

- WSAEWOULDBLOCK 通訊端會標示為非封鎖，而作業 `ReceiveFromEx` 會封鎖。

- WSAEMSGSIZE 資料包太大，無法放入指定的緩衝區，且已被截斷。

- WSAECONNABORTED 虛擬電路因為超時或其他失敗而中止。

- WSAECONNRESET 虛擬電路已由遠端重設。

### <a name="remarks"></a>備註

此函數是用來讀取 (可能已連線) 通訊端上的傳入資料，並捕捉傳送資料的來源位址。

此函式與 [CAsyncSocket：： ReceiveFrom](#receivefrom) 相同，不同之處在于它會處理 IPv6 位址以及較舊的通訊協定。

針對 SOCK_STREAM 類型的通訊端，會傳回目前所提供的緩衝區大小所提供的最多資訊。 如果通訊端已設定為以串聯方式接收頻外資料 (通訊端選項 SO_OOBINLINE) 和頻外資料未讀取，則只會傳回頻外資料。 應用程式可以使用 `IOCtlSIOCATMARK` 選項，或 `OnOutOfBandData` 判斷是否有任何其他頻外資料仍在讀取。 SOCK_STREAM 通訊端會忽略 *lpSockAddr* 和 *lpSockAddrLen* 參數。

針對資料包通訊端，資料會從第一個排入佇列的資料包中解壓縮，最多可達提供的緩衝區大小。 如果資料包大於提供的緩衝區，緩衝區就會填入訊息的第一個部分，而多餘的資料會遺失，並傳回 SOCKET_ERROR 的值，並將 `ReceiveFromEx` 錯誤碼設為 WSAEMSGSIZE。

如果 *lpSockAddr* 為非零值，且通訊端的類型為 SOCK_DGRAM，則傳送資料之通訊端的網路位址會複製到對應的 [SOCKADDR](/windows/win32/winsock/sockaddr-2) 結構。 *LpSockAddrLen*所指向的值會初始化為此結構的大小，並在傳回時修改，以指出儲存在該處的實際位址大小。 如果通訊端沒有內送資料可供使用， `ReceiveFromEx` 除非通訊端為非封鎖，否則呼叫會等待資料抵達。 在此情況下，會傳回 SOCKET_ERROR 的值，並將錯誤碼設定為 WSAEWOULDBLOCK。 `OnReceive`回呼可以用來判斷何時會有更多資料抵達。

如果通訊端是 SOCK_STREAM 類型，而遠端端已正常關閉連線，則 `ReceiveFromEx` 會立即完成，並收到0個位元組。

## <a name="casyncsocketsend"></a><a name="send"></a> CAsyncSocket：： Send

呼叫此成員函式以在連接的通訊端上傳送資料。

```
virtual int Send(
    const void* lpBuf,
    int nBufLen,
    int nFlags = 0);
```

### <a name="parameters"></a>參數

*lpBuf*<br/>
包含要傳輸之資料的緩衝區。

*nBufLen*<br/>
*LpBuf*中資料的長度（以位元組為單位）。

*nFlags*<br/>
指定進行呼叫的方式。 此函數的語法取決於通訊端選項和 *nFlags* 參數。 後者的構成方式是將下列任何值與 c + + **或** 運算子結合：

- MSG_DONTROUTE 指定資料不應受路由傳送。 Windows 通訊端供應商可以選擇忽略此旗標。

- MSG_OOB 只傳送頻外資料 (SOCK_STREAM) 。

### <a name="return-value"></a>傳回值

如果未發生錯誤，則會傳回 `Send` 已傳送的字元總數。  (請注意，這可能小於 *nBufLen*所表示的數位。 ) 否則會傳回 SOCKET_ERROR 的值，並藉由呼叫 [GetLastError](#getlasterror)來抓取特定的錯誤碼。 下列錯誤適用于這個成員函式：

- WSANOTINITIALISED 成功的 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) 必須在使用此 API 之前進行。

- WSAENETDOWN Windows 通訊端執行偵測到網路子系統失敗。

- WSAEACCES 要求的位址是廣播位址，但未設定適當的旗標。

- WSAEINPROGRESS 封鎖的 Windows 通訊端作業正在進行中。

- WSAEFAULT *lpBuf* 引數不在使用者位址空間的有效部分中。

- WSAENETRESET 連接必須重設，因為 Windows 通訊端的執行已卸載。

- WSAENOBUFS Windows 通訊端執行會報告緩衝區鎖死。

- WSAENOTCONN 通訊端未連線。

- WSAENOTSOCK 描述項不是通訊端。

- 指定了 WSAEOPNOTSUPP MSG_OOB，但通訊端不是 SOCK_STREAM 類型。

- WSAESHUTDOWN 通訊端已關機; `Send` 當 `ShutDown` *nHow* 設定為1或2時，無法在通訊端上呼叫。

- WSAEWOULDBLOCK 通訊端標示為非封鎖，要求的作業會封鎖。

- WSAEMSGSIZE 通訊端的型別 SOCK_DGRAM，且資料包大於 Windows 通訊端執行所支援的最大值。

- WSAEINVAL 通訊端尚未與系結 `Bind` 。

- WSAECONNABORTED 虛擬電路因為超時或其他失敗而中止。

- WSAECONNRESET 虛擬電路已由遠端重設。

### <a name="remarks"></a>備註

`Send` 用來寫入連接的資料流程或資料包通訊端上的傳出資料。 針對資料包通訊端，請小心不要超過基礎子網的 IP 封包大小上限，這是由所 `iMaxUdpDg` 傳回的 [WSADATA](/windows/win32/api/winsock2/ns-winsock2-wsadata) 結構中的元素所指定 `AfxSocketInit` 。 如果資料太長而無法透過基礎通訊協定以不可部分完成的方式傳遞，則會透過傳回錯誤 WSAEMSGSIZE， `GetLastError` 而且不會傳送任何資料。

請注意，資料包通訊端的成功完成 `Send` 並不表示已成功傳遞資料。

在 `CAsyncSocket` SOCK_STREAM 類型的物件上，寫入的位元組數目可以介於1和要求的長度之間，視本機和外部主機上的緩衝區可用性而定。

### <a name="example"></a>範例

  請參閱 [CAsyncSocket：： OnSend](#onsend)的範例。

## <a name="casyncsocketsendto"></a><a name="sendto"></a> CAsyncSocket：： SendTo

呼叫此成員函式，以將資料傳送至特定的目的地。

```
int SendTo(
    const void* lpBuf,
    int nBufLen,
    UINT nHostPort,
    LPCTSTR lpszHostAddress = NULL,
    int nFlags = 0);

int SendTo(
    const void* lpBuf,
    int nBufLen,
    const SOCKADDR* lpSockAddr,
    int nSockAddrLen,
    int nFlags = 0);
```

### <a name="parameters"></a>參數

*lpBuf*<br/>
包含要傳輸之資料的緩衝區。

*nBufLen*<br/>
*LpBuf*中資料的長度（以位元組為單位）。

*nHostPort*<br/>
識別通訊端應用程式的埠。

*lpszHostAddress*<br/>
此物件所連接之通訊端的網路位址：電腦名稱稱（例如 "ftp.microsoft.com"）或點號（例如 "128.56.22.8"）。

*nFlags*<br/>
指定進行呼叫的方式。 此函數的語法取決於通訊端選項和 *nFlags* 參數。 後者的構成方式是將下列任何值與 c + + **或** 運算子結合：

- MSG_DONTROUTE 指定資料不應受路由傳送。 Windows 通訊端供應商可以選擇忽略此旗標。

- MSG_OOB 只傳送頻外資料 (SOCK_STREAM) 。

*lpSockAddr*<br/>
[SOCKADDR](/windows/win32/winsock/sockaddr-2)結構的指標，其中包含目標通訊端的位址。

*nSockAddrLen*<br/>
*LpSockAddr*中位址的長度（以位元組為單位）。

### <a name="return-value"></a>傳回值

如果未發生錯誤，則會傳回 `SendTo` 已傳送的字元總數。  (請注意，這可能小於 *nBufLen*所表示的數位。 ) 否則會傳回 SOCKET_ERROR 的值，並藉由呼叫 [GetLastError](#getlasterror)來抓取特定的錯誤碼。 下列錯誤適用于這個成員函式：

- WSANOTINITIALISED 成功的 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) 必須在使用此 API 之前進行。

- WSAENETDOWN Windows 通訊端執行偵測到網路子系統失敗。

- WSAEACCES 要求的位址是廣播位址，但未設定適當的旗標。

- WSAEINPROGRESS 封鎖的 Windows 通訊端作業正在進行中。

- WSAEFAULT *lpBuf* 或 *lpSockAddr* 參數不是使用者位址空間的一部分，或 *lpSockAddr* 引數太小 (小於 [SOCKADDR](/windows/win32/winsock/sockaddr-2) 結構) 的大小。

- WSAEINVAL 主機名稱無效。

- WSAENETRESET 連接必須重設，因為 Windows 通訊端的執行已卸載。

- WSAENOBUFS Windows 通訊端執行會報告緩衝區鎖死。

- WSAENOTCONN 通訊端未連線 (只 SOCK_STREAM) 。

- WSAENOTSOCK 描述項不是通訊端。

- 指定了 WSAEOPNOTSUPP MSG_OOB，但通訊端不是 SOCK_STREAM 類型。

- WSAESHUTDOWN 通訊端已關機; `SendTo` 當 `ShutDown` *nHow* 設定為1或2時，無法在通訊端上呼叫。

- WSAEWOULDBLOCK 通訊端標示為非封鎖，要求的作業會封鎖。

- WSAEMSGSIZE 通訊端的型別 SOCK_DGRAM，且資料包大於 Windows 通訊端執行所支援的最大值。

- WSAECONNABORTED 虛擬電路因為超時或其他失敗而中止。

- WSAECONNRESET 虛擬電路已由遠端重設。

- WSAEADDRNOTAVAIL 指定的位址無法在本機電腦上使用。

- 指定系列中的 WSAEAFNOSUPPORT 位址不能與這個通訊端一起使用。

- 需要 WSAEDESTADDRREQ 目的地位址。

- WSAENETUNREACH 目前無法從這部主機連線到網路。

### <a name="remarks"></a>備註

`SendTo` 會用於資料包或串流通訊端，並用來寫入通訊端上的傳出資料。 針對資料包通訊端，請小心不要超過基礎子網的 IP 封包大小上限，這是由 `iMaxUdpDg` [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)填入的[WSADATA](/windows/win32/api/winsock2/ns-winsock2-wsadata)結構中的元素所指定。 如果資料太長而無法透過基礎通訊協定以不可部分完成的方式傳遞，則會傳回錯誤 WSAEMSGSIZE，而且不會傳送任何資料。

請注意，的成功完成 `SendTo` 並不表示已成功傳遞資料。

`SendTo` 只在 SOCK_DGRAM 通訊端上用來將資料包傳送至 *lpSockAddr* 參數所識別的特定通訊端。

若) 只要在 SOCK_DGRAM 上傳送廣播 (，則應使用 Windows 通訊端標頭檔 WINSOCK 中定義的特殊 IP 位址 INADDR_BROADCAST (來建立 *lpSockAddr* 參數中的位址。H) 搭配預期的埠號碼。 或者，如果 *lpszHostAddress* 參數為 Null，就會設定通訊端以進行廣播。 通常會 inadvisable 廣播資料包以超過片段的大小，這表示資料包 (排除標頭的資料部分) 不應超過512個位元組。

若要處理 IPv6 位址，請使用 [CAsyncSocket：： SendToEx](#sendtoex)。

## <a name="casyncsocketsendtoex"></a><a name="sendtoex"></a> CAsyncSocket：： SendToEx

呼叫此成員函式，以將資料傳送至特定的目的地， (處理 IPv6 位址) 。

```
int SendToEx(
    const void* lpBuf,
    int nBufLen,
    UINT nHostPort,
    LPCTSTR lpszHostAddress = NULL,
    int nFlags = 0);
```

### <a name="parameters"></a>參數

*lpBuf*<br/>
包含要傳輸之資料的緩衝區。

*nBufLen*<br/>
*LpBuf*中資料的長度（以位元組為單位）。

*nHostPort*<br/>
識別通訊端應用程式的埠。

*lpszHostAddress*<br/>
此物件所連接之通訊端的網路位址：電腦名稱稱（例如 "ftp.microsoft.com"）或點號（例如 "128.56.22.8"）。

*nFlags*<br/>
指定進行呼叫的方式。 此函數的語法取決於通訊端選項和 *nFlags* 參數。 後者的構成方式是將下列任何值與 c + + **或** 運算子結合：

- MSG_DONTROUTE 指定資料不應受路由傳送。 Windows 通訊端供應商可以選擇忽略此旗標。

- MSG_OOB 只傳送頻外資料 (SOCK_STREAM) 。

### <a name="return-value"></a>傳回值

如果未發生錯誤，則會傳回 `SendToEx` 已傳送的字元總數。  (請注意，這可能小於 *nBufLen*所表示的數位。 ) 否則會傳回 SOCKET_ERROR 的值，並藉由呼叫 [GetLastError](#getlasterror)來抓取特定的錯誤碼。 下列錯誤適用于這個成員函式：

- WSANOTINITIALISED 成功的 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) 必須在使用此 API 之前進行。

- WSAENETDOWN Windows 通訊端執行偵測到網路子系統失敗。

- WSAEACCES 要求的位址是廣播位址，但未設定適當的旗標。

- WSAEINPROGRESS 封鎖的 Windows 通訊端作業正在進行中。

- WSAEFAULT *lpBuf* 或 *lpSockAddr* 參數不是使用者位址空間的一部分，或 *lpSockAddr* 引數太小 (小於 [SOCKADDR](/windows/win32/winsock/sockaddr-2) 結構) 的大小。

- WSAEINVAL 主機名稱無效。

- WSAENETRESET 連接必須重設，因為 Windows 通訊端的執行已卸載。

- WSAENOBUFS Windows 通訊端執行會報告緩衝區鎖死。

- WSAENOTCONN 通訊端未連線 (只 SOCK_STREAM) 。

- WSAENOTSOCK 描述項不是通訊端。

- 指定了 WSAEOPNOTSUPP MSG_OOB，但通訊端不是 SOCK_STREAM 類型。

- WSAESHUTDOWN 通訊端已關機; `SendToEx` 當 `ShutDown` *nHow* 設定為1或2時，無法在通訊端上呼叫。

- WSAEWOULDBLOCK 通訊端標示為非封鎖，要求的作業會封鎖。

- WSAEMSGSIZE 通訊端的型別 SOCK_DGRAM，且資料包大於 Windows 通訊端執行所支援的最大值。

- WSAECONNABORTED 虛擬電路因為超時或其他失敗而中止。

- WSAECONNRESET 虛擬電路已由遠端重設。

- WSAEADDRNOTAVAIL 指定的位址無法在本機電腦上使用。

- 指定系列中的 WSAEAFNOSUPPORT 位址不能與這個通訊端一起使用。

- 需要 WSAEDESTADDRREQ 目的地位址。

- WSAENETUNREACH 目前無法從這部主機連線到網路。

### <a name="remarks"></a>備註

此方法與 [CAsyncSocket：： SendTo](#sendto) 相同，不同之處在于它會處理 IPv6 位址以及較舊的通訊協定。

`SendToEx` 會用於資料包或串流通訊端，並用來寫入通訊端上的傳出資料。 針對資料包通訊端，請小心不要超過基礎子網的 IP 封包大小上限，這是由 `iMaxUdpDg` [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)填入的[WSADATA](/windows/win32/api/winsock2/ns-winsock2-wsadata)結構中的元素所指定。 如果資料太長而無法透過基礎通訊協定以不可部分完成的方式傳遞，則會傳回錯誤 WSAEMSGSIZE，而且不會傳送任何資料。

請注意，的成功完成 `SendToEx` 並不表示已成功傳遞資料。

`SendToEx` 只在 SOCK_DGRAM 通訊端上用來將資料包傳送至 *lpSockAddr* 參數所識別的特定通訊端。

若) 只要在 SOCK_DGRAM 上傳送廣播 (，則應使用 Windows 通訊端標頭檔 WINSOCK 中定義的特殊 IP 位址 INADDR_BROADCAST (來建立 *lpSockAddr* 參數中的位址。H) 搭配預期的埠號碼。 或者，如果 *lpszHostAddress* 參數為 Null，就會設定通訊端以進行廣播。 通常會 inadvisable 廣播資料包以超過片段的大小，這表示資料包 (排除標頭的資料部分) 不應超過512個位元組。

## <a name="casyncsocketsetsockopt"></a><a name="setsockopt"></a> CAsyncSocket：： SetSockOpt

呼叫此成員函式以設定通訊端選項。

```
BOOL SetSockOpt(
    int nOptionName,
    const void* lpOptionValue,
    int nOptionLen,
    int nLevel = SOL_SOCKET);
```

### <a name="parameters"></a>參數

*nOptionName*<br/>
要設定其值的通訊端選項。

*lpOptionValue*<br/>
緩衝區的指標，其中會提供所要求選項的值。

*nOptionLen*<br/>
*LpOptionValue*緩衝區的大小（以位元組為單位）。

*nLevel*<br/>
定義選項的層級;唯一支援的層級為 SOL_SOCKET 和 IPPROTO_TCP。

### <a name="return-value"></a>傳回值

如果函式成功，則為非零;否則為0，而且可以藉由呼叫 [GetLastError](#getlasterror)來取出特定的錯誤碼。 下列錯誤適用于這個成員函式：

- WSANOTINITIALISED 成功的 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) 必須在使用此 API 之前進行。

- WSAENETDOWN Windows 通訊端執行偵測到網路子系統失敗。

- WSAEFAULT *lpOptionValue* 不在進程位址空間的有效部分中。

- WSAEINPROGRESS 封鎖的 Windows 通訊端作業正在進行中。

- WSAEINVAL *nLevel* 無效，或 *lpOptionValue* 中的資訊無效。

- 設定 SO_KEEPALIVE 時，WSAENETRESET 連接已經超時。

- WSAENOPROTOOPT 選項未知或不受支援。 尤其是在類型為 SOCK_STREAM 的通訊端上，不支援 SO_BROADCAST，但在類型 SO_LINGER 的通訊端上不支援 SO_DONTLINGER、SO_KEEPALIVE、SO_OOBINLINE 和 SOCK_DGRAM。

- WSAENOTCONN 連接已在設定 SO_KEEPALIVE 時重設。

- WSAENOTSOCK 描述項不是通訊端。

### <a name="remarks"></a>備註

`SetSockOpt` 在任何狀態下，設定與任何類型之通訊端相關聯之通訊端選項的目前值。 雖然選項可以存在於多個通訊協定層級，但此規格只會定義存在於最上層「通訊端」層級的選項。 選項會影響通訊端作業，例如，是否在一般資料流程中收到快速資料、是否可以在通訊端上傳送廣播訊息等等。

有兩種類型的通訊端選項：啟用或停用功能或行為的布林值選項，以及需要整數值或結構的選項。 若要啟用布林值選項， *lpOptionValue* 會指向非零的整數。 若要停用此選項， *lpOptionValue* 會指向等於零的整數。 *nOptionLen* 應該等於 `sizeof(BOOL)` 布林值選項。 針對其他選項， *lpOptionValue* 會指向包含選項所需值的整數或結構，而 *nOptionLen* 是整數或結構的長度。

SO_LINGER 控制當未傳送的資料在通訊端上排入佇列時所採取的動作，而且會呼叫該函式 `Close` 來關閉通訊端。

根據預設，無法系結通訊端 (請 [參閱將](#bind)) 系結至已在使用中的本機位址。 不過，在某些情況下，可能需要以這種方式「重複使用」位址。 因為每個連線都是透過本機和遠端位址的組合來唯一識別，所以有兩個通訊端系結至相同的本機位址並不會有任何問題，只要遠端位址不同。

若要通知 Windows 通訊端的執行， `Bind` 不允許對通訊端進行呼叫，因為所需的位址已由另一個通訊端使用中，應用程式應該在發出呼叫之前，先設定通訊端的 SO_REUSEADDR 通訊端選項 `Bind` 。 請注意，此選項只會在呼叫時進行解讀 `Bind` ：因此不需要 (但無害的) 在不會系結至現有位址的通訊端上設定選項，以及在呼叫不會 `Bind` 影響此或任何其他通訊端之後設定或重設選項。

應用程式可以藉由開啟 SO_KEEPALIVE 通訊端選項，要求 Windows 通訊端執行在傳輸控制通訊協定上使用「保持運作」封包 (TCP) 連接。 Windows 通訊端執行不需要支援持續進行的使用：如果有的話，精確的語法會是執行特有的，但應該符合 RFC 1122 的4.2.3.6：「網際網路主機的需求—通訊層」。 如果因為「保持連接」的結果而卸載連線，錯誤碼 WSAENETRESET 會傳回至通訊端上進行中的任何呼叫，而任何後續的呼叫將會失敗並產生 WSAENOTCONN。

TCP_NODELAY 選項會停用 Nagle 演算法。 Nagle 演算法用來減少主機傳送的小型封包數，方法是緩衝未認可的傳送資料，直到可以傳送完整大小的封包為止。 不過，對某些應用程式而言，這個演算法可能會妨礙效能，而 TCP_NODELAY 可以用來將它關閉。 應用程式寫入器應該不會 TCP_NODELAY 設定，除非這樣做的影響是很清楚且更想要的，因為設定 TCP_NODELAY 可能會對網路效能造成顯著的負面影響。 TCP_NODELAY 是唯一使用層級 IPPROTO_TCP 的支援通訊端選項;所有其他選項都會使用層級 SOL_SOCKET。

如果應用程式設定了 SO_DEBUG 選項，Windows 通訊端的某些執行會提供輸出的偵錯工具資訊。

支援下列選項 `SetSockOpt` 。 此類型會識別 *lpOptionValue*所定址的資料類型。

|值|類型|意義|
|-----------|----------|-------------|
|SO_BROADCAST|BOOL|允許傳輸通訊端上的廣播訊息。|
|SO_DEBUG|BOOL|記錄偵錯資訊。|
|SO_DONTLINGER|BOOL|請勿封鎖 `Close` 等候傳送未傳送的資料。 設定此選項相當於設定 `l_onoff` 為零的 SO_LINGER。|
|SO_DONTROUTE|BOOL|不要路由傳送：直接傳送至介面。|
|SO_KEEPALIVE|BOOL|傳送 keep-alive。|
|SO_LINGER|`struct LINGER`|`Close`如果有未傳送的資料，就會逗留。|
|SO_OOBINLINE|BOOL|接收標準資料流程中的頻外資料。|
|SO_RCVBUF|**`int`**|指定接收的緩衝區大小。|
|SO_REUSEADDR|BOOL|允許通訊端系結至已在使用中的位址。  (參閱 [Bind](#bind)。 ) |
|SO_SNDBUF|**`int`**|指定傳送的緩衝區大小。|
|TCP_NODELAY|BOOL|停用用於傳送聯合的 Nagle 演算法。|

不支援的 Berkeley Software 散發 (BSD) 選項 `SetSockOpt` 如下：

|值|類型|意義|
|-----------|----------|-------------|
|SO_ACCEPTCONN|BOOL|通訊端正在接聽|
|SO_ERROR|**`int`**|取得錯誤狀態並清除。|
|SO_RCVLOWAT|**`int`**|接收下限標準。|
|SO_RCVTIMEO|**`int`**|接收逾時|
|SO_SNDLOWAT|**`int`**|傳送低水位線。|
|SO_SNDTIMEO|**`int`**|傳送超時。|
|SO_TYPE|**`int`**|通訊端的型別。|
|IP_OPTIONS||設定 IP 標頭中的選項欄位。|

## <a name="casyncsocketshutdown"></a><a name="shutdown"></a> CAsyncSocket：： ShutDown

呼叫此成員函式，以停用通訊端上的傳送、接收或兩者。

```
BOOL ShutDown(int nHow = sends);
```

### <a name="parameters"></a>參數

*nHow*<br/>
使用下列列舉值的旗標，描述將不再允許的作業類型：

- **接收 = 0**

- **傳送 = 1**

- **兩者 = 2**

### <a name="return-value"></a>傳回值

如果函式成功，則為非零;否則為0，而且可以藉由呼叫 [GetLastError](#getlasterror)來取出特定的錯誤碼。 下列錯誤適用于這個成員函式：

- WSANOTINITIALISED 成功的 [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) 必須在使用此 API 之前進行。

- WSAENETDOWN Windows 通訊端執行偵測到網路子系統失敗。

- WSAEINVAL *nHow* 無效。

- WSAEINPROGRESS 封鎖的 Windows 通訊端作業正在進行中。

- WSAENOTCONN 通訊端未連線 (只 SOCK_STREAM) 。

- WSAENOTSOCK 描述項不是通訊端。

### <a name="remarks"></a>備註

`ShutDown` 適用于所有類型的通訊端，以停用接收、傳輸或兩者。 如果 *nHow* 為0，則不允許在通訊端上進行後續的接收。 這不會影響較低的通訊協定層。

若為傳輸控制通訊協定 (TCP) ，則不會變更 TCP 視窗，而且會接受傳入的資料 (但不會) 直到視窗用盡為止。 針對使用者資料包協定 (UDP) ，會接受傳入的資料包並將其排入佇列。 在任何情況下，都會產生 ICMP 錯誤封包。 如果 *nHow* 為1，則不允許後續的傳送。 TCP 通訊端將會傳送 FIN。 將 *nHow* 設定為2時，會同時停用傳送和接收，如上所述。

請注意，不會 `ShutDown` 關閉通訊端，而且附加至通訊端的資源將不會釋出，直到 `Close` 呼叫為止。 應用程式不應該依賴在關閉後重新使用通訊端的能力。 特別的是，不需要執行 Windows 通訊端，就能支援 `Connect` 在這類通訊端上使用。

### <a name="example"></a>範例

  請參閱 [CAsyncSocket：： OnReceive](#onreceive)的範例。

## <a name="casyncsocketsocket"></a><a name="socket"></a> CASyncSocket：： Socket

配置通訊端控制碼。

```
BOOL Socket(
    int nSocketType = SOCK_STREAM,
    long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE,
    int nProtocolType = 0,
    int nAddressFormat = PF_INET);
```

### <a name="parameters"></a>參數

*nSocketType*<br/>
指定 `SOCK_STREAM` 或 `SOCK_DGRAM` 。

*lEvent*<br/>
位元遮罩，指定應用程式感興趣的網路事件組合。

- `FD_READ`：您想要接收讀取準備就緒的通知。

- `FD_WRITE`：希望收到寫入準備就緒的通知。

- `FD_OOB`：希望接收頻外資料抵達的通知。

- `FD_ACCEPT`：想要接收連入連線的通知。

- `FD_CONNECT`：想要接收已完成連接的通知。

- `FD_CLOSE`：希望收到通訊端關閉的通知。

*nProtocolType*<br/>
要搭配指定的位址系列專屬通訊端使用的通訊協定。

*nAddressFormat*<br/>
位址系列規格。

### <a name="return-value"></a>傳回值

成功時傳回 `TRUE`，失敗時則傳回 `FALSE`。

### <a name="remarks"></a>備註

這個方法會配置一個通訊端控制碼。 它不會呼叫 [CAsyncSocket：： bind](#bind) 來將通訊端系結至指定的位址，因此您稍後需要呼叫 `Bind` 以將通訊端系結至指定的位址。 您可以使用 [CAsyncSocket：： SetSockOpt](#setsockopt) 來設定通訊端選項，然後再進行系結。

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CSocket 類別](../../mfc/reference/csocket-class.md)<br/>
[CSocketFile 類別](../../mfc/reference/csocketfile-class.md)
