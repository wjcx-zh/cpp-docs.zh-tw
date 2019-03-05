---
title: CAsyncSocket 類別
ms.date: 11/04/2016
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
ms.openlocfilehash: ef486e653eaf78914ea25663e0c1ab744ab30cd4
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57260006"
---
# <a name="casyncsocket-class"></a>CAsyncSocket 類別

代表 Windows 通訊端 — 網路通訊的端點。

## <a name="syntax"></a>語法

```
class CAsyncSocket : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CAsyncSocket::CAsyncSocket](#casyncsocket)|建構 `CAsyncSocket` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAsyncSocket::Accept](#accept)|接受通訊端上的連線。|
|[CAsyncSocket::AsyncSelect](#asyncselect)|通訊端的要求事件通知。|
|[CAsyncSocket::Attach](#attach)|附加的通訊端控制代碼`CAsyncSocket`物件。|
|[CAsyncSocket::Bind](#bind)|本機位址關聯的通訊端。|
|[CAsyncSocket::Close](#close)|關閉通訊端。|
|[CAsyncSocket::Connect](#connect)|建立對等通訊端連線。|
|[CAsyncSocket::Create](#create)|建立通訊端。|
|[CAsyncSocket::Detach](#detach)|中斷連結的通訊端控制代碼，從`CAsyncSocket`物件。|
|[CAsyncSocket::FromHandle](#fromhandle)|將指標傳回至`CAsyncSocket`指定通訊端控制代碼的物件。|
|[CAsyncSocket::GetLastError](#getlasterror)|取得上次作業失敗，錯誤狀態。|
|[CAsyncSocket::GetPeerName](#getpeername)|取得對等通訊端通訊端連線的位址。|
|[CAsyncSocket::GetPeerNameEx](#getpeernameex)|取得對等通訊端的通訊端是連接 （控點 IPv6 位址） 的位址。|
|[CAsyncSocket::GetSockName](#getsockname)|取得通訊端的本機名稱。|
|[CAsyncSocket::GetSockNameEx](#getsocknameex)|取得通訊端 （控點 IPv6 位址） 的本機名稱。|
|[CAsyncSocket::GetSockOpt](#getsockopt)|擷取通訊端選項。|
|[CAsyncSocket::IOCtl](#ioctl)|控制通訊端的模式。|
|[CAsyncSocket::Listen](#listen)|建立通訊端以接聽連入連線要求。|
|[CAsyncSocket::Receive](#receive)|從通訊端接收資料。|
|[CAsyncSocket::ReceiveFrom](#receivefrom)|接收資料包，並將來源位址。|
|[CAsyncSocket::ReceiveFromEx](#receivefromex)|接收資料包，並將來源位址 （控點 IPv6 位址）。|
|[CAsyncSocket::Send](#send)|將資料傳送到已連線的通訊端。|
|[CAsyncSocket::SendTo](#sendto)|將資料傳送到特定的目的地。|
|[CAsyncSocket::SendToEx](#sendtoex)|將資料傳送到特定的目的地 （控點 IPv6 位址）。|
|[CAsyncSocket::SetSockOpt](#setsockopt)|設定通訊端選項。|
|[CAsyncSocket::ShutDown](#shutdown)|停用`Send`及/或`Receive`通訊端上呼叫。|
|[CASyncSocket::Socket](#socket)|配置的通訊端控制代碼。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CAsyncSocket::OnAccept](#onaccept)|通知接聽的通訊端，其可接受暫止連接要求，藉由呼叫`Accept`。|
|[CAsyncSocket::OnClose](#onclose)|通知已關閉通訊端連線到該通訊端。|
|[CAsyncSocket::OnConnect](#onconnect)|通知連接的通訊端連線嘗試已完成的是否成功或錯誤。|
|[CAsyncSocket::OnOutOfBandData](#onoutofbanddata)|通知接收的通訊端通訊端，通常是緊急的訊息要讀取的頻外資料。|
|[CAsyncSocket::OnReceive](#onreceive)|藉由呼叫要擷取的資料會通知接聽的通訊端`Receive`。|
|[CAsyncSocket::OnSend](#onsend)|告知通訊端，它可以將資料傳送呼叫`Send`。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CAsyncSocket::operator =](#operator_eq)|指派新值到`CAsyncSocket`物件。|
|[CAsyncSocket::operator SOCKET](#operator_socket)|若要擷取的通訊端控制代碼使用這個運算子`CAsyncSocket`物件。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CAsyncSocket::m_hSocket](#m_hsocket)|表示附加至這個通訊端控制代碼`CAsyncSocket`物件。|

## <a name="remarks"></a>備註

類別`CAsyncSocket`封裝 Windows 通訊端函式 API，提供程式設計人員想要與 MFC 一起使用 Windows 通訊端物件導向的抽象。

這個類別根據您已了解網路通訊的假設。 您負責處理封鎖，位元組順序的差異，並在 Unicode 及多位元組字元集轉換時設定 (MBCS) 字串。 如果您想更方便的介面，可讓您管理這些問題，請參閱類別[CSocket](../../mfc/reference/csocket-class.md)。

若要使用`CAsyncSocket`物件，請呼叫其建構函式，然後呼叫[建立](#create)函式來建立基礎通訊端控制代碼 (型別`SOCKET`)，除非可接受的通訊端。 伺服器通訊端呼叫[接聽](#listen)成員函式，並針對用戶端通訊端呼叫[Connect](#connect)成員函式。 伺服器通訊端應該呼叫[接受](#accept)收到連線要求的函式。 使用其餘`CAsyncSocket`函式，以實現通訊端之間的通訊。 完成時，終結`CAsyncSocket`物件，如果它建立在堆積上; 解構函式會自動呼叫[關閉](#close)函式。 通訊端的資料類型文件中所述[Windows Sockets:背景](../../mfc/windows-sockets-background.md)。

> [!NOTE]
>  當使用靜態連結的 MFC 應用程式中的次要執行緒中的 MFC 通訊端，您必須呼叫`AfxSocketInit`中每個執行緒都使用通訊端進行初始化通訊端程式庫。 根據預設，`AfxSocketInit`只在主執行緒中呼叫。

如需詳細資訊，請參閱[Windows Sockets:使用類別 CAsyncSocket](../../mfc/windows-sockets-using-class-casyncsocket.md)和相關文章。 所[Windows Sockets 2 API](/windows/desktop/WinSock/windows-sockets-start-page-2)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

`CAsyncSocket`

## <a name="requirements"></a>需求

**標頭：** afxsock.h

##  <a name="accept"></a>  CAsyncSocket::Accept

呼叫此成員函式可接受通訊端上的連線。

```
virtual BOOL Accept(
    CAsyncSocket& rConnectedSocket,
    SOCKADDR* lpSockAddr = NULL,
    int* lpSockAddrLen = NULL);
```

### <a name="parameters"></a>參數

*rConnectedSocket*<br/>
識別可供連線的新通訊端參考。

*lpSockAddr*<br/>
指標[SOCKADDR](/windows/desktop/winsock/sockaddr-2)結構，就會收到連線的位址通訊端，為已知在網路上。 確切格式*lpSockAddr*引數取決於建立通訊端時所建立的位址家族。 如果*lpSockAddr*及/或*lpSockAddrLen*相等為 NULL，則會不傳回遠端位址接受通訊端的任何資訊。

*lpSockAddrLen*<br/>
中的位址長度的指標*lpSockAddr*以位元組為單位。 *LpSockAddrLen*是值結果參數： 一開始應該包含所指向的空間數量*lpSockAddr*; 在傳回時它會包含傳回的位址的實際長度 （以位元組為單位）。

### <a name="return-value"></a>傳回值

如果成功，函式，非零值。否則藉由呼叫擷取 0，而特定的錯誤碼[GetLastError](#getlasterror)。 此成員函式適用於下列錯誤：

- 成功的 WSANOTINITIALISED A [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必須先使用此 API。

- WSAENETDOWN Windows Sockets 實作偵測到的網路子系統失敗。

- WSAEFAULT *lpSockAddrLen*引數是太小 (大小大於或等於[SOCKADDR](/windows/desktop/winsock/sockaddr-2)結構)。

- 封鎖 Windows 通訊端呼叫 WSAEINPROGRESS A 正在進行中。

- WSAEINVAL`Listen`未叫用的之前接受。

- WSAEMFILE 佇列是空的項目接受時並沒有任何描述項可用。

- 使用 WSAENOBUFS 無緩衝區空間。

- WSAENOTSOCK 描述項不是通訊端。

- WSAEOPNOTSUPP 參考之通訊端不支援連線導向的服務類型。

- WSAEWOULDBLOCK 通訊端會標示為未封鎖及所有連接都都會存在，才能被接受。

### <a name="remarks"></a>備註

這個常式會擷取第一個連線佇列中的暫止連線、 建立新通訊端具有與這個通訊端，相同的屬性及將它附加至*rConnectedSocket*。 如果沒有暫止的連線會出現在佇列中，`Accept`會傳回零和`GetLastError`會傳回錯誤。 接受的通訊端 ( *rConnectedSocket)* 不能用來接受更多連線。 原始通訊端會保持開啟，接聽。

引數*lpSockAddr*通訊層的已知是連接的通訊端，位址會填入結果參數。 `Accept` 連接為基礎的通訊端類型，例如 SOCK_STREAM 搭配使用。

##  <a name="asyncselect"></a>  CAsyncSocket::AsyncSelect

呼叫此成員函式，以要求對通訊端的事件通知。

```
BOOL AsyncSelect(long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```

### <a name="parameters"></a>參數

*lEvent*<br/>
位元遮罩，指定應用程式想要在其中的網路事件的組合。

- FD_READ 想要接收通知的完備性進行讀取。

- FD_WRITE 想要可供讀取的資料時收到通知。

- FD_OOB 想要收到的頻外資料抵達的通知。

- FD_ACCEPT 想要接收通知的連入連線。

- FD_CONNECT 想要接收通知的連接結果。

- FD_CLOSE 想要對等電腦已關閉通訊端時收到通知。

### <a name="return-value"></a>傳回值

如果成功，函式，非零值。否則藉由呼叫擷取 0，而特定的錯誤碼[GetLastError](#getlasterror)。 此成員函式適用於下列錯誤：

- 成功的 WSANOTINITIALISED A [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必須先使用此 API。

- WSAENETDOWN Windows Sockets 實作偵測到的網路子系統失敗。

- WSAEINVAL 指出其中一個指定的參數無效。

- WSAEINPROGRESS 的封鎖 Windows 通訊端作業正在進行中。

### <a name="remarks"></a>備註

此函式用來指定通訊端，將呼叫哪一個 MFC 回呼通知函式。 `AsyncSelect` 自動將此通訊端設定未封鎖模式。 如需詳細資訊，請參閱文章[Windows Sockets:通訊端通知](../../mfc/windows-sockets-socket-notifications.md)。

##  <a name="attach"></a>  CAsyncSocket::Attach

呼叫此成員函式，來附加*hSocket*控制代碼`CAsyncSocket`物件。

```
BOOL Attach(
    SOCKET hSocket, long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```

### <a name="parameters"></a>參數

*hSocket*<br/>
包含通訊端的控制代碼。

*lEvent*<br/>
位元遮罩，指定應用程式想要在其中的網路事件的組合。

- FD_READ 想要接收通知的完備性進行讀取。

- FD_WRITE 想要可供讀取的資料時收到通知。

- FD_OOB 想要收到的頻外資料抵達的通知。

- FD_ACCEPT 想要接收通知的連入連線。

- FD_CONNECT 想要接收通知的連接結果。

- FD_CLOSE 想要對等電腦已關閉通訊端時收到通知。

### <a name="return-value"></a>傳回值

如果函式成功，則為非零。

### <a name="remarks"></a>備註

通訊端控制代碼會儲存在物件的[m_hSocket](#m_hsocket)資料成員。

##  <a name="bind"></a>  CAsyncSocket::Bind

呼叫此成員函式，通訊端相關聯的本機位址。

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
識別通訊端應用程式連接埠。

*lpszSocketAddress*<br/>
網路位址時，小數點的數字，例如"128.56.22.8 」。 將 NULL 傳遞此參數表示的字串`CAsyncSocket`應該接聽所有網路介面上的用戶端活動的執行個體。

*lpSockAddr*<br/>
指標[SOCKADDR](/windows/desktop/winsock/sockaddr-2)結構，其中包含要指派給此通訊端位址。

*nSockAddrLen*<br/>
中的地址的長度*lpSockAddr*以位元組為單位。

### <a name="return-value"></a>傳回值

如果成功，函式，非零值。否則藉由呼叫擷取 0，而特定的錯誤碼[GetLastError](#getlasterror)。 此成員函式適用於下列錯誤：

- 成功的 WSANOTINITIALISED A [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必須先使用此 API。

- WSAENETDOWN Windows Sockets 實作偵測到的網路子系統失敗。

- WSAEADDRINUSE 指定的位址已在使用中。 (請參閱下方的 SO_REUSEADDR 通訊端選項[SetSockOpt](#setsockopt)。)

- WSAEFAULT *nSockAddrLen*引數是太小 (大小大於或等於[SOCKADDR](/windows/desktop/winsock/sockaddr-2)結構)。

- 封鎖 Windows 通訊端呼叫 WSAEINPROGRESS A 正在進行中。

- WSAEAFNOSUPPORT 指定的通訊協定家族不支援此連接埠。

- WSAEINVAL 通訊端已繫結至地址。

- WSAENOBUFS 不足夠緩衝處理，太多的連線。

- WSAENOTSOCK 描述項不是通訊端。

### <a name="remarks"></a>備註

這個常式會之前用在未連接的資料流或資料流通訊端，後續`Connect`或`Listen`呼叫。 它可接受連接要求之前，接聽的伺服器通訊端必須選取一個連接埠號碼並使它成為已知 Windows 通訊端呼叫`Bind`。 `Bind` 建立通訊端的本機關聯 （主機位址/連接埠號碼），將本機名稱指派至未命名的通訊端。

##  <a name="casyncsocket"></a>  CAsyncSocket::CAsyncSocket

建構空白的通訊端物件。

```
CAsyncSocket();
```

### <a name="remarks"></a>備註

之後建構物件時，您必須呼叫其`Create`成員函式來建立通訊端的資料結構，並繫結其位址。 (在伺服器端的 Windows Sockets 通訊時接聽的通訊端會建立將用於在通訊端`Accept`呼叫中，您不能呼叫`Create`該通訊端。)

##  <a name="close"></a>  CAsyncSocket::Close

關閉通訊端。

```
virtual void Close();
```

### <a name="remarks"></a>備註

此函式會釋放通訊端描述項，以便進一步參考將會失敗並出現錯誤 WSAENOTSOCK。 如果這是基礎通訊端的最後一個參考，已排入佇列的資料與相關聯的命名資訊都會被捨棄。 通訊端物件的解構函式呼叫`Close`您。

針對`CAsyncSocket`，但並不適合`CSocket`的語意`Close`受到 SO_LINGER 和 SO_DONTLINGER 通訊端選項。 如需詳細資訊，請參閱成員函式`GetSockOpt`。

##  <a name="connect"></a>  CAsyncSocket::Connect

呼叫此成員函式，以連接到未連線的資料流或資料包通訊端。

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
這個物件所連接的通訊端的網路位址： 電腦名稱，例如 「 ftp.microsoft.com"或小數點的數字，例如"128.56.22.8 」。

*nHostPort*<br/>
識別通訊端應用程式連接埠。

*lpSockAddr*<br/>
指標[SOCKADDR](/windows/desktop/winsock/sockaddr-2)結構，其中包含連接的通訊端位址。

*nSockAddrLen*<br/>
中的地址的長度*lpSockAddr*以位元組為單位。

### <a name="return-value"></a>傳回值

如果成功，函式，非零值。否則藉由呼叫擷取 0，而特定的錯誤碼[GetLastError](#getlasterror)。 如果這表示錯誤碼的 WSAEWOULDBLOCK，且應用程式所使用的可覆寫回撥，您的應用程式會收到`OnConnect`訊息連線作業完成時。 此成員函式適用於下列錯誤：

- 成功的 WSANOTINITIALISED A [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必須先使用此 API。

- WSAENETDOWN Windows Sockets 實作偵測到的網路子系統失敗。

- WSAEADDRINUSE 指定的位址已在使用中。

- 封鎖 Windows 通訊端呼叫 WSAEINPROGRESS A 正在進行中。

- 無法從本機電腦使用 WSAEADDRNOTAVAIL 指定的位址。

- 指定系列中的 WSAEAFNOSUPPORT 位址不能與此通訊端。

- WSAECONNREFUSED，所以拒絕連線嘗試。

- 需要 WSAEDESTADDRREQ 的目的地位址。

- WSAEFAULT *nSockAddrLen*引數不正確。

- WSAEINVAL 無效的主機位址。

- 已連接 WSAEISCONN 通訊端。

- WSAEMFILE 沒有更多檔案描述項可用。

- WSAENETUNREACH 網路無法從這部主機這一次。

- 使用 WSAENOBUFS 無緩衝區空間。 無法連線通訊端。

- WSAENOTSOCK 描述項不是通訊端。

- WSAETIMEDOUT 嘗試連接逾時不須建立連接。

- WSAEWOULDBLOCK 通訊端會標示為未封鎖，無法立即完成連線。

### <a name="remarks"></a>備註

如果通訊端是未繫結，唯一的值指派給本機關聯系統、 通訊端會標示為繫結。 請注意，如果名稱結構的 [位址] 欄位是全部為零，`Connect`會傳回零。 若要取得延伸錯誤資訊，請呼叫`GetLastError`成員函式。

資料流通訊端 （型別 SOCK_STREAM），外部主機起始的使用中連接。 通訊端呼叫成功完成時，通訊端是準備好要傳送/接收資料。

資料包通訊端 （型別 SOCK_DGRAM），預設目的地設定，這將用於後續`Send`和`Receive`呼叫。

##  <a name="create"></a>  CAsyncSocket::Create

呼叫`Create`之後建構通訊端物件建立 Windows 通訊端，並將它附加的成員函式。

```
BOOL Create(
    UINT nSocketPort = 0,
    int nSocketType = SOCK_STREAM,
    long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE,
    LPCTSTR lpszSocketAddress = NULL);
```

### <a name="parameters"></a>參數

*nSocketPort*<br/>
若要使用通訊端，或 0，如果您想要選取連接埠的 Windows 通訊端的知名通訊埠。

*nSocketType*<br/>
SOCK_STREAM 或 SOCK_DGRAM。

*lEvent*<br/>
位元遮罩，指定應用程式想要在其中的網路事件的組合。

- FD_READ 想要接收通知的完備性進行讀取。

- FD_WRITE 想要接收通知的整備程度進行寫入。

- FD_OOB 想要收到的頻外資料抵達的通知。

- FD_ACCEPT 想要接收通知的連入連線。

- FD_CONNECT 想要接收通知的已完成的連線。

- FD_CLOSE 想要接收的通訊端關閉相關的通知。

*lpszSockAddress*<br/>
包含連接的通訊端，小數點的數字，例如"128.56.22.8 」 的網路位址的字串指標。將 NULL 傳遞此參數表示的字串`CAsyncSocket`應該接聽所有網路介面上的用戶端活動的執行個體。

### <a name="return-value"></a>傳回值

如果成功，函式，非零值。否則藉由呼叫擷取 0，而特定的錯誤碼[GetLastError](#getlasterror)。 此成員函式適用於下列錯誤：

- 成功的 WSANOTINITIALISED A [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必須先使用此 API。

- WSAENETDOWN Windows Sockets 實作偵測到的網路子系統失敗。

- 不支援指定的位址系列 WSAEAFNOSUPPORT。

- WSAEINPROGRESS 的封鎖 Windows 通訊端作業正在進行中。

- WSAEMFILE 沒有更多檔案描述項可用。

- 使用 WSAENOBUFS 無緩衝區空間。 無法建立通訊端。

- 不支援 WSAEPROTONOSUPPORT 指定的連接埠。

- WSAEPROTOTYPE 指定的連接埠是此通訊端的錯誤類型。

- WSAESOCKTNOSUPPORT 指定通訊端類型不支援這個通訊協定家族。

### <a name="remarks"></a>備註

`Create` 呼叫[通訊端](#socket)而且如果成功，它會呼叫[繫結](#bind)繫結至指定的位址的通訊端。 支援下列通訊端類型：

- SOCK_STREAM 提供排序、 可靠、 全雙工、 連接為基礎的位元組資料流。 用於網際網路位址家族中的傳輸控制通訊協定 (TCP)。

- SOCK_DGRAM 支援資料包是固定的 （一般為小型） 最大長度的無連線、 不可靠的封包。 用於網際網路位址家族中的使用者資料包通訊協定 (UDP)。

    > [!NOTE]
    >  `Accept`成員函式會參考新的空白`CSocket`做為其參數的物件。 您必須先建構這個物件，然後再呼叫`Accept`。 請記住，如果這個通訊端物件超出範圍，連接會關閉。 請勿呼叫`Create`這個新的通訊端物件。

> [!IMPORTANT]
> `Create` 已**不**安全執行緒。  如果您呼叫它在多執行緒環境中，就可以叫用同時由不同的執行緒，請務必保護每個呼叫與 mutex 或其他同步處理鎖定。

如需有關資料流和資料包通訊端的詳細資訊，請參閱文章[Windows Sockets:背景](../../mfc/windows-sockets-background.md)和[Windows Sockets:連接埠和通訊端位址](../../mfc/windows-sockets-ports-and-socket-addresses.md)並[Windows Sockets 2 API](/windows/desktop/WinSock/windows-sockets-start-page-2)。

##  <a name="detach"></a>  CAsyncSocket::Detach

呼叫此成員函式，以中斷連結中的通訊端控制代碼*m_hSocket*中的資料成員`CAsyncSocket`物件，並設定*m_hSocket*為 NULL。

```
SOCKET Detach();
```

##  <a name="fromhandle"></a>  CAsyncSocket::FromHandle

將指標傳回至`CAsyncSocket`物件。

```
static CAsyncSocket* PASCAL FromHandle(SOCKET hSocket);
```

### <a name="parameters"></a>參數

*hSocket*<br/>
包含通訊端的控制代碼。

### <a name="return-value"></a>傳回值

指標`CAsyncSocket`物件，則為 NULL，如果沒有任何`CAsyncSocket`物件附加至*hSocket*。

### <a name="remarks"></a>備註

如果指定通訊端控制代碼時`CAsyncSocket`物件沒有附加至控制代碼，此成員函式會傳回 NULL。

##  <a name="getlasterror"></a>  CAsyncSocket::GetLastError

呼叫此成員函式，以取得失敗的最後一次作業的錯誤狀態。

```
static int PASCAL GetLastError();
```

### <a name="return-value"></a>傳回值

傳回值，表示這個執行緒所執行的最後一個 Windows Sockets API 常式的錯誤碼。

### <a name="remarks"></a>備註

當特定成員函式可讓您表示已發生錯誤，`GetLastError`應該呼叫來擷取適當的錯誤碼。 請參閱適用錯誤碼的清單中的個別成員函式描述。

如需有關錯誤碼的詳細資訊，請參閱[Windows Sockets 2 API](/windows/desktop/WinSock/windows-sockets-start-page-2)。

##  <a name="getpeername"></a>  CAsyncSocket::GetPeerName

呼叫此成員函式，若要取得此通訊端所連接的對等通訊端位址。

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
若要參考`CString`接收小數點的數字 IP 位址的物件。

*rPeerPort*<br/>
儲存的連接埠 UINT 參考。

*lpSockAddr*<br/>
指標[SOCKADDR](/windows/desktop/winsock/sockaddr-2)結構會接收對等通訊端的名稱。

*lpSockAddrLen*<br/>
中的位址長度的指標*lpSockAddr*以位元組為單位。 在傳回時， *lpSockAddrLen*引數中包含的實際大小*lpSockAddr*傳回以位元組為單位。

### <a name="return-value"></a>傳回值

如果成功，函式，非零值。否則藉由呼叫擷取 0，而特定的錯誤碼[GetLastError](#getlasterror)。 此成員函式適用於下列錯誤：

- 成功的 WSANOTINITIALISED A [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必須先使用此 API。

- WSAENETDOWN Windows Sockets 實作偵測到的網路子系統失敗。

- WSAEFAULT *lpSockAddrLen*引數不是夠大。

- 封鎖 Windows 通訊端呼叫 WSAEINPROGRESS A 正在進行中。

- 未連接 WSAENOTCONN 通訊端。

- WSAENOTSOCK 描述項不是通訊端。

### <a name="remarks"></a>備註

若要處理的 IPv6 位址，請使用[CAsyncSocket::GetPeerNameEx](#getpeernameex)。

##  <a name="getpeernameex"></a>  CAsyncSocket::GetPeerNameEx

呼叫此成員函式，若要取得此通訊端是連接 （控點 IPv6 位址） 的對等通訊端位址。

```
BOOL GetPeerNameEx(
    CString& rPeerAddress,
    UINT& rPeerPort);
```

### <a name="parameters"></a>參數

*rPeerAddress*<br/>
若要參考`CString`接收小數點的數字 IP 位址的物件。

*rPeerPort*<br/>
儲存的連接埠 UINT 參考。

### <a name="return-value"></a>傳回值

如果成功，函式，非零值。否則藉由呼叫擷取 0，而特定的錯誤碼[GetLastError](#getlasterror)。 此成員函式適用於下列錯誤：

- 成功的 WSANOTINITIALISED A [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必須先使用此 API。

- WSAENETDOWN Windows Sockets 實作偵測到的網路子系統失敗。

- WSAEFAULT *lpSockAddrLen*引數不是夠大。

- 封鎖 Windows 通訊端呼叫 WSAEINPROGRESS A 正在進行中。

- 未連接 WSAENOTCONN 通訊端。

- WSAENOTSOCK 描述項不是通訊端。

### <a name="remarks"></a>備註

此函式是相同[CAsyncSocket::GetPeerName](#getpeername)不同之處在於它會處理 IPv6 位址以及為較舊的通訊協定。

##  <a name="getsockname"></a>  CAsyncSocket::GetSockName

呼叫此成員函式，以取得通訊端的本機名稱。

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
若要參考`CString`接收小數點的數字 IP 位址的物件。

*rSocketPort*<br/>
儲存的連接埠 UINT 參考。

*lpSockAddr*<br/>
指標[SOCKADDR](/windows/desktop/winsock/sockaddr-2)接收通訊端位址的結構。

*lpSockAddrLen*<br/>
中的位址長度的指標*lpSockAddr*以位元組為單位。

### <a name="return-value"></a>傳回值

如果成功，函式，非零值。否則藉由呼叫擷取 0，而特定的錯誤碼[GetLastError](#getlasterror)。 此成員函式適用於下列錯誤：

- 成功的 WSANOTINITIALISED A [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必須先使用此 API。

- WSAENETDOWN Windows Sockets 實作偵測到的網路子系統失敗。

- WSAEFAULT *lpSockAddrLen*引數不是夠大。

- WSAEINPROGRESS 的封鎖 Windows 通訊端作業正在進行中。

- WSAENOTSOCK 描述項不是通訊端。

- 通訊端尚未已繫結與位址的 WSAEINVAL `Bind`。

### <a name="remarks"></a>備註

這個呼叫時特別有用`Connect`已進行呼叫，而不需要這麼做`Bind`第一次; 這個呼叫提供唯一的方法可以判斷已由系統設定本機關聯。

若要處理的 IPv6 位址，請使用[CAsyncSocket::GetSockNameEx](#getsocknameex)

##  <a name="getsocknameex"></a>  CAsyncSocket::GetSockNameEx

呼叫此成員函式，以取得通訊端 （控點 IPv6 位址） 的本機名稱。

```
BOOL GetSockNameEx(
    CString& rSocketAddress,
    UINT& rSocketPort);
```

### <a name="parameters"></a>參數

*rSocketAddress*<br/>
若要參考`CString`接收小數點的數字 IP 位址的物件。

*rSocketPort*<br/>
儲存的連接埠 UINT 參考。

### <a name="return-value"></a>傳回值

如果成功，函式，非零值。否則藉由呼叫擷取 0，而特定的錯誤碼[GetLastError](#getlasterror)。 此成員函式適用於下列錯誤：

- 成功的 WSANOTINITIALISED A [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必須先使用此 API。

- WSAENETDOWN Windows Sockets 實作偵測到的網路子系統失敗。

- WSAEFAULT *lpSockAddrLen*引數不是夠大。

- WSAEINPROGRESS 的封鎖 Windows 通訊端作業正在進行中。

- WSAENOTSOCK 描述項不是通訊端。

- 通訊端尚未已繫結與位址的 WSAEINVAL `Bind`。

### <a name="remarks"></a>備註

這個呼叫是相同[CAsyncSocket::GetSockName](#getsockname)不同之處在於它會處理 IPv6 位址以及為較舊的通訊協定。

這個呼叫時特別有用`Connect`已進行呼叫，而不需要這麼做`Bind`第一次; 這個呼叫提供唯一的方法可以判斷已由系統設定本機關聯。

##  <a name="getsockopt"></a>  CAsyncSocket::GetSockOpt

呼叫此成員函式可擷取通訊端選項。

```
BOOL GetSockOpt(
    int nOptionName,
    void* lpOptionValue,
    int* lpOptionLen,
    int nLevel = SOL_SOCKET);
```

### <a name="parameters"></a>參數

*nOptionName*<br/>
要擷取值的通訊端選項。

*lpOptionValue*<br/>
要求選項的值為傳回緩衝區的指標。 選取的選項相關聯的值會傳回緩衝區中*lpOptionValue*。 所指向的整數*lpOptionLen*原本應該包含以位元組為單位; 此緩衝區的大小，而且在傳回時，它將會設定為傳回值的大小。 針對 SO_LINGER，這會是大小`LINGER`結構，如需所有其他選項中，它會是 BOOL 的大小或**int**，取決於選項。 請參閱選項和其大小 < 備註 > 一節中的清單。

*lpOptionLen*<br/>
指標的大小*lpOptionValue*以位元組為單位的緩衝區。

*nLevel*<br/>
在其中定義的選項; 層級唯一支援的層級是 SOL_SOCKET 和 IPPROTO_TCP。

### <a name="return-value"></a>傳回值

如果成功，函式，非零值。否則藉由呼叫擷取 0，而特定的錯誤碼[GetLastError](#getlasterror)。 如果從未設定選項`SetSockOpt`，然後`GetSockOpt`傳回選項的預設值。 此成員函式適用於下列錯誤：

- 成功的 WSANOTINITIALISED A [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必須先使用此 API。

- WSAENETDOWN Windows Sockets 實作偵測到的網路子系統失敗。

- WSAEFAULT *lpOptionLen*引數無效。

- WSAEINPROGRESS 的封鎖 Windows 通訊端作業正在進行中。

- WSAENOPROTOOPT 選項是未知或不受支援。 特別是，SO_BROADCAST 不支援的型別時 SO_ACCEPTCONN、 SO_DONTLINGER、 SO_KEEPALIVE、 SO_LINGER 和 SO_OOBINLINE SOCK_STREAM，不支援的型別 SOCK_DGRAM 的通訊端的通訊端。

- WSAENOTSOCK 描述項不是通訊端。

### <a name="remarks"></a>備註

`GetSockOpt` 擷取目前的值，是任何類型，在任何狀態下，通訊端相關聯的通訊端選項，並將導致*lpOptionValue*。 選項會影響通訊端作業，例如路由封包、 頻外的資料傳輸，等等。

支援下列選項`GetSockOpt`。 型別會識別所定址的資料型別*lpOptionValue*。 TCP_NODELAY 選項會使用層級 IPPROTO_TCP;所有其他選項會使用層級 SOL_SOCKET。

|值|類型|意義|
|-----------|----------|-------------|
|SO_ACCEPTCONN|BOOL|正在接聽通訊端。|
|SO_BROADCAST|BOOL|通訊端廣播訊息的傳輸設定。|
|SO_DEBUG|BOOL|啟用偵錯。|
|SO_DONTLINGER|BOOL|如果為 true，SO_LINGER 選項已停用。|
|SO_DONTROUTE|BOOL|已停用路由。|
|SO_ERROR|**int**|擷取錯誤狀態，並清除。|
|SO_KEEPALIVE|BOOL|傳送 keep-alive。|
|SO_LINGER|`struct LINGER`|傳回目前的延遲選項。|
|SO_OOBINLINE|BOOL|一般資料流中接收頻外的資料。|
|SO_RCVBUF|int|接收緩衝區大小。|
|SO_REUSEADDR|BOOL|通訊端可以繫結已在使用中的位址。|
|SO_SNDBUF|**int**|傳送的緩衝區大小。|
|SO_TYPE|**int**|通訊端 (例如 SOCK_STREAM) 型別。|
|TCP_NODELAY|BOOL|停用用於傳送聯合的 Nagle 演算法。|

不支援的 Berkeley 軟體散佈 (BSD) 選項`GetSockOpt`是：

|值|類型|意義|
|-----------|----------|-------------|
|SO_RCVLOWAT|**int**|收到下限標準。|
|SO_RCVTIMEO|**int**|接收逾時。|
|SO_SNDLOWAT|**int**|傳送下限標準。|
|SO_SNDTIMEO|**int**|傳送等候逾時。|
|IP_OPTIONS||取得在 IP 標頭中的選項。|
|TCP_MAXSEG|**int**|取得 TCP 區段大小上限。|

呼叫`GetSockOpt`不支援的選項會導致 WSAENOPROTOOPT 從傳回的錯誤碼`GetLastError`。

##  <a name="ioctl"></a>  CAsyncSocket::IOCtl

呼叫此成員函式，來控制通訊端的模式。

```
BOOL IOCtl(
    long lCommand,
    DWORD* lpArgument);
```

### <a name="parameters"></a>參數

*lCommand*<br/>
要在通訊端上執行的命令。

*lpArgument*<br/>
參數的指標*lCommand*。

### <a name="return-value"></a>傳回值

如果成功，函式，非零值。否則藉由呼叫擷取 0，而特定的錯誤碼[GetLastError](#getlasterror)。 此成員函式適用於下列錯誤：

- 成功的 WSANOTINITIALISED A [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必須先使用此 API。

- WSAENETDOWN Windows Sockets 實作偵測到的網路子系統失敗。

- WSAEINVAL *lCommand*不是有效的命令，或*lpArgument*不是可接受參數*lCommand*，或此命令不是適用於通訊端提供的類型.

- WSAEINPROGRESS 的封鎖 Windows 通訊端作業正在進行中。

- WSAENOTSOCK 描述項不是通訊端。

### <a name="remarks"></a>備註

這個常式可用在任何狀態的任何通訊端上使用。 它用來取得，或擷取作業的通訊端，無關的通訊協定和通訊子系統相關聯的參數。 支援下列命令：

- FIONBIO 啟用或停用未封鎖模式通訊端上。 *LpArgument*參數所指向`DWORD`，其為非零值，如果未封鎖模式會啟用，而且零，如果要停用。 如果`AsyncSelect`發出通訊端，則任何嘗試使用`IOCtl`設定通訊端上的一步 封鎖模式將會失敗並 WSAEINVAL。 若要回到封鎖模式中設定通訊端，並避免 WSAEINVAL 錯誤，應用程式必須先停用`AsyncSelect`藉由呼叫`AsyncSelect`具有*lEvent*參數等於 0，然後呼叫`IOCtl`。

- FIONREAD 判斷可以使用其中一個讀取的位元組數目上限`Receive`從這個通訊端呼叫。 *LpArgument*參數所指向`DWORD`所在`IOCtl`儲存結果。 如果這個通訊端是型別 SOCK_STREAM，FIONREAD 會傳回單一的可讀取的資料總量`Receive`; 這通常與是相同的資料總量排入佇列的通訊端上。 如果這個通訊端，型別 SOCK_DGRAM FIONREAD 會傳回第一個資料流的大小已排入佇列的通訊端上。

- SIOCATMARK 判斷是否已讀取超出訊號範圍的所有資料。 只適用於型別已設定為在列中接收的任何頻外的資料 (SO_OOBINLINE) SOCK_STREAM 通訊端。 如果沒有超出訊號範圍的資料正在等候讀取，則作業會傳回非零值。 否則會傳回 0，而下一步`Receive`或`ReceiveFrom`對通訊端會擷取部分或全部的 「 標記 」 前的資料，應用程式應該使用 SIOCATMARK 作業來判斷是否會維持狀態的任何資料。 如果沒有任何上述 「 urgent 」 （超出頻外） 資料的一般資料，它會接收訂單。 (請注意，`Receive`或`ReceiveFrom`永遠不會混用相同的呼叫中的頻外和一般資料。)*LpArgument*參數所指向`DWORD`所在`IOCtl`儲存結果。

此函式是子集`ioctl()`Berkeley 通訊端中使用。 特別的是，沒有相當於 FIOASYNC，SIOCATMARK 時只通訊端層級命令，這個命令會受到任何命令。

##  <a name="listen"></a>  CAsyncSocket::Listen

呼叫此成員函式，來接聽連入連線要求。

```
BOOL Listen(int nConnectionBacklog = 5);
```

### <a name="parameters"></a>參數

*nConnectionBacklog*<br/>
暫止連線的佇列所能成長的長度上限。 有效範圍是從 1 到 5。

### <a name="return-value"></a>傳回值

如果成功，函式，非零值。否則藉由呼叫擷取 0，而特定的錯誤碼[GetLastError](#getlasterror)。 此成員函式適用於下列錯誤：

- 成功的 WSANOTINITIALISED A [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必須先使用此 API。

- WSAENETDOWN Windows Sockets 實作偵測到的網路子系統失敗。

- WSAEADDRINUSE 嘗試已對使用中位址上接聽。

- WSAEINPROGRESS 的封鎖 Windows 通訊端作業正在進行中。

- 通訊端尚未已繫結與 WSAEINVAL`Bind`或已連線。

- 已連接 WSAEISCONN 通訊端。

- WSAEMFILE 沒有更多檔案描述項可用。

- 使用 WSAENOBUFS 無緩衝區空間。

- WSAENOTSOCK 描述項不是通訊端。

- 支援的類型不是參考之通訊端的 WSAEOPNOTSUPP`Listen`作業。

### <a name="remarks"></a>備註

若要接受連線，通訊端第一次建立與`Create`，指定連入連線的待處理項目`Listen`，並接著會使用接受連接`Accept`。 `Listen` 僅適用於支援連接的通訊端也就是其中一個型別 SOCK_STREAM。 此通訊端會進入 「 被動 」 模式的連入連線認可，而暫止接受程序排入佇列。

這個函數通常由伺服器 （或任何想要接受連線的應用程式），無法一次有多個連接要求： 如果連線要求與抵達佇列已滿，用戶端會收到指出發生錯誤WSAECONNREFUSED。

`Listen` 嘗試繼續理性判斷運作時沒有任何可用的連接埠 （描述）。 在清空佇列之前，它會接受連線。 如果連接埠可用，稍後呼叫`Listen`或`Accept`會重新填滿到目前或最近 」 待辦項目，「 佇列可能的話，並繼續接聽連入連線。

##  <a name="m_hsocket"></a>  CAsyncSocket::m_hSocket

包含封裝這個通訊端的通訊端控制代碼`CAsyncSocket`物件。

```
SOCKET m_hSocket;
```

##  <a name="onaccept"></a>  CAsyncSocket::OnAccept

由架構呼叫以通知它可以接受暫止連接要求，藉由呼叫接聽通訊端[接受](#accept)成員函式。

```
virtual void OnAccept(int nErrorCode);
```

### <a name="parameters"></a>參數

*nErrorCode*<br/>
通訊端上最近的錯誤。 適用於下列錯誤碼`OnAccept`成員函式：

- **0**成功執行的函式。

- WSAENETDOWN Windows Sockets 實作偵測到的網路子系統失敗。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[Windows Sockets:通訊端通知](../../mfc/windows-sockets-socket-notifications.md)。

##  <a name="onclose"></a>  CAsyncSocket::OnClose

由架構呼叫以通知這個通訊端連線的通訊端已關閉其程序。

```
virtual void OnClose(int nErrorCode);
```

### <a name="parameters"></a>參數

*nErrorCode*<br/>
通訊端上最近的錯誤。 下列的錯誤代碼適用於`OnClose`成員函式：

- **0**成功執行的函式。

- WSAENETDOWN Windows Sockets 實作偵測到的網路子系統失敗。

- WSAECONNRESET 已經重設遠端連接。

- WSAECONNABORTED 連線已中止，因為逾時或其他失敗。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[Windows Sockets:通訊端通知](../../mfc/windows-sockets-socket-notifications.md)。

##  <a name="onconnect"></a>  CAsyncSocket::OnConnect

由架構呼叫以通知此連線的通訊端，其嘗試連接完成時，是否成功或錯誤。

```
virtual void OnConnect(int nErrorCode);
```

### <a name="parameters"></a>參數

*nErrorCode*<br/>
通訊端上最近的錯誤。 下列的錯誤代碼適用於`OnConnect`成員函式：

- **0**成功執行的函式。

- WSAEADDRINUSE 指定的位址已在使用中。

- 無法從本機電腦使用 WSAEADDRNOTAVAIL 指定的位址。

- 指定系列中的 WSAEAFNOSUPPORT 位址不能與此通訊端。

- WSAECONNREFUSED 已強制拒絕連接嘗試。

- 需要 WSAEDESTADDRREQ 的目的地位址。

- WSAEFAULT *lpSockAddrLen*引數不正確。

- WSAEINVAL 通訊端已繫結至地址。

- 已連接 WSAEISCONN 通訊端。

- WSAEMFILE 沒有更多檔案描述項可用。

- WSAENETUNREACH 網路無法從這部主機這一次。

- 使用 WSAENOBUFS 無緩衝區空間。 無法連線通訊端。

- 未連接 WSAENOTCONN 通訊端。

- WSAENOTSOCK 描述元是檔案，而不是通訊端。

- WSAETIMEDOUT 連線嘗試逾時不須建立連接。

### <a name="remarks"></a>備註

> [!NOTE]
>  在  [CSocket](../../mfc/reference/csocket-class.md)，則`OnConnect`絕不會呼叫通知函式。 對於連線，您只要呼叫`Connect`，這會傳回時 （成功或錯誤），就可以完成連線。 如何處理連接通知是 MFC 實作細節。

如需詳細資訊，請參閱[Windows Sockets:通訊端通知](../../mfc/windows-sockets-socket-notifications.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCAsyncSocket#1](../../mfc/reference/codesnippet/cpp/casyncsocket-class_1.cpp)]

##  <a name="onoutofbanddata"></a>  CAsyncSocket::OnOutOfBandData

由架構呼叫以通知接收通訊端傳送的通訊端具有頻外傳送的資料。

```
virtual void OnOutOfBandData(int nErrorCode);
```

### <a name="parameters"></a>參數

*nErrorCode*<br/>
通訊端上最近的錯誤。 下列的錯誤代碼適用於`OnOutOfBandData`成員函式：

- **0**成功執行的函式。

- WSAENETDOWN Windows Sockets 實作偵測到的網路子系統失敗。

### <a name="remarks"></a>備註

超出訊號範圍的資料是邏輯上獨立的通道與連接的通訊端類型 SOCK_STREAM 的每一對相關聯。 通道通常用來傳送緊急的資料。

MFC 支援頻外的資料，但類別的使用者`CAsyncSocket`不鼓勵使用它。 更簡單的方法是建立傳遞這類資料的第二個通訊端。 如需頻外資料的詳細資訊，請參閱[Windows Sockets:通訊端通知](../../mfc/windows-sockets-socket-notifications.md)。

##  <a name="onreceive"></a>  CAsyncSocket::OnReceive

由架構呼叫以通知這個通訊端可以藉由呼叫擷取緩衝區中沒有資料`Receive`成員函式。

```
virtual void OnReceive(int nErrorCode);
```

### <a name="parameters"></a>參數

*nErrorCode*<br/>
通訊端上最近的錯誤。 下列的錯誤代碼適用於`OnReceive`成員函式：

- **0**成功執行的函式。

- WSAENETDOWN Windows Sockets 實作偵測到的網路子系統失敗。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[Windows Sockets:通訊端通知](../../mfc/windows-sockets-socket-notifications.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCAsyncSocket#2](../../mfc/reference/codesnippet/cpp/casyncsocket-class_2.cpp)]

##  <a name="onsend"></a>  CAsyncSocket::OnSend

由架構呼叫以通知它現在可以傳送資料所呼叫的通訊端`Send`成員函式。

```
virtual void OnSend(int nErrorCode);
```

### <a name="parameters"></a>參數

*nErrorCode*<br/>
通訊端上最近的錯誤。 下列的錯誤代碼適用於`OnSend`成員函式：

- **0**成功執行的函式。

- WSAENETDOWN Windows Sockets 實作偵測到的網路子系統失敗。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[Windows Sockets:通訊端通知](../../mfc/windows-sockets-socket-notifications.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCAsyncSocket#3](../../mfc/reference/codesnippet/cpp/casyncsocket-class_3.cpp)]

##  <a name="operator_eq"></a>  CAsyncSocket::operator =

指派新值到`CAsyncSocket`物件。

```
void operator=(const CAsyncSocket& rSrc);
```

### <a name="parameters"></a>參數

*rSrc*<br/>
若要將現有的參考`CAsyncSocket`物件。

### <a name="remarks"></a>備註

呼叫此函式，可複製現有`CAsyncSocket`物件與另一個`CAsyncSocket`物件。

##  <a name="operator_socket"></a>  CAsyncSocket::operator SOCKET

若要擷取的通訊端控制代碼使用這個運算子`CAsyncSocket`物件。

```
operator SOCKET() const;
```

### <a name="return-value"></a>傳回值

如果成功，通訊端物件的控制代碼否則為 NULL。

### <a name="remarks"></a>備註

您可以使用控制代碼來直接呼叫 Windows Api。

##  <a name="receive"></a>  CAsyncSocket::Receive

呼叫此成員函式可從通訊端接收資料。

```
virtual int Receive(
    void* lpBuf,
    int nBufLen,
    int nFlags = 0);
```

### <a name="parameters"></a>參數

*lpBuf*<br/>
內送資料的的緩衝區。

*nBufLen*<br/>
長度*lpBuf*以位元組為單位。

*nFlags*<br/>
指定用來進行呼叫的方法。 此函式的語意取決於通訊端選項和*nFlags*參數。 後者的建構方式是使用 c + + 結合下列值之一**或**運算子：

- 在 內送資料，查看 MSG_PEEK。 將資料複製到緩衝區，但不是會從輸入佇列移除。

- MSG_OOB 程序外的頻外的資料。

### <a name="return-value"></a>傳回值

如果未發生錯誤，`Receive`傳回接收的位元組數目。 如果連接已經關閉，它會傳回 0。 否則，SOCKET_ERROR 值會傳回，而且可以藉由呼叫擷取特定的錯誤碼[GetLastError](#getlasterror)。 此成員函式適用於下列錯誤：

- 成功的 WSANOTINITIALISED A [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必須先使用此 API。

- WSAENETDOWN Windows Sockets 實作偵測到的網路子系統失敗。

- 未連接 WSAENOTCONN 通訊端。

- WSAEINPROGRESS 的封鎖 Windows 通訊端作業正在進行中。

- WSAENOTSOCK 描述項不是通訊端。

- WSAEOPNOTSUPP MSG_OOB 已指定，但是通訊端不是型別 SOCK_STREAM。

- WSAESHUTDOWN 通訊端已關閉，則不可以呼叫`Receive`通訊端後`ShutDown`已用來叫用*nHow*設為 0 或 2。

- WSAEWOULDBLOCK 通訊端會標示為未封鎖和`Receive`將封鎖作業。

- WSAEMSGSIZE 資料包太大而無法放入指定的緩衝區，而且已被截斷。

- 通訊端尚未已繫結與 WSAEINVAL `Bind`。

- WSAECONNABORTED 虛擬電路已中止，因為逾時或其他失敗。

- 此虛擬電路已重設遠端 WSAECONNRESET。

### <a name="remarks"></a>備註

此函式用於連接的資料流或資料包通訊端和用來讀取內送資料。

型別的 SOCK_STREAM 通訊端，則傳回一樣多的資訊目前無法提供緩衝區的大小。 如果已設定頻外 （通訊端選項 SO_OOBINLINE） 的資料列中接收通訊端，而且未讀取超出訊號範圍的資料，則會傳回只有外的頻外的資料。 應用程式可以使用`IOCtlSIOCATMARK`選項或[OnOutOfBandData](#onoutofbanddata)來判斷任何更頻資料是否仍要讀取。

資料包通訊端，資料被擷取自第一次的已加入佇列的資料包，但不超過提供的緩衝區的大小。 如果資料包大於提供的緩衝區，緩衝區會填入資料包的第一個部分，過多的資料都會遺失，和`Receive`SOCKET_ERROR 錯誤程式碼與值設定為 WSAEMSGSIZE 傳回。 如果沒有連入的資料可在通訊端，SOCKET_ERROR 值會傳回設定為 WSAEWOULDBLOCK 的錯誤碼。 [OnReceive](#onreceive)回呼函式可以用來判斷 更多資料送達時。

如果是型別 SOCK_STREAM 通訊端，而另一端具有連線正常關閉，`Receive`立即會完成，但收到 0 個位元組。 如果已重設連接，`Receive`將會失敗並出現錯誤 WSAECONNRESET。

`Receive` 應該針對每次只有一次呼叫[CAsyncSocket::OnReceive](#onreceive)呼叫。

### <a name="example"></a>範例

  範例，請參閱[CAsyncSocket::OnReceive](#onreceive)。

##  <a name="receivefrom"></a>  CAsyncSocket::ReceiveFrom

呼叫此成員函式，來接收資料包 (datagram) 與儲存中的來源位址[SOCKADDR](/windows/desktop/winsock/sockaddr-2)結構或在*rSocketAddress*。

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
內送資料的的緩衝區。

*nBufLen*<br/>
長度*lpBuf*以位元組為單位。

*rSocketAddress*<br/>
若要參考`CString`接收小數點的數字 IP 位址的物件。

*rSocketPort*<br/>
儲存的連接埠 UINT 參考。

*lpSockAddr*<br/>
指標[SOCKADDR](/windows/desktop/winsock/sockaddr-2)結構，其中保存傳回時的來源位址。

*lpSockAddrLen*<br/>
中的來源位址的長度指標*lpSockAddr*以位元組為單位。

*nFlags*<br/>
指定用來進行呼叫的方法。 此函式的語意取決於通訊端選項和*nFlags*參數。 後者的建構方式是使用 c + + 結合下列值之一**或**運算子：

- 在 內送資料，查看 MSG_PEEK。 將資料複製到緩衝區，但不是會從輸入佇列移除。

- MSG_OOB 程序外的頻外的資料。

### <a name="return-value"></a>傳回值

如果未發生錯誤，`ReceiveFrom`傳回接收的位元組數目。 如果連接已經關閉，它會傳回 0。 否則，SOCKET_ERROR 值會傳回，而且可以擷取特定的錯誤程式碼呼叫`GetLastError`。 此成員函式適用於下列錯誤：

- 成功的 WSANOTINITIALISED A [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必須先使用此 API。

- WSAENETDOWN Windows Sockets 實作偵測到的網路子系統失敗。

- WSAEFAULT *lpSockAddrLen*引數無效： *lpSockAddr*緩衝區太小，無法容納的對等地址。

- WSAEINPROGRESS 的封鎖 Windows 通訊端作業正在進行中。

- 通訊端尚未已繫結與 WSAEINVAL `Bind`。

- WSAENOTCONN 不是通訊端連線 (僅 SOCK_STREAM)。

- WSAENOTSOCK 描述項不是通訊端。

- WSAEOPNOTSUPP MSG_OOB 已指定，但是通訊端不是型別 SOCK_STREAM。

- WSAESHUTDOWN 通訊端已關閉，則不可以呼叫`ReceiveFrom`通訊端後`ShutDown`已用來叫用*nHow*設為 0 或 2。

- WSAEWOULDBLOCK 通訊端會標示為未封鎖和`ReceiveFrom`將封鎖作業。

- WSAEMSGSIZE 資料包太大而無法放入指定的緩衝區，而且已被截斷。

- WSAECONNABORTED 虛擬電路已中止，因為逾時或其他失敗。

- 此虛擬電路已重設遠端 WSAECONNRESET。

### <a name="remarks"></a>備註

此函式用來讀取傳入的資料 （可能是連接） 的通訊端，並擷取資料已寄出的位址。

若要處理的 IPv6 位址，請使用[CAsyncSocket::ReceiveFromEx](#receivefromex)。

型別的 SOCK_STREAM 通訊端，則傳回一樣多的資訊目前無法提供緩衝區的大小。 如果已設定頻外 （通訊端選項 SO_OOBINLINE） 的資料列中接收通訊端，而且未讀取超出訊號範圍的資料，則會傳回只有外的頻外的資料。 應用程式可以使用`IOCtlSIOCATMARK`選項或`OnOutOfBandData`來判斷任何更頻資料是否仍要讀取。 *LpSockAddr*並*lpSockAddrLen* SOCK_STREAM 通訊端，則會忽略參數。

資料包通訊端，資料被擷取自第一次的已加入佇列的資料包，但不超過提供的緩衝區的大小。 如果資料包大於提供的緩衝區，緩衝區會填入訊息的第一個部分，過多的資料都會遺失，和`ReceiveFrom`SOCKET_ERROR 錯誤程式碼與值設定為 WSAEMSGSIZE 傳回。

如果*lpSockAddr*為非零值，且通訊端型別的 SOCK_DGRAM，傳送資料的通訊端的網路位址會複製到對應[SOCKADDR](/windows/desktop/winsock/sockaddr-2)結構。 值所指向*lpSockAddrLen*會初始化為此結構的大小，以及修改在傳回時，表示儲存於該處的位址的實際大小。 如果在通訊端，可使用任何內送資料`ReceiveFrom`呼叫等候資料到達除非通訊端是未封鎖。 在此情況下，會傳回 SOCKET_ERROR 值設為 WSAEWOULDBLOCK 的錯誤碼。 `OnReceive`回呼可以用來判斷 更多資料送達時。

如果是型別 SOCK_STREAM 通訊端，而另一端具有連線正常關閉，`ReceiveFrom`立即會完成，但收到 0 個位元組。

##  <a name="receivefromex"></a>  CAsyncSocket::ReceiveFromEx

呼叫此成員函式，來接收資料包 (datagram) 與儲存中的來源位址[SOCKADDR](/windows/desktop/winsock/sockaddr-2)結構或在*rSocketAddress* （處理 IPv6 位址）。

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
內送資料的的緩衝區。

*nBufLen*<br/>
長度*lpBuf*以位元組為單位。

*rSocketAddress*<br/>
若要參考`CString`接收小數點的數字 IP 位址的物件。

*rSocketPort*<br/>
儲存的連接埠 UINT 參考。

*nFlags*<br/>
指定用來進行呼叫的方法。 此函式的語意取決於通訊端選項和*nFlags*參數。 後者的建構方式是使用 c + + 結合下列值之一**或**運算子：

- 在 內送資料，查看 MSG_PEEK。 將資料複製到緩衝區，但不是會從輸入佇列移除。

- MSG_OOB 程序外的頻外的資料。

### <a name="return-value"></a>傳回值

如果未發生錯誤，`ReceiveFromEx`傳回接收的位元組數目。 如果連接已經關閉，它會傳回 0。 否則，SOCKET_ERROR 值會傳回，而且可以擷取特定的錯誤程式碼呼叫`GetLastError`。 此成員函式適用於下列錯誤：

- 成功的 WSANOTINITIALISED A [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必須先使用此 API。

- WSAENETDOWN Windows Sockets 實作偵測到的網路子系統失敗。

- WSAEFAULT *lpSockAddrLen*引數無效： *lpSockAddr*緩衝區太小，無法容納的對等地址。

- WSAEINPROGRESS 的封鎖 Windows 通訊端作業正在進行中。

- 通訊端尚未已繫結與 WSAEINVAL `Bind`。

- WSAENOTCONN 不是通訊端連線 (僅 SOCK_STREAM)。

- WSAENOTSOCK 描述項不是通訊端。

- WSAEOPNOTSUPP MSG_OOB 已指定，但是通訊端不是型別 SOCK_STREAM。

- WSAESHUTDOWN 通訊端已關閉，則不可以呼叫`ReceiveFromEx`通訊端後`ShutDown`已用來叫用*nHow*設為 0 或 2。

- WSAEWOULDBLOCK 通訊端會標示為未封鎖和`ReceiveFromEx`將封鎖作業。

- WSAEMSGSIZE 資料包太大而無法放入指定的緩衝區，而且已被截斷。

- WSAECONNABORTED 虛擬電路已中止，因為逾時或其他失敗。

- 此虛擬電路已重設遠端 WSAECONNRESET。

### <a name="remarks"></a>備註

此函式用來讀取傳入的資料 （可能是連接） 的通訊端，並擷取資料已寄出的位址。

此函式是相同[CAsyncSocket::ReceiveFrom](#receivefrom)不同之處在於它會處理 IPv6 位址以及為較舊的通訊協定。

型別的 SOCK_STREAM 通訊端，則傳回一樣多的資訊目前無法提供緩衝區的大小。 如果已設定頻外 （通訊端選項 SO_OOBINLINE） 的資料列中接收通訊端，而且未讀取超出訊號範圍的資料，則會傳回只有外的頻外的資料。 應用程式可以使用`IOCtlSIOCATMARK`選項或`OnOutOfBandData`來判斷任何更頻資料是否仍要讀取。 *LpSockAddr*並*lpSockAddrLen* SOCK_STREAM 通訊端，則會忽略參數。

資料包通訊端，資料被擷取自第一次的已加入佇列的資料包，但不超過提供的緩衝區的大小。 如果資料包大於提供的緩衝區，緩衝區會填入訊息的第一個部分，過多的資料都會遺失，和`ReceiveFromEx`SOCKET_ERROR 錯誤程式碼與值設定為 WSAEMSGSIZE 傳回。

如果*lpSockAddr*為非零值，且通訊端型別的 SOCK_DGRAM，傳送資料的通訊端的網路位址會複製到對應[SOCKADDR](/windows/desktop/winsock/sockaddr-2)結構。 值所指向*lpSockAddrLen*會初始化為此結構的大小，以及修改在傳回時，表示儲存於該處的位址的實際大小。 如果在通訊端，可使用任何內送資料`ReceiveFromEx`呼叫等候資料到達除非通訊端是未封鎖。 在此情況下，會傳回 SOCKET_ERROR 值設為 WSAEWOULDBLOCK 的錯誤碼。 `OnReceive`回呼可以用來判斷 更多資料送達時。

如果是型別 SOCK_STREAM 通訊端，而另一端具有連線正常關閉，`ReceiveFromEx`立即會完成，但收到 0 個位元組。

##  <a name="send"></a>  CAsyncSocket::Send

呼叫此成員函式，若要連接的通訊端上傳送的資料。

```
virtual int Send(
    const void* lpBuf,
    int nBufLen,
    int nFlags = 0);
```

### <a name="parameters"></a>參數

*lpBuf*<br/>
緩衝區，包含要傳送的資料。

*nBufLen*<br/>
中的資料長度*lpBuf*以位元組為單位。

*nFlags*<br/>
指定用來進行呼叫的方法。 此函式的語意取決於通訊端選項和*nFlags*參數。 後者的建構方式是使用 c + + 結合下列值之一**或**運算子：

- MSG_DONTROUTE 指定的資料應該不會受限於路由。 Windows 通訊端的供應商可以選擇忽略這個旗標。

- MSG_OOB 傳送出頻外資料 (只有 SOCK_STREAM)。

### <a name="return-value"></a>傳回值

如果未發生錯誤，`Send`傳回傳送的字元總數。 (請注意，這可以是由數字小於*nBufLen*。)否則，SOCKET_ERROR 值會傳回，而且可以藉由呼叫擷取特定的錯誤碼[GetLastError](#getlasterror)。 此成員函式適用於下列錯誤：

- 成功的 WSANOTINITIALISED A [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必須先使用此 API。

- WSAENETDOWN Windows Sockets 實作偵測到的網路子系統失敗。

- WSAEACCES 要求的位址是廣播的位址，但未設定適當的旗標。

- WSAEINPROGRESS 的封鎖 Windows 通訊端作業正在進行中。

- WSAEFAULT *lpBuf*引數不是有效的組件的使用者位址空間。

- 必須重設 WSAENETRESET 連接，因為 Windows Sockets 實作卸除它。

- WSAENOBUFS Windows Sockets 實作報告緩衝區死結。

- 未連接 WSAENOTCONN 通訊端。

- WSAENOTSOCK 描述項不是通訊端。

- WSAEOPNOTSUPP MSG_OOB 已指定，但是通訊端不是型別 SOCK_STREAM。

- WSAESHUTDOWN 通訊端已關閉，則不可以呼叫`Send`通訊端後`ShutDown`已用來叫用*nHow*設為 1 或 2。

- WSAEWOULDBLOCK 通訊端會標示為未封鎖，會封鎖要求的作業。

- WSAEMSGSIZE 通訊端的型別 SOCK_DGRAM，且大於 Windows Sockets 實作所支援的最大資料包。

- 通訊端尚未已繫結與 WSAEINVAL `Bind`。

- WSAECONNABORTED 虛擬電路已中止，因為逾時或其他失敗。

- 此虛擬電路已重設遠端 WSAECONNRESET。

### <a name="remarks"></a>備註

`Send` 用來寫入連接的資料流或資料包通訊端上的傳出資料。 資料包通訊端，必須小心不能超過最大的 IP 封包大小基礎的子網路，這由指定`iMaxUdpDg`中的項目[WSADATA](/windows/desktop/api/winsock2/ns-winsock2-wsadata)所傳回的結構`AfxSocketInit`。 如果資料太長而無法以不可分割方式傳遞的基礎通訊協定時，傳回的錯誤 WSAEMSGSIZE 是透過`GetLastError`，並且在沒有資料傳輸。

請注意，資料包通訊端成功完成`Send`不會指出已成功傳遞資料。

在  `CAsyncSocket` SOCK_STREAM 型別的物件，介於 1 到所要求的長度，根據本機和外部主機上的緩衝區可用性而定，可以是寫入的位元組數目。

### <a name="example"></a>範例

  範例，請參閱[CAsyncSocket::OnSend](#onsend)。

##  <a name="sendto"></a>  CAsyncSocket::SendTo

呼叫此成員函式，將資料傳送到特定的目的地。

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
緩衝區，包含要傳送的資料。

*nBufLen*<br/>
中的資料長度*lpBuf*以位元組為單位。

*nHostPort*<br/>
識別通訊端應用程式連接埠。

*lpszHostAddress*<br/>
這個物件所連接的通訊端的網路位址： 電腦名稱，例如 「"ftp.microsoft.com 或小數點的數字，例如"128.56.22.8 」。

*nFlags*<br/>
指定用來進行呼叫的方法。 此函式的語意取決於通訊端選項和*nFlags*參數。 後者的建構方式是使用 c + + 結合下列值之一**或**運算子：

- MSG_DONTROUTE 指定的資料應該不會受限於路由。 Windows 通訊端的供應商可以選擇忽略這個旗標。

- MSG_OOB 傳送出頻外資料 (只有 SOCK_STREAM)。

*lpSockAddr*<br/>
指標[SOCKADDR](/windows/desktop/winsock/sockaddr-2)結構，其中包含目標通訊端位址。

*nSockAddrLen*<br/>
中的地址的長度*lpSockAddr*以位元組為單位。

### <a name="return-value"></a>傳回值

如果未發生錯誤，`SendTo`傳回傳送的字元總數。 (請注意，這可以是由數字小於*nBufLen*。)否則，SOCKET_ERROR 值會傳回，而且可以藉由呼叫擷取特定的錯誤碼[GetLastError](#getlasterror)。 此成員函式適用於下列錯誤：

- 成功的 WSANOTINITIALISED A [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必須先使用此 API。

- WSAENETDOWN Windows Sockets 實作偵測到的網路子系統失敗。

- WSAEACCES 要求的位址是廣播的位址，但未設定適當的旗標。

- WSAEINPROGRESS 的封鎖 Windows 通訊端作業正在進行中。

- WSAEFAULT *lpBuf*或是*lpSockAddr*參數不是使用者位址空間的一部分，或有*lpSockAddr*引數是太小 (大小大於或等於[SOCKADDR](/windows/desktop/winsock/sockaddr-2)結構)。

- WSAEINVAL 的主機名稱無效。

- 必須重設 WSAENETRESET 連接，因為 Windows Sockets 實作卸除它。

- WSAENOBUFS Windows Sockets 實作報告緩衝區死結。

- WSAENOTCONN 不是通訊端連線 (僅 SOCK_STREAM)。

- WSAENOTSOCK 描述項不是通訊端。

- WSAEOPNOTSUPP MSG_OOB 已指定，但是通訊端不是型別 SOCK_STREAM。

- WSAESHUTDOWN 通訊端已關閉，則不可以呼叫`SendTo`通訊端後`ShutDown`已用來叫用*nHow*設為 1 或 2。

- WSAEWOULDBLOCK 通訊端會標示為未封鎖，會封鎖要求的作業。

- WSAEMSGSIZE 通訊端的型別 SOCK_DGRAM，且大於 Windows Sockets 實作所支援的最大資料包。

- WSAECONNABORTED 虛擬電路已中止，因為逾時或其他失敗。

- 此虛擬電路已重設遠端 WSAECONNRESET。

- 無法從本機電腦使用 WSAEADDRNOTAVAIL 指定的位址。

- 指定系列中的 WSAEAFNOSUPPORT 位址不能與此通訊端。

- 需要 WSAEDESTADDRREQ 的目的地位址。

- WSAENETUNREACH 網路無法從這部主機這一次。

### <a name="remarks"></a>備註

`SendTo` 資料包或資料流通訊端上使用，用以撰寫通訊端上的傳出資料。 資料包通訊端，必須小心不能超過最大的 IP 封包大小基礎的子網路，這由指定`iMaxUdpDg`中的項目[WSADATA](/windows/desktop/api/winsock2/ns-winsock2-wsadata)結構填好的[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit). 如果資料太長而無法以不可分割方式傳遞的基礎通訊協定，WSAEMSGSIZE 會傳回錯誤，並會傳輸任何資料。

請注意，成功完成`SendTo`不會指出已成功傳遞資料。

`SendTo` 只用於 SOCK_DGRAM 通訊端上傳送資料包 (datagram) 所識別的特定通訊端*lpSockAddr*參數。

若要傳送廣播 （SOCK_DGRAM 只)，在位址*lpSockAddr*參數應該使用特殊 IP 位址 （定義於 Windows Sockets 標頭檔 WINSOCK INADDR_BROADCAST 建構。H） 搭配使用預期的連接埠號碼。 或者，如果*lpszHostAddress*參數為 NULL，通訊端設定為廣播。 它是通常不建議的廣播資料包 (datagram) 超過大小的片段可能會發生，這表示資料包 （不含標頭） 的資料部分，不應超過 512 個位元組。

若要處理的 IPv6 位址，請使用[CAsyncSocket::SendToEx](#sendtoex)。

##  <a name="sendtoex"></a>  CAsyncSocket::SendToEx

呼叫此成員函式，將資料傳送到特定的目的地 （控點 IPv6 位址）。

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
緩衝區，包含要傳送的資料。

*nBufLen*<br/>
中的資料長度*lpBuf*以位元組為單位。

*nHostPort*<br/>
識別通訊端應用程式連接埠。

*lpszHostAddress*<br/>
這個物件所連接的通訊端的網路位址： 電腦名稱，例如 「"ftp.microsoft.com 或小數點的數字，例如"128.56.22.8 」。

*nFlags*<br/>
指定用來進行呼叫的方法。 此函式的語意取決於通訊端選項和*nFlags*參數。 後者的建構方式是使用 c + + 結合下列值之一**或**運算子：

- MSG_DONTROUTE 指定的資料應該不會受限於路由。 Windows 通訊端的供應商可以選擇忽略這個旗標。

- MSG_OOB 傳送出頻外資料 (只有 SOCK_STREAM)。

### <a name="return-value"></a>傳回值

如果未發生錯誤，`SendToEx`傳回傳送的字元總數。 (請注意，這可以是由數字小於*nBufLen*。)否則，SOCKET_ERROR 值會傳回，而且可以藉由呼叫擷取特定的錯誤碼[GetLastError](#getlasterror)。 此成員函式適用於下列錯誤：

- 成功的 WSANOTINITIALISED A [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必須先使用此 API。

- WSAENETDOWN Windows Sockets 實作偵測到的網路子系統失敗。

- WSAEACCES 要求的位址是廣播的位址，但未設定適當的旗標。

- WSAEINPROGRESS 的封鎖 Windows 通訊端作業正在進行中。

- WSAEFAULT *lpBuf*或是*lpSockAddr*參數不是使用者位址空間的一部分，或有*lpSockAddr*引數是太小 (大小大於或等於[SOCKADDR](/windows/desktop/winsock/sockaddr-2)結構)。

- WSAEINVAL 的主機名稱無效。

- 必須重設 WSAENETRESET 連接，因為 Windows Sockets 實作卸除它。

- WSAENOBUFS Windows Sockets 實作報告緩衝區死結。

- WSAENOTCONN 不是通訊端連線 (僅 SOCK_STREAM)。

- WSAENOTSOCK 描述項不是通訊端。

- WSAEOPNOTSUPP MSG_OOB 已指定，但是通訊端不是型別 SOCK_STREAM。

- WSAESHUTDOWN 通訊端已關閉，則不可以呼叫`SendToEx`通訊端後`ShutDown`已用來叫用*nHow*設為 1 或 2。

- WSAEWOULDBLOCK 通訊端會標示為未封鎖，會封鎖要求的作業。

- WSAEMSGSIZE 通訊端的型別 SOCK_DGRAM，且大於 Windows Sockets 實作所支援的最大資料包。

- WSAECONNABORTED 虛擬電路已中止，因為逾時或其他失敗。

- 此虛擬電路已重設遠端 WSAECONNRESET。

- 無法從本機電腦使用 WSAEADDRNOTAVAIL 指定的位址。

- 指定系列中的 WSAEAFNOSUPPORT 位址不能與此通訊端。

- 需要 WSAEDESTADDRREQ 的目的地位址。

- WSAENETUNREACH 網路無法從這部主機這一次。

### <a name="remarks"></a>備註

這個方法是相同[CAsyncSocket::SendTo](#sendto)不同之處在於它會處理 IPv6 位址以及為較舊的通訊協定。

`SendToEx` 資料包或資料流通訊端上使用，用以撰寫通訊端上的傳出資料。 資料包通訊端，必須小心不能超過最大的 IP 封包大小基礎的子網路，這由指定`iMaxUdpDg`中的項目[WSADATA](/windows/desktop/api/winsock2/ns-winsock2-wsadata)結構填好的[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit). 如果資料太長而無法以不可分割方式傳遞的基礎通訊協定，WSAEMSGSIZE 會傳回錯誤，並會傳輸任何資料。

請注意，成功完成`SendToEx`不會指出已成功傳遞資料。

`SendToEx` 只用於 SOCK_DGRAM 通訊端上傳送資料包 (datagram) 所識別的特定通訊端*lpSockAddr*參數。

若要傳送廣播 （SOCK_DGRAM 只)，在位址*lpSockAddr*參數應該使用特殊 IP 位址 （定義於 Windows Sockets 標頭檔 WINSOCK INADDR_BROADCAST 建構。H） 搭配使用預期的連接埠號碼。 或者，如果*lpszHostAddress*參數為 NULL，通訊端設定為廣播。 它是通常不建議的廣播資料包 (datagram) 超過大小的片段可能會發生，這表示資料包 （不含標頭） 的資料部分，不應超過 512 個位元組。

##  <a name="setsockopt"></a>  CAsyncSocket::SetSockOpt

呼叫此成員函式，將通訊端選項。

```
BOOL SetSockOpt(
    int nOptionName,
    const void* lpOptionValue,
    int nOptionLen,
    int nLevel = SOL_SOCKET);
```

### <a name="parameters"></a>參數

*nOptionName*<br/>
這個值是設定通訊端選項。

*lpOptionValue*<br/>
要求選項的值在其中提供的緩衝區指標。

*nOptionLen*<br/>
大小*lpOptionValue*以位元組為單位的緩衝區。

*nLevel*<br/>
在其中定義的選項; 層級唯一支援的層級是 SOL_SOCKET 和 IPPROTO_TCP。

### <a name="return-value"></a>傳回值

如果成功，函式，非零值。否則藉由呼叫擷取 0，而特定的錯誤碼[GetLastError](#getlasterror)。 此成員函式適用於下列錯誤：

- 成功的 WSANOTINITIALISED A [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必須先使用此 API。

- WSAENETDOWN Windows Sockets 實作偵測到的網路子系統失敗。

- WSAEFAULT *lpOptionValue*不是處於有效的組件的處理序位址空間。

- WSAEINPROGRESS 的封鎖 Windows 通訊端作業正在進行中。

- WSAEINVAL *nLevel*無效，或中的資訊*lpOptionValue*無效。

- WSAENETRESET 連線已逾時設定 SO_KEEPALIVE 時。

- WSAENOPROTOOPT 選項是未知或不受支援。 特別是，SO_BROADCAST 不支援的型別 SOCK_STREAM，SO_DONTLINGER、 SO_KEEPALIVE、 SO_LINGER 和 SO_OOBINLINE 時不支援的型別 SOCK_DGRAM 的通訊端的通訊端。

- Je-li nastavena SO_KEEPALIVE 已重設 WSAENOTCONN 連接。

- WSAENOTSOCK 描述項不是通訊端。

### <a name="remarks"></a>備註

`SetSockOpt` 設定中的任何狀態的任何類型的通訊端相關聯的通訊端選項的目前值。 雖然有選項可以存在多個通訊協定層級，此規格只會定義出現在最上方的 「 通訊端 」 層級的選項。 選項會影響通訊端作業，例如是否加速的資料收到一般資料流中，是否可以在通訊端，傳送廣播的訊息等等。

有兩種類型的通訊端選項：布林值的選項，啟用或停用的功能或行為，並需要整數值或結構的選項。 若要啟用的布林值的選項*lpOptionValue*指向非零的整數。 若要停用此選項*lpOptionValue*指向等於零的整數。 *nOptionLen*應該是等於`sizeof(BOOL)`布林值的選項。 如需其他選項， *lpOptionValue*指向的整數或結構，其中包含所需的值選項，並*nOptionLen*是整數或結構的長度。

SO_LINGER 控制通訊端上的未傳送的資料會排入佇列時所採取的動作和`Close`函式呼叫以關閉通訊端。

根據預設，通訊端無法繫結 (請參閱[繫結](#bind)) 到本機的地址已在使用中。 在某些情況下，不過，它可能需要 「 重複使用 」 這種方式中的位址。 本機和遠端位址的組合來唯一識別每個連線，因為沒有沒問題，有兩個繫結至相同的本機位址，只要遠端位址是不同的通訊端。

若要通知 Windows 通訊端實作，`Bind`應該不允許在通訊端的呼叫，因為所需的位址已在使用另一個通訊端，應用程式應該設定的通訊端 SO_REUSEADDR 通訊端選項，然後再發出`Bind`呼叫。 注意選項只在時解譯`Bind`呼叫： 因此不需要 （但也無害） 設定也就是未繫結至現有的位址，通訊端選項和設定，或重設選項時`Bind`呼叫不會影響這個或任何其他的通訊端。

應用程式可以要求 Windows Sockets 實作啟用 「 keep-alive 」 上的封包傳輸控制通訊協定 (TCP) 連線使用，藉由開啟 SO_KEEPALIVE 通訊端選項。 Windows Sockets 實作不需要支援時刻的使用： 如果有的話的精確語意是實作專屬，但是應該符合 4.2.3.6 的 RFC 1122:「 網際網路主機需求 — 通訊層。 」 如果連接斷開做為結果的 「 keep-alive 」 傳回的錯誤碼 WSAENETRESET 是進行中的任何呼叫通訊端，和任何後續呼叫將會失敗並 WSAENOTCONN。

TCP_NODELAY 選項會停用的 Nagle 演算法。 Nagle 演算法用來減少小的緩衝處理未的傳送的資料，直到可以傳送觀看完整大小的封包由主機傳送的封包數目。 不過，對於某些應用程式這種演算法可以嚴重妨礙效能，而且 TCP_NODELAY 可用來將它關閉。 應用程式寫入器不應該設定 TCP_NODELAY，除非影響這麼做的因此是人們已充分理解和所需的因為設定 TCP_NODELAY 可以對網路效能有顯著的負面影響。 TCP_NODELAY 是唯一支援的通訊端選項，它會使用層級 IPPROTO_TCP;所有其他選項會使用層級 SOL_SOCKET。

如果 SO_DEBUG 選項由應用程式設定，某些 Windows 通訊端提供的實作會輸出偵錯資訊。

支援下列選項`SetSockOpt`。 型別會識別所定址的資料型別*lpOptionValue*。

|值|類型|意義|
|-----------|----------|-------------|
|SO_BROADCAST|BOOL|允許的通訊端上的廣播訊息的傳輸。|
|SO_DEBUG|BOOL|記錄偵錯資訊。|
|SO_DONTLINGER|BOOL|不會封鎖`Close`等候要傳送之未傳送資料。 設定此選項相當於設定與 SO_LINGER`l_onoff`設為零。|
|SO_DONTROUTE|BOOL|沒有路由： 直接傳送介面。|
|SO_KEEPALIVE|BOOL|傳送 keep-alive。|
|SO_LINGER|`struct LINGER`|延遲`Close`如果未傳送的資料會出現。|
|SO_OOBINLINE|BOOL|一般資料流中收到的 out-of-band data。|
|SO_RCVBUF|**int**|指定接收緩衝區大小。|
|SO_REUSEADDR|BOOL|允許繫結至已在使用中位址的通訊端。 (請參閱[繫結](#bind)。)|
|SO_SNDBUF|**int**|指定傳送的緩衝區大小。|
|TCP_NODELAY|BOOL|停用用於傳送聯合的 Nagle 演算法。|

不支援的 Berkeley 軟體散佈 (BSD) 選項`SetSockOpt`是：

|值|類型|意義|
|-----------|----------|-------------|
|SO_ACCEPTCONN|BOOL|通訊端接聽|
|SO_ERROR|**int**|取得錯誤狀態，並清除。|
|SO_RCVLOWAT|**int**|收到下限標準。|
|SO_RCVTIMEO|**int**|接收逾時|
|SO_SNDLOWAT|**int**|傳送下限標準。|
|SO_SNDTIMEO|**int**|傳送等候逾時。|
|SO_TYPE|**int**|通訊端類型。|
|IP_OPTIONS||設定 IP 標頭中的選項欄位。|

##  <a name="shutdown"></a>  CAsyncSocket::ShutDown

呼叫此成員函式，若要停用傳送時，都會收到，或兩者在通訊端上。

```
BOOL ShutDown(int nHow = sends);
```

### <a name="parameters"></a>參數

*nHow*<br/>
旗標，告訴您哪些類型的作業將不再允許，請使用下列的列舉的值：

- **receives = 0**

- **sends = 1**

- **both = 2**

### <a name="return-value"></a>傳回值

如果成功，函式，非零值。否則藉由呼叫擷取 0，而特定的錯誤碼[GetLastError](#getlasterror)。 此成員函式適用於下列錯誤：

- 成功的 WSANOTINITIALISED A [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必須先使用此 API。

- WSAENETDOWN Windows Sockets 實作偵測到的網路子系統失敗。

- WSAEINVAL *nHow*無效。

- WSAEINPROGRESS 的封鎖 Windows 通訊端作業正在進行中。

- WSAENOTCONN 不是通訊端連線 (僅 SOCK_STREAM)。

- WSAENOTSOCK 描述項不是通訊端。

### <a name="remarks"></a>備註

`ShutDown` 用於所有類型的通訊端上停用接收、 傳輸，或兩者。 如果*nHow*是 0，則後續接收上不允許在通訊端。 這會有較低的通訊協定層級上沒有作用。

傳輸控制通訊協定 (TCP)、 TCP 視窗不會變更，並傳入資料將會接受 （但不是認可），直到用完的視窗。 針對 「 使用者資料包通訊協定 」 (UDP) 中，連入的資料包所接受並排入佇列。 在任何情況下將 ICMP 錯誤封包會產生。 如果*nHow*為 1，後續的傳送，不允許。 針對 TCP 通訊端，將會傳送 FIN。 設定*nHow*為 2 會停用這兩個傳送和接收上面所述。

請注意，`ShutDown`不會關閉通訊端，並附加到通訊端的資源將不之前不會釋放`Close`呼叫。 應用程式不應依賴能夠重複使用通訊端之後它已關閉。 特別是，Windows Sockets 實作不需要支援使用`Connect`這類通訊端上。

### <a name="example"></a>範例

  範例，請參閱[CAsyncSocket::OnReceive](#onreceive)。

##  <a name="socket"></a>  CASyncSocket::Socket

配置的通訊端控制代碼。

```
BOOL Socket(
    int nSocketType = SOCK_STREAM,
    long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE,
    int nProtocolType = 0,
    int nAddressFormat = PF_INET);
```

### <a name="parameters"></a>參數

*nSocketType*<br/>
指定`SOCK_STREAM`或`SOCK_DGRAM`。

*lEvent*<br/>
位元遮罩，指定應用程式想要在其中的網路事件的組合。

- `FD_READ`：要接收通知的完備性進行讀取。

- `FD_WRITE`：要接收通知的整備程度進行寫入。

- `FD_OOB`：要接收的頻外資料抵達的通知。

- `FD_ACCEPT`：要接收通知的連入連線。

- `FD_CONNECT`：要接收通知的已完成的連線。

- `FD_CLOSE`：要接收的通訊端關閉相關的通知。

*nProtocolType*<br/>
若要搭配指定的位址家族特定的通訊端的通訊協定。

*nAddressFormat*<br/>
位址家族的規格。

### <a name="return-value"></a>傳回值

成功時傳回 `TRUE`，失敗時則傳回 `FALSE`。

### <a name="remarks"></a>備註

這個方法會配置的通訊端控制代碼。 它不會呼叫[CAsyncSocket::Bind](#bind)到通訊端繫結至指定的位址，因此您必須呼叫`Bind`更新版本，才能將通訊端繫結至指定的地址。 您可以使用[CAsyncSocket::SetSockOpt](#setsockopt)設定通訊端選項，然後它會繫結。

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CSocket 類別](../../mfc/reference/csocket-class.md)<br/>
[CSocketFile 類別](../../mfc/reference/csocketfile-class.md)
