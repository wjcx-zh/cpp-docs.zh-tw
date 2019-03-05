---
title: CSocket 類別
ms.date: 11/04/2016
f1_keywords:
- CSocket
- AFXSOCK/CSocket
- AFXSOCK/CSocket::CSocket
- AFXSOCK/CSocket::Attach
- AFXSOCK/CSocket::CancelBlockingCall
- AFXSOCK/CSocket::Create
- AFXSOCK/CSocket::FromHandle
- AFXSOCK/CSocket::IsBlocking
- AFXSOCK/CSocket::OnMessagePending
helpviewer_keywords:
- CSocket [MFC], CSocket
- CSocket [MFC], Attach
- CSocket [MFC], CancelBlockingCall
- CSocket [MFC], Create
- CSocket [MFC], FromHandle
- CSocket [MFC], IsBlocking
- CSocket [MFC], OnMessagePending
ms.assetid: 7f23c081-d24d-42e3-b511-8053ca53d729
ms.openlocfilehash: a861e557b7368d13d615aaf796faded93c72b040
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57266558"
---
# <a name="csocket-class"></a>CSocket 類別

衍生自`CAsyncSocket`繼承其封裝的 Windows Sockets api，且代表較高層級的抽象層以外的`CAsyncSocket`物件。

## <a name="syntax"></a>語法

```
class CSocket : public CAsyncSocket
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CSocket::CSocket](#csocket)|建構 `CSocket` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CSocket::Attach](#attach)|附加的通訊端控制代碼`CSocket`物件。|
|[CSocket::CancelBlockingCall](#cancelblockingcall)|取消目前正在進行封鎖呼叫。|
|[CSocket::Create](#create)|建立通訊端。|
|[CSocket::FromHandle](#fromhandle)|將指標傳回至`CSocket`指定通訊端控制代碼的物件。|
|[CSocket::IsBlocking](#isblocking)|判斷封鎖的呼叫是否正在進行中。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CSocket::OnMessagePending](#onmessagepending)|等待封鎖的呼叫完成時呼叫至暫止訊息的處理序。|

## <a name="remarks"></a>備註

`CSocket` 類別會搭配`CSocketFile`和`CArchive`管理傳送和接收的資料。

A`CSocket`物件也提供封鎖，這是同步作業的`CArchive`。 封鎖函式，例如`Receive`， `Send`， `ReceiveFrom`， `SendTo`，並`Accept`(從所有繼承`CAsyncSocket`)，不會傳回`WSAEWOULDBLOCK`錯誤`CSocket`。 相反地，這些函式會等候直到作業完成為止。 此外，原始的呼叫就會終止，錯誤 WSAEINTR`CancelBlockingCall`時封鎖了其中一個函式會呼叫。

若要使用`CSocket`物件，請呼叫建構函式，然後呼叫`Create`建立基礎通訊端控制代碼 （型別通訊端）。 預設參數`Create`建立資料流通訊端，但如果您不想要使用的通訊端與`CArchive`物件，您可以指定的參數，相反地，建立對資料包通訊端，或建立伺服器通訊端繫結至特定連接埠。 連接到用戶端通訊端，使用`Connect`用戶端和`Accept`伺服器端上。 然後建立`CSocketFile`物件，並將它來產生關聯`CSocket`物件中`CSocketFile`建構函式。 接下來，建立`CArchive`傳送的物件，一個用於接收資料 （如有需要），然後將它們關聯具有`CSocketFile`物件中`CArchive`建構函式。 通訊完成時，終結`CArchive`， `CSocketFile`，和`CSocket`物件。 通訊端的資料類型文件中所述[Windows Sockets:背景](../../mfc/windows-sockets-background.md)。

當您使用`CArchive`與`CSocketFile`並`CSocket`，您可能會遇到一種情況其中`CSocket::Receive`進入迴圈 (由`PumpMessages(FD_READ)`) 等待所要求的位元組數量。 這是因為 Windows 通訊端允許 FD_READ 通知，每一個接收呼叫，但`CSocketFile`和`CSocket`允許每 FD_READ 的多個接收呼叫。 如果可讀取的資料時，您會收到 FD_READ，應用程式會停止回應。 如果您從未收到另一個 FD_READ，應用程式會停止透過通訊端進行通訊。

您可以解決這個問題，如下所示。 在 `OnReceive`通訊端類別，呼叫方法`CAsyncSocket::IOCtl(FIONREAD, ...)`之前先呼叫`Serialize`訊息類別時從通訊端讀取預期的資料超過一個 TCP 封包的網路中 （最大傳輸單位的大小方法通常至少 1096 位元組為單位)。 如果少於所需的可用資料的大小，等待要接收，然後才開始讀取的作業的所有資料。

在下列範例中，`m_dwExpected`是近似的使用者預期收到的位元組數目。 它會假設，您將它宣告其他位置中您的程式碼。

[!code-cpp[NVC_MFCSocketThread#4](../../mfc/reference/codesnippet/cpp/csocket-class_1.cpp)]

> [!NOTE]
>  當使用靜態連結的 MFC 應用程式中的次要執行緒中的 MFC 通訊端，您必須呼叫`AfxSocketInit`中每個執行緒都使用通訊端進行初始化通訊端程式庫。 根據預設，`AfxSocketInit`只在主執行緒中呼叫。

如需詳細資訊，請參閱 < [MFC 中的 Windows Sockets](../../mfc/windows-sockets-in-mfc.md)， [Windows Sockets:搭配使用通訊端與封存](../../mfc/windows-sockets-using-sockets-with-archives.md)， [Windows Sockets:通訊端與封存的運作方式](../../mfc/windows-sockets-how-sockets-with-archives-work.md)， [Windows Sockets:作業的順序](../../mfc/windows-sockets-sequence-of-operations.md)， [Windows Sockets:使用封存的通訊端範例](../../mfc/windows-sockets-example-of-sockets-using-archives.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CAsyncSocket](../../mfc/reference/casyncsocket-class.md)

`CSocket`

## <a name="requirements"></a>需求

**標頭：** afxsock.h

##  <a name="attach"></a>  CSocket::Attach

呼叫此成員函式，來附加`hSocket`控制代碼`CSocket`物件。

```
BOOL Attach(SOCKET hSocket);
```

### <a name="parameters"></a>參數

*hSocket*<br/>
包含通訊端的控制代碼。

### <a name="return-value"></a>傳回值

如果函式成功，則為非零。

### <a name="remarks"></a>備註

通訊端控制代碼會儲存在物件的[m_hSocket](../../mfc/reference/casyncsocket-class.md#m_hsocket)資料成員。

如需詳細資訊，請參閱[Windows Sockets:搭配使用通訊端與封存](../../mfc/windows-sockets-using-sockets-with-archives.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCSocketThread#1](../../mfc/reference/codesnippet/cpp/csocket-class_2.h)]

[!code-cpp[NVC_MFCSocketThread#2](../../mfc/reference/codesnippet/cpp/csocket-class_3.cpp)]

[!code-cpp[NVC_MFCSocketThread#3](../../mfc/reference/codesnippet/cpp/csocket-class_4.cpp)]

##  <a name="cancelblockingcall"></a>  CSocket::CancelBlockingCall

呼叫此成員函式，以取消封鎖的呼叫正在進行中。

```
void CancelBlockingCall();
```

### <a name="remarks"></a>備註

此函式會取消任何未處理的封鎖作業，此通訊端。 原始的封鎖呼叫將會儘速終止 WSAEINTR 錯誤碼。

在封鎖的情況下`Connect`作業，只要可能，但它不可能被釋放，直到連接有完成 （並再重設） 的通訊端資源的 Windows Sockets 實作將會終止封鎖的呼叫或逾時。這很可能會注意到，只有當應用程式會立即嘗試開啟的新通訊端 （如果不有可用的任何通訊端），或連接到相同的對等項目。

而不取消任何作業`Accept`可以將通訊端保留處於不定狀態。 如果應用程式取消封鎖通訊端作業，唯一可能取決於應用程式能夠在通訊端上執行的作業是呼叫`Close`，不過其他作業可能在某些 Windows Sockets 實作上運作。 如果您希望應用程式的最大可攜性，您必須小心，不要仰賴後取消執行作業。

如需詳細資訊，請參閱[Windows Sockets:搭配使用通訊端與封存](../../mfc/windows-sockets-using-sockets-with-archives.md)。

##  <a name="create"></a>  CSocket::Create

呼叫**建立**之後建構通訊端物件建立 Windows 通訊端，並將它附加的成員函式。

```
BOOL Create(
    UINT nSocketPort = 0,
    int nSocketType = SOCK_STREAM,
    LPCTSTR lpszSocketAddress = NULL);
```

### <a name="parameters"></a>參數

*nSocketPort*<br/>
若要使用通訊端，或 0，如果您想要選取連接埠的 MFC 特定的連接埠。

*nSocketType*<br/>
SOCK_STREAM 或 SOCK_DGRAM。

*lpszSocketAddress*<br/>
包含連接的通訊端，小數點的數字，例如"128.56.22.8 」 的網路位址的字串指標。 將 NULL 傳遞此參數表示的字串`CSocket`應該接聽所有網路介面上的用戶端活動的執行個體。

### <a name="return-value"></a>傳回值

如果成功，函式，非零值。否則為 0，而特定的錯誤碼可以擷取呼叫`GetLastError`。

### <a name="remarks"></a>備註

`Create` 然後呼叫`Bind`繫結至指定的位址的通訊端。 支援下列通訊端類型：

- SOCK_STREAM 提供排序、 可靠、 雙向、 連接為基礎的位元組資料流。 用於網際網路位址家族中的傳輸控制通訊協定 (TCP)。

- SOCK_DGRAM 支援資料包，也就是無連線、 不可靠的固定 （一般為小型） 最大長度的緩衝區。 用於網際網路位址家族中的使用者資料包通訊協定 (UDP)。 若要使用此選項，您必須使用與通訊端`CArchive`物件。

    > [!NOTE]
    >  `Accept`成員函式會參考新的空白`CSocket`做為其參數的物件。 您必須先建構這個物件，然後再呼叫`Accept`。 請記住，如果這個通訊端物件超出範圍，連接會關閉。 請勿呼叫`Create`這個新的通訊端物件。

如需有關資料流和資料包通訊端的詳細資訊，請參閱文章[Windows Sockets:背景](../../mfc/windows-sockets-background.md)， [Windows Sockets:連接埠和通訊端位址](../../mfc/windows-sockets-ports-and-socket-addresses.md)，和[Windows Sockets:搭配使用通訊端與封存](../../mfc/windows-sockets-using-sockets-with-archives.md)。

##  <a name="csocket"></a>  CSocket::CSocket

建構 `CSocket` 物件。

```
CSocket();
```

### <a name="remarks"></a>備註

建構完成之後，您必須呼叫`Create`成員函式。

如需詳細資訊，請參閱[Windows Sockets:搭配使用通訊端與封存](../../mfc/windows-sockets-using-sockets-with-archives.md)。

##  <a name="fromhandle"></a>  CSocket::FromHandle

將指標傳回至`CSocket`物件。

```
static CSocket* PASCAL FromHandle(SOCKET hSocket);
```

### <a name="parameters"></a>參數

*hSocket*<br/>
包含通訊端的控制代碼。

### <a name="return-value"></a>傳回值

指標`CSocket`物件，則為 NULL，如果沒有任何`CSocket`物件附加至*hSocket*。

### <a name="remarks"></a>備註

如果指定通訊端控制代碼時`CSocket`物件沒有附加至控制代碼，此成員函式會傳回 NULL，而且不會建立暫存物件。

如需詳細資訊，請參閱[Windows Sockets:搭配使用通訊端與封存](../../mfc/windows-sockets-using-sockets-with-archives.md)。

##  <a name="isblocking"></a>  CSocket::IsBlocking

呼叫此成員函式，以判斷封鎖的呼叫是否在進行中。

```
BOOL IsBlocking();
```

### <a name="return-value"></a>傳回值

如果封鎖通訊端，為非零否則為 0。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[Windows Sockets:搭配使用通訊端與封存](../../mfc/windows-sockets-using-sockets-with-archives.md)。

##  <a name="onmessagepending"></a>  CSocket::OnMessagePending

覆寫此成員函式，從 Windows 中尋找特定的訊息，並在您的通訊端回應。

```
virtual BOOL OnMessagePending();
```

### <a name="return-value"></a>傳回值

非零值，如果已處理的訊息;否則為 0。

### <a name="remarks"></a>備註

這是一種進階可覆寫。

這個架構會呼叫`OnMessagePending`時通訊端會提取 Windows 訊息，讓您處理的訊息感興趣，您的應用程式的機會。 如需如何使用您的範例`OnMessagePending`，請參閱文章[Windows Sockets:從通訊端類別衍生](../../mfc/windows-sockets-deriving-from-socket-classes.md)。

如需詳細資訊，請參閱[Windows Sockets:搭配使用通訊端與封存](../../mfc/windows-sockets-using-sockets-with-archives.md)。

## <a name="see-also"></a>另請參閱

[CAsyncSocket 類別](../../mfc/reference/casyncsocket-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CAsyncSocket 類別](../../mfc/reference/casyncsocket-class.md)<br/>
[CSocketFile 類別](../../mfc/reference/csocketfile-class.md)
