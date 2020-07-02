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
ms.openlocfilehash: 9a3a04046d75a4cfdbb50347259820eb727eeb38
ms.sourcegitcommit: 83ea5df40917885e261089b103d5de3660314104
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85813581"
---
# <a name="casyncsocket-class"></a>CAsyncSocket 類別

代表 Windows 通訊端—網路通訊的端點。

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
|[CAsyncSocket：： CreateEx](#createex)|使用 advanced 選項建立通訊端。|
|[CAsyncSocket：:D etach](#detach)|從物件卸離通訊端控制碼 `CAsyncSocket` 。|
|[CAsyncSocket：： FromHandle](#fromhandle)|`CAsyncSocket`指定通訊端控制碼，傳回物件的指標。|
|[CAsyncSocket：： GetLastError](#getlasterror)|取得最後一個失敗作業的錯誤狀態。|
|[CAsyncSocket：： GetPeerName](#getpeername)|取得通訊端所連接的對等通訊端位址。|
|[CAsyncSocket：： GetPeerNameEx](#getpeernameex)|取得通訊端所連接的對等通訊端位址（處理 IPv6 位址）。|
|[CAsyncSocket：： GetSockName](#getsockname)|取得通訊端的區功能變數名稱稱。|
|[CAsyncSocket：： GetSockNameEx](#getsocknameex)|取得通訊端的本機名稱（處理 IPv6 位址）。|
|[CAsyncSocket：： GetSockOpt](#getsockopt)|抓取通訊端選項。|
|[CAsyncSocket：： IOCtl](#ioctl)|控制通訊端的模式。|
|[CAsyncSocket：：接聽](#listen)|建立通訊端來接聽連入連線要求。|
|[CAsyncSocket：： Receive](#receive)|從通訊端接收資料。|
|[CAsyncSocket：： ReceiveFrom](#receivefrom)|接收資料包並儲存來源位址。|
|[CAsyncSocket：： ReceiveFromEx](#receivefromex)|接收資料包並儲存來源位址（處理 IPv6 位址）。|
|[CAsyncSocket：： Send](#send)|將資料傳送到已連線的通訊端。|
|[CAsyncSocket：： SendTo](#sendto)|將資料傳送到特定目的地。|
|[CAsyncSocket：： SendToEx](#sendtoex)|將資料傳送至特定目的地（處理 IPv6 位址）。|
|[CAsyncSocket：： SetSockOpt](#setsockopt)|設定通訊端選項。|
|[CAsyncSocket：： ShutDown](#shutdown)|停用 `Send` 和/或對 `Receive` 通訊端的呼叫。|
|[CASyncSocket：： Socket](#socket)|配置通訊端控制碼。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CAsyncSocket：： OnAccept](#onaccept)|通知接聽通訊端，它可以藉由呼叫來接受暫止的連接要求 `Accept` 。|
|[CAsyncSocket：： OnClose](#onclose)|通知通訊端連接到它的通訊端已關閉。|
|[CAsyncSocket：： OnConnect](#onconnect)|通知連接的通訊端，連線嘗試已完成，無論是成功或錯誤。|
|[CAsyncSocket：： OnOutOfBandData](#onoutofbanddata)|通知接收通訊端有頻外資料要在通訊端上讀取，通常是緊急訊息。|
|[CAsyncSocket：： OnReceive](#onreceive)|藉由呼叫來通知接聽通訊端有要抓取的資料 `Receive` 。|
|[CAsyncSocket：： OnSend](#onsend)|通知通訊端它可以藉由呼叫來傳送資料 `Send` 。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CAsyncSocket：： operator =](#operator_eq)|將新值指派給 `CAsyncSocket` 物件。|
|[CAsyncSocket：： operator 通訊端](#operator_socket)|使用這個運算子來抓取物件的通訊端控制碼 `CAsyncSocket` 。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CAsyncSocket：： m_hSocket](#m_hsocket)|表示附加至此物件的通訊端控制碼 `CAsyncSocket` 。|

## <a name="remarks"></a>備註

類別會 `CAsyncSocket` 封裝 Windows 通訊端函式 API，為想要搭配 MFC 使用 Windows 通訊端的程式設計人員提供物件導向的抽象概念。

這個類別是以您瞭解網路通訊的假設為基礎。 您必須負責處理封鎖、位元組順序的差異，以及 Unicode 和多位元組字元集（MBCS）字串之間的轉換。 如果您想要更方便的介面來為您管理這些問題，請參閱類別[CSocket](../../mfc/reference/csocket-class.md)。

若要使用 `CAsyncSocket` 物件，請呼叫其函式，然後呼叫[create](#create)函式來建立基礎通訊端控制碼（類型 `SOCKET` ），但已接受的通訊端除外。 若為伺服器通訊端，請呼叫[接聽](#listen)成員函式，並針對用戶端通訊端呼叫[Connect](#connect)成員函式。 伺服器通訊端應該在收到連接要求時呼叫[Accept](#accept)函式。 使用其餘 `CAsyncSocket` 函數來執行通訊端之間的通訊。 完成時， `CAsyncSocket` 如果物件是建立在堆積上，則會終結它，而此析構函式會自動呼叫[Close](#close)函數。 SOCKET 資料類型會在[Windows 通訊端：背景](../../mfc/windows-sockets-background.md)一文中說明。

> [!NOTE]
> 在靜態連結 MFC 應用程式的次要執行緒中使用 MFC 通訊端時，您必須 `AfxSocketInit` 在每個使用通訊端的執行緒中呼叫，以初始化通訊端程式庫。 根據預設， `AfxSocketInit` 只會在主執行緒中呼叫。

如需詳細資訊，請參閱[Windows 通訊端：使用類別 CAsyncSocket](../../mfc/windows-sockets-using-class-casyncsocket.md)和相關文章，以及[WINDOWS socket 2 API](/windows/win32/WinSock/windows-sockets-start-page-2)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

`CAsyncSocket`

## <a name="requirements"></a>需求

**標頭：** afxsock。h

## <a name="casyncsocketaccept"></a><a name="accept"></a>CAsyncSocket：： Accept

呼叫此成員函式以接受通訊端上的連接。

```
virtual BOOL Accept(
    CAsyncSocket& rConnectedSocket,
    SOCKADDR* lpSockAddr = NULL,
    int* lpSockAddrLen = NULL);
```

### <a name="parameters"></a>參數

*rConnectedSocket*<br/>
參考，識別可供連接的新通訊端。

*lpSockAddr*<br/>
[SOCKADDR](/windows/win32/winsock/sockaddr-2)結構的指標，接收連接通訊端的位址，如網路上所知。 *LpSockAddr*引數的確切格式取決於建立通訊端時所建立的位址系列。 如果*lpSockAddr*和/或*lpSockAddrLen*等於 Null，則不會傳回已接受之通訊端的遠端位址相關資訊。

*lpSockAddrLen*<br/>
*LpSockAddr*中位址長度的指標（以位元組為單位）。 *LpSockAddrLen*是值結果參數：它一開始應該包含*lpSockAddr*所指向的空間量;傳回時，它會包含所傳回位址的實際長度（以位元組為單位）。

### <a name="return-value"></a>傳回值

如果函式成功，則為非零;否則，您可以藉由呼叫[GetLastError](#getlasterror)來抓取特定的錯誤碼。 下列錯誤適用于此成員函式：

- WSANOTINITIALISED 成功的[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必須在使用此 API 之前進行。

- WSAENETDOWN Windows 通訊端執行偵測到網路子系統失敗。

- WSAEFAULT *lpSockAddrLen*引數太小（小於[SOCKADDR](/windows/win32/winsock/sockaddr-2)結構的大小）。

- WSAEINPROGRESS 封鎖的 Windows 通訊端呼叫正在進行中。

- `Listen`在接受之前，不會叫用 WSAEINVAL。

- WSAEMFILE 在進入接受時佇列是空的，而且沒有可用的描述項。

- WSAENOBUFS 沒有可用的緩衝區空間。

- WSAENOTSOCK 描述元不是通訊端。

- WSAEOPNOTSUPP 參考的通訊端不是支援連線導向服務的類型。

- WSAEWOULDBLOCK 通訊端標示為非封鎖，且沒有任何連線可接受。

### <a name="remarks"></a>備註

此常式會解壓縮暫止連接佇列中的第一個連接、使用與此通訊端相同的屬性來建立新的通訊端，並將其附加至*rConnectedSocket*。 如果佇列中沒有暫止的連接，則會傳回 `Accept` 零，並傳回 `GetLastError` 錯誤。 接受的通訊端（ *rConnectedSocket）* 不能用來接受更多連接。 原始通訊端會保持開啟並接聽。

引數*lpSockAddr*是一個結果參數，會以連接通訊端的位址填入，如同通訊層所知。 `Accept`會與以連接為基礎的通訊端類型搭配使用，例如 SOCK_STREAM。

## <a name="casyncsocketasyncselect"></a><a name="asyncselect"></a>CAsyncSocket：： AsyncSelect

呼叫此成員函式以要求通訊端的事件通知。

```
BOOL AsyncSelect(long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```

### <a name="parameters"></a>參數

*lEvent*<br/>
位元遮罩，指定應用程式感興趣的網路事件組合。

- FD_READ 想要接收已準備好讀取的通知。

- FD_WRITE 想要在資料可供讀取時收到通知。

- FD_OOB 想要接收頻外資料抵達的通知。

- FD_ACCEPT 想要接收連入連線的通知。

- FD_CONNECT 想要接收連接結果的通知。

- FD_CLOSE 想要在對等端關閉通訊端時收到通知。

### <a name="return-value"></a>傳回值

如果函式成功，則為非零;否則，您可以藉由呼叫[GetLastError](#getlasterror)來抓取特定的錯誤碼。 下列錯誤適用于此成員函式：

- WSANOTINITIALISED 成功的[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必須在使用此 API 之前進行。

- WSAENETDOWN Windows 通訊端執行偵測到網路子系統失敗。

- WSAEINVAL 表示其中一個指定的參數無效。

- WSAEINPROGRESS 封鎖的 Windows 通訊端作業正在進行中。

### <a name="remarks"></a>備註

此函式是用來指定要為通訊端呼叫的 MFC 回呼通知函式。 `AsyncSelect`會自動將此通訊端設定為非封鎖模式。 如需詳細資訊，請參閱[Windows 通訊端：通訊端通知](../../mfc/windows-sockets-socket-notifications.md)文章。

## <a name="casyncsocketattach"></a><a name="attach"></a>CAsyncSocket：： Attach

呼叫這個成員函式，將*hSocket*控制碼附加至 `CAsyncSocket` 物件。

```
BOOL Attach(
    SOCKET hSocket, long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```

### <a name="parameters"></a>參數

*hSocket*<br/>
包含通訊端的控制碼。

*lEvent*<br/>
位元遮罩，指定應用程式感興趣的網路事件組合。

- FD_READ 想要接收已準備好讀取的通知。

- FD_WRITE 想要在資料可供讀取時收到通知。

- FD_OOB 想要接收頻外資料抵達的通知。

- FD_ACCEPT 想要接收連入連線的通知。

- FD_CONNECT 想要接收連接結果的通知。

- FD_CLOSE 想要在對等端關閉通訊端時收到通知。

### <a name="return-value"></a>傳回值

如果函式成功，則為非零。

### <a name="remarks"></a>備註

通訊端控制碼會儲存在物件的[m_hSocket](#m_hsocket)資料成員中。

## <a name="casyncsocketbind"></a><a name="bind"></a>CAsyncSocket：： Bind

呼叫這個成員函式，將本機位址與通訊端產生關聯。

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
網路位址，這是一個點號，例如 "128.56.22.8"。 傳遞這個參數的 Null 字串，表示 `CAsyncSocket` 實例應該接聽所有網路介面上的用戶端活動。

*lpSockAddr*<br/>
[SOCKADDR](/windows/win32/winsock/sockaddr-2)結構的指標，其中包含要指派給這個通訊端的位址。

*nSockAddrLen*<br/>
*LpSockAddr*中位址的長度（以位元組為單位）。

### <a name="return-value"></a>傳回值

如果函式成功，則為非零;否則，您可以藉由呼叫[GetLastError](#getlasterror)來抓取特定的錯誤碼。 下列清單涵蓋一些可能會傳回的錯誤。 如需完整清單，請參閱[Windows Socket 錯誤碼](/windows/win32/winsock/windows-sockets-error-codes-2)。

- WSANOTINITIALISED 成功的[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必須在使用此 API 之前進行。

- WSAENETDOWN Windows 通訊端執行偵測到網路子系統失敗。

- WSAEADDRINUSE 指定的位址已在使用中。 （請參閱[SetSockOpt](#setsockopt)底下的 SO_REUSEADDR 通訊端選項）。

- WSAEFAULT *nSockAddrLen*引數太小（小於[SOCKADDR](/windows/win32/winsock/sockaddr-2)結構的大小）。

- WSAEINPROGRESS 封鎖的 Windows 通訊端呼叫正在進行中。

- 此埠不支援 WSAEAFNOSUPPORT 指定的位址系列。

- WSAEINVAL 通訊端已系結至位址。

- WSAENOBUFS 沒有足夠的可用緩衝區，連接太多。

- WSAENOTSOCK 描述元不是通訊端。

### <a name="remarks"></a>備註

此常式會用於未連接的資料包或資料流程通訊端，然後再進行後續 `Connect` 或 `Listen` 呼叫。 在接受連線要求之前，接聽伺服器通訊端必須選取埠號碼，並藉由呼叫讓 Windows 通訊端知道 `Bind` 。 `Bind`將區功能變數名稱稱指派給未命名的通訊端，以建立通訊端的本機關聯（主機位址/埠號碼）。

## <a name="casyncsocketcasyncsocket"></a><a name="casyncsocket"></a>CAsyncSocket：： CAsyncSocket

構造空白的通訊端物件。

```
CAsyncSocket();
```

### <a name="remarks"></a>備註

在建立物件之後，您必須呼叫其 `Create` 成員函式以建立通訊端資料結構，並系結其位址。 （在 Windows 通訊端通訊的伺服器端上，當接聽通訊端建立要在呼叫中使用的通訊端時， `Accept` 您不會 `Create` 針對該通訊端呼叫）。

## <a name="casyncsocketclose"></a><a name="close"></a>CAsyncSocket：： Close

關閉通訊端。

```
virtual void Close();
```

### <a name="remarks"></a>備註

此函式會釋出通訊端描述元，以便進一步參考它將會失敗，並出現錯誤 WSAENOTSOCK。 如果這是基礎通訊端的最後一個參考，則會捨棄相關聯的命名資訊和佇列資料。 通訊端物件的析構函式 `Close` 會為您呼叫。

對於 `CAsyncSocket` （但不適用於 `CSocket` ），的語義 `Close` 會受到通訊端選項 SO_LINGER 和 SO_DONTLINGER 的影響。 如需詳細資訊，請參閱成員函式 `GetSockOpt` 。

## <a name="casyncsocketconnect"></a><a name="connect"></a>CAsyncSocket：： Connect

呼叫這個成員函式，以建立與未連接資料流程或資料包通訊端的連線。

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
[SOCKADDR](/windows/win32/winsock/sockaddr-2)結構的指標，其中包含已連接之通訊端的位址。

*nSockAddrLen*<br/>
*LpSockAddr*中位址的長度（以位元組為單位）。

### <a name="return-value"></a>傳回值

如果函式成功，則為非零;否則，您可以藉由呼叫[GetLastError](#getlasterror)來抓取特定的錯誤碼。 如果這表示錯誤碼為 WSAEWOULDBLOCK，且您的應用程式使用可覆寫的回呼，則當連接作業完成時，您的應用程式將會收到 `OnConnect` 訊息。 下列錯誤適用于此成員函式：

- WSANOTINITIALISED 成功的[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必須在使用此 API 之前進行。

- WSAENETDOWN Windows 通訊端執行偵測到網路子系統失敗。

- WSAEADDRINUSE 指定的位址已在使用中。

- WSAEINPROGRESS 封鎖的 Windows 通訊端呼叫正在進行中。

- WSAEADDRNOTAVAIL 指定的位址無法從本機電腦使用。

- 指定系列中的 WSAEAFNOSUPPORT 位址無法與此通訊端搭配使用。

- WSAECONNREFUSED 已拒絕連線嘗試。

- 需要 WSAEDESTADDRREQ 目的地位址。

- WSAEFAULT *nSockAddrLen*引數不正確。

- WSAEINVAL 不正確主機位址。

- WSAEISCONN 通訊端已連線。

- WSAEMFILE 沒有其他可用的檔案描述項。

- 目前無法從這部主機連線到網路 WSAENETUNREACH。

- WSAENOBUFS 沒有可用的緩衝區空間。 無法連接通訊端。

- WSAENOTSOCK 描述元不是通訊端。

- WSAETIMEDOUT 嘗試連接逾時，而未建立連線。

- WSAEWOULDBLOCK 通訊端標示為非封鎖，且無法立即完成連接。

### <a name="remarks"></a>備註

如果通訊端未系結，則系統會將唯一的值指派給本機關聯，並將通訊端標示為已系結。 請注意，如果名稱結構的 [位址] 欄位全部為零， `Connect` 則會傳回零。 若要取得擴充的錯誤資訊，請呼叫成員函式 `GetLastError` 。

對於資料流程通訊端（類型 SOCK_STREAM），會起始作用中的連接到外部主機。 當通訊端呼叫成功完成時，通訊端已準備好傳送/接收資料。

若為資料包通訊端（類型 SOCK_DGRAM），則會設定預設目的地，以用於後續 `Send` 和 `Receive` 呼叫。

## <a name="casyncsocketcreate"></a><a name="create"></a>CAsyncSocket：： Create

`Create`在建立通訊端物件後呼叫成員函式，以建立 Windows 通訊端並加以附加。

```
BOOL Create(
    UINT nSocketPort = 0,
    int nSocketType = SOCK_STREAM,
    long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE,
    LPCTSTR lpszSocketAddress = NULL);
```

### <a name="parameters"></a>參數

*nSocketPort*<br/>
要與通訊端搭配使用的知名埠; 如果您想要讓 Windows 通訊端選取埠，則為0。

*nSocketType*<br/>
SOCK_STREAM 或 SOCK_DGRAM。

*lEvent*<br/>
位元遮罩，指定應用程式感興趣的網路事件組合。

- FD_READ 想要接收已準備好讀取的通知。

- FD_WRITE 想要接收寫入準備就緒的通知。

- FD_OOB 想要接收頻外資料抵達的通知。

- FD_ACCEPT 想要接收連入連線的通知。

- FD_CONNECT 想要接收已完成連接的通知。

- FD_CLOSE 想要接收通訊端關閉的通知。

*lpszSockAddress*<br/>
字串的指標，其中包含已連接之通訊端的網路位址，這是一個點的數位，例如 "128.56.22.8"。傳遞這個參數的 Null 字串，表示 `CAsyncSocket` 實例應該接聽所有網路介面上的用戶端活動。

### <a name="return-value"></a>傳回值

如果函式成功，則為非零;否則，您可以藉由呼叫[GetLastError](#getlasterror)來抓取特定的錯誤碼。 下列錯誤適用于此成員函式：

- WSANOTINITIALISED 成功的[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必須在使用此 API 之前進行。

- WSAENETDOWN Windows 通訊端執行偵測到網路子系統失敗。

- 不支援 WSAEAFNOSUPPORT 指定的位址系列。

- WSAEINPROGRESS 封鎖的 Windows 通訊端作業正在進行中。

- WSAEMFILE 沒有其他可用的檔案描述項。

- WSAENOBUFS 沒有可用的緩衝區空間。 無法建立通訊端。

- 不支援 WSAEPROTONOSUPPORT 指定的埠。

- WSAEPROTOTYPE 指定的埠是此通訊端的錯誤類型。

- 此位址系列不支援 WSAESOCKTNOSUPPORT 指定的通訊端類型。

### <a name="remarks"></a>備註

`Create`呼叫[通訊端](#socket)，如果成功，它會呼叫[bind](#bind)來將通訊端系結至指定的位址。 支援的通訊端類型如下：

- SOCK_STREAM 提供排序、可靠、全雙工、以連接為基礎的位元組資料流程。 使用網際網路位址系列的傳輸控制通訊協定（TCP）。

- SOCK_DGRAM 支援資料包，其為固定（通常是小型）最大長度的無連接、不可靠的封包。 針對網際網路位址系列使用使用者資料包協定（UDP）。

    > [!NOTE]
    >  成員函式 `Accept` 會採用新的空白物件的參考 `CSocket` 做為其參數。 在呼叫之前，您必須先建立這個物件 `Accept` 。 請記住，如果此通訊端物件超出範圍，連接就會關閉。 請勿呼叫 `Create` 這個新通訊端物件的。

> [!IMPORTANT]
> `Create`不**是安全**執行緒。  如果您要在多執行緒環境中呼叫它，而執行緒可以由不同的執行緒同時叫用，請務必使用 mutex 或其他同步處理鎖定來保護每個呼叫。

如需串流和資料包通訊端的詳細資訊，請參閱[Windows 通訊端：背景](../../mfc/windows-sockets-background.md)和[windows 通訊端：埠和通訊端位址](../../mfc/windows-sockets-ports-and-socket-addresses.md)和[windows socket 2 API](/windows/win32/WinSock/windows-sockets-start-page-2)文章。

## <a name="casyncsocketcreateex"></a><a name="createex"></a>CAsyncSocket：： CreateEx

`CreateEx`在建立通訊端物件後呼叫成員函式，以建立 Windows 通訊端並加以附加。

當您需要提供如通訊端類型的 advanced 選項時，請使用此函數。

```
BOOL CreateEx(
    ADDRINFOT* pAI,
    long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```

### <a name="parameters"></a>參數

*pAI*<br/>
[ADDRINFOT](https://docs.microsoft.com/windows/win32/api/ws2def/ns-ws2def-addrinfoa)的指標，用來存放通訊端資訊，例如系列和通訊端類型。

*lEvent*<br/>
位元遮罩，指定應用程式感興趣的網路事件組合。

- FD_READ 想要接收已準備好讀取的通知。

- FD_WRITE 想要接收寫入準備就緒的通知。

- FD_OOB 想要接收頻外資料抵達的通知。

- FD_ACCEPT 想要接收連入連線的通知。

- FD_CONNECT 想要接收已完成連接的通知。

- FD_CLOSE 想要接收通訊端關閉的通知。

### <a name="return-value"></a>傳回值

請參閱[Create （）](#return-value-5)的傳回值。

### <a name="remarks"></a>備註

請參閱[Create （）](#remarks-8)的備註。

## <a name="casyncsocketdetach"></a><a name="detach"></a>CAsyncSocket：:D etach

呼叫這個成員函式，將*m_hSocket*資料成員中的通訊端控制碼從物件卸離 `CAsyncSocket` ，並將*m_hSocket*設定為 Null。

```
SOCKET Detach();
```

## <a name="casyncsocketfromhandle"></a><a name="fromhandle"></a>CAsyncSocket：： FromHandle

傳回物件的指標 `CAsyncSocket` 。

```
static CAsyncSocket* PASCAL FromHandle(SOCKET hSocket);
```

### <a name="parameters"></a>參數

*hSocket*<br/>
包含通訊端的控制碼。

### <a name="return-value"></a>傳回值

物件的指標 `CAsyncSocket` ，如果沒有 `CAsyncSocket` 物件附加至*hSocket*，則為 Null。

### <a name="remarks"></a>備註

當提供通訊端控制碼時，如果 `CAsyncSocket` 物件未附加至控制碼，則成員函式會傳回 Null。

## <a name="casyncsocketgetlasterror"></a><a name="getlasterror"></a>CAsyncSocket：： GetLastError

呼叫這個成員函式，以取得最後一個失敗作業的錯誤狀態。

```
static int PASCAL GetLastError();
```

### <a name="return-value"></a>傳回值

傳回值會指出這個執行緒執行的最後一個 Windows 通訊端 API 常式的錯誤碼。

### <a name="remarks"></a>備註

當特定成員函式指出發生錯誤時， `GetLastError` 應該呼叫來取得適當的錯誤碼。 如需適用的錯誤碼清單，請參閱個別成員函式描述。

如需錯誤碼的詳細資訊，請參閱[Windows socket 2 API](/windows/win32/WinSock/windows-sockets-start-page-2)。

## <a name="casyncsocketgetpeername"></a><a name="getpeername"></a>CAsyncSocket：： GetPeerName

呼叫這個成員函式，以取得此通訊端所連接的對等通訊端位址。

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
參考儲存埠的 UINT。

*lpSockAddr*<br/>
接收對等通訊端名稱之[SOCKADDR](/windows/win32/winsock/sockaddr-2)結構的指標。

*lpSockAddrLen*<br/>
*LpSockAddr*中位址長度的指標（以位元組為單位）。 傳回時， *lpSockAddrLen*引數包含以位元組為單位傳回的實際*lpSockAddr*大小。

### <a name="return-value"></a>傳回值

如果函式成功，則為非零;否則，您可以藉由呼叫[GetLastError](#getlasterror)來抓取特定的錯誤碼。 下列錯誤適用于此成員函式：

- WSANOTINITIALISED 成功的[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必須在使用此 API 之前進行。

- WSAENETDOWN Windows 通訊端執行偵測到網路子系統失敗。

- WSAEFAULT *lpSockAddrLen*引數不夠大。

- WSAEINPROGRESS 封鎖的 Windows 通訊端呼叫正在進行中。

- WSAENOTCONN 通訊端未連線。

- WSAENOTSOCK 描述元不是通訊端。

### <a name="remarks"></a>備註

若要處理 IPv6 位址，請使用[CAsyncSocket：： GetPeerNameEx](#getpeernameex)。

## <a name="casyncsocketgetpeernameex"></a><a name="getpeernameex"></a>CAsyncSocket：： GetPeerNameEx

呼叫這個成員函式，以取得此通訊端所連接的對等通訊端位址（處理 IPv6 位址）。

```
BOOL GetPeerNameEx(
    CString& rPeerAddress,
    UINT& rPeerPort);
```

### <a name="parameters"></a>參數

*rPeerAddress*<br/>
參考 `CString` 接收點數位 IP 位址的物件。

*rPeerPort*<br/>
參考儲存埠的 UINT。

### <a name="return-value"></a>傳回值

如果函式成功，則為非零;否則，您可以藉由呼叫[GetLastError](#getlasterror)來抓取特定的錯誤碼。 下列錯誤適用于此成員函式：

- WSANOTINITIALISED 成功的[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必須在使用此 API 之前進行。

- WSAENETDOWN Windows 通訊端執行偵測到網路子系統失敗。

- WSAEFAULT *lpSockAddrLen*引數不夠大。

- WSAEINPROGRESS 封鎖的 Windows 通訊端呼叫正在進行中。

- WSAENOTCONN 通訊端未連線。

- WSAENOTSOCK 描述元不是通訊端。

### <a name="remarks"></a>備註

此函式與[CAsyncSocket：： GetPeerName](#getpeername)相同，不同之處在于它會處理 IPv6 位址以及較舊的通訊協定。

## <a name="casyncsocketgetsockname"></a><a name="getsockname"></a>CAsyncSocket：： GetSockName

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
參考儲存埠的 UINT。

*lpSockAddr*<br/>
接收通訊端位址之[SOCKADDR](/windows/win32/winsock/sockaddr-2)結構的指標。

*lpSockAddrLen*<br/>
*LpSockAddr*中位址長度的指標（以位元組為單位）。

### <a name="return-value"></a>傳回值

如果函式成功，則為非零;否則，您可以藉由呼叫[GetLastError](#getlasterror)來抓取特定的錯誤碼。 下列錯誤適用于此成員函式：

- WSANOTINITIALISED 成功的[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必須在使用此 API 之前進行。

- WSAENETDOWN Windows 通訊端執行偵測到網路子系統失敗。

- WSAEFAULT *lpSockAddrLen*引數不夠大。

- WSAEINPROGRESS 封鎖的 Windows 通訊端作業正在進行中。

- WSAENOTSOCK 描述元不是通訊端。

- WSAEINVAL 通訊端尚未系結至具有的位址 `Bind` 。

### <a name="remarks"></a>備註

此呼叫在進行呼叫時特別有用， `Connect` 而不需要先執行 `Bind` ; 此呼叫會提供唯一的方法，讓您判斷系統已設定的本機關聯。

若要處理 IPv6 位址，請使用[CAsyncSocket：： GetSockNameEx](#getsocknameex)

## <a name="casyncsocketgetsocknameex"></a><a name="getsocknameex"></a>CAsyncSocket：： GetSockNameEx

呼叫此成員函式以取得通訊端的本機名稱（處理 IPv6 位址）。

```
BOOL GetSockNameEx(
    CString& rSocketAddress,
    UINT& rSocketPort);
```

### <a name="parameters"></a>參數

*rSocketAddress*<br/>
參考 `CString` 接收點數位 IP 位址的物件。

*rSocketPort*<br/>
參考儲存埠的 UINT。

### <a name="return-value"></a>傳回值

如果函式成功，則為非零;否則，您可以藉由呼叫[GetLastError](#getlasterror)來抓取特定的錯誤碼。 下列錯誤適用于此成員函式：

- WSANOTINITIALISED 成功的[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必須在使用此 API 之前進行。

- WSAENETDOWN Windows 通訊端執行偵測到網路子系統失敗。

- WSAEFAULT *lpSockAddrLen*引數不夠大。

- WSAEINPROGRESS 封鎖的 Windows 通訊端作業正在進行中。

- WSAENOTSOCK 描述元不是通訊端。

- WSAEINVAL 通訊端尚未系結至具有的位址 `Bind` 。

### <a name="remarks"></a>備註

此呼叫與[CAsyncSocket：： GetSockName](#getsockname)相同，不同之處在于它會處理 IPv6 位址以及較舊的通訊協定。

此呼叫在進行呼叫時特別有用， `Connect` 而不需要先執行 `Bind` ; 此呼叫會提供唯一的方法，讓您判斷系統已設定的本機關聯。

## <a name="casyncsocketgetsockopt"></a><a name="getsockopt"></a>CAsyncSocket：： GetSockOpt

呼叫這個成員函式以抓取通訊端選項。

```
BOOL GetSockOpt(
    int nOptionName,
    void* lpOptionValue,
    int* lpOptionLen,
    int nLevel = SOL_SOCKET);
```

### <a name="parameters"></a>參數

*nOptionName*<br/>
要取得其值的通訊端選項。

*lpOptionValue*<br/>
緩衝區的指標，其中會傳回所要求之選項的值。 與選取的選項相關聯的值會在緩衝區*lpOptionValue*中傳回。 *LpOptionLen*所指向的整數原本應該包含這個緩衝區的大小（以位元組為單位）;傳回時，會將它設定為傳回值的大小。 若為 SO_LINGER，這會是結構的大小， `LINGER` 而所有其他選項則會是 BOOL 或**int**的大小，視選項而定。 請在 [備註] 區段中查看選項及其大小的清單。

*lpOptionLen*<br/>
*LpOptionValue*緩衝區大小的指標（以位元組為單位）。

*nLevel*<br/>
定義選項的層級;唯一支援的層級為 SOL_SOCKET 和 IPPROTO_TCP。

### <a name="return-value"></a>傳回值

如果函式成功，則為非零;否則，您可以藉由呼叫[GetLastError](#getlasterror)來抓取特定的錯誤碼。 如果從未使用設定選項 `SetSockOpt` ，則會傳回 `GetSockOpt` 選項的預設值。 下列錯誤適用于此成員函式：

- WSANOTINITIALISED 成功的[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必須在使用此 API 之前進行。

- WSAENETDOWN Windows 通訊端執行偵測到網路子系統失敗。

- WSAEFAULT *lpOptionLen*引數無效。

- WSAEINPROGRESS 封鎖的 Windows 通訊端作業正在進行中。

- WSAENOPROTOOPT 選項不明或不受支援。 特別的是，類型 SOCK_STREAM 的通訊端不支援 SO_BROADCAST，但 SO_ACCEPTCONN、SO_DONTLINGER、SO_KEEPALIVE、SO_LINGER 和 SO_OOBINLINE 在類型 SOCK_DGRAM 的通訊端上不受支援。

- WSAENOTSOCK 描述元不是通訊端。

### <a name="remarks"></a>備註

`GetSockOpt`在任何狀態下，抓取與任何類型之通訊端相關聯之通訊端選項的目前值，並將結果儲存在*lpOptionValue*中。 選項會影響通訊端作業，例如封包的路由、頻外資料傳輸等等。

支援下列選項 `GetSockOpt` 。 型別會識別*lpOptionValue*所定址的資料類型。 TCP_NODELAY 選項會使用層級 IPPROTO_TCP;所有其他選項都會使用層級 SOL_SOCKET。

|值|類型|意義|
|-----------|----------|-------------|
|SO_ACCEPTCONN|BOOL|通訊端正在接聽。|
|SO_BROADCAST|BOOL|通訊端會針對廣播訊息的傳輸進行設定。|
|SO_DEBUG|BOOL|已啟用調試。|
|SO_DONTLINGER|BOOL|若為 true，則會停用 SO_LINGER 選項。|
|SO_DONTROUTE|BOOL|已停用路由。|
|SO_ERROR|**int**|取出錯誤狀態並清除。|
|SO_KEEPALIVE|BOOL|已傳送 keep-alive。|
|SO_LINGER|`struct LINGER`|傳回目前的逗留選項。|
|SO_OOBINLINE|BOOL|在正常資料流程中收到頻外資料。|
|SO_RCVBUF|int|接收的緩衝區大小。|
|SO_REUSEADDR|BOOL|通訊端可以系結至已在使用中的位址。|
|SO_SNDBUF|**int**|傳送的緩衝區大小。|
|SO_TYPE|**int**|通訊端的類型（例如 SOCK_STREAM）。|
|TCP_NODELAY|BOOL|停用用於傳送聯合的 Nagle 演算法。|

不支援的 Berkeley 軟體發佈（BSD）選項如下 `GetSockOpt` ：

|值|類型|意義|
|-----------|----------|-------------|
|SO_RCVLOWAT|**int**|接收下限標準。|
|SO_RCVTIMEO|**int**|接收超時。|
|SO_SNDLOWAT|**int**|傳送下限標準。|
|SO_SNDTIMEO|**int**|傳送超時。|
|IP_OPTIONS||取得 IP 標頭中的選項。|
|TCP_MAXSEG|**int**|取得 TCP 區段大小上限。|

`GetSockOpt`使用不支援的選項呼叫，會導致從傳回 WSAENOPROTOOPT 的錯誤碼 `GetLastError` 。

## <a name="casyncsocketioctl"></a><a name="ioctl"></a>CAsyncSocket：： IOCtl

呼叫此成員函式以控制通訊端的模式。

```
BOOL IOCtl(
    long lCommand,
    DWORD* lpArgument);
```

### <a name="parameters"></a>參數

*lCommand*<br/>
要在通訊端上執行的命令。

*lpArgument*<br/>
*LCommand*之參數的指標。

### <a name="return-value"></a>傳回值

如果函式成功，則為非零;否則，您可以藉由呼叫[GetLastError](#getlasterror)來抓取特定的錯誤碼。 下列錯誤適用于此成員函式：

- WSANOTINITIALISED 成功的[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必須在使用此 API 之前進行。

- WSAENETDOWN Windows 通訊端執行偵測到網路子系統失敗。

- WSAEINVAL *lCommand*不是有效的命令，或*LpArgument*不是*lCommand*可接受的參數，或命令不適用於提供的通訊端類型。

- WSAEINPROGRESS 封鎖的 Windows 通訊端作業正在進行中。

- WSAENOTSOCK 描述元不是通訊端。

### <a name="remarks"></a>備註

此常式可用於任何狀態的任何通訊端。 它可用來取得或抓取與通訊端相關聯的指令引數，而不受通訊協定和通訊子系統的影響。 支援的命令如下：

- FIONBIO 啟用或停用通訊端上的非封鎖模式。 *LpArgument*參數指向 `DWORD` ，如果要啟用非封鎖模式則為非零，如果要停用則為零。 如果 `AsyncSelect` 已在通訊端上發出，則任何使用將 `IOCtl` 通訊端設定回封鎖模式的嘗試都會失敗，並產生 WSAEINVAL。 若要將通訊端設定回封鎖模式並防止 WSAEINVAL 錯誤，應用程式必須先透過 `AsyncSelect` 呼叫 `AsyncSelect` 並以等於0的*lEvent*參數來停用，然後再呼叫 `IOCtl` 。

- FIONREAD 會判斷可以使用此通訊端的一個呼叫來讀取的最大位元組數目 `Receive` 。 *LpArgument*參數指向 `DWORD` `IOCtl` 儲存結果的。 如果此通訊端屬於 SOCK_STREAM 類型，則 FIONREAD 會傳回可在單一中讀取的總數據量， `Receive` 通常與在通訊端上排入佇列的總數據量相同。 如果此通訊端屬於 SOCK_DGRAM 類型，則 FIONREAD 會傳回在通訊端上排入佇列的第一個資料包大小。

- SIOCATMARK 判斷是否已讀取所有頻外資料。 這只適用于 SOCK_STREAM 類型的通訊端，其已設定為可在任何頻外資料（SO_OOBINLINE）的行內接收。 如果沒有頻外資料正在等候讀取，作業會傳回非零值。 否則，它會傳回0，而下一個 `Receive` 或 `ReceiveFrom` 在通訊端上執行的將會抓取 "mark" 前面的部分或全部資料; 應用程式應該使用 SIOCATMARK 作業來判斷是否有任何資料保留。 如果在「緊急」（頻外）資料之前有任何一般資料，則會依序接收。 （請注意， `Receive` 或 `ReceiveFrom` 永遠不會在相同的呼叫中混用頻外和一般資料）。*LpArgument*參數指向 `DWORD` `IOCtl` 儲存結果的。

此函式是 `ioctl()` Berkeley 通訊端中使用的子集。 特別的是，沒有相當於 FIOASYNC 的命令，而 SIOCATMARK 是唯一支援的通訊端層級命令。

## <a name="casyncsocketlisten"></a><a name="listen"></a>CAsyncSocket：：接聽

呼叫此成員函式以接聽連入連線要求。

```
BOOL Listen(int nConnectionBacklog = 5);
```

### <a name="parameters"></a>參數

*nConnectionBacklog*<br/>
擱置連接的佇列可以成長的最大長度。 有效範圍是從1到5。

### <a name="return-value"></a>傳回值

如果函式成功，則為非零;否則，您可以藉由呼叫[GetLastError](#getlasterror)來抓取特定的錯誤碼。 下列錯誤適用于此成員函式：

- WSANOTINITIALISED 成功的[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必須在使用此 API 之前進行。

- WSAENETDOWN Windows 通訊端執行偵測到網路子系統失敗。

- WSAEADDRINUSE 已嘗試在使用中的位址上進行接聽。

- WSAEINPROGRESS 封鎖的 Windows 通訊端作業正在進行中。

- WSAEINVAL 通訊端尚未系結， `Bind` 或已連線。

- WSAEISCONN 通訊端已連線。

- WSAEMFILE 沒有其他可用的檔案描述項。

- WSAENOBUFS 沒有可用的緩衝區空間。

- WSAENOTSOCK 描述元不是通訊端。

- WSAEOPNOTSUPP 參考的通訊端不屬於支援作業的類型 `Listen` 。

### <a name="remarks"></a>備註

若要接受連接，會先使用建立通訊端 `Create` ，並以指定連入連線的待處理專案 `Listen` ，然後使用來接受連接 `Accept` 。 `Listen`僅適用于支援連接的通訊端，也就是 SOCK_STREAM 類型的 socket。 此通訊端會進入「被動」模式，其中的傳入連線會被認可並排入佇列等待處理常式接受。

此函式通常是由伺服器（或任何想要接受連線的應用程式）所使用，其中可能會有一個以上的連線要求：如果連接要求抵達佇列已滿，用戶端將會收到錯誤，指出 WSAECONNREFUSED。

`Listen`當沒有可用的埠（描述項）時，會嘗試繼續執行等理性判斷功能。 它會接受連線，直到佇列清空為止。 如果埠可供使用，稍後對或的呼叫 `Listen` `Accept` 會將佇列重新填滿目前或最新的「待處理專案」（如果可能的話），並繼續接聽連入連接。

## <a name="casyncsocketm_hsocket"></a><a name="m_hsocket"></a>CAsyncSocket：： m_hSocket

包含此物件所封裝之通訊端的通訊端控制碼 `CAsyncSocket` 。

```
SOCKET m_hSocket;
```

## <a name="casyncsocketonaccept"></a><a name="onaccept"></a>CAsyncSocket：： OnAccept

由架構呼叫以通知接聽通訊端，它可以藉由呼叫[accept](#accept)成員函式來接受暫止的連接要求。

```
virtual void OnAccept(int nErrorCode);
```

### <a name="parameters"></a>參數

*nErrorCode*<br/>
最新的通訊端錯誤。 下列錯誤碼適用于成員函式 `OnAccept` ：

- **0**已成功執行函數。

- WSAENETDOWN Windows 通訊端執行偵測到網路子系統失敗。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[Windows socket：通訊端通知](../../mfc/windows-sockets-socket-notifications.md)。

## <a name="casyncsocketonclose"></a><a name="onclose"></a>CAsyncSocket：： OnClose

由架構呼叫以通知這個通訊端，連線的通訊端已由其進程關閉。

```
virtual void OnClose(int nErrorCode);
```

### <a name="parameters"></a>參數

*nErrorCode*<br/>
最新的通訊端錯誤。 下列錯誤碼適用于成員函式 `OnClose` ：

- **0**已成功執行函數。

- WSAENETDOWN Windows 通訊端執行偵測到網路子系統失敗。

- WSAECONNRESET 遠端端已重設連接。

- WSAECONNABORTED 連接已因超時或其他失敗而中止。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[Windows socket：通訊端通知](../../mfc/windows-sockets-socket-notifications.md)。

## <a name="casyncsocketonconnect"></a><a name="onconnect"></a>CAsyncSocket：： OnConnect

由架構呼叫，以通知此連接的通訊端其連線嘗試已完成，無論是成功或錯誤。

```
virtual void OnConnect(int nErrorCode);
```

### <a name="parameters"></a>參數

*nErrorCode*<br/>
最新的通訊端錯誤。 下列錯誤碼適用于成員函式 `OnConnect` ：

- **0**已成功執行函數。

- WSAEADDRINUSE 指定的位址已在使用中。

- WSAEADDRNOTAVAIL 指定的位址無法從本機電腦使用。

- 指定系列中的 WSAEAFNOSUPPORT 位址無法與此通訊端搭配使用。

- WSAECONNREFUSED 已強制拒絕連接的嘗試。

- 需要 WSAEDESTADDRREQ 目的地位址。

- WSAEFAULT *lpSockAddrLen*引數不正確。

- WSAEINVAL 通訊端已系結至位址。

- WSAEISCONN 通訊端已連線。

- WSAEMFILE 沒有其他可用的檔案描述項。

- 目前無法從這部主機連線到網路 WSAENETUNREACH。

- WSAENOBUFS 沒有可用的緩衝區空間。 無法連接通訊端。

- WSAENOTCONN 通訊端未連線。

- WSAENOTSOCK 描述元是一個檔案，而不是通訊端。

- WSAETIMEDOUT 在未建立連線的情況下，連接的嘗試超時。

### <a name="remarks"></a>備註

> [!NOTE]
> 在[CSocket](../../mfc/reference/csocket-class.md)中， `OnConnect` 永遠不會呼叫通知函式。 針對連線，您只需要呼叫 `Connect` ，這會在連接完成時傳回（不論成功或發生錯誤）。 連接通知的處理方式是 MFC 的執行詳細資料。

如需詳細資訊，請參閱[Windows socket：通訊端通知](../../mfc/windows-sockets-socket-notifications.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCAsyncSocket#1](../../mfc/reference/codesnippet/cpp/casyncsocket-class_1.cpp)]

## <a name="casyncsocketonoutofbanddata"></a><a name="onoutofbanddata"></a>CAsyncSocket：： OnOutOfBandData

由架構呼叫，以通知接收通訊端傳送的通訊端有頻外資料要傳送。

```
virtual void OnOutOfBandData(int nErrorCode);
```

### <a name="parameters"></a>參數

*nErrorCode*<br/>
最新的通訊端錯誤。 下列錯誤碼適用于成員函式 `OnOutOfBandData` ：

- **0**已成功執行函數。

- WSAENETDOWN Windows 通訊端執行偵測到網路子系統失敗。

### <a name="remarks"></a>備註

頻外資料是邏輯上獨立的通道，與 SOCK_STREAM 類型的每一對連接通訊端相關聯。 通道通常用來傳送緊急資料。

MFC 支援頻外資料，但不鼓勵使用類別的使用者 `CAsyncSocket` 。 較簡單的方式是建立第二個通訊端來傳遞這類資料。 如需頻外資料的詳細資訊，請參閱[Windows socket：通訊端通知](../../mfc/windows-sockets-socket-notifications.md)。

## <a name="casyncsocketonreceive"></a><a name="onreceive"></a>CAsyncSocket：： OnReceive

由架構呼叫以通知這個通訊端，緩衝區中有資料可以藉由呼叫成員函式來抓取 `Receive` 。

```
virtual void OnReceive(int nErrorCode);
```

### <a name="parameters"></a>參數

*nErrorCode*<br/>
最新的通訊端錯誤。 下列錯誤碼適用于成員函式 `OnReceive` ：

- **0**已成功執行函數。

- WSAENETDOWN Windows 通訊端執行偵測到網路子系統失敗。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[Windows socket：通訊端通知](../../mfc/windows-sockets-socket-notifications.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCAsyncSocket#2](../../mfc/reference/codesnippet/cpp/casyncsocket-class_2.cpp)]

## <a name="casyncsocketonsend"></a><a name="onsend"></a>CAsyncSocket：： OnSend

由架構呼叫，以通知通訊端它現在可以藉由呼叫成員函式來傳送資料 `Send` 。

```
virtual void OnSend(int nErrorCode);
```

### <a name="parameters"></a>參數

*nErrorCode*<br/>
最新的通訊端錯誤。 下列錯誤碼適用于成員函式 `OnSend` ：

- **0**已成功執行函數。

- WSAENETDOWN Windows 通訊端執行偵測到網路子系統失敗。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[Windows socket：通訊端通知](../../mfc/windows-sockets-socket-notifications.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCAsyncSocket#3](../../mfc/reference/codesnippet/cpp/casyncsocket-class_3.cpp)]

## <a name="casyncsocketoperator-"></a><a name="operator_eq"></a>CAsyncSocket：： operator =

將新值指派給 `CAsyncSocket` 物件。

```cpp
void operator=(const CAsyncSocket& rSrc);
```

### <a name="parameters"></a>參數

*.Rsrc*<br/>
現有物件的參考 `CAsyncSocket` 。

### <a name="remarks"></a>備註

呼叫此函式可將現有的 `CAsyncSocket` 物件複製到另一個 `CAsyncSocket` 物件。

## <a name="casyncsocketoperator-socket"></a><a name="operator_socket"></a>CAsyncSocket：： operator 通訊端

使用這個運算子來抓取物件的通訊端控制碼 `CAsyncSocket` 。

```
operator SOCKET() const;
```

### <a name="return-value"></a>傳回值

如果成功，則為通訊端物件的控制碼;否則為 Null。

### <a name="remarks"></a>備註

您可以使用控制碼直接呼叫 Windows Api。

## <a name="casyncsocketreceive"></a><a name="receive"></a>CAsyncSocket：： Receive

呼叫這個成員函式可從通訊端接收資料。

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
指定進行呼叫的方式。 此函式的語法是由通訊端選項和*nFlags*參數所決定。 後者的建立方式是將下列任何值與 c + +**或**運算子結合：

- MSG_PEEK 查看傳入的資料。 資料會複製到緩衝區中，但不會從輸入佇列中移除。

- MSG_OOB 處理頻外資料。

### <a name="return-value"></a>傳回值

如果沒有發生錯誤， `Receive` 則會傳回接收的位元組數目。 如果連接已關閉，它會傳回0。 否則，會傳回 SOCKET_ERROR 的值，並藉由呼叫[GetLastError](#getlasterror)來抓取特定的錯誤碼。 下列錯誤適用于此成員函式：

- WSANOTINITIALISED 成功的[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必須在使用此 API 之前進行。

- WSAENETDOWN Windows 通訊端執行偵測到網路子系統失敗。

- WSAENOTCONN 通訊端未連線。

- WSAEINPROGRESS 封鎖的 Windows 通訊端作業正在進行中。

- WSAENOTSOCK 描述元不是通訊端。

- 已指定 WSAEOPNOTSUPP MSG_OOB，但通訊端不是 SOCK_STREAM 類型。

- WSAESHUTDOWN 通訊端已關閉;在 `Receive` `ShutDown` 使用設定為0或2的*nHow*叫用之後，就不能在通訊端上呼叫。

- WSAEWOULDBLOCK 通訊端已標示為非封鎖，且作業 `Receive` 會封鎖。

- WSAEMSGSIZE 資料包太大，無法放入指定的緩衝區中，而且已被截斷。

- WSAEINVAL 通訊端尚未與系結 `Bind` 。

- WSAECONNABORTED 虛擬電路因超時或其他失敗而中止。

- WSAECONNRESET 虛擬電路已由遠端端重設。

### <a name="remarks"></a>備註

此函式會用於連接的資料流程或資料包通訊端，並用於讀取傳入的資料。

針對類型 SOCK_STREAM 的通訊端，會傳回目前提供的緩衝區大小最多的資訊。 如果通訊端已設定為用於頻外資料的行內接收（通訊端選項 SO_OOBINLINE），而且未讀取頻外資料，則只會傳回頻外資料。 應用程式可以使用 `IOCtlSIOCATMARK` 選項或[OnOutOfBandData](#onoutofbanddata) ，來判斷是否仍要讀取其他超出範圍的資料。

對於資料包通訊端，資料會從第一個已排入佇列的資料包（最大到提供的緩衝區大小）解壓縮。 如果資料包大於提供的緩衝區，緩衝區會填入資料包的第一個部分，多餘的資料會遺失，並傳回 SOCKET_ERROR 的值，並將 `Receive` 錯誤碼設定為 WSAEMSGSIZE。 如果通訊端沒有內送資料可供使用，則會傳回 SOCKET_ERROR 的值，並將錯誤碼設定為 WSAEWOULDBLOCK。 [OnReceive](#onreceive)回呼函數可以用來判斷何時會到達更多資料。

如果通訊端的類型是 SOCK_STREAM，而遠端端已正常關閉連線，則 `Receive` 會立即完成，並收到0個位元組。 如果已重設連接， `Receive` 將會失敗並出現錯誤 WSAECONNRESET。

`Receive`每次呼叫[CAsyncSocket：： OnReceive](#onreceive)時，應該只呼叫一次。

### <a name="example"></a>範例

  請參閱[CAsyncSocket：： OnReceive](#onreceive)的範例。

## <a name="casyncsocketreceivefrom"></a><a name="receivefrom"></a>CAsyncSocket：： ReceiveFrom

呼叫這個成員函式來接收資料包，並將來源位址儲存在[SOCKADDR](/windows/win32/winsock/sockaddr-2)結構或*rSocketAddress*中。

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
參考儲存埠的 UINT。

*lpSockAddr*<br/>
[SOCKADDR](/windows/win32/winsock/sockaddr-2)結構的指標，它會在傳回時保存來源位址。

*lpSockAddrLen*<br/>
*LpSockAddr*中來源位址長度的指標（以位元組為單位）。

*nFlags*<br/>
指定進行呼叫的方式。 此函式的語法是由通訊端選項和*nFlags*參數所決定。 後者的建立方式是將下列任何值與 c + +**或**運算子結合：

- MSG_PEEK 查看傳入的資料。 資料會複製到緩衝區中，但不會從輸入佇列中移除。

- MSG_OOB 處理頻外資料。

### <a name="return-value"></a>傳回值

如果沒有發生錯誤， `ReceiveFrom` 則會傳回接收的位元組數目。 如果連接已關閉，它會傳回0。 否則，會傳回 SOCKET_ERROR 的值，而且可以藉由呼叫來抓取特定的錯誤碼 `GetLastError` 。 下列錯誤適用于此成員函式：

- WSANOTINITIALISED 成功的[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必須在使用此 API 之前進行。

- WSAENETDOWN Windows 通訊端執行偵測到網路子系統失敗。

- WSAEFAULT *lpSockAddrLen*引數無效： *lpSockAddr*緩衝區太小，無法容納對等位址。

- WSAEINPROGRESS 封鎖的 Windows 通訊端作業正在進行中。

- WSAEINVAL 通訊端尚未與系結 `Bind` 。

- WSAENOTCONN 通訊端未連線（僅限 SOCK_STREAM）。

- WSAENOTSOCK 描述元不是通訊端。

- 已指定 WSAEOPNOTSUPP MSG_OOB，但通訊端不是 SOCK_STREAM 類型。

- WSAESHUTDOWN 通訊端已關閉;在 `ReceiveFrom` `ShutDown` 使用設定為0或2的*nHow*叫用之後，就不能在通訊端上呼叫。

- WSAEWOULDBLOCK 通訊端已標示為非封鎖，且作業 `ReceiveFrom` 會封鎖。

- WSAEMSGSIZE 資料包太大，無法放入指定的緩衝區中，而且已被截斷。

- WSAECONNABORTED 虛擬電路因超時或其他失敗而中止。

- WSAECONNRESET 虛擬電路已由遠端端重設。

### <a name="remarks"></a>備註

此函式是用來讀取（可能連接的）通訊端上的傳入資料，並捕捉傳送資料的來源位址。

若要處理 IPv6 位址，請使用[CAsyncSocket：： ReceiveFromEx](#receivefromex)。

針對類型 SOCK_STREAM 的通訊端，會傳回目前提供的緩衝區大小最多的資訊。 如果通訊端已設定為用於頻外資料的行內接收（通訊端選項 SO_OOBINLINE），而且未讀取頻外資料，則只會傳回頻外資料。 應用程式可以使用 `IOCtlSIOCATMARK` 選項，或 `OnOutOfBandData` 判斷是否仍要讀取其他超出範圍的資料。 SOCK_STREAM 通訊端會忽略*lpSockAddr*和*lpSockAddrLen*參數。

對於資料包通訊端，資料會從第一個已排入佇列的資料包（最大到提供的緩衝區大小）解壓縮。 如果資料包大於提供的緩衝區，則緩衝區會填入訊息的第一個部分，多餘的資料會遺失，並傳回 SOCKET_ERROR 的值，並將 `ReceiveFrom` 錯誤碼設定為 WSAEMSGSIZE。

如果*lpSockAddr*為非零值，而通訊端的類型 SOCK_DGRAM，則傳送資料之通訊端的網路位址會複製到對應的[SOCKADDR](/windows/win32/winsock/sockaddr-2)結構。 *LpSockAddrLen*所指向的值會初始化為此結構的大小，並在傳回時修改，以表示儲存在該處的位址實際大小。 如果通訊端沒有內送資料可供使用，則 `ReceiveFrom` 呼叫會等待資料抵達，除非通訊端為非封鎖。 在此情況下，會傳回 SOCKET_ERROR 的值，並將錯誤碼設定為 WSAEWOULDBLOCK。 `OnReceive`回呼可以用來判斷何時會有更多資料抵達。

如果通訊端的類型是 SOCK_STREAM，而遠端端已正常關閉連線，則 `ReceiveFrom` 會立即完成，並收到0個位元組。

## <a name="casyncsocketreceivefromex"></a><a name="receivefromex"></a>CAsyncSocket：： ReceiveFromEx

呼叫此成員函式以接收資料包，並將來源位址儲存在[SOCKADDR](/windows/win32/winsock/sockaddr-2)結構或*rSocketAddress*中（處理 IPv6 位址）。

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
參考儲存埠的 UINT。

*nFlags*<br/>
指定進行呼叫的方式。 此函式的語法是由通訊端選項和*nFlags*參數所決定。 後者的建立方式是將下列任何值與 c + +**或**運算子結合：

- MSG_PEEK 查看傳入的資料。 資料會複製到緩衝區中，但不會從輸入佇列中移除。

- MSG_OOB 處理頻外資料。

### <a name="return-value"></a>傳回值

如果沒有發生錯誤， `ReceiveFromEx` 則會傳回接收的位元組數目。 如果連接已關閉，它會傳回0。 否則，會傳回 SOCKET_ERROR 的值，而且可以藉由呼叫來抓取特定的錯誤碼 `GetLastError` 。 下列錯誤適用于此成員函式：

- WSANOTINITIALISED 成功的[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必須在使用此 API 之前進行。

- WSAENETDOWN Windows 通訊端執行偵測到網路子系統失敗。

- WSAEFAULT *lpSockAddrLen*引數無效： *lpSockAddr*緩衝區太小，無法容納對等位址。

- WSAEINPROGRESS 封鎖的 Windows 通訊端作業正在進行中。

- WSAEINVAL 通訊端尚未與系結 `Bind` 。

- WSAENOTCONN 通訊端未連線（僅限 SOCK_STREAM）。

- WSAENOTSOCK 描述元不是通訊端。

- 已指定 WSAEOPNOTSUPP MSG_OOB，但通訊端不是 SOCK_STREAM 類型。

- WSAESHUTDOWN 通訊端已關閉;在 `ReceiveFromEx` `ShutDown` 使用設定為0或2的*nHow*叫用之後，就不能在通訊端上呼叫。

- WSAEWOULDBLOCK 通訊端已標示為非封鎖，且作業 `ReceiveFromEx` 會封鎖。

- WSAEMSGSIZE 資料包太大，無法放入指定的緩衝區中，而且已被截斷。

- WSAECONNABORTED 虛擬電路因超時或其他失敗而中止。

- WSAECONNRESET 虛擬電路已由遠端端重設。

### <a name="remarks"></a>備註

此函式是用來讀取（可能連接的）通訊端上的傳入資料，並捕捉傳送資料的來源位址。

此函式與[CAsyncSocket：： ReceiveFrom](#receivefrom)相同，不同之處在于它會處理 IPv6 位址以及較舊的通訊協定。

針對類型 SOCK_STREAM 的通訊端，會傳回目前提供的緩衝區大小最多的資訊。 如果通訊端已設定為用於頻外資料的行內接收（通訊端選項 SO_OOBINLINE），而且未讀取頻外資料，則只會傳回頻外資料。 應用程式可以使用 `IOCtlSIOCATMARK` 選項，或 `OnOutOfBandData` 判斷是否仍要讀取其他超出範圍的資料。 SOCK_STREAM 通訊端會忽略*lpSockAddr*和*lpSockAddrLen*參數。

對於資料包通訊端，資料會從第一個已排入佇列的資料包（最大到提供的緩衝區大小）解壓縮。 如果資料包大於提供的緩衝區，則緩衝區會填入訊息的第一個部分，多餘的資料會遺失，並傳回 SOCKET_ERROR 的值，並將 `ReceiveFromEx` 錯誤碼設定為 WSAEMSGSIZE。

如果*lpSockAddr*為非零值，而通訊端的類型 SOCK_DGRAM，則傳送資料之通訊端的網路位址會複製到對應的[SOCKADDR](/windows/win32/winsock/sockaddr-2)結構。 *LpSockAddrLen*所指向的值會初始化為此結構的大小，並在傳回時修改，以表示儲存在該處的位址實際大小。 如果通訊端沒有內送資料可供使用，則 `ReceiveFromEx` 呼叫會等待資料抵達，除非通訊端為非封鎖。 在此情況下，會傳回 SOCKET_ERROR 的值，並將錯誤碼設定為 WSAEWOULDBLOCK。 `OnReceive`回呼可以用來判斷何時會有更多資料抵達。

如果通訊端的類型是 SOCK_STREAM，而遠端端已正常關閉連線，則 `ReceiveFromEx` 會立即完成，並收到0個位元組。

## <a name="casyncsocketsend"></a><a name="send"></a>CAsyncSocket：： Send

呼叫這個成員函式，在連接的通訊端上傳送資料。

```
virtual int Send(
    const void* lpBuf,
    int nBufLen,
    int nFlags = 0);
```

### <a name="parameters"></a>參數

*lpBuf*<br/>
包含要傳送之資料的緩衝區。

*nBufLen*<br/>
*LpBuf*中的資料長度（以位元組為單位）。

*nFlags*<br/>
指定進行呼叫的方式。 此函式的語法是由通訊端選項和*nFlags*參數所決定。 後者的建立方式是將下列任何值與 c + +**或**運算子結合：

- MSG_DONTROUTE 指定資料不應受限於路由。 Windows 通訊端供應商可以選擇忽略此旗標。

- MSG_OOB 傳送頻外資料（僅限 SOCK_STREAM）。

### <a name="return-value"></a>傳回值

如果沒有發生錯誤， `Send` 則會傳回已傳送的字元總數。 （請注意，這可能小於*nBufLen*所指出的數位）。否則，會傳回 SOCKET_ERROR 的值，並藉由呼叫[GetLastError](#getlasterror)來抓取特定的錯誤碼。 下列錯誤適用于此成員函式：

- WSANOTINITIALISED 成功的[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必須在使用此 API 之前進行。

- WSAENETDOWN Windows 通訊端執行偵測到網路子系統失敗。

- WSAEACCES 要求的位址是廣播位址，但未設定適當的旗標。

- WSAEINPROGRESS 封鎖的 Windows 通訊端作業正在進行中。

- WSAEFAULT *lpBuf*引數不在使用者位址空間的有效部分。

- WSAENETRESET 必須重設連接，因為 Windows 通訊端執行已卸載。

- WSAENOBUFS Windows 通訊端執行會報告緩衝區鎖死。

- WSAENOTCONN 通訊端未連線。

- WSAENOTSOCK 描述元不是通訊端。

- 已指定 WSAEOPNOTSUPP MSG_OOB，但通訊端不是 SOCK_STREAM 類型。

- WSAESHUTDOWN 通訊端已關閉;在 `Send` `ShutDown` 使用設定為1或2的*nHow*叫用之後，就不能在通訊端上呼叫。

- WSAEWOULDBLOCK 通訊端標示為非封鎖，而要求的作業會封鎖。

- WSAEMSGSIZE 通訊端的類型 SOCK_DGRAM，而且資料包大於 Windows 通訊端執行所支援的最大值。

- WSAEINVAL 通訊端尚未與系結 `Bind` 。

- WSAECONNABORTED 虛擬電路因超時或其他失敗而中止。

- WSAECONNRESET 虛擬電路已由遠端端重設。

### <a name="remarks"></a>備註

`Send`用來寫入已連接資料流程或資料包通訊端上的傳出資料。 對於資料包通訊端，必須小心不要超過基礎子網的 IP 封包大小上限，這是由所傳回之 `iMaxUdpDg` [WSADATA](/windows/win32/api/winsock2/ns-winsock2-wsadata)結構中的元素所提供 `AfxSocketInit` 。 如果資料太長而無法透過基礎通訊協定以不變的方式傳遞，則會透過傳回錯誤 WSAEMSGSIZE `GetLastError` ，而且不會傳輸任何資料。

請注意，對於資料包通訊端，成功完成， `Send` 並不表示已成功傳遞資料。

在 `CAsyncSocket` 類型 SOCK_STREAM 的物件上，寫入的位元組數目可以介於1到要求的長度之間，視本機和外部主機上的緩衝區可用性而定。

### <a name="example"></a>範例

  請參閱[CAsyncSocket：： OnSend](#onsend)的範例。

## <a name="casyncsocketsendto"></a><a name="sendto"></a>CAsyncSocket：： SendTo

呼叫這個成員函式，將資料傳送到特定目的地。

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
包含要傳送之資料的緩衝區。

*nBufLen*<br/>
*LpBuf*中的資料長度（以位元組為單位）。

*nHostPort*<br/>
識別通訊端應用程式的埠。

*lpszHostAddress*<br/>
此物件所連接之通訊端的網路位址：電腦名稱稱，例如 "ftp.microsoft.com"，或點數位，例如 "128.56.22.8"。

*nFlags*<br/>
指定進行呼叫的方式。 此函式的語法是由通訊端選項和*nFlags*參數所決定。 後者的建立方式是將下列任何值與 c + +**或**運算子結合：

- MSG_DONTROUTE 指定資料不應受限於路由。 Windows 通訊端供應商可以選擇忽略此旗標。

- MSG_OOB 傳送頻外資料（僅限 SOCK_STREAM）。

*lpSockAddr*<br/>
[SOCKADDR](/windows/win32/winsock/sockaddr-2)結構的指標，其中包含目標通訊端的位址。

*nSockAddrLen*<br/>
*LpSockAddr*中位址的長度（以位元組為單位）。

### <a name="return-value"></a>傳回值

如果沒有發生錯誤， `SendTo` 則會傳回已傳送的字元總數。 （請注意，這可能小於*nBufLen*所指出的數位）。否則，會傳回 SOCKET_ERROR 的值，並藉由呼叫[GetLastError](#getlasterror)來抓取特定的錯誤碼。 下列錯誤適用于此成員函式：

- WSANOTINITIALISED 成功的[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必須在使用此 API 之前進行。

- WSAENETDOWN Windows 通訊端執行偵測到網路子系統失敗。

- WSAEACCES 要求的位址是廣播位址，但未設定適當的旗標。

- WSAEINPROGRESS 封鎖的 Windows 通訊端作業正在進行中。

- WSAEFAULT *lpBuf*或*lpSockAddr*參數不是使用者位址空間的一部分，或*lpSockAddr*引數太小（小於[SOCKADDR](/windows/win32/winsock/sockaddr-2)結構的大小）。

- WSAEINVAL 主機名稱無效。

- WSAENETRESET 必須重設連接，因為 Windows 通訊端執行已卸載。

- WSAENOBUFS Windows 通訊端執行會報告緩衝區鎖死。

- WSAENOTCONN 通訊端未連線（僅限 SOCK_STREAM）。

- WSAENOTSOCK 描述元不是通訊端。

- 已指定 WSAEOPNOTSUPP MSG_OOB，但通訊端不是 SOCK_STREAM 類型。

- WSAESHUTDOWN 通訊端已關閉;在 `SendTo` `ShutDown` 使用設定為1或2的*nHow*叫用之後，就不能在通訊端上呼叫。

- WSAEWOULDBLOCK 通訊端標示為非封鎖，而要求的作業會封鎖。

- WSAEMSGSIZE 通訊端的類型 SOCK_DGRAM，而且資料包大於 Windows 通訊端執行所支援的最大值。

- WSAECONNABORTED 虛擬電路因超時或其他失敗而中止。

- WSAECONNRESET 虛擬電路已由遠端端重設。

- WSAEADDRNOTAVAIL 指定的位址無法從本機電腦使用。

- 指定系列中的 WSAEAFNOSUPPORT 位址無法與此通訊端搭配使用。

- 需要 WSAEDESTADDRREQ 目的地位址。

- 目前無法從這部主機連線到網路 WSAENETUNREACH。

### <a name="remarks"></a>備註

`SendTo`會用於資料包或資料流程通訊端上，並且用來寫入通訊端上的輸出資料。 對於資料包通訊端，必須小心不要超過基礎子網的 IP 封包大小上限，這是由 `iMaxUdpDg` [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)填入的[WSADATA](/windows/win32/api/winsock2/ns-winsock2-wsadata)結構中的元素所提供。 如果資料太長而無法透過基礎通訊協定以不變的方式傳遞，則會傳回錯誤 WSAEMSGSIZE，而且不會傳輸任何資料。

請注意，成功完成， `SendTo` 並不表示已成功傳遞資料。

`SendTo`僅用於 SOCK_DGRAM 通訊端，以將資料包傳送至*lpSockAddr*參數所識別的特定通訊端。

若要傳送廣播（僅限 SOCK_DGRAM），應使用特殊 IP 位址 INADDR_BROADCAST （定義于 Windows Socket 標頭檔 WINSOCK 中）來建立*lpSockAddr*參數中的位址。H）以及所需的埠號碼。 或者，如果*lpszHostAddress*參數為 Null，就會針對廣播設定通訊端。 通常會將廣播資料包 inadvisable 到超過片段可能發生的大小，這表示資料包（不包括標頭）的資料部分不應超過512個位元組。

若要處理 IPv6 位址，請使用[CAsyncSocket：： SendToEx](#sendtoex)。

## <a name="casyncsocketsendtoex"></a><a name="sendtoex"></a>CAsyncSocket：： SendToEx

呼叫此成員函式，將資料傳送至特定目的地（處理 IPv6 位址）。

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
包含要傳送之資料的緩衝區。

*nBufLen*<br/>
*LpBuf*中的資料長度（以位元組為單位）。

*nHostPort*<br/>
識別通訊端應用程式的埠。

*lpszHostAddress*<br/>
此物件所連接之通訊端的網路位址：電腦名稱稱，例如 "ftp.microsoft.com"，或點數位，例如 "128.56.22.8"。

*nFlags*<br/>
指定進行呼叫的方式。 此函式的語法是由通訊端選項和*nFlags*參數所決定。 後者的建立方式是將下列任何值與 c + +**或**運算子結合：

- MSG_DONTROUTE 指定資料不應受限於路由。 Windows 通訊端供應商可以選擇忽略此旗標。

- MSG_OOB 傳送頻外資料（僅限 SOCK_STREAM）。

### <a name="return-value"></a>傳回值

如果沒有發生錯誤， `SendToEx` 則會傳回已傳送的字元總數。 （請注意，這可能小於*nBufLen*所指出的數位）。否則，會傳回 SOCKET_ERROR 的值，並藉由呼叫[GetLastError](#getlasterror)來抓取特定的錯誤碼。 下列錯誤適用于此成員函式：

- WSANOTINITIALISED 成功的[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必須在使用此 API 之前進行。

- WSAENETDOWN Windows 通訊端執行偵測到網路子系統失敗。

- WSAEACCES 要求的位址是廣播位址，但未設定適當的旗標。

- WSAEINPROGRESS 封鎖的 Windows 通訊端作業正在進行中。

- WSAEFAULT *lpBuf*或*lpSockAddr*參數不是使用者位址空間的一部分，或*lpSockAddr*引數太小（小於[SOCKADDR](/windows/win32/winsock/sockaddr-2)結構的大小）。

- WSAEINVAL 主機名稱無效。

- WSAENETRESET 必須重設連接，因為 Windows 通訊端執行已卸載。

- WSAENOBUFS Windows 通訊端執行會報告緩衝區鎖死。

- WSAENOTCONN 通訊端未連線（僅限 SOCK_STREAM）。

- WSAENOTSOCK 描述元不是通訊端。

- 已指定 WSAEOPNOTSUPP MSG_OOB，但通訊端不是 SOCK_STREAM 類型。

- WSAESHUTDOWN 通訊端已關閉;在 `SendToEx` `ShutDown` 使用設定為1或2的*nHow*叫用之後，就不能在通訊端上呼叫。

- WSAEWOULDBLOCK 通訊端標示為非封鎖，而要求的作業會封鎖。

- WSAEMSGSIZE 通訊端的類型 SOCK_DGRAM，而且資料包大於 Windows 通訊端執行所支援的最大值。

- WSAECONNABORTED 虛擬電路因超時或其他失敗而中止。

- WSAECONNRESET 虛擬電路已由遠端端重設。

- WSAEADDRNOTAVAIL 指定的位址無法從本機電腦使用。

- 指定系列中的 WSAEAFNOSUPPORT 位址無法與此通訊端搭配使用。

- 需要 WSAEDESTADDRREQ 目的地位址。

- 目前無法從這部主機連線到網路 WSAENETUNREACH。

### <a name="remarks"></a>備註

這個方法與[CAsyncSocket：： SendTo](#sendto)相同，不同之處在于它會處理 IPv6 位址以及較舊的通訊協定。

`SendToEx`會用於資料包或資料流程通訊端上，並且用來寫入通訊端上的輸出資料。 對於資料包通訊端，必須小心不要超過基礎子網的 IP 封包大小上限，這是由 `iMaxUdpDg` [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)填入的[WSADATA](/windows/win32/api/winsock2/ns-winsock2-wsadata)結構中的元素所提供。 如果資料太長而無法透過基礎通訊協定以不變的方式傳遞，則會傳回錯誤 WSAEMSGSIZE，而且不會傳輸任何資料。

請注意，成功完成， `SendToEx` 並不表示已成功傳遞資料。

`SendToEx`僅用於 SOCK_DGRAM 通訊端，以將資料包傳送至*lpSockAddr*參數所識別的特定通訊端。

若要傳送廣播（僅限 SOCK_DGRAM），應使用特殊 IP 位址 INADDR_BROADCAST （定義于 Windows Socket 標頭檔 WINSOCK 中）來建立*lpSockAddr*參數中的位址。H）以及所需的埠號碼。 或者，如果*lpszHostAddress*參數為 Null，就會針對廣播設定通訊端。 通常會將廣播資料包 inadvisable 到超過片段可能發生的大小，這表示資料包（不包括標頭）的資料部分不應超過512個位元組。

## <a name="casyncsocketsetsockopt"></a><a name="setsockopt"></a>CAsyncSocket：： SetSockOpt

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
緩衝區的指標，其中提供所要求之選項的值。

*nOptionLen*<br/>
*LpOptionValue*緩衝區的大小（以位元組為單位）。

*nLevel*<br/>
定義選項的層級;唯一支援的層級為 SOL_SOCKET 和 IPPROTO_TCP。

### <a name="return-value"></a>傳回值

如果函式成功，則為非零;否則，您可以藉由呼叫[GetLastError](#getlasterror)來抓取特定的錯誤碼。 下列錯誤適用于此成員函式：

- WSANOTINITIALISED 成功的[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必須在使用此 API 之前進行。

- WSAENETDOWN Windows 通訊端執行偵測到網路子系統失敗。

- WSAEFAULT *lpOptionValue*不在進程位址空間的有效部分。

- WSAEINPROGRESS 封鎖的 Windows 通訊端作業正在進行中。

- WSAEINVAL *nLevel*無效，或*lpOptionValue*中的資訊無效。

- 設定 SO_KEEPALIVE 時，WSAENETRESET 連接逾時。

- WSAENOPROTOOPT 選項不明或不受支援。 特別的是，類型 SOCK_STREAM 的通訊端不支援 SO_BROADCAST，但 SO_DONTLINGER、SO_KEEPALIVE、SO_LINGER 和 SO_OOBINLINE 在類型 SOCK_DGRAM 的通訊端上不受支援。

- 設定 SO_KEEPALIVE 時，已重設 WSAENOTCONN 連接。

- WSAENOTSOCK 描述元不是通訊端。

### <a name="remarks"></a>備註

`SetSockOpt`以任何狀態設定與任何類型之通訊端相關聯的通訊端選項目前值。 雖然選項可以存在於多個通訊協定層級，但此規格只會定義存在於最上方「通訊端」層級的選項。 選項會影響通訊端作業，例如，在一般資料流程中是否接收到快速資料、是否可以在通訊端上傳送廣播訊息等等。

通訊端選項有兩種類型：啟用或停用功能或行為的布林值選項，以及需要整數值或結構的選項。 若要啟用布林值選項， *lpOptionValue*會指向非零整數。 若要停用選項*lpOptionValue*指向等於零的整數。 *nOptionLen* `sizeof(BOOL)` 對於布林值選項，nOptionLen 應該等於。 針對其他選項， *lpOptionValue*會指向包含選項所需值的整數或結構，而*nOptionLen*是整數或結構的長度。

SO_LINGER 控制當未傳送的資料在通訊端上排入佇列時所採取的動作，並呼叫函式 `Close` 來關閉通訊端。

根據預設，通訊端無法系結（請參閱[Bind](#bind)）至已在使用中的本機位址。 不過，在某些情況下，可能會希望以這種方式「重複使用」位址。 由於每個連線都是由本機和遠端位址的組合唯一識別，因此，只要遠端位址不同，就不會有兩個通訊端系結至相同的本機位址的問題。

為了通知 Windows 通訊端執行， `Bind` 不允許對通訊端呼叫，因為所需的位址已由另一個通訊端使用中，所以應用程式應該先設定通訊端的 SO_REUSEADDR 通訊端選項，然後再發出 `Bind` 呼叫。 請注意，只有在呼叫時才會解讀此選項 `Bind` ：因此，在不會系結到現有位址的通訊端上設定選項，並在 `Bind` 呼叫對此或任何其他通訊端沒有任何影響之後，設定或重設此選項是不必要的（但無害）。

應用程式可以藉由開啟 [SO_KEEPALIVE 通訊端] 選項，要求 Windows 通訊端執行允許在傳輸控制通訊協定（TCP）連線上使用「keep-alive」封包。 Windows 通訊端執行不需要支援使用 keep-alive：如果有的話，精確的語義就是執行特有的，但應符合 RFC 1122：「網際網路主機的需求—通訊層」的區段4.2.3.6。 如果因為「保持不中斷」而卸載連接，錯誤碼 WSAENETRESET 會傳回至通訊端上進行中的任何呼叫，而任何後續的呼叫都會失敗並產生 WSAENOTCONN。

TCP_NODELAY 選項會停用 Nagle 演算法。 Nagle 演算法是用來減少主機傳送的小型封包數，方法是緩衝未認可的傳送資料，直到可以傳送完整大小的封包為止。 不過，針對某些應用程式，此演算法可能會妨礙效能，而 TCP_NODELAY 可以用來將它關閉。 應用程式寫入器不應設定 TCP_NODELAY，除非這麼做的影響已充分瞭解和需要，因為設定 TCP_NODELAY 可能會對網路效能造成嚴重的負面影響。 TCP_NODELAY 是唯一支援的通訊端選項，其使用層級 IPPROTO_TCP;所有其他選項都會使用層級 SOL_SOCKET。

如果應用程式設定 SO_DEBUG 選項，則 Windows 通訊端的某些執行會提供輸出的偵錯工具資訊。

支援下列選項 `SetSockOpt` 。 型別會識別*lpOptionValue*所定址的資料類型。

|值|類型|意義|
|-----------|----------|-------------|
|SO_BROADCAST|BOOL|允許在通訊端上傳輸廣播訊息。|
|SO_DEBUG|BOOL|記錄偵錯資訊。|
|SO_DONTLINGER|BOOL|不要封鎖 `Close` 等候傳送未傳送的資料。 設定此選項相當於將 `l_onoff` 設定為零的 SO_LINGER。|
|SO_DONTROUTE|BOOL|不路由：直接傳送至介面。|
|SO_KEEPALIVE|BOOL|傳送 keep-alive。|
|SO_LINGER|`struct LINGER`|如果沒有 `Close` 未傳送的資料，則會逗留。|
|SO_OOBINLINE|BOOL|在一般資料流程中接收頻外資料。|
|SO_RCVBUF|**int**|指定接收的緩衝區大小。|
|SO_REUSEADDR|BOOL|允許通訊端系結至已在使用中的位址。 （請參閱[Bind](#bind)）。|
|SO_SNDBUF|**int**|指定傳送的緩衝區大小。|
|TCP_NODELAY|BOOL|停用用於傳送聯合的 Nagle 演算法。|

不支援的 Berkeley 軟體發佈（BSD）選項如下 `SetSockOpt` ：

|值|類型|意義|
|-----------|----------|-------------|
|SO_ACCEPTCONN|BOOL|通訊端正在接聽|
|SO_ERROR|**int**|取得錯誤狀態並清除。|
|SO_RCVLOWAT|**int**|接收下限標準。|
|SO_RCVTIMEO|**int**|接收逾時|
|SO_SNDLOWAT|**int**|傳送下限標準。|
|SO_SNDTIMEO|**int**|傳送超時。|
|SO_TYPE|**int**|通訊端的類型。|
|IP_OPTIONS||[IP 標頭] 中的 [設定選項] 欄位。|

## <a name="casyncsocketshutdown"></a><a name="shutdown"></a>CAsyncSocket：： ShutDown

呼叫這個成員函式可停用通訊端上的傳送、接收或兩者。

```
BOOL ShutDown(int nHow = sends);
```

### <a name="parameters"></a>參數

*nHow*<br/>
使用下列列舉值來描述哪些類型的作業將不再允許的旗標：

- **接收 = 0**

- **傳送 = 1**

- **兩者 = 2**

### <a name="return-value"></a>傳回值

如果函式成功，則為非零;否則，您可以藉由呼叫[GetLastError](#getlasterror)來抓取特定的錯誤碼。 下列錯誤適用于此成員函式：

- WSANOTINITIALISED 成功的[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必須在使用此 API 之前進行。

- WSAENETDOWN Windows 通訊端執行偵測到網路子系統失敗。

- WSAEINVAL *nHow*無效。

- WSAEINPROGRESS 封鎖的 Windows 通訊端作業正在進行中。

- WSAENOTCONN 通訊端未連線（僅限 SOCK_STREAM）。

- WSAENOTSOCK 描述元不是通訊端。

### <a name="remarks"></a>備註

`ShutDown`會在所有類型的通訊端上使用，以停用接收、傳輸或兩者。 如果*nHow*為0，則不允許在通訊端上進行後續的接收。 這不會影響較低的通訊協定層。

對於傳輸控制通訊協定（TCP），TCP 視窗不會變更，而且會接受傳入的資料（但不會被認可），直到視窗耗盡為止。 針對使用者資料包協定（UDP），會接受傳入的資料包並將其排入佇列。 在任何情況下，都會產生 ICMP 錯誤封包。 如果*nHow*為1，則不允許後續的傳送。 若為 TCP 通訊端，將會傳送一則 FIN。 將*nHow*設定為2會同時停用傳送和接收，如上所述。

請注意，不會 `ShutDown` 關閉通訊端，而附加至通訊端的資源將不會釋放，直到 `Close` 呼叫為止。 應用程式不應該依賴能夠在關閉後重複使用通訊端。 特別是，不需要 Windows 通訊端執行，就能支援 `Connect` 在這類通訊端上使用。

### <a name="example"></a>範例

  請參閱[CAsyncSocket：： OnReceive](#onreceive)的範例。

## <a name="casyncsocketsocket"></a><a name="socket"></a>CASyncSocket：： Socket

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

- `FD_READ`：想要接收已準備好讀取的通知。

- `FD_WRITE`：想要接收寫入準備就緒的通知。

- `FD_OOB`：想要接收頻外資料抵達的通知。

- `FD_ACCEPT`：想要接收連入連線的通知。

- `FD_CONNECT`：想要接收已完成連接的通知。

- `FD_CLOSE`：想要接收通訊端關閉的通知。

*nProtocolType*<br/>
要與指定位址系列特定的通訊端搭配使用的通訊協定。

*nAddressFormat*<br/>
位址系列規格。

### <a name="return-value"></a>傳回值

成功時傳回 `TRUE`，失敗時則傳回 `FALSE`。

### <a name="remarks"></a>備註

這個方法會配置通訊端控制碼。 它不會呼叫[CAsyncSocket：： bind](#bind)將通訊端系結至指定的位址，因此您需要 `Bind` 稍後呼叫以將通訊端系結至指定的位址。 您可以使用[CAsyncSocket：： SetSockOpt](#setsockopt)來設定通訊端選項，然後再進行系結。

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CSocket 類別](../../mfc/reference/csocket-class.md)<br/>
[CSocketFile 類別](../../mfc/reference/csocketfile-class.md)
