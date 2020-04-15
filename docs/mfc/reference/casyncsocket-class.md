---
title: CAsyncSocket 類別
ms.date: 09/03/2019
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
ms.openlocfilehash: 7ab02dba4bf10b04dddac4e2e954623223af42d9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81353030"
---
# <a name="casyncsocket-class"></a>CAsyncSocket 類別

表示 Windows 套接字 - 網路通信的終結點。

## <a name="syntax"></a>語法

```
class CAsyncSocket : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[同步通訊::CAsyncSocket](#casyncsocket)|建構 `CAsyncSocket` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAsyncSocket:接受](#accept)|接受套接字上的連接。|
|[同步通訊::非同步選擇](#asyncselect)|請求套接字的事件通知。|
|[同步通訊::附加](#attach)|將套接字句柄附加到`CAsyncSocket`物件。|
|[CAsyncSocket::綁定](#bind)|將本地位址與套接字關聯。|
|[CAsyncSocket:關閉](#close)|關閉插座。|
|[CAsyncSocket:連接](#connect)|建立到對等套接字的連接。|
|[CAsyncSocket::Create](#create)|創建套接字。|
|[CAsyncSocket::D](#detach)|從`CAsyncSocket`物件分離套接字句柄。|
|[CAsyncSocket:從手柄](#fromhandle)|返回指向`CAsyncSocket`物件的指標,給定套接字句柄。|
|[CAsyncSocket::取得上次錯誤](#getlasterror)|獲取上次失敗操作的錯誤狀態。|
|[CAsyncSocket:取得對等名稱](#getpeername)|獲取套接字連接到的對等套接字的位址。|
|[CAsyncSocket:取得對等名稱Ex](#getpeernameex)|獲取套接字連接到的對等套接字的位址(處理IPv6位址)。|
|[CAsyncSocket:取得索克名稱](#getsockname)|獲取套接字的本地名稱。|
|[CAsyncSocket::獲取索諾克名稱Ex](#getsocknameex)|獲取套接字的本地名稱(處理 IPv6 位址)。|
|[CAsyncSocket:getSockOpt](#getsockopt)|檢索套接字選項。|
|[CAsyncSocket::IOCtl](#ioctl)|控制套接字的模式。|
|[CAsyncSocket:聽](#listen)|建立一個套接字以偵聽傳入連接請求。|
|[CAsyncSocket:接收](#receive)|從套接字接收數據。|
|[CAsyncSocket:接收來自](#receivefrom)|接收數據報並存儲源位址。|
|[CAsyncSocket::接收來自Ex](#receivefromex)|接收數據報並存儲源位址(處理IPv6位址)。|
|[CAsyncSocket:傳送](#send)|將資料傳送到已連線的通訊端。|
|[同步通訊::傳送至](#sendto)|將數據發送到特定目標。|
|[同步通訊::寄件](#sendtoex)|將資料發送到特定目標(處理 IPv6 位址)。|
|[CAsyncSocket:setSockOpt](#setsockopt)|設置套接字選項。|
|[同步通訊::關閉](#shutdown)|禁用`Send`套接字`Receive`上的 和/或呼叫。|
|[卡同步插槽::套接字](#socket)|分配套接字句柄。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CAsyncSocket::接受](#onaccept)|通知偵聽套接字,它可以通過調`Accept`用 來接受掛起的連接請求。|
|[同步通訊::關閉](#onclose)|通知連接到它的套接字已關閉。|
|[CAsyncSocket:開啟連線](#onconnect)|通知連接套接字的連接嘗試已完成,無論是成功還是錯誤。|
|[CAsyncsocket::在帶外數據上](#onoutofbanddata)|通知接收套接字在套接字上讀取帶外數據,通常是緊急消息。|
|[CAsyncSocket:開啟接收](#onreceive)|通知偵聽套接字,通過調用`Receive`來檢索數據。|
|[CAsyncSocket:開啟傳送](#onsend)|通知套接字,它可以通過調`Send`用 發送數據。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CAsyncSocket::運算符 |](#operator_eq)|為`CAsyncSocket`物件分配新值。|
|[CAsyncSocket::操作員](#operator_socket)|使用此運算符檢索`CAsyncSocket`物件的 SOCKET 句柄。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CAsyncSocket:m_hSocket](#m_hsocket)|指示附加到此`CAsyncSocket`物件的 SOCKET 句柄。|

## <a name="remarks"></a>備註

類`CAsyncSocket`封裝 Windows 套接字函數 API,為希望與 MFC 結合使用 Windows 套接字的程式師提供面向物件的抽象。

此類基於您瞭解網路通信的假設。 您負責處理 Unicode 和多位元組字元集 (MBCS) 字串之間的阻塞、位元組順序差異和轉換。 如果想要一個更方便的介面來為您管理這些問題,請參閱[類 CSocket](../../mfc/reference/csocket-class.md)。

要使用`CAsyncSocket`物件,請調用其建構函數,然後調用[Create](#create)函數以創建基礎套接字`SOCKET`句柄( 類型),但接受的套接字除外。 對於伺服器套接字,調用[偵聽](#listen)成員函數,對於用戶端套接字,調用[Connect](#connect)成員函數。 伺服器套接字應在收到連接請求時調用[Accept](#accept)函數。 使用其餘`CAsyncSocket`功能在套接字之間執行通信。 完成後,`CAsyncSocket`如果物件是在堆上創建的,則銷毀該物件;析構函數自動調用[Close](#close)函數。 在[Windows 套接字:背景](../../mfc/windows-sockets-background.md)) 一文中介紹了 SOCKET 數據類型。

> [!NOTE]
> 在靜態連結的 MFC 應用程式中的輔助線程中使用 MFC`AfxSocketInit`套接字時,必須呼叫使用 socket 初始化套接字型檔的每個線程。 預設情況下,`AfxSocketInit`僅在主線程中呼叫。

有關詳細資訊,請參閱[Windows 套接字:使用類 CAsyncSocket](../../mfc/windows-sockets-using-class-casyncsocket.md)和相關文章,以及[Windows 套接字 2 API](/windows/win32/WinSock/windows-sockets-start-page-2)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

`CAsyncSocket`

## <a name="requirements"></a>需求

**標題:** afxsock.h

## <a name="casyncsocketaccept"></a><a name="accept"></a>CAsyncSocket:接受

調用此成員函數以接受套接字上的連接。

```
virtual BOOL Accept(
    CAsyncSocket& rConnectedSocket,
    SOCKADDR* lpSockAddr = NULL,
    int* lpSockAddrLen = NULL);
```

### <a name="parameters"></a>參數

*rConnectedSocket*<br/>
標識可用於連接的新套接字的引用。

*lpSockAddr*<br/>
指向[SOCKADDR](/windows/win32/winsock/sockaddr-2)結構的指標,該結構接收連接套接字的位址,在網路上已知。 *lpSockAddr*參數的確切格式由創建套接字時建立的位址族確定。 如果*lpSockAddr*和/ 或*lpSockAddrLen*等於 NULL,則不會返回有關接受套接字的遠端位址的資訊。

*lpSockAddrLen*<br/>
以*lpSockAddr(* 以位元組為單位)指向位址長度的指標。 *lpSockAddrLen*是一個值結果參數:它最初應包含*lpSockAddr*指向的空間量;返回時,它將包含返回的地址的實際長度(以位元組為單位)。

### <a name="return-value"></a>傳回值

如果函數成功,則非零;否則 0,可以通過調用[GetLastError](#getlasterror)來檢索特定的錯誤代碼。 以下錯誤適用於此成員函數:

- 在使用此 API 之前,必須成功進行[Afxsocketinit。](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Windows 套接字實現檢測到網路子系統失敗。

- wsAEFAULT *lpSockAddrLen*參數太小(小於[SOCKADDR](/windows/win32/winsock/sockaddr-2)結構的大小)。

- WSAEINPROGRESS 阻止 Windows 套接字調用正在進行中。

- 在接受之前未調用`Listen`WSAEINVAL。

- WSAEMFILE 佇列在輸入時為空,但不存在可用的描述符。

- WSAENOBUFS 沒有可用的緩衝區空間。

- WSANotSOCK 描述符不是套接字。

- WSAEOPNOTSUPP 引用的套接字不是支援面向連接的服務的類型。

- WSAETOBLOCK 套接字標記為非阻塞,並且不存在要接受的連接。

### <a name="remarks"></a>備註

此例程式擷取掛起連接佇列的第一個連線,建立具有相同套接字屬性的新套接字,並將其附加到*rConnectedSocket*。 如果佇列中不存在掛起的連接,`Accept`則傳回`GetLastError`零並傳回錯誤。 接受的套接字 ( *rConnected Socket)* 不能用於接受更多連接。 原始插座保持打開和偵聽。

參數*lpSockAddr*是一個結果參數,該參數填充了連接套接字的位址,如通信層所知。 `Accept`用於基於連接的套接字類型,如SOCK_STREAM。

## <a name="casyncsocketasyncselect"></a><a name="asyncselect"></a>同步通訊::非同步選擇

調用此成員函數以請求套接字的事件通知。

```
BOOL AsyncSelect(long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```

### <a name="parameters"></a>參數

*lEvent*<br/>
指定應用程式感興趣的網路事件的組合的位掩碼。

- FD_READ希望收到準備閱讀的通知。

- FD_WRITE希望在數據可供讀取時收到通知。

- FD_OOB希望收到帶外數據到達的通知。

- FD_ACCEPT希望接收傳入連接的通知。

- FD_CONNECT希望收到連接結果的通知。

- FD_CLOSE希望當同字套字已由對等體關閉時接收通知。

### <a name="return-value"></a>傳回值

如果函數成功,則非零;否則 0,可以通過調用[GetLastError](#getlasterror)來檢索特定的錯誤代碼。 以下錯誤適用於此成員函數:

- 在使用此 API 之前,必須成功進行[Afxsocketinit。](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Windows 套接字實現檢測到網路子系統失敗。

- WSAEINVAL 指示其中一個指定的參數無效。

- WSAEINPROGRESS 阻止 Windows 套接字操作正在進行中。

### <a name="remarks"></a>備註

此功能用於指定要為套接字調用哪些 MFC 回調通知函數。 `AsyncSelect`自動將此套接字設置為非阻塞模式。 有關詳細資訊,請參閱文章 Windows[套接字:socket 通知](../../mfc/windows-sockets-socket-notifications.md)。

## <a name="casyncsocketattach"></a><a name="attach"></a>同步通訊::附加

調用此成員函數將*hSocket*句柄`CAsyncSocket`附加到 物件。

```
BOOL Attach(
    SOCKET hSocket, long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```

### <a name="parameters"></a>參數

*hSocket*<br/>
包含套接字的句柄。

*lEvent*<br/>
指定應用程式感興趣的網路事件的組合的位掩碼。

- FD_READ希望收到準備閱讀的通知。

- FD_WRITE希望在數據可供讀取時收到通知。

- FD_OOB希望收到帶外數據到達的通知。

- FD_ACCEPT希望接收傳入連接的通知。

- FD_CONNECT希望收到連接結果的通知。

- FD_CLOSE希望當同字套字已由對等體關閉時接收通知。

### <a name="return-value"></a>傳回值

如果函式成功，則為非零。

### <a name="remarks"></a>備註

SOCKET 句柄存儲在物件的[m_hSocket](#m_hsocket)數據成員中。

## <a name="casyncsocketbind"></a><a name="bind"></a>CAsyncSocket::綁定

調用此成員函數將本地位址與套接字相關聯。

```
BOOL Bind(
    UINT nSocketPort,
    LPCTSTR lpszSocketAddress = NULL);

BOOL Bind (
    const SOCKADDR* lpSockAddr,
    int nSockAddrLen);
```

### <a name="parameters"></a>參數

*nSocket連接埠*<br/>
標識套接字應用程式的埠。

*lpszSocket位址*<br/>
網路地址,虛數如"128.56.22.8"。 傳遞此參數的 NULL 字串`CAsyncSocket`指示 實例應偵聽所有網路介面上的用戶端活動。

*lpSockAddr*<br/>
指向[SOCKADDR](/windows/win32/winsock/sockaddr-2)結構的指標,其中包含要分配給此套接字的位址。

*恩索克·阿德爾倫*<br/>
以*lpSockAddr(* 以位元組為單位)的位址長度。

### <a name="return-value"></a>傳回值

如果函數成功,則非零;否則 0,可以通過調用[GetLastError](#getlasterror)來檢索特定的錯誤代碼。 下面的清單涵蓋了可能返回的一些錯誤。 有關完整清單,請參閱[Windows 通訊卡字錯誤程式](/windows/win32/winsock/windows-sockets-error-codes-2)。

- 在使用此 API 之前,必須成功進行[Afxsocketinit。](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Windows 套接字實現檢測到網路子系統失敗。

- WSAEADDRINUSE 指定的位址已在使用中。 ( 請參考[SetSockOpt](#setsockopt)的SO_REUSEADDR通訊字選項 。

- wsAEFAULT *nSockAddrLen*參數太小(小於[SOCKADDR](/windows/win32/winsock/sockaddr-2)結構的大小)。

- WSAEINPROGRESS 阻止 Windows 套接字調用正在進行中。

- 此埠不支援指定的位址族。

- WSAEINVAL 套接字已綁定到位址。

- WSAENOBUFS 沒有足夠的可用緩衝區,連接太多。

- WSANotSOCK 描述符不是套接字。

### <a name="remarks"></a>備註

此例程在後續`Connect``Listen`或調用之前在未連接的數據報或流套接字上使用。 在接收連接請求之前,偵聽伺服器套接字必須選擇埠號,並透過調用`Bind`來使其為 Windows 套接字。 `Bind`通過將本地名稱分配給未命名的套接字,建立套接字的本地關聯(主機位址/埠號)。

## <a name="casyncsocketcasyncsocket"></a><a name="casyncsocket"></a>同步通訊::CAsyncSocket

構造空白套接字物件。

```
CAsyncSocket();
```

### <a name="remarks"></a>備註

建構物件後,必須調用其成員`Create`函數以創建 SOCKET 數據結構並綁定其位址。 (在 Windows 套接字通訊的伺服器端,當偵聽套接字`Accept`創建要在呼叫中使用的套接`Create`字時 ,您不會呼叫該套接字。

## <a name="casyncsocketclose"></a><a name="close"></a>CAsyncSocket:關閉

關閉插座。

```
virtual void Close();
```

### <a name="remarks"></a>備註

此函數釋放套接字描述元,以便進一步引用它將失敗與錯誤 WSANOTSOCK。 如果這是對基礎套接字的最後一個引用,則將丟棄關聯的命名資訊和排隊數據。 套接字物件的析構函數會`Close`為你調用。

對於`CAsyncSocket`,但不`CSocket`適用於`Close`,的語義受套接字選項SO_LINGER和SO_DONTLINGER。 有關詳細資訊,請參閱成員函數`GetSockOpt`。

## <a name="casyncsocketconnect"></a><a name="connect"></a>CAsyncSocket:連接

呼叫此成員函數以建立與未連接的流或數據報接字的連接。

```
BOOL Connect(
    LPCTSTR lpszHostAddress,
    UINT nHostPort);

BOOL Connect(
    const SOCKADDR* lpSockAddr,
    int nSockAddrLen);
```

### <a name="parameters"></a>參數

*lpszHost 位址*<br/>
此物件連接到的套接字的網路位址:計算機名稱(如"ftp.microsoft.com")或虛線數位(如"128.56.22.8")。

*nHostPort*<br/>
標識套接字應用程式的埠。

*lpSockAddr*<br/>
指向包含連接套接字位址的[SOCKADDR](/windows/win32/winsock/sockaddr-2)結構的指標。

*恩索克·阿德爾倫*<br/>
以*lpSockAddr(* 以位元組為單位)的位址長度。

### <a name="return-value"></a>傳回值

如果函數成功,則非零;否則 0,可以通過調用[GetLastError](#getlasterror)來檢索特定的錯誤代碼。 如果這表示 WSAEWILLBLOCK 的錯誤代碼,並且應用程式正在使用可重寫的回調,則應用程式將在連接操作完成後`OnConnect`收到消息 。 以下錯誤適用於此成員函數:

- 在使用此 API 之前,必須成功進行[Afxsocketinit。](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Windows 套接字實現檢測到網路子系統失敗。

- WSAEADDRINUSE 指定的位址已在使用中。

- WSAEINPROGRESS 阻止 Windows 套接字調用正在進行中。

- WSAEADDRNOTA 指定位址不在本地電腦中。

- 指定族中的 WSAEAFNOSUPPORT 位址不能與此套接字一起使用。

- WSAECONN被拒絕連接嘗試。

- 需要位址。

- wsAEFAULT *nSockAddrLen*參數不正確。

- WSAEINVAL 無效主機位址。

- WSAEISCONN 插座已連接。

- WSAEMFILE 沒有更多的檔描述符可用。

- 此時無法從此主機到達網路。

- WSAENOBUFS 沒有可用的緩衝區空間。 無法連接插座。

- WSANotSOCK 描述符不是套接字。

- WSATimeDOUT 嘗試在不建立連接的情況下連接超時。

- WSAE到格,套接字被標記為非阻塞,連接無法立即完成。

### <a name="remarks"></a>備註

如果套接字未綁定,則系統將唯一值分配給本地關聯,並且套接字標記為綁定。 請注意,如果名稱結構的位址欄位為全零,`Connect`則返回零。 要取得延伸的錯誤資訊,`GetLastError`請呼叫成員函數。

對於流套接字(類型SOCK_STREAM),將啟動到外接主機的活動連接。 當套接字調用成功完成時,套接字已準備好發送/接收數據。

對於數據圖套接字(類型SOCK_DGRAM),將設置預設目標,該目標將用於後續`Send``Receive`和調用。

## <a name="casyncsocketcreate"></a><a name="create"></a>CAsyncSocket:建立

建構套`Create`接字物件後調用成員函數以創建 Windows 套接字並附加它。

```
BOOL Create(
    UINT nSocketPort = 0,
    int nSocketType = SOCK_STREAM,
    long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE,
    LPCTSTR lpszSocketAddress = NULL);
```

### <a name="parameters"></a>參數

*nSocket連接埠*<br/>
要與套接字一起使用的已知埠,如果希望 Windows 套接字選擇埠,則為 0。

*nSocket 類型*<br/>
SOCK_STREAM或SOCK_DGRAM。

*lEvent*<br/>
指定應用程式感興趣的網路事件的組合的位掩碼。

- FD_READ希望收到準備閱讀的通知。

- FD_WRITE希望收到準備寫作的通知。

- FD_OOB希望收到帶外數據到達的通知。

- FD_ACCEPT希望接收傳入連接的通知。

- FD_CONNECT希望收到已完成連接的通知。

- FD_CLOSE希望收到套接字關閉通知。

*lpszSock 位址*<br/>
指向包含連接套接字的網路位址的字串的指標,虛線數位,如"128.56.22.8"。傳遞此參數的 NULL 字串`CAsyncSocket`指示 實例應偵聽所有網路介面上的用戶端活動。

### <a name="return-value"></a>傳回值

如果函數成功,則非零;否則 0,可以通過調用[GetLastError](#getlasterror)來檢索特定的錯誤代碼。 以下錯誤適用於此成員函數:

- 在使用此 API 之前,必須成功進行[Afxsocketinit。](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Windows 套接字實現檢測到網路子系統失敗。

- WSAEAFNOSUPPORT 不支援指定的位址族。

- WSAEINPROGRESS 阻止 Windows 套接字操作正在進行中。

- WSAEMFILE 沒有更多的檔描述符可用。

- WSAENOBUFS 沒有可用的緩衝區空間。 無法創建套接字。

- WSAEPROTONOSUPPORT 不支援指定的埠。

- WSAEPROTOTYPE 指定埠是此套接字的錯誤類型。

- WSAESOCKTNOSUPPORT 此位址系列中不支援指定的套接字類型。

### <a name="remarks"></a>備註

`Create`呼叫[Socket](#socket),如果成功,它將呼叫[Bind](#bind)以綁定套接字到指定的位址。 支援以下通訊型態:

- SOCK_STREAM 提供序列化、可靠、全雙工、基於連接的位元組流。 對互聯網位址系列使用傳輸控制協定 (TCP)。

- SOCK_DGRAM支援資料圖,這是固定(通常較小)最大長度的無連接不可靠數據包。 對 Internet 位址系列使用使用者數據報協定 (UDP)。

    > [!NOTE]
    >  成員`Accept`函數以引用新的`CSocket`空 物件作為其參數。 在調用`Accept`之前,必須構造此物件。 請記住,如果此套接字物件超出範圍,連接將關閉。 不要調用`Create`此新套接字物件。

> [!IMPORTANT]
> `Create`**不是**線程安全的。  如果在多線程環境中調用它,不同線程可以同時調用它,請確保使用互斥體或其他同步鎖保護每個調用。

有關流和資料報套接字的詳細資訊,請參閱 Windows[套接字:後台](../../mfc/windows-sockets-background.md)和[Windows 套接字:連接埠和 socket 位址和](../../mfc/windows-sockets-ports-and-socket-addresses.md) [Windows 套接字 2 API](/windows/win32/WinSock/windows-sockets-start-page-2)。

## <a name="casyncsocketdetach"></a><a name="detach"></a>CAsyncSocket::D

呼叫此成員函數以將*m_hSocket*資料成員中的 SOCKET`CAsyncSocket`句柄從物件 中分離出來,並將*m_hSocket*設定為 NULL。

```
SOCKET Detach();
```

## <a name="casyncsocketfromhandle"></a><a name="fromhandle"></a>CAsyncSocket:從手柄

返回指向`CAsyncSocket`物件的指標。

```
static CAsyncSocket* PASCAL FromHandle(SOCKET hSocket);
```

### <a name="parameters"></a>參數

*hSocket*<br/>
包含套接字的句柄。

### <a name="return-value"></a>傳回值

指向`CAsyncSocket`物件的指標,如果沒有附加到`CAsyncSocket`*hSocket*的物件,則為 NULL。

### <a name="remarks"></a>備註

當給定一個 SOCKET`CAsyncSocket`句柄 時,如果物件未附加到句柄,則成員函數將返回 NULL。

## <a name="casyncsocketgetlasterror"></a><a name="getlasterror"></a>CAsyncSocket::取得上次錯誤

呼叫此成員函數以獲取上次失敗操作的錯誤狀態。

```
static int PASCAL GetLastError();
```

### <a name="return-value"></a>傳回值

返回值指示此線程執行的最後一個 Windows 套接字 API 例程的錯誤代碼。

### <a name="remarks"></a>備註

當特定成員函數指示已發生錯誤時,`GetLastError`應呼叫以檢索相應的錯誤程式碼。 有關適用錯誤代碼的清單,請參閱各個成員函數說明。

有關錯誤代碼的詳細資訊,請參閱 Windows[套接字 2 API](/windows/win32/WinSock/windows-sockets-start-page-2)。

## <a name="casyncsocketgetpeername"></a><a name="getpeername"></a>CAsyncSocket:取得對等名稱

呼叫此成員函數以獲取此套接字所連接到的對等套接字的位址。

```
BOOL GetPeerName(
    CString& rPeerAddress,
    UINT& rPeerPort);

BOOL GetPeerName(
    SOCKADDR* lpSockAddr,
    int* lpSockAddrLen);
```

### <a name="parameters"></a>參數

*r 佩爾位址*<br/>
對接收虛`CString`線數 IP 位址的物件的引用。

*rPeerPort*<br/>
引用存儲埠的 UINT。

*lpSockAddr*<br/>
指向接收對等套接字名稱的[SOCKADDR](/windows/win32/winsock/sockaddr-2)結構的指標。

*lpSockAddrLen*<br/>
以*lpSockAddr(* 以位元組為單位)指向位址長度的指標。 返回時 *,lpSockAddrLen*參數包含以位元組為單位返回的*lpSockAddr*的實際大小。

### <a name="return-value"></a>傳回值

如果函數成功,則非零;否則 0,可以通過調用[GetLastError](#getlasterror)來檢索特定的錯誤代碼。 以下錯誤適用於此成員函數:

- 在使用此 API 之前,必須成功進行[Afxsocketinit。](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Windows 套接字實現檢測到網路子系統失敗。

- WSAEFAULT *lpSockAddrLen*參數不夠大。

- WSAEINPROGRESS 阻止 Windows 套接字調用正在進行中。

- WSAENOTCONN 插座未連接。

- WSANotSOCK 描述符不是套接字。

### <a name="remarks"></a>備註

要處理 IPv6 位址,請使用[CAsyncSocket::取得對等名稱Ex](#getpeernameex)。

## <a name="casyncsocketgetpeernameex"></a><a name="getpeernameex"></a>CAsyncSocket:取得對等名稱Ex

調用此成員函數獲取此套接字連接到的對等套接字的位址(處理IPv6位址)。

```
BOOL GetPeerNameEx(
    CString& rPeerAddress,
    UINT& rPeerPort);
```

### <a name="parameters"></a>參數

*r 佩爾位址*<br/>
對接收虛`CString`線數 IP 位址的物件的引用。

*rPeerPort*<br/>
引用存儲埠的 UINT。

### <a name="return-value"></a>傳回值

如果函數成功,則非零;否則 0,可以通過調用[GetLastError](#getlasterror)來檢索特定的錯誤代碼。 以下錯誤適用於此成員函數:

- 在使用此 API 之前,必須成功進行[Afxsocketinit。](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Windows 套接字實現檢測到網路子系統失敗。

- WSAEFAULT *lpSockAddrLen*參數不夠大。

- WSAEINPROGRESS 阻止 Windows 套接字調用正在進行中。

- WSAENOTCONN 插座未連接。

- WSANotSOCK 描述符不是套接字。

### <a name="remarks"></a>備註

此功能與[CAsyncSocket:getPeerName](#getpeername)相同,只不過它處理 IPv6 位址以及較舊的協定。

## <a name="casyncsocketgetsockname"></a><a name="getsockname"></a>CAsyncSocket:取得索克名稱

呼叫此成員函數以獲取套接字的本地名稱。

```
BOOL GetSockName(
    CString& rSocketAddress,
    UINT& rSocketPort);

BOOL GetSockName(
    SOCKADDR* lpSockAddr,
    int* lpSockAddrLen);
```

### <a name="parameters"></a>參數

*rSocket位址*<br/>
對接收虛`CString`線數 IP 位址的物件的引用。

*rSocket連接埠*<br/>
引用存儲埠的 UINT。

*lpSockAddr*<br/>
指向接收套接字位址的[SOCKADDR](/windows/win32/winsock/sockaddr-2)結構的指標。

*lpSockAddrLen*<br/>
以*lpSockAddr(* 以位元組為單位)指向位址長度的指標。

### <a name="return-value"></a>傳回值

如果函數成功,則非零;否則 0,可以通過調用[GetLastError](#getlasterror)來檢索特定的錯誤代碼。 以下錯誤適用於此成員函數:

- 在使用此 API 之前,必須成功進行[Afxsocketinit。](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Windows 套接字實現檢測到網路子系統失敗。

- WSAEFAULT *lpSockAddrLen*參數不夠大。

- WSAEINPROGRESS 阻止 Windows 套接字操作正在進行中。

- WSANotSOCK 描述符不是套接字。

- WSAEINVAL 套接字未綁定到`Bind`帶 的位址。

### <a name="remarks"></a>備註

此調用在未進行第一`Connect``Bind`次調用的情況下特別有用;此調用提供了確定系統已設置的本地關聯的唯一方法。

要處理 IPv6 位址,請使用[CAsyncSocket::getSockNameEx](#getsocknameex)

## <a name="casyncsocketgetsocknameex"></a><a name="getsocknameex"></a>CAsyncSocket::獲取索諾克名稱Ex

調用此成員函數獲取套接字的本地名稱(處理IPv6位址)。

```
BOOL GetSockNameEx(
    CString& rSocketAddress,
    UINT& rSocketPort);
```

### <a name="parameters"></a>參數

*rSocket位址*<br/>
對接收虛`CString`線數 IP 位址的物件的引用。

*rSocket連接埠*<br/>
引用存儲埠的 UINT。

### <a name="return-value"></a>傳回值

如果函數成功,則非零;否則 0,可以通過調用[GetLastError](#getlasterror)來檢索特定的錯誤代碼。 以下錯誤適用於此成員函數:

- 在使用此 API 之前,必須成功進行[Afxsocketinit。](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Windows 套接字實現檢測到網路子系統失敗。

- WSAEFAULT *lpSockAddrLen*參數不夠大。

- WSAEINPROGRESS 阻止 Windows 套接字操作正在進行中。

- WSANotSOCK 描述符不是套接字。

- WSAEINVAL 套接字未綁定到`Bind`帶 的位址。

### <a name="remarks"></a>備註

此調用與[CAsyncSocket:getSockName](#getsockname)相同,只不過它處理 IPv6 位址以及較舊的協定。

此調用在未進行第一`Connect``Bind`次調用的情況下特別有用;此調用提供了確定系統已設置的本地關聯的唯一方法。

## <a name="casyncsocketgetsockopt"></a><a name="getsockopt"></a>CAsyncSocket:getSockOpt

調用此成員函數以檢索套接字選項。

```
BOOL GetSockOpt(
    int nOptionName,
    void* lpOptionValue,
    int* lpOptionLen,
    int nLevel = SOL_SOCKET);
```

### <a name="parameters"></a>參數

*nOption名稱*<br/>
要為其檢索值的套接字選項。

*lpOption值*<br/>
指向要返回所請求選項的值的緩衝區的指標。 與選取的選項關聯的值將傳回緩衝區*lpOptionValue*。 *lpOptionLen*指向的整數最初應包含此緩衝區的大小(以位元組為單位);並在返回時,它將設置為返回的值的大小。 對於SO_LINGER,這將是一個`LINGER`結構的大小;對於所有其他選項,它將是 BOOL 或**int**的大小,具體取決於選項。 請參閱「備註」部分中的選項及其大小清單。

*lpOptionLen*<br/>
指向以位元組為單位的*lpOptionValue*緩衝區大小的指標。

*n 等級*<br/>
定義選項的級別;唯一支持的級別是SOL_SOCKET和IPPROTO_TCP。

### <a name="return-value"></a>傳回值

如果函數成功,則非零;否則 0,可以通過調用[GetLastError](#getlasterror)來檢索特定的錯誤代碼。 如果從未使用`SetSockOpt`設定選項,`GetSockOpt`則返回該選項的預設值。 以下錯誤適用於此成員函數:

- 在使用此 API 之前,必須成功進行[Afxsocketinit。](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Windows 套接字實現檢測到網路子系統失敗。

- WSAEFAULT *lpOptionlen*參數無效。

- WSAEINPROGRESS 阻止 Windows 套接字操作正在進行中。

- WSAENOPROTOOPT 選項未知或不受支援。 特別是,SOCK_STREAM類型的套接字不支援SO_BROADCAST,而SOCK_DGRAM類型的套接字不支援SO_ACCEPTCONN、SO_DONTLINGER、SO_KEEPALIVE、SO_LINGER和SO_OOBINLINE。

- WSANotSOCK 描述符不是套接字。

### <a name="remarks"></a>備註

`GetSockOpt`檢索與任何類型的套接字關聯的套接字選項的當前值,並將結果存儲在*lpOptionValue*中。 選項會影響套接字操作,例如數據包的路由、帶外數據傳輸等。

支援以下選項。 `GetSockOpt` 類型標識*lpOptionValue*定址的數據類型。 TCP_NODELAY選項使用IPPROTO_TCP級別;所有其他選項使用級別SOL_SOCKET。

|值|類型|意義|
|-----------|----------|-------------|
|SO_ACCEPTCONN|BOOL|插座正在偵聽。|
|SO_BROADCAST|BOOL|套接字配置為傳輸廣播消息。|
|SO_DEBUG|BOOL|已啟用調試。|
|SO_DONTLINGER|BOOL|如果為 true,則禁用SO_LINGER選項。|
|SO_DONTROUTE|BOOL|路由已禁用。|
|SO_ERROR|**int**|檢索錯誤狀態並清除。|
|SO_KEEPALIVE|BOOL|正在發送保持生命。|
|SO_LINGER|`struct LINGER`|返回當前留日選項。|
|SO_OOBINLINE|BOOL|在正常數據流中接收帶外數據。|
|SO_RCVBUF|int|接收的緩衝區大小。|
|SO_REUSEADDR|BOOL|套接字可以綁定到已在使用的位址。|
|SO_SNDBUF|**int**|發送的緩衝區大小。|
|SO_TYPE|**int**|套接字的類型(例如,SOCK_STREAM)。|
|TCP_NODELAY|BOOL|停用用於傳送聯合的 Nagle 演算法。|

Bake 模式 (BSD) 選項不支援`GetSockOpt`:

|值|類型|意義|
|-----------|----------|-------------|
|SO_RCVLOWAT|**int**|接收低水位線。|
|SO_RCVTIMEO|**int**|接收超時。|
|SO_SNDLOWAT|**int**|發送低水位線。|
|SO_SNDTIMEO|**int**|發送超時。|
|IP_OPTIONS||取得 IP 標頭中的選項。|
|TCP_MAXSEG|**int**|獲取 TCP 最大段大小。|

使用`GetSockOpt`不支援的選項呼叫將導致`GetLastError`從返回 WSAENOPROTOOPT 的錯誤代碼。

## <a name="casyncsocketioctl"></a><a name="ioctl"></a>CAsyncSocket::IOCtl

調用此成員函數以控制套接字模式。

```
BOOL IOCtl(
    long lCommand,
    DWORD* lpArgument);
```

### <a name="parameters"></a>參數

*lCommand*<br/>
要對套接字執行的操作。

*lp參數*<br/>
指向*lCommand*的參數的指標。

### <a name="return-value"></a>傳回值

如果函數成功,則非零;否則 0,可以通過調用[GetLastError](#getlasterror)來檢索特定的錯誤代碼。 以下錯誤適用於此成員函數:

- 在使用此 API 之前,必須成功進行[Afxsocketinit。](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Windows 套接字實現檢測到網路子系統失敗。

- WSAEINVAL *lCommand*不是一個有效的命令,或者*lpArgument*不是*lCommand*的可接受參數,或者該命令不適用於提供的套接字類型。

- WSAEINPROGRESS 阻止 Windows 套接字操作正在進行中。

- WSANotSOCK 描述符不是套接字。

### <a name="remarks"></a>備註

此例程可用於任何狀態的任何套接字。 它用於獲取或檢索與套接字關聯的操作參數,獨立於協定和通信子系統。 支援的命令如下：

- FIONBIO 啟用或禁用插座上的非阻塞模式。 *lpArgument*參數`DWORD`指向 ,如果啟用非阻塞模式,則該參數為非零;如果要禁用該參數,則為零。 如果在`AsyncSelect`套接字上已發出,則任何嘗試`IOCtl`將 套接字設置為阻塞模式的嘗試都將失敗,而 WSAEINVAL 也會失敗。 要將 socket 設定為阻塞模式並防止 WSAEINVAL 錯誤,應用程式必須`AsyncSelect``AsyncSelect`先透過呼叫*lEvent*參數等於`IOCtl`0 來停用,然後呼叫 。

- FIONREAD 確定通過一`Receive`個調用從該套接字讀取的最大位元組數。 *lpArgument*參數`IOCtl`指向`DWORD`儲存結果的 。 如果此套接字的類型為SOCK_STREAM,FIONREAD 返回可在單`Receive`個 中讀取的數據總量;這通常與套接字上排隊的數據總量相同。 如果此套接字的類型為 SOCK_DGRAM,FIONREAD 返回在套接字上排隊的第一個數據報的大小。

- SIOCATMARK 確定是否已讀取所有帶外數據。 這僅適用於已配置為在線接收任何帶外資料(SO_OOBINLINE)的類型SOCK_STREAM套接字。 如果沒有等待讀取帶外數據,則操作將返回非零。 否則,它將返回 0,在`Receive`下`ReceiveFrom`一個或對套接字執行的數據將檢索「標記」前面的部分或全部數據;否則,在套接字上執行的下一個或執行的數據將檢索到 「標記」之前的部分或全部數據。應用程式應使用 SIOCATMARK 操作來確定是否存在任何數據。 如果「緊急」(帶外)數據之前有任何正常數據,則按順序接收。 (請注意,或`Receive``ReceiveFrom`永遠不會在同一調用中混合帶外數據和正常數據。*lpArgument*參數`IOCtl`指向`DWORD`儲存結果的 。

此函數是伯克利套接`ioctl()`字中使用的子集。 特別是,沒有相當於FIOASYNC的命令,而SIOCATMARK是唯一支援的套接字級命令。

## <a name="casyncsocketlisten"></a><a name="listen"></a>CAsyncSocket:聽

調用此成員函數以偵聽傳入連接請求。

```
BOOL Listen(int nConnectionBacklog = 5);
```

### <a name="parameters"></a>參數

*N 連接積壓*<br/>
掛起連接佇列可以增長到的最大長度。 有效範圍為 1 到 5。

### <a name="return-value"></a>傳回值

如果函數成功,則非零;否則 0,可以通過調用[GetLastError](#getlasterror)來檢索特定的錯誤代碼。 以下錯誤適用於此成員函數:

- 在使用此 API 之前,必須成功進行[Afxsocketinit。](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Windows 套接字實現檢測到網路子系統失敗。

- 已嘗試偵聽正在使用的位址。

- WSAEINPROGRESS 阻止 Windows 套接字操作正在進行中。

- WSAEINVAL 套接字尚未綁`Bind`定 或已連接。

- WSAEISCONN 插座已連接。

- WSAEMFILE 沒有更多的檔描述符可用。

- WSAENOBUFS 沒有可用的緩衝區空間。

- WSANotSOCK 描述符不是套接字。

- WSAEOPNOTSUPP 引用的套接字不是支援`Listen`該 操作的類型。

### <a name="remarks"></a>備註

要接受連接,首先使用`Create`創建套接字,`Listen`使用 指定傳入連接的積壓工作,`Accept`然後使用 接受連接。 `Listen`僅適用於支援連接的套接字,即SOCK_STREAM類型的套接字。 此套接字被置於"被動"模式,其中傳入連接被確認並排隊等待進程接受。

此函數通常由伺服器(或任何想要接受連接的應用程式)使用,這些伺服器(或任何應用程式)一次可能有多個連接請求:如果連接請求到達時佇列已滿,則用戶端將收到一個錯誤,指示 WSAECONNREFUSED。

`Listen`嘗試在沒有可用埠(描述符)時繼續合理運行。 它將接受連接,直到佇列清空。 如果埠可用,則稍後調用`Listen`或`Accept`將佇列重新填充到當前或最新的「積壓」,如果可能,並繼續偵聽傳入連接。

## <a name="casyncsocketm_hsocket"></a><a name="m_hsocket"></a>CAsyncSocket:m_hSocket

包含此`CAsyncSocket`物件封裝的套接字的 SOCKET 句柄。

```
SOCKET m_hSocket;
```

## <a name="casyncsocketonaccept"></a><a name="onaccept"></a>CAsyncSocket::接受

由框架調用以通知偵聽套接字,它可以通過調用[Accept](#accept)成員函數來接受掛起的連接請求。

```
virtual void OnAccept(int nErrorCode);
```

### <a name="parameters"></a>參數

*n 錯誤代碼*<br/>
套接字上的最新錯誤。 以下錯誤代碼適用於`OnAccept`成員函數:

- **0**已成功執行函數。

- WSAENETDOWN Windows 套接字實現檢測到網路子系統失敗。

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[Windows 通訊排單:socket 通知](../../mfc/windows-sockets-socket-notifications.md)。

## <a name="casyncsocketonclose"></a><a name="onclose"></a>同步通訊::關閉

由框架呼叫,以通知此套接字由其行程關閉連接的套接字。

```
virtual void OnClose(int nErrorCode);
```

### <a name="parameters"></a>參數

*n 錯誤代碼*<br/>
套接字上的最新錯誤。 以下錯誤代碼適用於`OnClose`成員函數:

- **0**已成功執行函數。

- WSAENETDOWN Windows 套接字實現檢測到網路子系統失敗。

- WSAECONNRESET 連接被遠端端重置。

- WSAECONABORTED 由於超時或其他故障導致連接中止。

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[Windows 通訊排單:socket 通知](../../mfc/windows-sockets-socket-notifications.md)。

## <a name="casyncsocketonconnect"></a><a name="onconnect"></a>CAsyncSocket:開啟連線

框架呼叫以通知此連接套接字,其連接嘗試已完成,無論是成功還是錯誤。

```
virtual void OnConnect(int nErrorCode);
```

### <a name="parameters"></a>參數

*n 錯誤代碼*<br/>
套接字上的最新錯誤。 以下錯誤代碼適用於`OnConnect`成員函數:

- **0**已成功執行函數。

- WSAEADDRINUSE 指定的位址已在使用中。

- WSAEADDRNOTA 指定位址不在本地電腦中。

- 指定族中的 WSAEAFNOSUPPORT 位址不能與此套接字一起使用。

- WSAECONN一條連接嘗試被強行拒絕。

- 需要位址。

- WSAEFAULT *lpSockAddrLen*參數不正確。

- WSAEINVAL 套接字已綁定到位址。

- WSAEISCONN 插座已連接。

- WSAEMFILE 沒有更多的檔描述符可用。

- 此時無法從此主機到達網路。

- WSAENOBUFS 沒有可用的緩衝區空間。 無法連接插座。

- WSAENOTCONN 插座未連接。

- WSAENOTSOCK 描述符是檔,而不是套接字。

- WSAETIMEDOUT 嘗試連接超時而不建立連接。

### <a name="remarks"></a>備註

> [!NOTE]
> 在[CSocket](../../mfc/reference/csocket-class.md)`OnConnect`中,永遠不會呼叫通知函數。 對於連接,只需調用`Connect`,連接完成後將返回(成功或錯誤)。 如何處理連接通知是 MFC 實現的詳細資訊。

有關詳細資訊,請參閱[Windows 通訊排單:socket 通知](../../mfc/windows-sockets-socket-notifications.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCAsyncSocket#1](../../mfc/reference/codesnippet/cpp/casyncsocket-class_1.cpp)]

## <a name="casyncsocketonoutofbanddata"></a><a name="onoutofbanddata"></a>CAsyncsocket::在帶外數據上

由框架呼叫以通知接收套接字發送套接字具有要發送的帶外數據。

```
virtual void OnOutOfBandData(int nErrorCode);
```

### <a name="parameters"></a>參數

*n 錯誤代碼*<br/>
套接字上的最新錯誤。 以下錯誤代碼適用於`OnOutOfBandData`成員函數:

- **0**已成功執行函數。

- WSAENETDOWN Windows 套接字實現檢測到網路子系統失敗。

### <a name="remarks"></a>備註

帶外數據是一個邏輯上獨立的通道,與SOCK_STREAM類型的每對連接的套接字相關聯。 通道通常用於發送緊急數據。

MFC 支援帶外數據,但禁止`CAsyncSocket`類 使用者使用它。 更簡單的方法是創建第二個套接字以傳遞此類數據。 有關帶外資料的詳細資訊,請參閱[Windows 套接字:套接字通知](../../mfc/windows-sockets-socket-notifications.md)。

## <a name="casyncsocketonreceive"></a><a name="onreceive"></a>CAsyncSocket:開啟接收

由框架調用以通知此套接字緩衝區中有可以通過調`Receive`用 成員函數檢索的數據。

```
virtual void OnReceive(int nErrorCode);
```

### <a name="parameters"></a>參數

*n 錯誤代碼*<br/>
套接字上的最新錯誤。 以下錯誤代碼適用於`OnReceive`成員函數:

- **0**已成功執行函數。

- WSAENETDOWN Windows 套接字實現檢測到網路子系統失敗。

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[Windows 通訊排單:socket 通知](../../mfc/windows-sockets-socket-notifications.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCAsyncSocket#2](../../mfc/reference/codesnippet/cpp/casyncsocket-class_2.cpp)]

## <a name="casyncsocketonsend"></a><a name="onsend"></a>CAsyncSocket:開啟傳送

由框架調用,以通知套接字,它現在可以通過調`Send`用 成員函數發送數據。

```
virtual void OnSend(int nErrorCode);
```

### <a name="parameters"></a>參數

*n 錯誤代碼*<br/>
套接字上的最新錯誤。 以下錯誤代碼適用於`OnSend`成員函數:

- **0**已成功執行函數。

- WSAENETDOWN Windows 套接字實現檢測到網路子系統失敗。

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[Windows 通訊排單:socket 通知](../../mfc/windows-sockets-socket-notifications.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCAsyncSocket#3](../../mfc/reference/codesnippet/cpp/casyncsocket-class_3.cpp)]

## <a name="casyncsocketoperator-"></a><a name="operator_eq"></a>CAsyncSocket::運算符 |

為`CAsyncSocket`物件分配新值。

```
void operator=(const CAsyncSocket& rSrc);
```

### <a name="parameters"></a>參數

*rSrc*<br/>
對現有`CAsyncSocket`物件的引用。

### <a name="remarks"></a>備註

調用此函數以將現有`CAsyncSocket`物件複製到另`CAsyncSocket`一 個物件。

## <a name="casyncsocketoperator-socket"></a><a name="operator_socket"></a>CAsyncSocket::操作員

使用此運算符檢索`CAsyncSocket`物件的 SOCKET 句柄。

```
operator SOCKET() const;
```

### <a name="return-value"></a>傳回值

如果成功,則處理 SOCKET 物件的句柄;如果成功,則處理否則,NULL。

### <a name="remarks"></a>備註

您可以使用該句柄直接呼叫 Windows API。

## <a name="casyncsocketreceive"></a><a name="receive"></a>CAsyncSocket:接收

調用此成員函數從套接字接收數據。

```
virtual int Receive(
    void* lpBuf,
    int nBufLen,
    int nFlags = 0);
```

### <a name="parameters"></a>參數

*lpBuf*<br/>
傳入數據的緩衝區。

*恩布夫倫*<br/>
以位元組為單位的*lpBuf*的長度。

*nFlags*<br/>
指定調用的方式。 此函數的語義由套接字選項和*nFlags*參數決定。 後者是通過將以下任一值與C++ **OR**運算子組合而成的:

- MSG_PEEK查看傳入數據。 數據將複製到緩衝區中,但不會從輸入佇列中刪除。

- MSG_OOB處理帶外數據。

### <a name="return-value"></a>傳回值

如果未發生錯誤,`Receive`則傳回接收的位元數。 如果連接已關閉,則返回 0。 否則,將返回SOCKET_ERROR值,並且可以通過調用[GetLastError](#getlasterror)來檢索特定的錯誤代碼。 以下錯誤適用於此成員函數:

- 在使用此 API 之前,必須成功進行[Afxsocketinit。](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Windows 套接字實現檢測到網路子系統失敗。

- WSAENOTCONN 插座未連接。

- WSAEINPROGRESS 阻止 Windows 套接字操作正在進行中。

- WSANotSOCK 描述符不是套接字。

- 已指定 WSAOpNOTSUPp MSG_OOB,但套接字不是類型SOCK_STREAM。

- WSAE關閉 插座已關閉;在使用*nHow*`Receive`設置`ShutDown`為 0 或 2 調用後,無法調用套接字。

- WSAEANDBLOCK 套接字標記為非阻塞`Receive`, 操作將阻塞。

- WSAEMSGSIZE 數據報太大,無法放入指定的緩衝區並被截斷。

- WSAEINVAL socket 未結合`Bind`。

- WSAECONABORTED 虛擬電路由於超時或其他故障而中止。

- WSAECONNRESET 虛擬電路被遠端端重置。

### <a name="remarks"></a>備註

此功能用於連接的流或數據報接字,用於讀取傳入資料。

對於SOCK_STREAM類型的套接字,返回截至提供的緩衝區大小的當前可用資訊。 如果套接字已配置為在線接收帶外數據(套接字選項SO_OOBINLINE),並且未讀取帶外數據,則僅返回帶外數據。 應用程式可以使用`IOCtlSIOCATMARK`選項或[OnOutOfBandData](#onoutofbanddata)來確定是否還需要更多的帶外數據讀取。

對於 Datagram 套接字,將從第一個排隊的數據報中提取數據,最多為提供的緩衝區大小。 如果數據報大於提供的緩衝區,則緩衝區將填充數據報的第一部分,多餘的數據將丟失,`Receive`並返回一個值SOCKET_ERROR,錯誤代碼設置為 WSAEMSGSIZE。 如果套接字上沒有傳入數據可用,則返回一個值SOCKET_ERROR,錯誤代碼設置為 WSAETOBLOCK。 [OnReceive](#onreceive)回調功能可用於確定更多數據到達時間。

如果套接字的類型為SOCK_STREAM並且遠端端已正常關閉連接,則將立即完成`Receive`0 位元組。 如果連接已重置,則`Receive`a 將失敗,錯誤為 WSAECONNRESET。

`Receive`每次[調用 CAsyncSocket 時](#onreceive),應只調用一次:onReceive。

### <a name="example"></a>範例

  請參閱[CAsyncSocket 的範例::開啟接收](#onreceive)。

## <a name="casyncsocketreceivefrom"></a><a name="receivefrom"></a>CAsyncSocket:接收來自

調用此成員函數以接收資料報,並將源位址存儲在[SOCKADDR](/windows/win32/winsock/sockaddr-2)結構或*rSocket 位址*中。

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
傳入數據的緩衝區。

*恩布夫倫*<br/>
以位元組為單位的*lpBuf*的長度。

*rSocket位址*<br/>
對接收虛`CString`線數 IP 位址的物件的引用。

*rSocket連接埠*<br/>
引用存儲埠的 UINT。

*lpSockAddr*<br/>
指向[SOCKADDR](/windows/win32/winsock/sockaddr-2)結構的指標,該結構在返回時保存源位址。

*lpSockAddrLen*<br/>
指向*以 lpSockAddr*為單位的源位址長度的指標(以位元組為單位)。

*nFlags*<br/>
指定調用的方式。 此函數的語義由套接字選項和*nFlags*參數決定。 後者是通過將以下任一值與C++ **OR**運算子組合而成的:

- MSG_PEEK查看傳入數據。 數據將複製到緩衝區中,但不會從輸入佇列中刪除。

- MSG_OOB處理帶外數據。

### <a name="return-value"></a>傳回值

如果未發生錯誤,`ReceiveFrom`則傳回接收的位元數。 如果連接已關閉,則返回 0。 否則,將返回SOCKET_ERROR值,並且可以通過調`GetLastError`用 檢索特定的錯誤代碼。 以下錯誤適用於此成員函數:

- 在使用此 API 之前,必須成功進行[Afxsocketinit。](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Windows 套接字實現檢測到網路子系統失敗。

- WSAEFAULT *lpSockAddrLen*參數無效 *:lpSockAddr*緩衝區太小,無法容納對等位址。

- WSAEINPROGRESS 阻止 Windows 套接字操作正在進行中。

- WSAEINVAL socket 未結合`Bind`。

- WSAENOTCONN 插座未連接(僅SOCK_STREAM)。

- WSANotSOCK 描述符不是套接字。

- 已指定 WSAOpNOTSUPp MSG_OOB,但套接字不是類型SOCK_STREAM。

- WSAE關閉 插座已關閉;在使用*nHow*`ReceiveFrom`設置`ShutDown`為 0 或 2 調用後,無法調用套接字。

- WSAEANDBLOCK 套接字標記為非阻塞`ReceiveFrom`, 操作將阻塞。

- WSAEMSGSIZE 數據報太大,無法放入指定的緩衝區並被截斷。

- WSAECONABORTED 虛擬電路由於超時或其他故障而中止。

- WSAECONNRESET 虛擬電路被遠端端重置。

### <a name="remarks"></a>備註

此功能用於讀取(可能已連接的)套接字上的傳入數據,並捕獲從中發送數據的位址。

要處理 IPv6 位址,請使用[CAsyncSocket::接收從前。](#receivefromex)

對於SOCK_STREAM類型的套接字,返回截至提供的緩衝區大小的當前可用資訊。 如果套接字已配置為在線接收帶外數據(套接字選項SO_OOBINLINE),並且未讀取帶外數據,則僅返回帶外數據。 應用程式可以使用`IOCtlSIOCATMARK`該`OnOutOfBandData`選項或 確定是否還需要讀取任何帶外數據。 對於SOCK_STREAM套接字,將忽略*lpSockAddr*和*lpSockAddrLen*參數。

對於 Datagram 套接字,將從第一個排隊的數據報中提取數據,最多為提供的緩衝區大小。 如果數據報大於提供的緩衝區,則緩衝區將填充消息的第一部分,多餘的數據將丟失,`ReceiveFrom`並返回一個值 SOCKET_ERROR,錯誤代碼設置為 WSAMSGSIZE。

如果*lpSockAddr*是非零,並且套接字的類型為SOCK_DGRAM,則發送數據的套接字的網路位址將複製到相應的[SOCKADDR](/windows/win32/winsock/sockaddr-2)結構。 *lpSockAddrLen*指向的值初始化為此結構的大小,並在返回時修改以指示存儲在那裡的位址的實際大小。 如果套接字沒有傳入資料可用,`ReceiveFrom`則呼叫將等待數據到達,除非套接字未阻塞。 在這種情況下,將返回SOCKET_ERROR值,並將錯誤代碼設置為 WSAETOBLOCK。 `OnReceive`回調可用於確定更多數據到達時間。

如果套接字的類型為SOCK_STREAM並且遠端端已正常關閉連接,則將立即完成`ReceiveFrom`0 位元組。

## <a name="casyncsocketreceivefromex"></a><a name="receivefromex"></a>CAsyncSocket::接收來自Ex

呼叫此成員函數以接收資料報,並將來源位址儲存在[SOCKADDR](/windows/win32/winsock/sockaddr-2)結構或*rSocket 位址*(句柄 IPv6 位址)中。

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
傳入數據的緩衝區。

*恩布夫倫*<br/>
以位元組為單位的*lpBuf*的長度。

*rSocket位址*<br/>
對接收虛`CString`線數 IP 位址的物件的引用。

*rSocket連接埠*<br/>
引用存儲埠的 UINT。

*nFlags*<br/>
指定調用的方式。 此函數的語義由套接字選項和*nFlags*參數決定。 後者是通過將以下任一值與C++ **OR**運算子組合而成的:

- MSG_PEEK查看傳入數據。 數據將複製到緩衝區中,但不會從輸入佇列中刪除。

- MSG_OOB處理帶外數據。

### <a name="return-value"></a>傳回值

如果未發生錯誤,`ReceiveFromEx`則傳回接收的位元數。 如果連接已關閉,則返回 0。 否則,將返回SOCKET_ERROR值,並且可以通過調`GetLastError`用 檢索特定的錯誤代碼。 以下錯誤適用於此成員函數:

- 在使用此 API 之前,必須成功進行[Afxsocketinit。](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Windows 套接字實現檢測到網路子系統失敗。

- WSAEFAULT *lpSockAddrLen*參數無效 *:lpSockAddr*緩衝區太小,無法容納對等位址。

- WSAEINPROGRESS 阻止 Windows 套接字操作正在進行中。

- WSAEINVAL socket 未結合`Bind`。

- WSAENOTCONN 插座未連接(僅SOCK_STREAM)。

- WSANotSOCK 描述符不是套接字。

- 已指定 WSAOpNOTSUPp MSG_OOB,但套接字不是類型SOCK_STREAM。

- WSAE關閉 插座已關閉;在使用*nHow*`ReceiveFromEx`設置`ShutDown`為 0 或 2 調用後,無法調用套接字。

- WSAEANDBLOCK 套接字標記為非阻塞`ReceiveFromEx`, 操作將阻塞。

- WSAEMSGSIZE 數據報太大,無法放入指定的緩衝區並被截斷。

- WSAECONABORTED 虛擬電路由於超時或其他故障而中止。

- WSAECONNRESET 虛擬電路被遠端端重置。

### <a name="remarks"></a>備註

此功能用於讀取(可能已連接的)套接字上的傳入數據,並捕獲從中發送數據的位址。

此功能與[CAsyncSocket:ReceiveFrom](#receivefrom)相同,只不過它處理 IPv6 位址以及較舊的協定。

對於SOCK_STREAM類型的套接字,返回截至提供的緩衝區大小的當前可用資訊。 如果套接字已配置為在線接收帶外數據(套接字選項SO_OOBINLINE),並且未讀取帶外數據,則僅返回帶外數據。 應用程式可以使用`IOCtlSIOCATMARK`該`OnOutOfBandData`選項或 確定是否還需要讀取任何帶外數據。 對於SOCK_STREAM套接字,將忽略*lpSockAddr*和*lpSockAddrLen*參數。

對於 Datagram 套接字,將從第一個排隊的數據報中提取數據,最多為提供的緩衝區大小。 如果數據報大於提供的緩衝區,則緩衝區將填充消息的第一部分,多餘的數據將丟失,`ReceiveFromEx`並返回一個值 SOCKET_ERROR,錯誤代碼設置為 WSAMSGSIZE。

如果*lpSockAddr*是非零,並且套接字的類型為SOCK_DGRAM,則發送數據的套接字的網路位址將複製到相應的[SOCKADDR](/windows/win32/winsock/sockaddr-2)結構。 *lpSockAddrLen*指向的值初始化為此結構的大小,並在返回時修改以指示存儲在那裡的位址的實際大小。 如果套接字沒有傳入資料可用,`ReceiveFromEx`則呼叫將等待數據到達,除非套接字未阻塞。 在這種情況下,將返回SOCKET_ERROR值,並將錯誤代碼設置為 WSAETOBLOCK。 `OnReceive`回調可用於確定更多數據到達時間。

如果套接字的類型為SOCK_STREAM並且遠端端已正常關閉連接,則將立即完成`ReceiveFromEx`0 位元組。

## <a name="casyncsocketsend"></a><a name="send"></a>CAsyncSocket:傳送

呼叫此成員函數以在連接的套接字上發送數據。

```
virtual int Send(
    const void* lpBuf,
    int nBufLen,
    int nFlags = 0);
```

### <a name="parameters"></a>參數

*lpBuf*<br/>
包含要傳輸的數據的緩衝區。

*恩布夫倫*<br/>
以*lpBuf(* 以位元組為單位)的數據長度。

*nFlags*<br/>
指定調用的方式。 此函數的語義由套接字選項和*nFlags*參數決定。 後者是通過將以下任一值與C++ **OR**運算子組合而成的:

- MSG_DONTROUTE 指定數據不應受路由約束。 Windows 套接字供應商可以選擇忽略此標誌。

- MSG_OOB發送帶外數據(僅限SOCK_STREAM)。

### <a name="return-value"></a>傳回值

如果未發生錯誤,`Send`則傳回發送的字元總數。 (請注意,這可能小於*nBufLen*指示的數位。否則,將返回SOCKET_ERROR值,並且可以通過調用[GetLastError](#getlasterror)來檢索特定的錯誤代碼。 以下錯誤適用於此成員函數:

- 在使用此 API 之前,必須成功進行[Afxsocketinit。](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Windows 套接字實現檢測到網路子系統失敗。

- WSAEACCES 請求的位址是廣播位址,但未設置相應的標誌。

- WSAEINPROGRESS 阻止 Windows 套接字操作正在進行中。

- WSAEFAULT *lpBuf*參數不在使用者位址空間的有效部分。

- 必須重置連接,因為 Windows 套接字實現將其丟棄。

- WSAENOBUFS Windows 套接字實現報告緩衝區死鎖。

- WSAENOTCONN 插座未連接。

- WSANotSOCK 描述符不是套接字。

- 已指定 WSAOpNOTSUPp MSG_OOB,但套接字不是類型SOCK_STREAM。

- WSAE關閉 插座已關閉;在使用*nHow*`Send`設置`ShutDown`為 1 或 2 調用後,無法調用套接字。

- WSAEANDBLOCK 套接字標記為非阻塞,請求的操作將阻塞。

- WSAEMSGSIZE 套接字的類型為SOCK_DGRAM,並且數據報比 Windows 套接字實現支援的最大值要大。

- WSAEINVAL socket 未結合`Bind`。

- WSAECONABORTED 虛擬電路由於超時或其他故障而中止。

- WSAECONNRESET 虛擬電路被遠端端重置。

### <a name="remarks"></a>備註

`Send`用於在連接的流或數據圖套接字上寫入傳出數據。 對於 Datagram 套接字,必須小心不要超過基礎子網的最大 IP 數據包大小,`iMaxUdpDg``AfxSocketInit`該大小由返回的[WSADATA](/windows/win32/api/winsock2/ns-winsock2-wsadata)結構中的元素給出。 如果數據太長,無法通過基礎協定以原子方式傳遞,則通過`GetLastError`返回錯誤 WSAEMSGSIZE,並且不會傳輸任何數據。

請注意,對於數據報套接字,成功完成`Send`的並不表示數據已成功傳遞。

在`CAsyncSocket`SOCK_STREAM類型的物件上,寫入的位元組數可以介於 1 和請求的長度之間,具體取決於本地主機和外主機上的緩衝區可用性。

### <a name="example"></a>範例

  請參閱[CAsyncSocket 的範例::打開。](#onsend)

## <a name="casyncsocketsendto"></a><a name="sendto"></a>同步通訊::傳送至

調用此成員函數將數據發送到特定目標。

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
包含要傳輸的數據的緩衝區。

*恩布夫倫*<br/>
以*lpBuf(* 以位元組為單位)的數據長度。

*nHostPort*<br/>
標識套接字應用程式的埠。

*lpszHost 位址*<br/>
此物件連接到的套接字的網路位址:計算機名稱(如"ftp.microsoft.com")或虛線數位(如"128.56.22.8")。

*nFlags*<br/>
指定調用的方式。 此函數的語義由套接字選項和*nFlags*參數決定。 後者是通過將以下任一值與C++ **OR**運算子組合而成的:

- MSG_DONTROUTE 指定數據不應受路由約束。 Windows 套接字供應商可以選擇忽略此標誌。

- MSG_OOB發送帶外數據(僅限SOCK_STREAM)。

*lpSockAddr*<br/>
指向包含目標套接字位址的[SOCKADDR](/windows/win32/winsock/sockaddr-2)結構的指標。

*恩索克·阿德爾倫*<br/>
以*lpSockAddr(* 以位元組為單位)的位址長度。

### <a name="return-value"></a>傳回值

如果未發生錯誤,`SendTo`則傳回發送的字元總數。 (請注意,這可能小於*nBufLen*指示的數位。否則,將返回SOCKET_ERROR值,並且可以通過調用[GetLastError](#getlasterror)來檢索特定的錯誤代碼。 以下錯誤適用於此成員函數:

- 在使用此 API 之前,必須成功進行[Afxsocketinit。](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Windows 套接字實現檢測到網路子系統失敗。

- WSAEACCES 請求的位址是廣播位址,但未設置相應的標誌。

- WSAEINPROGRESS 阻止 Windows 套接字操作正在進行中。

- wsAEFAULT *lpBuf*或*lpSockAddr*參數不是使用者位址空間的一部分,或者*lpSockAddr*參數太小(小於[SOCKADDR](/windows/win32/winsock/sockaddr-2)結構的大小)。

- WSAEINVAL 主機名無效。

- 必須重置連接,因為 Windows 套接字實現將其丟棄。

- WSAENOBUFS Windows 套接字實現報告緩衝區死鎖。

- WSAENOTCONN 插座未連接(僅SOCK_STREAM)。

- WSANotSOCK 描述符不是套接字。

- 已指定 WSAOpNOTSUPp MSG_OOB,但套接字不是類型SOCK_STREAM。

- WSAE關閉 插座已關閉;在使用*nHow*`SendTo`設置`ShutDown`為 1 或 2 調用後,無法調用套接字。

- WSAEANDBLOCK 套接字標記為非阻塞,請求的操作將阻塞。

- WSAEMSGSIZE 套接字的類型為SOCK_DGRAM,並且數據報比 Windows 套接字實現支援的最大值要大。

- WSAECONABORTED 虛擬電路由於超時或其他故障而中止。

- WSAECONNRESET 虛擬電路被遠端端重置。

- WSAEADDRNOTA 指定位址不在本地電腦中。

- 指定族中的 WSAEAFNOSUPPORT 位址不能與此套接字一起使用。

- 需要位址。

- 此時無法從此主機到達網路。

### <a name="remarks"></a>備註

`SendTo`用於數據報或流套接字,用於在套接字上寫入傳出數據。 對於數據圖套接字,必須注意不要超過基礎子網的最大 IP 數據包大小,這是由[由 AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)填寫的`iMaxUdpDg`[WSADATA](/windows/win32/api/winsock2/ns-winsock2-wsadata)結構中 的元素給出的。 如果數據太長,無法通過基礎協定以原子方式傳遞,則返回錯誤 WSAEMSGSIZE,並且不會傳輸任何數據。

請注意,成功完成`SendTo`的並不表示數據已成功傳遞。

`SendTo`僅用於SOCK_DGRAM套接字,將數據報發送到*lpSockAddr*參數標識的特定套接字。

要發送廣播(僅在SOCK_DGRAM),應使用特殊 IP 位址INADDR_BROADCAST(在 Windows 套接字頭檔 WINSOCK 中定義)構造*lpSockAddr*參數中的位址。H) 連同預期的埠號。 或者,如果*lpszHost 位址*參數為 NULL,則配置套接字用於廣播。 通常不建議廣播數據報超過發生碎片的大小,這意味著數據報(不包括標頭)的數據部分不應超過 512 位元組。

要處理 IPv6 位址,請使用[CAsyncSocket::SendToEx](#sendtoex)。

## <a name="casyncsocketsendtoex"></a><a name="sendtoex"></a>同步通訊::寄件

呼叫此成員函數將資料發送到特定目標(處理IPv6位址)。

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
包含要傳輸的數據的緩衝區。

*恩布夫倫*<br/>
以*lpBuf(* 以位元組為單位)的數據長度。

*nHostPort*<br/>
標識套接字應用程式的埠。

*lpszHost 位址*<br/>
此物件連接到的套接字的網路位址:計算機名稱(如"ftp.microsoft.com")或虛線數位(如"128.56.22.8")。

*nFlags*<br/>
指定調用的方式。 此函數的語義由套接字選項和*nFlags*參數決定。 後者是通過將以下任一值與C++ **OR**運算子組合而成的:

- MSG_DONTROUTE 指定數據不應受路由約束。 Windows 套接字供應商可以選擇忽略此標誌。

- MSG_OOB發送帶外數據(僅限SOCK_STREAM)。

### <a name="return-value"></a>傳回值

如果未發生錯誤,`SendToEx`則傳回發送的字元總數。 (請注意,這可能小於*nBufLen*指示的數位。否則,將返回SOCKET_ERROR值,並且可以通過調用[GetLastError](#getlasterror)來檢索特定的錯誤代碼。 以下錯誤適用於此成員函數:

- 在使用此 API 之前,必須成功進行[Afxsocketinit。](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Windows 套接字實現檢測到網路子系統失敗。

- WSAEACCES 請求的位址是廣播位址,但未設置相應的標誌。

- WSAEINPROGRESS 阻止 Windows 套接字操作正在進行中。

- wsAEFAULT *lpBuf*或*lpSockAddr*參數不是使用者位址空間的一部分,或者*lpSockAddr*參數太小(小於[SOCKADDR](/windows/win32/winsock/sockaddr-2)結構的大小)。

- WSAEINVAL 主機名無效。

- 必須重置連接,因為 Windows 套接字實現將其丟棄。

- WSAENOBUFS Windows 套接字實現報告緩衝區死鎖。

- WSAENOTCONN 插座未連接(僅SOCK_STREAM)。

- WSANotSOCK 描述符不是套接字。

- 已指定 WSAOpNOTSUPp MSG_OOB,但套接字不是類型SOCK_STREAM。

- WSAE關閉 插座已關閉;在使用*nHow*`SendToEx`設置`ShutDown`為 1 或 2 調用後,無法調用套接字。

- WSAEANDBLOCK 套接字標記為非阻塞,請求的操作將阻塞。

- WSAEMSGSIZE 套接字的類型為SOCK_DGRAM,並且數據報比 Windows 套接字實現支援的最大值要大。

- WSAECONABORTED 虛擬電路由於超時或其他故障而中止。

- WSAECONNRESET 虛擬電路被遠端端重置。

- WSAEADDRNOTA 指定位址不在本地電腦中。

- 指定族中的 WSAEAFNOSUPPORT 位址不能與此套接字一起使用。

- 需要位址。

- 此時無法從此主機到達網路。

### <a name="remarks"></a>備註

此方法與[CAsyncSocket::SendTo](#sendto)相同,只不過它處理 IPv6 位址以及較舊的協定。

`SendToEx`用於數據報或流套接字,用於在套接字上寫入傳出數據。 對於數據圖套接字,必須注意不要超過基礎子網的最大 IP 數據包大小,這是由[由 AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)填寫的`iMaxUdpDg`[WSADATA](/windows/win32/api/winsock2/ns-winsock2-wsadata)結構中 的元素給出的。 如果數據太長,無法通過基礎協定以原子方式傳遞,則返回錯誤 WSAEMSGSIZE,並且不會傳輸任何數據。

請注意,成功完成`SendToEx`的並不表示數據已成功傳遞。

`SendToEx`僅用於SOCK_DGRAM套接字,將數據報發送到*lpSockAddr*參數標識的特定套接字。

要發送廣播(僅在SOCK_DGRAM),應使用特殊 IP 位址INADDR_BROADCAST(在 Windows 套接字頭檔 WINSOCK 中定義)構造*lpSockAddr*參數中的位址。H) 連同預期的埠號。 或者,如果*lpszHost 位址*參數為 NULL,則配置套接字用於廣播。 通常不建議廣播數據報超過發生碎片的大小,這意味著數據報(不包括標頭)的數據部分不應超過 512 位元組。

## <a name="casyncsocketsetsockopt"></a><a name="setsockopt"></a>CAsyncSocket:setSockOpt

調用此成員函數以設置套接字選項。

```
BOOL SetSockOpt(
    int nOptionName,
    const void* lpOptionValue,
    int nOptionLen,
    int nLevel = SOL_SOCKET);
```

### <a name="parameters"></a>參數

*nOption名稱*<br/>
要為其設置值的套接字選項。

*lpOption值*<br/>
指向提供所請求選項的值的緩衝區的指標。

*nOptionLen*<br/>
*lpOptionValue*緩衝區的大小(以位元組為單位)。

*n 等級*<br/>
定義選項的級別;唯一支持的級別是SOL_SOCKET和IPPROTO_TCP。

### <a name="return-value"></a>傳回值

如果函數成功,則非零;否則 0,可以通過調用[GetLastError](#getlasterror)來檢索特定的錯誤代碼。 以下錯誤適用於此成員函數:

- 在使用此 API 之前,必須成功進行[Afxsocketinit。](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Windows 套接字實現檢測到網路子系統失敗。

- WSAEFAULT *lpOptionValue*不在行程位址空間的有效部分。

- WSAEINPROGRESS 阻止 Windows 套接字操作正在進行中。

- WSAEINVAL *nLevel*無效,或者*lpOptionValue*中的資訊無效。

- 設置SO_KEEPALIVE時,WSAENETRESET 連接已超時。

- WSAENOPROTOOPT 選項未知或不受支援。 特別是,SOCK_STREAM類型的套接字不支援SO_BROADCAST,而SOCK_DGRAM類型的套接字不支援SO_DONTLINGER、SO_KEEPALIVE、SO_LINGER和SO_OOBINLINE。

- 設置SO_KEEPALIVE時,已重置 WSANOTCONN 連接。

- WSANotSOCK 描述符不是套接字。

### <a name="remarks"></a>備註

`SetSockOpt`設置與任何類型、任何類型的套接字關聯的套接字選項的當前值。 儘管選項可以存在於多個協定級別,但此規範僅定義存在於最上層"套接字"級別的選項。 選項會影響套接字操作,例如在正常數據流中是否接收加急數據、是否可以在套接字上發送廣播訊息等。

有兩種類型的套接字選項:啟用或禁用特徵或行為的布爾選項,以及需要整數值或結構的選項。 要啟用布林選項 *,lpOptionValue*指向非零整數。 要關閉選項*lpOptionValue,* 請指向等於零的整數。 *nOptionLen*應等`sizeof(BOOL)`於 布爾選項。 對於其他選項 *,lpOptionValue*指向包含該選項所需值的整數或結構 *,nOptionLen*是整數或結構的長度。

SO_LINGER控制在套接字上排隊時執行的操作,`Close`並且調用函數關閉套接字。

默認情況下,無法將套接字綁定(請參閱[綁定](#bind)) 綁定到已在使用的本地位址。 但是,有時最好以這種方式"重用"位址。 由於每個連接都由本地地址和遠端位址的組合唯一標識,因此只要遠端位址不同,將兩個套接字綁定到同一本地位址是沒有問題的。

要通知 Windows 套接`Bind`字實現 ,不應禁止對套接字進行調用,因為其他套接字已在使用所需的位址,應用程式`Bind`應在發出 呼叫之前為套接字設置SO_REUSEADDR套接字選項。 請注意,該選項僅在`Bind`調用時進行解釋:因此,沒有必要(但無害)在未綁定到現有位址的套接字上設置該選項,並在`Bind`調用后設置或重置該選項對此或任何其他套接字沒有影響。

應用程式可以通過打開SO_KEEPALIVE套接字選項請求 Windows 套接字實現啟用傳輸控制協定 (TCP) 連接上的"保持活動"數據包。 Windows 套接字實現不需要支援使用保持-生命:如果是,則精確的語義是特定於實現的,但應符合 RFC 1122 的第 4.2.3.6 節:「Internet 主機的要求 - 通信層」。。 如果由於"保持"而斷開連接,錯誤代碼 WSAENETRESET 將返回到套接字上正在進行的任何調用,並且任何後續調用都將在 WSAENOTCONN 中失敗。

TCP_NODELAY選項禁用 Nagle 演演演算法。 Nagle 演演算法用於透過緩衝未確認的發送資料,直到發送全尺寸資料包來減少主機發送的小資料包數。 但是,對於某些應用程式,此演演演算法可能會妨礙性能,並且TCP_NODELAY可用於將其關閉。 應用程式編寫器不應設置TCP_NODELAY除非對這樣做的影響是廣為人知和想要的,因為設置TCP_NODELAY會對網路性能產生重大的負面影響。 TCP_NODELAY是唯一受支援的套接字選項,它使用級別IPPROTO_TCP;所有其他選項使用級別SOL_SOCKET。

如果SO_DEBUG選項由應用程式設置,則 Windows 套接字的某些實現提供輸出調試資訊。

支援以下選項。 `SetSockOpt` 類型標識*lpOptionValue*定址的數據類型。

|值|類型|意義|
|-----------|----------|-------------|
|SO_BROADCAST|BOOL|允許在套接字上傳輸廣播消息。|
|SO_DEBUG|BOOL|記錄偵錯資訊。|
|SO_DONTLINGER|BOOL|不要阻止`Close`等待發送未發送的數據。 設置此選項等效於將SO_LINGER`l_onoff`設置為零。|
|SO_DONTROUTE|BOOL|不要路由:直接發送到介面。|
|SO_KEEPALIVE|BOOL|發送保持生命。|
|SO_LINGER|`struct LINGER`|`Close`如果存在未發送的數據。|
|SO_OOBINLINE|BOOL|在正常數據流中接收帶外數據。|
|SO_RCVBUF|**int**|指定接收的緩衝區大小。|
|SO_REUSEADDR|BOOL|允許將套接字綁定到已使用的位址。 (請參閱[繫結](#bind)。)|
|SO_SNDBUF|**int**|為發送指定緩衝區大小。|
|TCP_NODELAY|BOOL|停用用於傳送聯合的 Nagle 演算法。|

Bake 模式 (BSD) 選項不支援`SetSockOpt`:

|值|類型|意義|
|-----------|----------|-------------|
|SO_ACCEPTCONN|BOOL|通訊端字正在偵聽|
|SO_ERROR|**int**|獲取錯誤狀態並清除。|
|SO_RCVLOWAT|**int**|接收低水位線。|
|SO_RCVTIMEO|**int**|接收逾時|
|SO_SNDLOWAT|**int**|發送低水位線。|
|SO_SNDTIMEO|**int**|發送超時。|
|SO_TYPE|**int**|套接字的類型。|
|IP_OPTIONS||在 IP 標頭中設定選項欄位。|

## <a name="casyncsocketshutdown"></a><a name="shutdown"></a>同步通訊::關閉

調用此成員函數以禁用套接字上的發送、接收或兩者。

```
BOOL ShutDown(int nHow = sends);
```

### <a name="parameters"></a>參數

*n 如何*<br/>
使用以下枚舉值描述不再允許的操作類型的標誌:

- **接收 = 0**

- **傳送 = 1**

- **兩者 = 2**

### <a name="return-value"></a>傳回值

如果函數成功,則非零;否則 0,可以通過調用[GetLastError](#getlasterror)來檢索特定的錯誤代碼。 以下錯誤適用於此成員函數:

- 在使用此 API 之前,必須成功進行[Afxsocketinit。](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Windows 套接字實現檢測到網路子系統失敗。

- WSAEINVAL *nHow*無效。

- WSAEINPROGRESS 阻止 Windows 套接字操作正在進行中。

- WSAENOTCONN 插座未連接(僅SOCK_STREAM)。

- WSANotSOCK 描述符不是套接字。

### <a name="remarks"></a>備註

`ShutDown`用於所有類型的插座,以禁用接收、傳輸或兩者。 如果*nHow*為 0,則不允許在套接字上後續接收。 這對下級協議層沒有影響。

對於傳輸控制協定 (TCP),TCP 視窗不會更改,在視窗用盡之前將接受(但未確認)傳入數據。 對於用戶數據圖協定 (UDP),接受傳入的圖和排隊。 在任何情況下,也不會生成ICMP錯誤資料包。 如果*nHow*是 1,則不允許後續發送。 對於 TCP 套接字,將發送 FIN。 按照上述方式將 nHow 設置為 *"2"* 將禁用發送和接收。

請注意,`ShutDown`不會關閉套接字,並且在調用`Close`之前 不會釋放附加到套接字的資源。 應用程式不應依賴於在關閉套接字后能夠重用它。 特別是,不需要 Windows 套接字實現來支援在此類套`Connect`接字 上使用。

### <a name="example"></a>範例

  請參閱[CAsyncSocket 的範例::開啟接收](#onreceive)。

## <a name="casyncsocketsocket"></a><a name="socket"></a>卡同步插槽::套接字

分配套接字句柄。

```
BOOL Socket(
    int nSocketType = SOCK_STREAM,
    long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE,
    int nProtocolType = 0,
    int nAddressFormat = PF_INET);
```

### <a name="parameters"></a>參數

*nSocket 類型*<br/>
指定`SOCK_STREAM``SOCK_DGRAM`或 。

*lEvent*<br/>
指定應用程式感興趣的網路事件組合的位掩碼。

- `FD_READ`:要收到準備閱讀的通知。

- `FD_WRITE`:要收到準備寫作的通知。

- `FD_OOB`:要接收帶外數據到達的通知。

- `FD_ACCEPT`:要接收傳入連接的通知。

- `FD_CONNECT`:要接收已完成連接的通知。

- `FD_CLOSE`:要接收套接字關閉通知。

*n 協定類型*<br/>
與特定於指示的位址族的套接字一起使用的協定。

*n 位址格式*<br/>
地址系列規範。

### <a name="return-value"></a>傳回值

成功時傳回 `TRUE`，失敗時則傳回 `FALSE`。

### <a name="remarks"></a>備註

此方法分配套接字句柄。 它不調用[CAsyncSocket::綁定](#bind)以將套接字綁定到指定的位址,因此您需要稍後`Bind`調用 以將套接字綁定到指定的位址。 您可以使用[CAsyncSocket:setSockOpt](#setsockopt)在綁定之前設定套接字選項。

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CSocket 類別](../../mfc/reference/csocket-class.md)<br/>
[CSocketFile 類別](../../mfc/reference/csocketfile-class.md)
