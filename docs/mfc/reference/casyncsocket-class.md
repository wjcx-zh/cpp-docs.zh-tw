---
title: CAsyncSocket 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7c98703cbe68efc0ca7e40d3b25d0178d826855a
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2018
ms.locfileid: "36952602"
---
# <a name="casyncsocket-class"></a>CAsyncSocket 類別
表示 Windows Socket — 網路通訊的端點。  
  
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
|[CAsyncSocket::Accept](#accept)|接受通訊端上的連接。|  
|[CAsyncSocket::AsyncSelect](#asyncselect)|通訊端要求事件通知。|  
|[CAsyncSocket::Attach](#attach)|將附加的通訊端控制代碼`CAsyncSocket`物件。|  
|[CAsyncSocket::Bind](#bind)|將本機位址與通訊端產生關聯。|  
|[CAsyncSocket::Close](#close)|會關閉通訊端。|  
|[CAsyncSocket::Connect](#connect)|建立對等通訊端連線。|  
|[CAsyncSocket::Create](#create)|建立通訊端。|  
|[CAsyncSocket::Detach](#detach)|中斷連結的通訊端控制代碼，從`CAsyncSocket`物件。|  
|[CAsyncSocket::FromHandle](#fromhandle)|將指標傳回至`CAsyncSocket`物件，指定的通訊端控制代碼。|  
|[CAsyncSocket::GetLastError](#getlasterror)|取得上次作業失敗，錯誤狀態。|  
|[CAsyncSocket::GetPeerName](#getpeername)|取得通訊端所連接之對等通訊端位址。|  
|[CAsyncSocket::GetPeerNameEx](#getpeernameex)|取得通訊端是連接 （控點 IPv6 位址） 的對等通訊端位址。|  
|[CAsyncSocket::GetSockName](#getsockname)|取得通訊端的本機名稱。|  
|[CAsyncSocket::GetSockNameEx](#getsocknameex)|取得通訊端 （控點 IPv6 位址） 的本機名稱。|  
|[CAsyncSocket::GetSockOpt](#getsockopt)|擷取通訊端選項。|  
|[CAsyncSocket::IOCtl](#ioctl)|控制模式通訊端。|  
|[CAsyncSocket::Listen](#listen)|建立通訊端接聽內送連接要求。|  
|[CAsyncSocket::Receive](#receive)|從通訊端接收資料。|  
|[CAsyncSocket::ReceiveFrom](#receivefrom)|會接收資料包並儲存來源位址。|  
|[CAsyncSocket::ReceiveFromEx](#receivefromex)|會接收資料包並儲存來源位址 （也就是控制代碼的 IPv6 位址）。|  
|[CAsyncSocket::Send](#send)|將資料傳送到已連線的通訊端。|  
|[CAsyncSocket::SendTo](#sendto)|將資料傳送到特定的目的地。|  
|[CAsyncSocket::SendToEx](#sendtoex)|將資料傳送到特定的目的地 （控點 IPv6 位址）。|  
|[CAsyncSocket::SetSockOpt](#setsockopt)|設定通訊端選項。|  
|[CAsyncSocket::ShutDown](#shutdown)|停用`Send`及/或`Receive`通訊端上呼叫。|  
|[CASyncSocket::Socket](#socket)|配置通訊端控制代碼。|  
  
### <a name="protected-methods"></a>保護方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CAsyncSocket::OnAccept](#onaccept)|通知接聽的通訊端，其可接受暫止的連接要求，藉由呼叫`Accept`。|  
|[CAsyncSocket::OnClose](#onclose)|告知通訊端通訊端連接到它已關閉。|  
|[CAsyncSocket::OnConnect](#onconnect)|通知連接的通訊端，連線嘗試已完成，是否成功或錯誤。|  
|[CAsyncSocket::OnOutOfBandData](#onoutofbanddata)|沒有要讀取通訊端，通常緊急郵件上的頻外資料通知接收通訊端。|  
|[CAsyncSocket::OnReceive](#onreceive)|通知接聽通訊端沒有資料可以藉由呼叫擷取`Receive`。|  
|[CAsyncSocket::OnSend](#onsend)|它可以將資料傳送藉由呼叫會告知通訊端`Send`。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CAsyncSocket::operator =](#operator_eq)|指派新值`CAsyncSocket`物件。|  
|[CAsyncSocket::operator 通訊端](#operator_socket)|使用此運算子來擷取**通訊端**控點`CAsyncSocket`物件。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CAsyncSocket::m_hSocket](#m_hsocket)|指出**通訊端**控制代碼附加至此`CAsyncSocket`物件。|  
  
## <a name="remarks"></a>備註  
 類別`CAsyncSocket`封裝 Windows 通訊端函式 API，提供物件導向的抽象的程式設計人員想要使用搭配 MFC Windows Sockets。  
  
 這個類別為基礎的假設您已了解網路通訊。 您必須負責處理封鎖，位元組順序的差異，並在 Unicode 和多位元組字元轉換設定 (MBCS) 字串。 如果您想更方便的介面，會為您管理這些問題，請參閱類別[CSocket](../../mfc/reference/csocket-class.md)。  
  
 若要使用`CAsyncSocket`物件，呼叫其建構函式，然後呼叫[建立](#create)函式來建立基礎通訊端控制代碼 (型別`SOCKET`)，但不接受通訊端。 針對伺服器通訊端呼叫[接聽](#listen)成員函式，以及用戶端通訊端呼叫[連接](#connect)成員函式。 伺服器通訊端應該呼叫[接受](#accept)接收連線要求時的函式。 使用其餘`CAsyncSocket`函式，以實現通訊端之間的通訊。 完成時，摧毀`CAsyncSocket`物件是在堆積上建立; 解構函式自動呼叫[關閉](#close)函式。 **通訊端**資料類型文件中所述[Windows Sockets： 背景](../../mfc/windows-sockets-background.md)。  
  
> [!NOTE]
>  當使用靜態連結的 MFC 應用程式中的次要執行緒中的 MFC 通訊端，您必須呼叫`AfxSocketInit`中使用通訊端初始化通訊端程式庫的每個執行緒。 根據預設，`AfxSocketInit`只能在主執行緒中呼叫。  
  
 如需詳細資訊，請參閱[Windows Sockets： 使用類別 CAsyncSocket](../../mfc/windows-sockets-using-class-casyncsocket.md)和相關文章。 以及[Windows Sockets 2 API](http://msdn.microsoft.com/library/windows/desktop/ms740673)。  
  
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
 *rConnectedSocket*  
 參考，識別新的通訊端，可供連線。  
  
 *lpSockAddr*  
 指標[SOCKADDR](../../mfc/reference/sockaddr-structure.md)接收的連接位址的結構通訊端，因為知道網路上。 正確格式*lpSockAddr*引數取決於建立時建立通訊端位址系列。 如果*lpSockAddr*及/或*lpSockAddrLen*等於**NULL**，則會不傳回遠端位址接受通訊端的任何資訊。  
  
 *lpSockAddrLen*  
 中的位址長度的指標*lpSockAddr*以位元組為單位。 *LpSockAddrLen*是值結果參數： 一開始應該包含所指向的空間數量*lpSockAddr*; 在傳回時，它會包含傳回的位址的實際長度 （以位元組為單位）。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功，則為非零否則為 0，並傳回特定的錯誤碼可以擷取藉由呼叫[GetLastError](#getlasterror)。 此成員函式適用於下列錯誤：  
  
- **WSANOTINITIALISED**成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必須先使用此 API。  
  
- **WSAENETDOWN**網路子系統無法偵測到的 Windows Sockets 實作。  
  
- **WSAEFAULT** *lpSockAddrLen*引數是太小 (的大小大於或等於[SOCKADDR](../../mfc/reference/sockaddr-structure.md)結構)。  
  
- **WSAEINPROGRESS**封鎖 Windows Sockets 呼叫正在進行中。  
  
- **WSAEINVAL** `Listen`未叫用的之前接受。  
  
- **WSAEMFILE**佇列是空的時接受的項目，而且沒有任何描述項可用。  
  
- **WSAENOBUFS**沒有緩衝區空間。  
  
- **WSAENOTSOCK**描述項不是通訊端。  
  
- **WSAEOPNOTSUPP**參考之通訊端不是支援連線導向的服務類型。  
  
- **WSAEWOULDBLOCK**通訊端已標示為封鎖且所有連接都都會存在，才能被接受。  
  
### <a name="remarks"></a>備註  
 這個常式會擷取第一個佇列中的擱置連線連接、 建立新的通訊端使用相同的屬性，為這個通訊端，和將其附加至*rConnectedSocket*。 如果沒有擱置中的連線會出現在佇列上`Accept`傳回零和`GetLastError`會傳回錯誤。 接受通訊端 ( *rConnectedSocket)* 無法用來接受更多的連線。 開啟並在接聽，則會保留原始通訊端。  
  
 引數*lpSockAddr*已知通訊層時連接的通訊端，位址會填入結果參數。 `Accept` 這類的使用與連線為基礎的通訊端型別**SOCK_STREAM**。  
  
##  <a name="asyncselect"></a>  CAsyncSocket::AsyncSelect  
 呼叫此成員函式可要求通訊端的事件通知。  
  
```  
BOOL AsyncSelect(long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```  
  
### <a name="parameters"></a>參數  
 *lEvent*  
 位元遮罩指定的網路應用程式有興趣的事件組合。  
  
- **FD_READ**要接收通知的整備進行讀取。  
  
- **FD_WRITE**想要可供讀取資料時收到通知。  
  
- **FD_OOB**想要接收通知的頻外資料抵達。  
  
- **FD_ACCEPT**要接收通知的連入連線。  
  
- **FD_CONNECT**要接收通知的連接結果。  
  
- **FD_CLOSE**想要對等體已關閉通訊端時收到通知。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功，則為非零否則為 0，並傳回特定的錯誤碼可以擷取藉由呼叫[GetLastError](#getlasterror)。 此成員函式適用於下列錯誤：  
  
- **WSANOTINITIALISED**成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必須先使用此 API。  
  
- **WSAENETDOWN**網路子系統無法偵測到的 Windows Sockets 實作。  
  
- **WSAEINVAL**指出其中一個指定的參數無效。  
  
- **WSAEINPROGRESS**封鎖 Windows 通訊端作業正在進行中。  
  
### <a name="remarks"></a>備註  
 此函式用來指定哪些 MFC 回呼通知函式會呼叫通訊端。 `AsyncSelect` 自動將此通訊端設定為封鎖模式。 如需詳細資訊，請參閱文章[Windows Sockets： 通訊端告知](../../mfc/windows-sockets-socket-notifications.md)。  
  
##  <a name="attach"></a>  CAsyncSocket::Attach  
 呼叫此成員函式附加*hSocket*的控制代碼`CAsyncSocket`物件。  
  
```  
BOOL Attach(
    SOCKET hSocket, long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```  
  
### <a name="parameters"></a>參數  
 *hSocket*  
 包含通訊端的控制代碼。  
  
 *lEvent*  
 位元遮罩指定的網路應用程式有興趣的事件組合。  
  
- **FD_READ**要接收通知的整備進行讀取。  
  
- **FD_WRITE**想要可供讀取資料時收到通知。  
  
- **FD_OOB**想要接收通知的頻外資料抵達。  
  
- **FD_ACCEPT**要接收通知的連入連線。  
  
- **FD_CONNECT**要接收通知的連接結果。  
  
- **FD_CLOSE**想要對等體已關閉通訊端時收到通知。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功，則為非零。  
  
### <a name="remarks"></a>備註  
 **通訊端**控制代碼會儲存在物件的[m_hSocket](#m_hsocket)資料成員。  
  
##  <a name="bind"></a>  CAsyncSocket::Bind  
 呼叫此成員函式，使本機位址與通訊端。  
  
```  
BOOL Bind(
    UINT nSocketPort,  
    LPCTSTR lpszSocketAddress = NULL);

 
BOOL Bind (
    const SOCKADDR* lpSockAddr,  
    int nSockAddrLen);
```  
  
### <a name="parameters"></a>參數  
 *nSocketPort*  
 識別通訊端應用程式連接埠。  
  
 *lpszSocketAddress*  
 網路位址時，小數點的數字，例如"128.56.22.8"。 傳遞**NULL**此參數表示的字串`CAsyncSocket`應接聽所有網路介面上的用戶端活動的執行個體。  
  
 *lpSockAddr*  
 指標[SOCKADDR](../../mfc/reference/sockaddr-structure.md)結構，其中包含要指派給此通訊端位址。  
  
 *nSockAddrLen*  
 中的位址長度*lpSockAddr*以位元組為單位。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功，則為非零否則為 0，並傳回特定的錯誤碼可以擷取藉由呼叫[GetLastError](#getlasterror)。 此成員函式適用於下列錯誤：  
  
- **WSANOTINITIALISED**成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必須先使用此 API。  
  
- **WSAENETDOWN**網路子系統無法偵測到的 Windows Sockets 實作。  
  
- **WSAEADDRINUSE**指定的位址已在使用。 (請參閱**SO_REUSEADDR**通訊端選項底下[SetSockOpt](#setsockopt)。)  
  
- **WSAEFAULT** *nSockAddrLen*引數是太小 (的大小大於或等於[SOCKADDR](../../mfc/reference/sockaddr-structure.md)結構)。  
  
- **WSAEINPROGRESS**封鎖 Windows Sockets 呼叫正在進行中。  
  
- **WSAEAFNOSUPPORT**此連接埠不支援指定的位址系列。  
  
- **WSAEINVAL**通訊端已經繫結至地址。  
  
- **WSAENOBUFS**沒有足夠可用的緩衝區、 太多的連線。  
  
- **WSAENOTSOCK**描述項不是通訊端。  
  
### <a name="remarks"></a>備註  
 這個常式會先用在未連接的資料流或資料流通訊端，後續`Connect`或`Listen`呼叫。 它可以接受連線要求之前，接聽伺服器通訊端必須選取一個連接埠號碼並設為已知 Windows 通訊端藉由呼叫`Bind`。 `Bind` 將本機名稱指派給未命名的通訊端，以建立通訊端的本機關聯 （主機位址/連接埠號碼）。  
  
##  <a name="casyncsocket"></a>  CAsyncSocket::CAsyncSocket  
 建構空白通訊端物件。  
  
```  
CAsyncSocket();
```  
  
### <a name="remarks"></a>備註  
 之後建構物件，您必須呼叫其`Create`成員函式來建立**通訊端**資料結構，並將其位址的繫結。 (在伺服器端的 Windows Sockets 通訊，接聽的通訊端建立要在中使用的通訊端時`Accept`呼叫時，您不會呼叫`Create`該通訊端。)  
  
##  <a name="close"></a>  CAsyncSocket::Close  
 會關閉通訊端。  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>備註  
 此函式會釋放通訊端描述項，以便進一步參考將會失敗並出現錯誤**WSAENOTSOCK**。 如果這是基礎通訊端的最後一個參考，會捨棄相關聯的名稱資訊和佇列的資料。 通訊端物件的解構函式呼叫`Close`您。  
  
 如`CAsyncSocket`，但不適用於`CSocket`的語意`Close`受到通訊端選項**SO_LINGER**和**SO_DONTLINGER**。 如需詳細資訊，請參閱成員函式`GetSockOpt`。  
  
##  <a name="connect"></a>  CAsyncSocket::Connect  
 呼叫此成員函式建立的未連接的資料流或資料包通訊端的連接。  
  
```  
BOOL Connect(
    LPCTSTR lpszHostAddress,  
    UINT nHostPort);

 
BOOL Connect(
    const SOCKADDR* lpSockAddr,  
    int nSockAddrLen);
```  
  
### <a name="parameters"></a>參數  
 *lpszHostAddress*  
 這個物件所連接的通訊端的網路位址： 電腦名稱，例如"ftp.microsoft.com"或小數點的數字，例如"128.56.22.8"。  
  
 *nHostPort*  
 識別通訊端應用程式連接埠。  
  
 *lpSockAddr*  
 指標[SOCKADDR](../../mfc/reference/sockaddr-structure.md)結構，其中包含連接的通訊端位址。  
  
 *nSockAddrLen*  
 中的位址長度*lpSockAddr*以位元組為單位。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功，則為非零否則為 0，並傳回特定的錯誤碼可以擷取藉由呼叫[GetLastError](#getlasterror)。 如果這表示錯誤碼**WSAEWOULDBLOCK**，且您的應用程式使用的可覆寫的回呼，您的應用程式將會收到`OnConnect`連線作業完成時的訊息。 此成員函式適用於下列錯誤：  
  
- **WSANOTINITIALISED**成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必須先使用此 API。  
  
- **WSAENETDOWN**網路子系統無法偵測到的 Windows Sockets 實作。  
  
- **WSAEADDRINUSE**指定的位址已在使用。  
  
- **WSAEINPROGRESS**封鎖 Windows Sockets 呼叫正在進行中。  
  
- **WSAEADDRNOTAVAIL**指定的位址不是可從本機電腦。  
  
- **WSAEAFNOSUPPORT**指定系列中的位址不能使用此通訊端。  
  
- **WSAECONNREFUSED** ，所以拒絕連線嘗試。  
  
- **WSAEDESTADDRREQ**目的地位址是必要項。  
  
- **WSAEFAULT** *nSockAddrLen*引數不正確。  
  
- **WSAEINVAL**不正確的主機位址。  
  
- **WSAEISCONN**通訊端已連線。  
  
- **WSAEMFILE**沒有更多檔案描述項可用。  
  
- **WSAENETUNREACH**無法透過此主機連接網路，這一次。  
  
- **WSAENOBUFS**沒有緩衝區空間。 無法連線通訊端。  
  
- **WSAENOTSOCK**描述項不是通訊端。  
  
- **WSAETIMEDOUT**嘗試連線逾時，而不必建立連線。  
  
- **WSAEWOULDBLOCK**通訊端已標示為封鎖而且無法立即完成連線。  
  
### <a name="remarks"></a>備註  
 如果解除繫結通訊端時，唯一的值由系統指派給本機關聯通訊端標示為繫結。 請注意，如果名稱結構的地址欄位是全部為零，`Connect`會傳回零。 若要取得延伸錯誤資訊，請呼叫`GetLastError`成員函式。  
  
 資料流通訊端 (型別**SOCK_STREAM**)，起始的作用中連接至外部的主機。 通訊端呼叫成功完成時，通訊端已傳送/接收資料。  
  
 資料包通訊端 (型別**SOCK_DGRAM**)，設定預設的目的地，這將用於後續`Send`和`Receive`呼叫。  
  
##  <a name="create"></a>  CAsyncSocket::Create  
 呼叫`Create`之後建構建立 Windows 通訊端，並將其連接的通訊端物件的成員函式。  
  
```  
BOOL Create(
    UINT nSocketPort = 0,  
    int nSocketType = SOCK_STREAM,  
    long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE,  
    LPCTSTR lpszSocketAddress = NULL);
```  
  
### <a name="parameters"></a>參數  
 *nSocketPort*  
 若要使用通訊端，或 0，如果您想要選取連接埠的 Windows Sockets 的已知通訊埠。  
  
 *nSocketType*  
 **SOCK_STREAM**或**SOCK_DGRAM**。  
  
 *lEvent*  
 位元遮罩指定的網路應用程式有興趣的事件組合。  
  
- **FD_READ**要接收通知的整備進行讀取。  
  
- **FD_WRITE**要接收通知的整備進行寫入。  
  
- **FD_OOB**想要接收通知的頻外資料抵達。  
  
- **FD_ACCEPT**要接收通知的連入連線。  
  
- **FD_CONNECT**要接收通知的完整連接。  
  
- **FD_CLOSE**想要接收通訊端關閉相關的通知。  
  
 *lpszSockAddress*  
 包含連接的通訊端，小數點的數字，例如"128.56.22.8 」 的網路位址的字串指標。傳遞**NULL**此參數表示的字串**CAsyncSocket**應接聽所有網路介面上的用戶端活動的執行個體。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功，則為非零否則為 0，並傳回特定的錯誤碼可以擷取藉由呼叫[GetLastError](#getlasterror)。 此成員函式適用於下列錯誤：  
  
- **WSANOTINITIALISED**成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必須先使用此 API。  
  
- **WSAENETDOWN**網路子系統無法偵測到的 Windows Sockets 實作。  
  
- **WSAEAFNOSUPPORT**不支援指定的位址系列。  
  
- **WSAEINPROGRESS**封鎖 Windows 通訊端作業正在進行中。  
  
- **WSAEMFILE**沒有更多檔案描述項可用。  
  
- **WSAENOBUFS**沒有緩衝區空間。 無法建立通訊端。  
  
- **WSAEPROTONOSUPPORT**不支援指定的連接埠。  
  
- **WSAEPROTOTYPE**指定的連接埠已對這個通訊端錯誤的類型。  
  
- **WSAESOCKTNOSUPPORT**指定的通訊端型別不支援此位址系列。  
  
### <a name="remarks"></a>備註  
 `Create` 呼叫[通訊端](#socket)而且如果成功的話，它會呼叫[繫結](#bind)繫結至指定的位址的通訊端。 支援下列通訊端類型：  
  
- **SOCK_STREAM**排序，提供可靠、 全雙工、 連線基礎位元組資料流。 針對網際網路位址家族，會使用傳輸控制通訊協定 (TCP)。  
  
- **SOCK_DGRAM**支援資料流，也就是無連接且不可靠的封包的固定 （通常很短） 的最大長度。 針對網際網路位址家族，會使用使用者資料包通訊協定 (UDP)。  
  
    > [!NOTE]
    >  `Accept`成員函式會採用新的空白參考`CSocket`做為其參數的物件。 您必須先建構這個物件，才能呼叫`Accept`。 請注意，如果這個通訊端物件超出範圍，連接會關閉。 請勿呼叫`Create`對這個新通訊端物件。  
  
> [!IMPORTANT]
> `Create` 是**不**具備執行緒安全。  如果您將會呼叫它多執行緒環境中，就無法叫用同時由不同的執行緒，請務必保護每個呼叫 mutex 或其他同步鎖定。  
  
 如需有關資料流和資料包通訊端的詳細資訊，請參閱文章[Windows Sockets： 背景](../../mfc/windows-sockets-background.md)和[Windows Sockets： 連接埠和通訊端位址](../../mfc/windows-sockets-ports-and-socket-addresses.md)和[Windows Sockets 2 API](http://msdn.microsoft.com/library/windows/desktop/ms740673).  
  
##  <a name="detach"></a>  CAsyncSocket::Detach  
 呼叫此成員函式，要卸離**通訊端**中處理*m_hSocket*資料成員從`CAsyncSocket`物件，並設定*m_hSocket*至**NULL**.  
  
```  
SOCKET Detach();
```  
  
##  <a name="fromhandle"></a>  CAsyncSocket::FromHandle  
 將指標傳回至`CAsyncSocket`物件。  
  
```  
static CAsyncSocket* PASCAL FromHandle(SOCKET hSocket);
```  
  
### <a name="parameters"></a>參數  
 *hSocket*  
 包含通訊端的控制代碼。  
  
### <a name="return-value"></a>傳回值  
 指標`CAsyncSocket`物件，或**NULL**如果沒有任何`CAsyncSocket`物件附加至*hSocket*。  
  
### <a name="remarks"></a>備註  
 當指定時**通訊端**處理，如果`CAsyncSocket`物件沒有附加至控制代碼，則成員函式會傳回**NULL**。  
  
##  <a name="getlasterror"></a>  CAsyncSocket::GetLastError  
 呼叫此成員函式可取得最後一個作業失敗的錯誤狀態。  
  
```  
static int PASCAL GetLastError();
```  
  
### <a name="return-value"></a>傳回值  
 傳回值會指出這個執行緒所執行的最後一個 Windows Sockets API 常式的錯誤碼。  
  
### <a name="remarks"></a>備註  
 當特定成員函式表示，已發生錯誤，`GetLastError`應該呼叫以擷取適當的錯誤程式碼。 請參閱個別成員函式描述清單的適用的錯誤碼。  
  
 如需錯誤碼的詳細資訊，請參閱[Windows Sockets 2 API](http://msdn.microsoft.com/library/windows/desktop/ms740673)。  
  
##  <a name="getpeername"></a>  CAsyncSocket::GetPeerName  
 呼叫此成員函式可取得這個通訊端所連接之對等通訊端位址。  
  
```  
BOOL GetPeerName(
    CString& rPeerAddress,  
    UINT& rPeerPort);

 
BOOL GetPeerName(
    SOCKADDR* lpSockAddr,  
    int* lpSockAddrLen);
```  
  
### <a name="parameters"></a>參數  
 *rPeerAddress*  
 若要參考`CString`接收小數點的數字 IP 位址的物件。  
  
 *rPeerPort*  
 若要參考**UINT**儲存連接埠。  
  
 *lpSockAddr*  
 指標[SOCKADDR](../../mfc/reference/sockaddr-structure.md)接收對等通訊端的名稱的結構。  
  
 *lpSockAddrLen*  
 中的位址長度的指標*lpSockAddr*以位元組為單位。 在傳回時， *lpSockAddrLen*引數中包含的實際大小*lpSockAddr*傳回以位元組為單位。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功，則為非零否則為 0，並傳回特定的錯誤碼可以擷取藉由呼叫[GetLastError](#getlasterror)。 此成員函式適用於下列錯誤：  
  
- **WSANOTINITIALISED**成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必須先使用此 API。  
  
- **WSAENETDOWN**網路子系統無法偵測到的 Windows Sockets 實作。  
  
- **WSAEFAULT** *lpSockAddrLen*引數不足夠。  
  
- **WSAEINPROGRESS**封鎖 Windows Sockets 呼叫正在進行中。  
  
- **WSAENOTCONN**通訊端未連線。  
  
- **WSAENOTSOCK**描述項不是通訊端。  
  
### <a name="remarks"></a>備註  
 若要處理的 IPv6 位址，使用[CAsyncSocket::GetPeerNameEx](#getpeernameex)。  
  
##  <a name="getpeernameex"></a>  CAsyncSocket::GetPeerNameEx  
 呼叫此成員函式可取得這個通訊端是連接 （控點 IPv6 位址） 的對等通訊端位址。  
  
```  
BOOL GetPeerNameEx(
    CString& rPeerAddress,  
    UINT& rPeerPort);
```  
  
### <a name="parameters"></a>參數  
 *rPeerAddress*  
 若要參考`CString`接收小數點的數字 IP 位址的物件。  
  
 *rPeerPort*  
 若要參考**UINT**儲存連接埠。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功，則為非零否則為 0，並傳回特定的錯誤碼可以擷取藉由呼叫[GetLastError](#getlasterror)。 此成員函式適用於下列錯誤：  
  
- **WSANOTINITIALISED**成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必須先使用此 API。  
  
- **WSAENETDOWN**網路子系統無法偵測到的 Windows Sockets 實作。  
  
- **WSAEFAULT** *lpSockAddrLen*引數不足夠。  
  
- **WSAEINPROGRESS**封鎖 Windows Sockets 呼叫正在進行中。  
  
- **WSAENOTCONN**通訊端未連線。  
  
- **WSAENOTSOCK**描述項不是通訊端。  
  
### <a name="remarks"></a>備註  
 此函式是相同[CAsyncSocket::GetPeerName](#getpeername)不同之處在於它會處理 IPv6 位址以及為舊的通訊協定。  
  
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
 *rSocketAddress*  
 若要參考`CString`接收小數點的數字 IP 位址的物件。  
  
 *rSocketPort*  
 若要參考**UINT**儲存連接埠。  
  
 *lpSockAddr*  
 指標[SOCKADDR](../../mfc/reference/sockaddr-structure.md)接收通訊端位址的結構。  
  
 *lpSockAddrLen*  
 中的位址長度的指標*lpSockAddr*以位元組為單位。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功，則為非零否則為 0，並傳回特定的錯誤碼可以擷取藉由呼叫[GetLastError](#getlasterror)。 此成員函式適用於下列錯誤：  
  
- **WSANOTINITIALISED**成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必須先使用此 API。  
  
- **WSAENETDOWN**網路子系統無法偵測到的 Windows Sockets 實作。  
  
- **WSAEFAULT** *lpSockAddrLen*引數不足夠。  
  
- **WSAEINPROGRESS**封鎖 Windows 通訊端作業正在進行中。  
  
- **WSAENOTSOCK**描述項不是通訊端。  
  
- **WSAEINVAL**通訊端已經沒有繫結與位址`Bind`。  
  
### <a name="remarks"></a>備註  
 這個呼叫時特別有用`Connect`已進行呼叫，而這樣做不`Bind`首先; 此呼叫會提供您可以決定這已由系統設定本機關聯的唯一方法。  
  
 若要處理的 IPv6 位址，使用[CAsyncSocket::GetSockNameEx](#getsocknameex)  
  
##  <a name="getsocknameex"></a>  CAsyncSocket::GetSockNameEx  
 呼叫此成員函式，以取得通訊端 （控點 IPv6 位址） 的本機名稱。  
  
```  
BOOL GetSockNameEx(
    CString& rSocketAddress,  
    UINT& rSocketPort);
```  
  
### <a name="parameters"></a>參數  
 *rSocketAddress*  
 若要參考`CString`接收小數點的數字 IP 位址的物件。  
  
 *rSocketPort*  
 若要參考**UINT**儲存連接埠。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功，則為非零否則為 0，並傳回特定的錯誤碼可以擷取藉由呼叫[GetLastError](#getlasterror)。 此成員函式適用於下列錯誤：  
  
- **WSANOTINITIALISED**成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必須先使用此 API。  
  
- **WSAENETDOWN**網路子系統無法偵測到的 Windows Sockets 實作。  
  
- **WSAEFAULT** *lpSockAddrLen*引數不足夠。  
  
- **WSAEINPROGRESS**封鎖 Windows 通訊端作業正在進行中。  
  
- **WSAENOTSOCK**描述項不是通訊端。  
  
- **WSAEINVAL**通訊端已經沒有繫結與位址`Bind`。  
  
### <a name="remarks"></a>備註  
 這個呼叫是相同[CAsyncSocket::GetSockName](#getsockname)不同之處在於它會處理 IPv6 位址以及為舊的通訊協定。  
  
 這個呼叫時特別有用`Connect`已進行呼叫，而這樣做不`Bind`首先; 此呼叫會提供您可以決定這已由系統設定本機關聯的唯一方法。  
  
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
 *nOptionName*  
 要擷取值的通訊端選項。  
  
 *lpOptionValue*  
 要求選項的值會傳回至緩衝區的指標。 選取的選項相關聯的值會傳回緩衝區中*lpOptionValue*。 所指向之整數*lpOptionLen*原本應該包含以位元組為單位; 緩衝區的大小，並在傳回時，它就會設定為傳回值的大小。 如**SO_LINGER**，這是大小的`LINGER`結構; 所有其他選項中，它會需要的大小**BOOL**或**int**，視使用的選項。 請參閱選項及其大小 < 備註 > 一節中的清單。  
  
 *lpOptionLen*  
 大小的指標*lpOptionValue*以位元組為單位的緩衝區。  
  
 *nLevel*  
 層級的定義選項。唯一支援的層級為**SOL_SOCKET**和**IPPROTO_TCP**。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功，則為非零否則為 0，並傳回特定的錯誤碼可以擷取藉由呼叫[GetLastError](#getlasterror)。 如果從未設定選項`SetSockOpt`，然後`GetSockOpt`傳回選項的預設值。 此成員函式適用於下列錯誤：  
  
- **WSANOTINITIALISED**成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必須先使用此 API。  
  
- **WSAENETDOWN**網路子系統無法偵測到的 Windows Sockets 實作。  
  
- **WSAEFAULT** *lpOptionLen*引數無效。  
  
- **WSAEINPROGRESS**封鎖 Windows 通訊端作業正在進行中。  
  
- **WSAENOPROTOOPT**的選項是未知或不受支援。 特別是， **SO_BROADCAST**不支援類型的通訊端**SOCK_STREAM**，雖然**SO_ACCEPTCONN**， **SO_DONTLINGER**， **SO_KEEPALIVE**， **SO_LINGER**，和**SO_OOBINLINE**通訊端的類型上不支援**SOCK_DGRAM**。  
  
- **WSAENOTSOCK**描述項不是通訊端。  
  
### <a name="remarks"></a>備註  
 `GetSockOpt` 擷取相關聯的任何狀態中的任何型別，通訊端通訊端選項的目前值，並且儲存中的結果*lpOptionValue*。 選項會影響通訊端作業，例如路由傳送封包，超出訊號範圍的資料傳輸，以及等等。  
  
 支援下列選項`GetSockOpt`。 型別會識別所定址的資料型別*lpOptionValue*。 **TCP_NODELAY**選項會使用層級**IPPROTO_TCP**; 所有其他選項使用層級**SOL_SOCKET**。  
  
|值|類型|意義|  
|-----------|----------|-------------|  
|**SO_ACCEPTCONN**|**BOOL**|正在接聽通訊端。|  
|**SO_BROADCAST**|**BOOL**|通訊端廣播訊息的傳輸設定。|  
|**SO_DEBUG**|**BOOL**|啟用偵錯。|  
|**SO_DONTLINGER**|**BOOL**|如果為 true， **SO_LINGER**選項已停用。|  
|**SO_DONTROUTE**|**BOOL**|路由會停用。|  
|**SO_ERROR**|**int**|擷取錯誤狀態並清除。|  
|**SO_KEEPALIVE**|**BOOL**|傳送持續作用。|  
|**SO_LINGER**|**延遲結構**|傳回目前的延遲選項。|  
|**SO_OOBINLINE**|**BOOL**|在一般資料流中收到的頻外資料。|  
|**SO_RCVBUF**|**int**|接收緩衝區大小。|  
|**SO_REUSEADDR**|**BOOL**|通訊端可以繫結已在使用一個位址。|  
|**SO_SNDBUF**|**int**|傳送的緩衝區大小。|  
|**SO_TYPE**|**int**|通訊端型別 (例如， **SOCK_STREAM**)。|  
|**TCP_NODELAY**|**BOOL**|停用用於傳送聯合的 Nagle 演算法。|  
  
 不支援的柏克萊軟體發佈 (BSD) 選項`GetSockOpt`是：  
  
|值|類型|意義|  
|-----------|----------|-------------|  
|**SO_RCVLOWAT**|**int**|收到下限標準。|  
|**SO_RCVTIMEO**|**int**|接收逾時。|  
|**SO_SNDLOWAT**|**int**|傳送下限標準。|  
|**SO_SNDTIMEO**|**int**|傳送逾時。|  
|**IP_OPTIONS**||取得 IP 標頭中的選項。|  
|**TCP_MAXSEG**|**int**|取得 TCP 區段大小上限。|  
  
 呼叫`GetSockOpt`與不支援的選項會導致錯誤碼**WSAENOPROTOOPT**傳回`GetLastError`。  
  
##  <a name="ioctl"></a>  CAsyncSocket::IOCtl  
 呼叫此成員函式，來控制通訊端的模式。  
  
```  
BOOL IOCtl(
    long lCommand,  
    DWORD* lpArgument);
```  
  
### <a name="parameters"></a>參數  
 *lCommand*  
 要在通訊端上執行的命令。  
  
 *lpArgument*  
 參數的指標*lCommand*。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功，則為非零否則為 0，並傳回特定的錯誤碼可以擷取藉由呼叫[GetLastError](#getlasterror)。 此成員函式適用於下列錯誤：  
  
- **WSANOTINITIALISED**成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必須先使用此 API。  
  
- **WSAENETDOWN**網路子系統無法偵測到的 Windows Sockets 實作。  
  
- **WSAEINVAL** *lCommand*不是有效的命令，或*lpArgument*不是可接受參數*lCommand*，或此命令不適用通訊端提供的型別。  
  
- **WSAEINPROGRESS**封鎖 Windows 通訊端作業正在進行中。  
  
- **WSAENOTSOCK**描述項不是通訊端。  
  
### <a name="remarks"></a>備註  
 這個常式可以用於任何狀態中的任何通訊端上。 它用來取得或擷取相關聯的通訊端，獨立的通訊協定與通訊子系統的作業參數。 支援下列命令：  
  
- **FIONBIO**啟用或停用未封鎖模式通訊端上的。 *LpArgument*參數指向`DWORD`即為非零，如果未封鎖模式為啟用，如果它是停用。 如果`AsyncSelect`發出通訊端，則任何嘗試使用`IOCtl`設回封鎖模式通訊端將會失敗並**WSAEINVAL**。 若要設定回封鎖模式通訊端，並防止**WSAEINVAL**錯誤，應用程式必須先停用`AsyncSelect`藉由呼叫`AsyncSelect`與*lEvent*參數等於 0，然後呼叫`IOCtl`.  
  
- **FIONREAD**判斷可以與一個讀取的位元組數目上限`Receive`從這個通訊端呼叫。 *LpArgument*參數指向`DWORD`所在`IOCtl`儲存結果。 如果此通訊端型別**SOCK_STREAM**， **FIONREAD**傳回單一的可讀取的資料總量`Receive`; 這通常是相同為在通訊端佇列的資料總量。 如果此通訊端型別**SOCK_DGRAM**， **FIONREAD**傳回的第一個資料流大小排入佇列的通訊端上。  
  
- **SIOCATMARK**判斷是否已讀取的頻外的所有資料。 這只適用於類型的通訊端**SOCK_STREAM** ，已設定為任何超出訊號範圍的資料行中接收 ( **SO_OOBINLINE**)。 如果有任何不足的頻外資料正在不等待讀取，作業會傳回非零值。 否則它會傳回 0，並在下一個`Receive`或`ReceiveFrom`對通訊端將會擷取部分或所有的資料前面 「 標記 」; 應用程式應該使用**SIOCATMARK**運算，判斷是否有任何資料會保留。 如果沒有任何一般資料前面 「 緊急 」 （超出頻外） 資料，它會接收訂單。 (請注意，`Receive`或`ReceiveFrom`永遠不會混用相同的呼叫中的頻外和一般的資料。)*LpArgument*參數指向`DWORD`所在`IOCtl`儲存結果。  
  
 此函式是子集`ioctl()`會用在 Berkeley 通訊端。 特別是，沒有任何命令，這相當於**FIOASYNC**，雖然**SIOCATMARK**是支援的只有通訊端層級命令。  
  
##  <a name="listen"></a>  CAsyncSocket::Listen  
 呼叫此成員函式來接聽內送連接要求。  
  
```  
BOOL Listen(int nConnectionBacklog = 5);
```  
  
### <a name="parameters"></a>參數  
 *nConnectionBacklog*  
 暫止連線的佇列所能成長的最大長度。 有效範圍是從 1 到 5。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功，則為非零否則為 0，並傳回特定的錯誤碼可以擷取藉由呼叫[GetLastError](#getlasterror)。 此成員函式適用於下列錯誤：  
  
- **WSANOTINITIALISED**成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必須先使用此 API。  
  
- **WSAENETDOWN**網路子系統無法偵測到的 Windows Sockets 實作。  
  
- **WSAEADDRINUSE**嘗試在使用中的位址上接聽。  
  
- **WSAEINPROGRESS**封鎖 Windows 通訊端作業正在進行中。  
  
- **WSAEINVAL**通訊端已經沒有繫結與`Bind`或已連線。  
  
- **WSAEISCONN**通訊端已連線。  
  
- **WSAEMFILE**沒有更多檔案描述項可用。  
  
- **WSAENOBUFS**沒有緩衝區空間。  
  
- **WSAENOTSOCK**描述項不是通訊端。  
  
- **WSAEOPNOTSUPP**參考之通訊端不是支援的型別`Listen`作業。  
  
### <a name="remarks"></a>備註  
 若要可接受連接，通訊端第一次建立與`Create`，連入連線的待處理項目指定`Listen`，然後以接受連接和`Accept`。 `Listen` 僅適用於支援連接，也就是通訊端類型**SOCK_STREAM**。 這個通訊端會放入 「 被動 」 模式的連入連線認可，而暫止接受由處理程序排入佇列。  
  
 此函式通常是由伺服器 （或任何想要接受連線的應用程式），可能會有一個以上的連線要求一次： 如果連線要求與抵達佇列已滿，用戶端會收到表示發生錯誤**WSAECONNREFUSED**。  
  
 `Listen` 嘗試將繼續運作所在，進而時沒有可用的連接埠 （描述）。 它會接受連線，直到清空佇列。 如果連接埠供稍後呼叫`Listen`或`Accept`將會重新填滿目前或最近 」 待辦項目，「 佇列可能的話，並繼續接聽連入連線。  
  
##  <a name="m_hsocket"></a>  CAsyncSocket::m_hSocket  
 包含**通訊端**處理通訊端由這個封裝的`CAsyncSocket`物件。  
  
```  
SOCKET m_hSocket;  
```  
  
##  <a name="onaccept"></a>  CAsyncSocket::OnAccept  
 由架構呼叫以通知它可以接受暫止的連接要求，藉由呼叫接聽通訊端[接受](#accept)成員函式。  
  
```  
virtual void OnAccept(int nErrorCode);
```  
  
### <a name="parameters"></a>參數  
 *nErrorCode*  
 通訊端上最近的錯誤。 適用於下列的錯誤代碼`OnAccept`成員函式：  
  
- **0**函式執行成功。  
  
- **WSAENETDOWN**網路子系統無法偵測到的 Windows Sockets 實作。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[Windows Sockets： 通訊端告知](../../mfc/windows-sockets-socket-notifications.md)。  
  
##  <a name="onclose"></a>  CAsyncSocket::OnClose  
 由架構呼叫以通知這個通訊端連線的通訊端已關閉其處理程序。  
  
```  
virtual void OnClose(int nErrorCode);
```  
  
### <a name="parameters"></a>參數  
 *nErrorCode*  
 通訊端上最近的錯誤。 下列的錯誤代碼適用於`OnClose`成員函式：  
  
- **0**函式執行成功。  
  
- **WSAENETDOWN**網路子系統無法偵測到的 Windows Sockets 實作。  
  
- **WSAECONNRESET**遠端已經重設連接。  
  
- **WSAECONNABORTED**連接已中止，因為逾時或其他失敗。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[Windows Sockets： 通訊端告知](../../mfc/windows-sockets-socket-notifications.md)。  
  
##  <a name="onconnect"></a>  CAsyncSocket::OnConnect  
 由架構呼叫以通知此連線的通訊端完成其嘗試連線，不論成功或錯誤。  
  
```  
virtual void OnConnect(int nErrorCode);
```  
  
### <a name="parameters"></a>參數  
 *nErrorCode*  
 通訊端上最近的錯誤。 下列的錯誤代碼適用於`OnConnect`成員函式：  
  
- **0**函式執行成功。  
  
- **WSAEADDRINUSE**指定的位址已在使用。  
  
- **WSAEADDRNOTAVAIL**指定的位址不是可從本機電腦。  
  
- **WSAEAFNOSUPPORT**指定系列中的位址不能使用此通訊端。  
  
- **WSAECONNREFUSED**已強制拒絕連線嘗試。  
  
- **WSAEDESTADDRREQ**目的地位址是必要項。  
  
- **WSAEFAULT** *lpSockAddrLen*引數不正確。  
  
- **WSAEINVAL**通訊端已經繫結至地址。  
  
- **WSAEISCONN**通訊端已連線。  
  
- **WSAEMFILE**沒有更多檔案描述項可用。  
  
- **WSAENETUNREACH**無法透過此主機連接網路，這一次。  
  
- **WSAENOBUFS**沒有緩衝區空間。 無法連線通訊端。  
  
- **WSAENOTCONN**通訊端未連線。  
  
- **WSAENOTSOCK**描述元是檔案時，不通訊端。  
  
- **WSAETIMEDOUT**連線嘗試逾時，而不必建立連線。  
  
### <a name="remarks"></a>備註  
  
> [!NOTE]
>  在[CSocket](../../mfc/reference/csocket-class.md)、`OnConnect`絕不會呼叫通知函式。 進行連線，您只需呼叫`Connect`，這會傳回時 （成功或錯誤），就可以完成連線。 連接告知的處理方式為 MFC 實作詳細資料。  
  
 如需詳細資訊，請參閱[Windows Sockets： 通訊端告知](../../mfc/windows-sockets-socket-notifications.md)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCAsyncSocket#1](../../mfc/reference/codesnippet/cpp/casyncsocket-class_1.cpp)]  
  
##  <a name="onoutofbanddata"></a>  CAsyncSocket::OnOutOfBandData  
 由架構呼叫以通知傳送的封包有要傳送的頻外資料接收通訊端。  
  
```  
virtual void OnOutOfBandData(int nErrorCode);
```  
  
### <a name="parameters"></a>參數  
 *nErrorCode*  
 通訊端上最近的錯誤。 下列的錯誤代碼適用於`OnOutOfBandData`成員函式：  
  
- **0**函式執行成功。  
  
- **WSAENETDOWN**網路子系統無法偵測到的 Windows Sockets 實作。  
  
### <a name="remarks"></a>備註  
 超出訊號範圍的資料是邏輯上獨立的通道所連接的通訊端類型的每一對關聯**SOCK_STREAM**。 通道通常用來傳送緊急資料。  
  
 MFC 支援的頻外的資料，但類別的使用者`CAsyncSocket`不建議使用它。 更簡單的方法是建立第二個通訊端，用來傳遞這類資料。 更多的頻外資料的詳細資訊，請參閱[Windows Sockets： 通訊端告知](../../mfc/windows-sockets-socket-notifications.md)。  
  
##  <a name="onreceive"></a>  CAsyncSocket::OnReceive  
 由架構呼叫以通知這個通訊端可以藉由呼叫擷取緩衝區中沒有資料`Receive`成員函式。  
  
```  
virtual void OnReceive(int nErrorCode);
```  
  
### <a name="parameters"></a>參數  
 *nErrorCode*  
 通訊端上最近的錯誤。 下列的錯誤代碼適用於`OnReceive`成員函式：  
  
- **0**函式執行成功。  
  
- **WSAENETDOWN**網路子系統無法偵測到的 Windows Sockets 實作。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[Windows Sockets： 通訊端告知](../../mfc/windows-sockets-socket-notifications.md)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCAsyncSocket#2](../../mfc/reference/codesnippet/cpp/casyncsocket-class_2.cpp)]  
  
##  <a name="onsend"></a>  CAsyncSocket::OnSend  
 由架構呼叫以告知通訊端，則它現在可以藉由呼叫傳送資料**傳送**成員函式。  
  
```  
virtual void OnSend(int nErrorCode);
```  
  
### <a name="parameters"></a>參數  
 *nErrorCode*  
 通訊端上最近的錯誤。 下列的錯誤代碼適用於`OnSend`成員函式：  
  
- **0**函式執行成功。  
  
- **WSAENETDOWN**網路子系統無法偵測到的 Windows Sockets 實作。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[Windows Sockets： 通訊端告知](../../mfc/windows-sockets-socket-notifications.md)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCAsyncSocket#3](../../mfc/reference/codesnippet/cpp/casyncsocket-class_3.cpp)]  
  
##  <a name="operator_eq"></a>  CAsyncSocket::operator =  
 指派新值`CAsyncSocket`物件。  
  
```  
void operator=(const CAsyncSocket& rSrc);
```  
  
### <a name="parameters"></a>參數  
 *rSrc*  
 若要將現有的參考`CAsyncSocket`物件。  
  
### <a name="remarks"></a>備註  
 呼叫此函式可複製現有`CAsyncSocket`物件與其他`CAsyncSocket`物件。  
  
##  <a name="operator_socket"></a>  CAsyncSocket::operator 通訊端  
 使用此運算子來擷取**通訊端**控點`CAsyncSocket`物件。  
  
```  
operator SOCKET() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果成功的話的控制代碼**通訊端**物件; 否則**NULL**。  
  
### <a name="remarks"></a>備註  
 您可以直接呼叫 Windows Api 中使用控制代碼。  
  
##  <a name="receive"></a>  CAsyncSocket::Receive  
 呼叫此成員函式可從通訊端接收資料。  
  
```  
virtual int Receive(
    void* lpBuf,  
    int nBufLen,  
    int nFlags = 0);
```  
  
### <a name="parameters"></a>參數  
 *lpBuf*  
 內送資料的的緩衝區。  
  
 *nBufLen*  
 長度*lpBuf*以位元組為單位。  
  
 *nFlags*  
 指定用來進行呼叫的方法。 此函式的語意由通訊端選項和*nFlags*參數。 後者的建構方式合併任何下列的值具有 c + +**或**運算子：  
  
- **MSG_PEEK**窺視內送資料。 資料複製到緩衝區，但不是會從輸入佇列移除。  
  
- **MSG_OOB**處理超出訊號範圍的資料。  
  
### <a name="return-value"></a>傳回值  
 如果沒有發生錯誤，`Receive`傳回接收的位元組數目。 如果連接已關閉，它會傳回 0。 否則，值為**SOCKET_ERROR**傳回，而且可以擷取特定的錯誤碼，藉由呼叫[GetLastError](#getlasterror)。 此成員函式適用於下列錯誤：  
  
- **WSANOTINITIALISED**成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必須先使用此 API。  
  
- **WSAENETDOWN**網路子系統無法偵測到的 Windows Sockets 實作。  
  
- **WSAENOTCONN**通訊端未連線。  
  
- **WSAEINPROGRESS**封鎖 Windows 通訊端作業正在進行中。  
  
- **WSAENOTSOCK**描述項不是通訊端。  
  
- **WSAEOPNOTSUPP MSG_OOB**已指定，但是通訊端不是型別**SOCK_STREAM**。  
  
- **WSAESHUTDOWN**通訊端關閉，它不能呼叫`Receive`之後通訊端上`ShutDown`以叫用*nHow*設為 0 或 2。  
  
- **WSAEWOULDBLOCK**通訊端已標示為封鎖及`Receive`將封鎖作業。  
  
- **WSAEMSGSIZE**資料包太大而無法放入指定的緩衝區，而且已被截斷。  
  
- **WSAEINVAL**通訊端已經沒有繫結與`Bind`。  
  
- **WSAECONNABORTED**虛擬電路由於逾時或其他失敗已中止。  
  
- **WSAECONNRESET**遠端重設此虛擬電路。  
  
### <a name="remarks"></a>備註  
 此函式用於連接的資料流或資料包通訊端和用來讀取內送資料。  
  
 類型的通訊端**SOCK_STREAM**，這會傳回目前可用但不超過提供的緩衝區的大小資訊。 如果已設定出頻外資料行中接收通訊端 (socket 選項**SO_OOBINLINE**) 和不足的頻外資料未讀取，會傳回只的頻外的資料。 應用程式可以使用**IOCtlSIOCATMARK**選項或[OnOutOfBandData](#onoutofbanddata)來判斷是否有更多的頻外遺留的資料讀取。  
  
 資料包通訊端，資料被擷取自第一個加入佇列資料包，但不超過提供的緩衝區的大小。 如果資料包大於提供的緩衝區，緩衝區會填入資料包的第一個部分，超過的資料會遺失，和`Receive`傳回值的**SOCKET_ERROR**錯誤程式碼設為**WSAEMSGSIZE**。 如果沒有連入的資料上通訊端，而值為**SOCKET_ERROR**傳回錯誤碼設定為**WSAEWOULDBLOCK**。 [OnReceive](#onreceive)回呼函式可用來判斷當資料抵達時。  
  
 如果通訊端型別**SOCK_STREAM**和遠端已關閉連線正常，`Receive`立即完成時會收到 0 個位元組。 如果連接已重設，`Receive`將會失敗並出現錯誤**WSAECONNRESET**。  
  
 `Receive` 應該針對每次只有一次呼叫[CAsyncSocket::OnReceive](#onreceive)呼叫。  
  
### <a name="example"></a>範例  
  請參閱範例的[CAsyncSocket::OnReceive](#onreceive)。  
  
##  <a name="receivefrom"></a>  CAsyncSocket::ReceiveFrom  
 呼叫此成員函式，來接收資料包 (datagram) 和儲存中的來源位址[SOCKADDR](../../mfc/reference/sockaddr-structure.md)結構或*rSocketAddress*。  
  
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
 *lpBuf*  
 內送資料的的緩衝區。  
  
 *nBufLen*  
 長度*lpBuf*以位元組為單位。  
  
 *rSocketAddress*  
 若要參考`CString`接收小數點的數字 IP 位址的物件。  
  
 *rSocketPort*  
 若要參考**UINT**儲存連接埠。  
  
 *lpSockAddr*  
 指標[SOCKADDR](../../mfc/reference/sockaddr-structure.md)結構，可保存傳回時的來源位址。  
  
 *lpSockAddrLen*  
 中的來源位址長度的指標*lpSockAddr*以位元組為單位。  
  
 *nFlags*  
 指定用來進行呼叫的方法。 此函式的語意由通訊端選項和*nFlags*參數。 後者的建構方式合併任何下列的值具有 c + +**或**運算子：  
  
- **MSG_PEEK**窺視內送資料。 資料複製到緩衝區，但不是會從輸入佇列移除。  
  
- **MSG_OOB**處理超出訊號範圍的資料。  
  
### <a name="return-value"></a>傳回值  
 如果沒有發生錯誤，`ReceiveFrom`傳回接收的位元組數目。 如果連接已關閉，它會傳回 0。 否則，值為**SOCKET_ERROR**傳回，而且可以擷取特定的錯誤碼，藉由呼叫`GetLastError`。 此成員函式適用於下列錯誤：  
  
- **WSANOTINITIALISED**成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必須先使用此 API。  
  
- **WSAENETDOWN**網路子系統無法偵測到的 Windows Sockets 實作。  
  
- **WSAEFAULT** *lpSockAddrLen*引數無效： *lpSockAddr*緩衝區太小，無法容納的對等地址。  
  
- **WSAEINPROGRESS**封鎖 Windows 通訊端作業正在進行中。  
  
- **WSAEINVAL**通訊端已經沒有繫結與`Bind`。  
  
- **WSAENOTCONN**未連接通訊端 ( **SOCK_STREAM**只)。  
  
- **WSAENOTSOCK**描述項不是通訊端。  
  
- **WSAEOPNOTSUPP MSG_OOB**已指定，但是通訊端不是型別**SOCK_STREAM**。  
  
- **WSAESHUTDOWN**通訊端關閉，它不能呼叫`ReceiveFrom`之後通訊端上`ShutDown`以叫用*nHow*設為 0 或 2。  
  
- **WSAEWOULDBLOCK**通訊端已標示為封鎖及`ReceiveFrom`將封鎖作業。  
  
- **WSAEMSGSIZE**資料包太大而無法放入指定的緩衝區，而且已被截斷。  
  
- **WSAECONNABORTED**虛擬電路由於逾時或其他失敗已中止。  
  
- **WSAECONNRESET**遠端重設此虛擬電路。  
  
### <a name="remarks"></a>備註  
 此函式用來讀取內送資料上 （可能是連接） 的通訊端，和擷取已從中傳送資料的位址。  
  
 若要處理的 IPv6 位址，使用[CAsyncSocket::ReceiveFromEx](#receivefromex)。  
  
 類型的通訊端**SOCK_STREAM**，這會傳回目前可用但不超過提供的緩衝區的大小資訊。 如果已設定出頻外資料行中接收通訊端 (socket 選項**SO_OOBINLINE**) 和不足的頻外資料未讀取，會傳回只的頻外的資料。 應用程式可以使用**IOCtlSIOCATMARK**選項或`OnOutOfBandData`來判斷是否有更多的頻外遺留的資料讀取。 *LpSockAddr*和*lpSockAddrLen*參數也會被忽略**SOCK_STREAM**通訊端。  
  
 資料包通訊端，資料被擷取自第一個加入佇列資料包，但不超過提供的緩衝區的大小。 如果資料包大於提供的緩衝區，緩衝區會填入訊息的第一個部分，超過的資料會遺失，和`ReceiveFrom`傳回值的**SOCKET_ERROR**錯誤程式碼設為**WSAEMSGSIZE**。  
  
 如果*lpSockAddr*非零，而且通訊端的類型是**SOCK_DGRAM**，傳送資料，通訊端的網路位址會複製到對應[SOCKADDR](../../mfc/reference/sockaddr-structure.md)結構。 所指向的值*lpSockAddrLen*會初始化為此結構的大小和修改在傳回時，表示儲存於該處的位址的實際大小。 如果在通訊端，可使用任何內送資料`ReceiveFrom`等候資料到達除非通訊端的呼叫未封鎖。 這種情況下，值為**SOCKET_ERROR**傳回錯誤碼設定為**WSAEWOULDBLOCK**。 `OnReceive`回呼可以用來判斷當資料抵達時。  
  
 如果通訊端型別**SOCK_STREAM**和遠端已關閉連線正常，`ReceiveFrom`立即完成時會收到 0 個位元組。  
  
##  <a name="receivefromex"></a>  CAsyncSocket::ReceiveFromEx  
 呼叫此成員函式，來接收資料包 (datagram) 和儲存中的來源位址[SOCKADDR](../../mfc/reference/sockaddr-structure.md)結構或*rSocketAddress* （處理 IPv6 位址）。  
  
```  
int ReceiveFromEx(
    void* lpBuf,  
    int nBufLen,  
    CString& rSocketAddress,  
    UINT& rSocketPort,  
    int nFlags = 0);
```  
  
### <a name="parameters"></a>參數  
 *lpBuf*  
 內送資料的的緩衝區。  
  
 *nBufLen*  
 長度*lpBuf*以位元組為單位。  
  
 *rSocketAddress*  
 若要參考`CString`接收小數點的數字 IP 位址的物件。  
  
 *rSocketPort*  
 若要參考**UINT**儲存連接埠。  
  
 *nFlags*  
 指定用來進行呼叫的方法。 此函式的語意由通訊端選項和*nFlags*參數。 後者的建構方式合併任何下列的值具有 c + +**或**運算子：  
  
- **MSG_PEEK**窺視內送資料。 資料複製到緩衝區，但不是會從輸入佇列移除。  
  
- **MSG_OOB**處理超出訊號範圍的資料。  
  
### <a name="return-value"></a>傳回值  
 如果沒有發生錯誤，`ReceiveFromEx`傳回接收的位元組數目。 如果連接已關閉，它會傳回 0。 否則，值為**SOCKET_ERROR**傳回，而且可以擷取特定的錯誤碼，藉由呼叫`GetLastError`。 此成員函式適用於下列錯誤：  
  
- **WSANOTINITIALISED**成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必須先使用此 API。  
  
- **WSAENETDOWN**網路子系統無法偵測到的 Windows Sockets 實作。  
  
- **WSAEFAULT** *lpSockAddrLen*引數無效： *lpSockAddr*緩衝區太小，無法容納的對等地址。  
  
- **WSAEINPROGRESS**封鎖 Windows 通訊端作業正在進行中。  
  
- **WSAEINVAL**通訊端已經沒有繫結與`Bind`。  
  
- **WSAENOTCONN**未連接通訊端 ( **SOCK_STREAM**只)。  
  
- **WSAENOTSOCK**描述項不是通訊端。  
  
- **WSAEOPNOTSUPP MSG_OOB**已指定，但是通訊端不是型別**SOCK_STREAM**。  
  
- **WSAESHUTDOWN**通訊端關閉，它不能呼叫`ReceiveFromEx`之後通訊端上`ShutDown`以叫用*nHow*設為 0 或 2。  
  
- **WSAEWOULDBLOCK**通訊端已標示為封鎖及`ReceiveFromEx`將封鎖作業。  
  
- **WSAEMSGSIZE**資料包太大而無法放入指定的緩衝區，而且已被截斷。  
  
- **WSAECONNABORTED**虛擬電路由於逾時或其他失敗已中止。  
  
- **WSAECONNRESET**遠端重設此虛擬電路。  
  
### <a name="remarks"></a>備註  
 此函式用來讀取內送資料上 （可能是連接） 的通訊端，和擷取已從中傳送資料的位址。  
  
 此函式是相同[CAsyncSocket::ReceiveFrom](#receivefrom)不同之處在於它會處理 IPv6 位址以及為舊的通訊協定。  
  
 類型的通訊端**SOCK_STREAM**，這會傳回目前可用但不超過提供的緩衝區的大小資訊。 如果已設定出頻外資料行中接收通訊端 (socket 選項**SO_OOBINLINE**) 和不足的頻外資料未讀取，會傳回只的頻外的資料。 應用程式可以使用**IOCtlSIOCATMARK**選項或`OnOutOfBandData`來判斷是否有更多的頻外遺留的資料讀取。 *LpSockAddr*和*lpSockAddrLen*參數也會被忽略**SOCK_STREAM**通訊端。  
  
 資料包通訊端，資料被擷取自第一個加入佇列資料包，但不超過提供的緩衝區的大小。 如果資料包大於提供的緩衝區，緩衝區會填入訊息的第一個部分，超過的資料會遺失，和`ReceiveFromEx`傳回值的**SOCKET_ERROR**錯誤程式碼設為**WSAEMSGSIZE**。  
  
 如果*lpSockAddr*非零，而且通訊端的類型是**SOCK_DGRAM**，傳送資料，通訊端的網路位址會複製到對應[SOCKADDR](../../mfc/reference/sockaddr-structure.md)結構。 所指向的值*lpSockAddrLen*會初始化為此結構的大小和修改在傳回時，表示儲存於該處的位址的實際大小。 如果在通訊端，可使用任何內送資料`ReceiveFromEx`等候資料到達除非通訊端的呼叫未封鎖。 這種情況下，值為**SOCKET_ERROR**傳回錯誤碼設定為**WSAEWOULDBLOCK**。 `OnReceive`回呼可以用來判斷當資料抵達時。  
  
 如果通訊端型別**SOCK_STREAM**和遠端已關閉連線正常，`ReceiveFromEx`立即完成時會收到 0 個位元組。  
  
##  <a name="send"></a>  CAsyncSocket::Send  
 呼叫此成員函式連接的通訊端上傳送的資料。  
  
```  
virtual int Send(
    const void* lpBuf,  
    int nBufLen,  
    int nFlags = 0);
```  
  
### <a name="parameters"></a>參數  
 *lpBuf*  
 包含要傳送的資料緩衝區。  
  
 *nBufLen*  
 中的資料長度*lpBuf*以位元組為單位。  
  
 *nFlags*  
 指定用來進行呼叫的方法。 此函式的語意由通訊端選項和*nFlags*參數。 後者的建構方式合併任何下列的值具有 c + +**或**運算子：  
  
- **MSG_DONTROUTE**指定的資料不應該受限於路由。 Windows Sockets 供應商可以選擇忽略此旗標。  
  
- **MSG_OOB**傳送不足的頻外資料 ( **SOCK_STREAM**只)。  
  
### <a name="return-value"></a>傳回值  
 如果沒有發生錯誤，`Send`傳回送出的字元總數。 (請注意，這可以是所指定的數目小於*nBufLen*。)否則，值為**SOCKET_ERROR**傳回，而且可以擷取特定的錯誤碼，藉由呼叫[GetLastError](#getlasterror)。 此成員函式適用於下列錯誤：  
  
- **WSANOTINITIALISED**成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必須先使用此 API。  
  
- **WSAENETDOWN**網路子系統無法偵測到的 Windows Sockets 實作。  
  
- **WSAEACCES**所要求的位址是廣播的位址，但未設定適當的旗標。  
  
- **WSAEINPROGRESS**封鎖 Windows 通訊端作業正在進行中。  
  
- **WSAEFAULT** *lpBuf*引數不是有效的組件的使用者位址空間。  
  
- **WSAENETRESET**必須重設連接，因為 Windows Sockets 實作卸除它。  
  
- **WSAENOBUFS** Windows Sockets 實作報告緩衝區死結。  
  
- **WSAENOTCONN**通訊端未連線。  
  
- **WSAENOTSOCK**描述項不是通訊端。  
  
- **WSAEOPNOTSUPP MSG_OOB**已指定，但是通訊端不是型別**SOCK_STREAM**。  
  
- **WSAESHUTDOWN**通訊端關閉，它不能呼叫`Send`之後通訊端上`ShutDown`以叫用*nHow*設為 1 或 2。  
  
- **WSAEWOULDBLOCK**通訊端已標示為封鎖，要求的作業會封鎖。  
  
- **WSAEMSGSIZE**通訊端屬於型別**SOCK_DGRAM**，而且資料包大小超過支援的 Windows Sockets 實作的最大值。  
  
- **WSAEINVAL**通訊端已經沒有繫結與`Bind`。  
  
- **WSAECONNABORTED**虛擬電路由於逾時或其他失敗已中止。  
  
- **WSAECONNRESET**遠端重設此虛擬電路。  
  
### <a name="remarks"></a>備註  
 `Send` 用來寫入輸出的資料連接的資料流或資料包通訊端上。 資料包通訊端，必須小心不超過最大的 IP 封包大小基礎的子網路，這由提供**iMaxUdpDg**中的項目[WSADATA](../../mfc/reference/wsadata-structure.md)所傳回的結構`AfxSocketInit`。 如果資料太長，無法以不可分割方式傳遞的基礎通訊協定錯誤**WSAEMSGSIZE**傳回透過`GetLastError`，並在傳送任何資料。  
  
 請注意，對資料包通訊端成功完成`Send`並不表示已成功傳送資料。  
  
 在`CAsyncSocket`類型的物件**SOCK_STREAM**，寫入的位元組數目可以是介於 1 到所要求的長度，根據在本機和外部主機上的緩衝區可用性。  
  
### <a name="example"></a>範例  
  請參閱範例的[CAsyncSocket::OnSend](#onsend)。  
  
##  <a name="sendto"></a>  CAsyncSocket::SendTo  
 呼叫此成員函式，將資料傳送至特定目的地。  
  
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
 *lpBuf*  
 包含要傳送的資料緩衝區。  
  
 *nBufLen*  
 中的資料長度*lpBuf*以位元組為單位。  
  
 *nHostPort*  
 識別通訊端應用程式連接埠。  
  
 *lpszHostAddress*  
 這個物件所連接的通訊端的網路位址： 電腦名稱，例如"ftp.microsoft.com"或小數點的數字，例如"128.56.22.8"。  
  
 *nFlags*  
 指定用來進行呼叫的方法。 此函式的語意由通訊端選項和*nFlags*參數。 後者的建構方式合併任何下列的值具有 c + +**或**運算子：  
  
- **MSG_DONTROUTE**指定的資料不應該受限於路由。 Windows Sockets 供應商可以選擇忽略此旗標。  
  
- **MSG_OOB**傳送不足的頻外資料 ( **SOCK_STREAM**只)。  
  
 *lpSockAddr*  
 指標[SOCKADDR](../../mfc/reference/sockaddr-structure.md)結構，其中包含目標通訊端位址。  
  
 *nSockAddrLen*  
 中的位址長度*lpSockAddr*以位元組為單位。  
  
### <a name="return-value"></a>傳回值  
 如果沒有發生錯誤，`SendTo`傳回送出的字元總數。 (請注意，這可以是所指定的數目小於*nBufLen*。)否則，值為**SOCKET_ERROR**傳回，而且可以擷取特定的錯誤碼，藉由呼叫[GetLastError](#getlasterror)。 此成員函式適用於下列錯誤：  
  
- **WSANOTINITIALISED**成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必須先使用此 API。  
  
- **WSAENETDOWN**網路子系統無法偵測到的 Windows Sockets 實作。  
  
- **WSAEACCES**所要求的位址是廣播的位址，但未設定適當的旗標。  
  
- **WSAEINPROGRESS**封鎖 Windows 通訊端作業正在進行中。  
  
- **WSAEFAULT** *lpBuf*或*lpSockAddr*參數不是使用者位址空間的一部分或*lpSockAddr*引數是 （低於大小太小[SOCKADDR](../../mfc/reference/sockaddr-structure.md)結構)。  
  
- **WSAEINVAL**主機名稱無效。  
  
- **WSAENETRESET**必須重設連接，因為 Windows Sockets 實作卸除它。  
  
- **WSAENOBUFS** Windows Sockets 實作報告緩衝區死結。  
  
- **WSAENOTCONN**未連接通訊端 ( **SOCK_STREAM**只)。  
  
- **WSAENOTSOCK**描述項不是通訊端。  
  
- **WSAEOPNOTSUPP MSG_OOB**已指定，但是通訊端不是型別**SOCK_STREAM**。  
  
- **WSAESHUTDOWN**通訊端關閉，它不能呼叫`SendTo`之後通訊端上`ShutDown`以叫用*nHow*設為 1 或 2。  
  
- **WSAEWOULDBLOCK**通訊端已標示為封鎖，要求的作業會封鎖。  
  
- **WSAEMSGSIZE**通訊端屬於型別**SOCK_DGRAM**，而且資料包大小超過支援的 Windows Sockets 實作的最大值。  
  
- **WSAECONNABORTED**虛擬電路由於逾時或其他失敗已中止。  
  
- **WSAECONNRESET**遠端重設此虛擬電路。  
  
- **WSAEADDRNOTAVAIL**指定的位址不是可從本機電腦。  
  
- **WSAEAFNOSUPPORT**指定系列中的位址不能使用此通訊端。  
  
- **WSAEDESTADDRREQ**目的地位址是必要項。  
  
- **WSAENETUNREACH**無法透過此主機連接網路，這一次。  
  
### <a name="remarks"></a>備註  
 `SendTo` 使用資料流或資料流通訊端上，用來寫入輸出的資料，通訊端上。 資料包通訊端，必須小心不超過最大的 IP 封包大小基礎的子網路，這由提供**iMaxUdpDg**中的項目[WSADATA](../../mfc/reference/wsadata-structure.md)結構填寫[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)。 如果資料太長，無法以不可分割方式傳遞的基礎通訊協定錯誤**WSAEMSGSIZE**傳回，並在傳送任何資料。  
  
 請注意，成功完成`SendTo`並不表示已成功傳送資料。  
  
 `SendTo` 只會用於**SOCK_DGRAM**資料包傳送到特定的通訊端所識別的通訊端*lpSockAddr*參數。  
  
 若要傳送廣播 (上**SOCK_DGRAM**只)，在位址*lpSockAddr*參數應該使用特殊的 IP 位址建構**INADDR_BROADCAST** （定義Windows Sockets 標頭中的檔案 WINSOCK。H） 並搭配預期的連接埠號碼。 或者，如果*lpszHostAddress*參數是**NULL**，通訊端設定為廣播。 通常不得為廣播資料包 (datagram) 超過大小的片段可能會發生，這表示資料包 （不含標頭） 的資料部分不可超過 512 個位元組。  
  
 若要處理的 IPv6 位址，使用[CAsyncSocket::SendToEx](#sendtoex)。  
  
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
 *lpBuf*  
 包含要傳送的資料緩衝區。  
  
 *nBufLen*  
 中的資料長度*lpBuf*以位元組為單位。  
  
 *nHostPort*  
 識別通訊端應用程式連接埠。  
  
 *lpszHostAddress*  
 這個物件所連接的通訊端的網路位址： 電腦名稱，例如"ftp.microsoft.com"或小數點的數字，例如"128.56.22.8"。  
  
 *nFlags*  
 指定用來進行呼叫的方法。 此函式的語意由通訊端選項和*nFlags*參數。 後者的建構方式合併任何下列的值具有 c + +**或**運算子：  
  
- **MSG_DONTROUTE**指定的資料不應該受限於路由。 Windows Sockets 供應商可以選擇忽略此旗標。  
  
- **MSG_OOB**傳送不足的頻外資料 ( **SOCK_STREAM**只)。  
  
### <a name="return-value"></a>傳回值  
 如果沒有發生錯誤，`SendToEx`傳回送出的字元總數。 (請注意，這可以是所指定的數目小於*nBufLen*。)否則，值為**SOCKET_ERROR**傳回，而且可以擷取特定的錯誤碼，藉由呼叫[GetLastError](#getlasterror)。 此成員函式適用於下列錯誤：  
  
- **WSANOTINITIALISED**成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必須先使用此 API。  
  
- **WSAENETDOWN**網路子系統無法偵測到的 Windows Sockets 實作。  
  
- **WSAEACCES**所要求的位址是廣播的位址，但未設定適當的旗標。  
  
- **WSAEINPROGRESS**封鎖 Windows 通訊端作業正在進行中。  
  
- **WSAEFAULT** *lpBuf*或*lpSockAddr*參數不是使用者位址空間的一部分或*lpSockAddr*引數是 （低於大小太小[SOCKADDR](../../mfc/reference/sockaddr-structure.md)結構)。  
  
- **WSAEINVAL**主機名稱無效。  
  
- **WSAENETRESET**必須重設連接，因為 Windows Sockets 實作卸除它。  
  
- **WSAENOBUFS** Windows Sockets 實作報告緩衝區死結。  
  
- **WSAENOTCONN**未連接通訊端 ( **SOCK_STREAM**只)。  
  
- **WSAENOTSOCK**描述項不是通訊端。  
  
- **WSAEOPNOTSUPP MSG_OOB**已指定，但是通訊端不是型別**SOCK_STREAM**。  
  
- **WSAESHUTDOWN**通訊端關閉，它不能呼叫`SendToEx`之後通訊端上`ShutDown`以叫用*nHow*設為 1 或 2。  
  
- **WSAEWOULDBLOCK**通訊端已標示為封鎖，要求的作業會封鎖。  
  
- **WSAEMSGSIZE**通訊端屬於型別**SOCK_DGRAM**，而且資料包大小超過支援的 Windows Sockets 實作的最大值。  
  
- **WSAECONNABORTED**虛擬電路由於逾時或其他失敗已中止。  
  
- **WSAECONNRESET**遠端重設此虛擬電路。  
  
- **WSAEADDRNOTAVAIL**指定的位址不是可從本機電腦。  
  
- **WSAEAFNOSUPPORT**指定系列中的位址不能使用此通訊端。  
  
- **WSAEDESTADDRREQ**目的地位址是必要項。  
  
- **WSAENETUNREACH**無法透過此主機連接網路，這一次。  
  
### <a name="remarks"></a>備註  
 這個方法相當於[CAsyncSocket::SendTo](#sendto)不同之處在於它會處理 IPv6 位址以及為舊的通訊協定。  
  
 `SendToEx` 使用資料流或資料流通訊端上，用來寫入輸出的資料，通訊端上。 資料包通訊端，必須小心不超過最大的 IP 封包大小基礎的子網路，這由提供**iMaxUdpDg**中的項目[WSADATA](../../mfc/reference/wsadata-structure.md)結構填寫[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)。 如果資料太長，無法以不可分割方式傳遞的基礎通訊協定錯誤**WSAEMSGSIZE**傳回，並在傳送任何資料。  
  
 請注意，成功完成`SendToEx`並不表示已成功傳送資料。  
  
 `SendToEx` 只會用於**SOCK_DGRAM**資料包傳送到特定的通訊端所識別的通訊端*lpSockAddr*參數。  
  
 若要傳送廣播 (上**SOCK_DGRAM**只)，在位址*lpSockAddr*參數應該使用特殊的 IP 位址建構**INADDR_BROADCAST** （定義Windows Sockets 標頭中的檔案 WINSOCK。H） 並搭配預期的連接埠號碼。 或者，如果*lpszHostAddress*參數是**NULL**，通訊端設定為廣播。 通常不得為廣播資料包 (datagram) 超過大小的片段可能會發生，這表示資料包 （不含標頭） 的資料部分不可超過 512 個位元組。  
  
##  <a name="setsockopt"></a>  CAsyncSocket::SetSockOpt  
 呼叫此成員函式，設定通訊端選項。  
  
```  
BOOL SetSockOpt(
    int nOptionName,  
    const void* lpOptionValue,  
    int nOptionLen,  
    int nLevel = SOL_SOCKET);
```  
  
### <a name="parameters"></a>參數  
 *nOptionName*  
 這個值是設定通訊端選項。  
  
 *lpOptionValue*  
 提供要求的選項的值時緩衝區的指標。  
  
 *nOptionLen*  
 大小*lpOptionValue*以位元組為單位的緩衝區。  
  
 *nLevel*  
 層級的定義選項。唯一支援的層級為**SOL_SOCKET**和**IPPROTO_TCP**。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功，則為非零否則為 0，並傳回特定的錯誤碼可以擷取藉由呼叫[GetLastError](#getlasterror)。 此成員函式適用於下列錯誤：  
  
- **WSANOTINITIALISED**成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必須先使用此 API。  
  
- **WSAENETDOWN**網路子系統無法偵測到的 Windows Sockets 實作。  
  
- **WSAEFAULT** *lpOptionValue*不是處於有效的組件的處理序位址空間。  
  
- **WSAEINPROGRESS**封鎖 Windows 通訊端作業正在進行中。  
  
- **WSAEINVAL** *nLevel*不正確，或在資訊*lpOptionValue*不正確。  
  
- **WSAENETRESET**連線已逾時**SO_KEEPALIVE**設定。  
  
- **WSAENOPROTOOPT**的選項是未知或不受支援。 特別是， **SO_BROADCAST**不支援類型的通訊端**SOCK_STREAM**，雖然**SO_DONTLINGER**， **SO_KEEPALIVE**， **SO_LINGER**，和**SO_OOBINLINE**通訊端的類型上不支援**SOCK_DGRAM**。  
  
- **WSAENOTCONN**連接已經重設時**SO_KEEPALIVE**設定。  
  
- **WSAENOTSOCK**描述項不是通訊端。  
  
### <a name="remarks"></a>備註  
 `SetSockOpt` 設定通訊端選項相關聯的任何狀態中的任何型別，通訊端的目前值。 雖然選項可以有多個通訊協定層級，但是此規格只會定義存在於最上方的 「 通訊端 」 層級的選項。 選項會影響通訊端作業，例如是否加速的資料收到一般資料流中，是否可以在通訊端，傳送廣播的訊息等等。  
  
 有兩種類型的通訊端選項： 布林值的選項來啟用或停用的功能或行為和需要整數值或結構的選項。 若要啟用，則為 True 的選項， *lpOptionValue*點則為非零的整數。 若要停用此選項*lpOptionValue*指向等於零的整數。 *nOptionLen*應該會等於**sizeof(BOOL)** 布林值的選項。 如需其他選項， *lpOptionValue*指向整數或結構，其中包含所需選項的值和*nOptionLen*是整數或結構的長度。  
  
 **SO_LINGER**時採取的動作未傳送的資料會排入佇列的通訊端的控制項和`Close`函式呼叫以關閉通訊端。  
  
 根據預設，不能繫結通訊端 (請參閱[繫結](#bind)) 至已在使用的本機位址。 在某些情況下，不過，它可能想要以這種方式的地址 」 重複使用 」。 因為本機與遠端位址的組合來唯一識別每個連接，所以沒有沒問題，有兩個繫結至相同的本機位址，只要遠端位址是不同的通訊端。  
  
 若要通知 Windows Sockets 實作的`Bind`應該不允許在通訊端的呼叫，因為所需的位址已由另一個通訊端使用中，應用程式應該**SO_REUSEADDR**通訊端選項通訊端，然後再發出`Bind`呼叫。 注意選項即只在時解譯`Bind`呼叫： 因此不需要 （但無害） 來設定選項，也就是未繫結至現有的位址，通訊端上，設定或重設選項時`Bind`呼叫有在這個或其他通訊端上沒有作用。  
  
 應用程式可以要求 Windows Sockets 實作啟用 「 保持運作 」 上的封包傳輸控制通訊協定 (TCP) 連接使用，藉由開啟**SO_KEEPALIVE**通訊端選項。 Windows Sockets 實作不需要支援持續作用的使用： 如果這樣做，精確語意依實作而定，但應該符合 4.2.3.6 的 RFC 1122: 「 網際網路主機需求 — 通訊層。 」 如果連接斷開"keep-alive"的結果，錯誤碼**WSAENETRESET**會傳回到任何呼叫正在進行中通訊端，而且任何後續呼叫都會失敗並**WSAENOTCONN**。  
  
 **TCP_NODELAY**選項會停用 Nagle 演算法。 Nagle 演算法用來減少傳送由主應用程式的緩衝處理未通知的傳送資料，直到可以傳送完整大小的封包的小型封包數目。 不過，對於某些應用程式此演算法可能地降低效能，以及**TCP_NODELAY**可用來將它關閉。 應用程式寫入器不應將**TCP_NODELAY**除非這樣的影響是良好容易理解且想要的因為設定**TCP_NODELAY**可以對網路效能造成顯著負面影響. **TCP_NODELAY**是唯一支援的通訊端選項，其使用等級**IPPROTO_TCP**; 所有其他選項使用層級**SOL_SOCKET**。  
  
 Windows Sockets 供應器的某些實作輸出偵錯資訊，如果**SO_DEBUG**應用程式設定選項。  
  
 支援下列選項`SetSockOpt`。 型別會識別所定址的資料型別*lpOptionValue*。  
  
|值|類型|意義|  
|-----------|----------|-------------|  
|**SO_BROADCAST**|**BOOL**|允許在通訊端廣播訊息的傳輸。|  
|**SO_DEBUG**|**BOOL**|記錄偵錯資訊。|  
|**SO_DONTLINGER**|**BOOL**|不會阻擋**關閉**等候傳送未傳送資料。 設定此選項相當於設定**SO_LINGER**與**l_onoff**設為零。|  
|**SO_DONTROUTE**|**BOOL**|不會路由傳送： 直接與介面傳送。|  
|**SO_KEEPALIVE**|**BOOL**|傳送持續作用。|  
|**SO_LINGER**|**延遲結構**|延遲**關閉**如果未傳送的資料是否都出現。|  
|**SO_OOBINLINE**|**BOOL**|在一般資料流中收到的頻外資料。|  
|**SO_RCVBUF**|**int**|指定接收緩衝區大小。|  
|**SO_REUSEADDR**|**BOOL**|允許繫結至已在使用位址的通訊端。 (請參閱[繫結](#bind)。)|  
|**SO_SNDBUF**|**int**|指定傳送的緩衝區大小。|  
|**TCP_NODELAY**|**BOOL**|停用用於傳送聯合的 Nagle 演算法。|  
  
 不支援的柏克萊軟體發佈 (BSD) 選項`SetSockOpt`是：  
  
|值|類型|意義|  
|-----------|----------|-------------|  
|**SO_ACCEPTCONN**|**BOOL**|正在接聽通訊端|  
|**SO_ERROR**|**int**|取得錯誤狀態並清除。|  
|**SO_RCVLOWAT**|**int**|收到下限標準。|  
|**SO_RCVTIMEO**|**int**|接收逾時|  
|**SO_SNDLOWAT**|**int**|傳送下限標準。|  
|**SO_SNDTIMEO**|**int**|傳送逾時。|  
|**SO_TYPE**|**int**|通訊端類型。|  
|**IP_OPTIONS**||設定 IP 標頭中的選項欄位。|  
  
##  <a name="shutdown"></a>  CAsyncSocket::ShutDown  
 呼叫此成員函式，若要停用傳送時，都會收到，或兩者都在通訊端。  
  
```  
BOOL ShutDown(int nHow = sends);
```  
  
### <a name="parameters"></a>參數  
 *nHow*  
 描述哪些類型的作業的旗標，也一律不再允許使用下列的列舉的值：  
  
- **接收 = 0**  
  
- **傳送 = 1**  
  
- **同時 = 2**  
  
### <a name="return-value"></a>傳回值  
 如果函式成功，則為非零否則為 0，並傳回特定的錯誤碼可以擷取藉由呼叫[GetLastError](#getlasterror)。 此成員函式適用於下列錯誤：  
  
- **WSANOTINITIALISED**成功[AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)必須先使用此 API。  
  
- **WSAENETDOWN**網路子系統無法偵測到的 Windows Sockets 實作。  
  
- **WSAEINVAL** *nHow*不正確。  
  
- **WSAEINPROGRESS**封鎖 Windows 通訊端作業正在進行中。  
  
- **WSAENOTCONN**未連接通訊端 ( **SOCK_STREAM**只)。  
  
- **WSAENOTSOCK**描述項不是通訊端。  
  
### <a name="remarks"></a>備註  
 `ShutDown` 適用於所有類型的通訊端若要停用接收、 傳輸，或兩者。 如果*nHow*是 0，則在後續接收通訊端將不允許。 這有不會影響的較低的通訊協定層。  
  
 傳輸控制通訊協定 (TCP)、 TCP 視窗不會變更，而且會傳入資料之前的視窗已用完，接受 （但未認可）。 針對使用者資料包通訊協定 (UDP) 中，輸入資料包所接受和排入佇列。 在任何情況下將 ICMP 錯誤封包會產生。 如果*nHow*為 1，後續的將不被允許。 TCP 通訊端，將會傳送 FIN。 設定*nHow* 2 來停用這兩個傳送和接收 （如上所述）。  
  
 請注意，`ShutDown`不會關閉通訊端，並連接到通訊端的資源將不之前不會釋放`Close`呼叫。 應用程式不應依賴能夠重複使用的通訊端之後已被關閉。 特別是，Windows Sockets 實作不需要支援使用`Connect`這類通訊端上。  
  
### <a name="example"></a>範例  
  請參閱範例的[CAsyncSocket::OnReceive](#onreceive)。  
  
##  <a name="socket"></a>  CASyncSocket::Socket  
 配置通訊端控制代碼。  
  
```  
BOOL Socket(
    int nSocketType = SOCK_STREAM,  
    long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE,  
    int nProtocolType = 0,  
    int nAddressFormat = PF_INET);
```  
  
### <a name="parameters"></a>參數  
 *nSocketType*  
 指定`SOCK_STREAM`或`SOCK_DGRAM`。  
  
 *lEvent*  
 位元遮罩，指定的網路應用程式有興趣的事件組合。  
  
- `FD_READ`： 想要接收通知的整備進行讀取。  
  
- `FD_WRITE`： 想要接收通知的整備進行寫入。  
  
- `FD_OOB`： 要接收通知的頻外資料抵達。  
  
- `FD_ACCEPT`： 想要接收通知的連入連線。  
  
- `FD_CONNECT`： 想要接收通知的完整連接。  
  
- `FD_CLOSE`： 想要接收通訊端關閉相關的通知。  
  
 *nProtocolType*  
 通訊協定以用於的通訊端的特定指示的位址系列。  
  
 *nAddressFormat*  
 位址家族的規格。  
  
### <a name="return-value"></a>傳回值  
 成功時傳回 `TRUE`，失敗時則傳回 `FALSE`。  
  
### <a name="remarks"></a>備註  
 這個方法配置的通訊端控制代碼。 它不會呼叫[CAsyncSocket::Bind](#bind)至指定的位址、 繫結通訊端，因此您必須呼叫`Bind`更新版本，才能繫結至指定之位址的通訊端。 您可以使用[CAsyncSocket::SetSockOpt](#setsockopt)之前它已繫結設定的通訊端選項。  
  
## <a name="see-also"></a>另請參閱  
 [CObject 類別](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CSocket 類別](../../mfc/reference/csocket-class.md)   
 [CSocketFile 類別](../../mfc/reference/csocketfile-class.md)
