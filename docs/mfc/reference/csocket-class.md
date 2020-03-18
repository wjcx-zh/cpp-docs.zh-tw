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
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79421167"
---
# <a name="csocket-class"></a>CSocket 類別

衍生自 `CAsyncSocket`，繼承其 Windows 通訊端 API 的封裝，並代表比 `CAsyncSocket` 物件更高的抽象層級。

## <a name="syntax"></a>語法

```
class CSocket : public CAsyncSocket
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CSocket：： CSocket](#csocket)|建構 `CSocket` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CSocket：： Attach](#attach)|將通訊端控制碼附加至 `CSocket` 物件。|
|[CSocket：： CancelBlockingCall](#cancelblockingcall)|取消目前正在進行中的封鎖呼叫。|
|[CSocket：： Create](#create)|建立通訊端。|
|[CSocket：： FromHandle](#fromhandle)|指定通訊端控制碼，傳回 `CSocket` 物件的指標。|
|[CSocket：： IsBlocking](#isblocking)|判斷封鎖呼叫是否正在進行中。|

### <a name="protected-methods"></a>受保護的方法

|名稱|描述|
|----------|-----------------|
|[CSocket：： OnMessagePending](#onmessagepending)|呼叫以在等候封鎖呼叫完成時處理擱置中的訊息。|

## <a name="remarks"></a>備註

`CSocket` 可以與 `CSocketFile` 和 `CArchive` 的類別搭配使用，以管理資料的傳送和接收。

`CSocket` 物件也會提供封鎖，這對 `CArchive`的同步作業而言是不可或缺的。 封鎖函式（例如 `Receive`、`Send`、`ReceiveFrom`、`SendTo`和 `Accept` （全都繼承自 `CAsyncSocket`）不會傳回 `WSAEWOULDBLOCK` 中的 `CSocket`錯誤。 相反地，這些函式會等到作業完成。 此外，如果在其中一個函式被封鎖時呼叫 `CancelBlockingCall`，則原始呼叫將會以錯誤 WSAEINTR 終止。

若要使用 `CSocket` 物件，請呼叫此函式，然後呼叫 `Create` 以建立基礎通訊端控制碼（類型 SOCKET）。 `Create` 的預設參數會建立資料流程通訊端，但如果您不是使用具有 `CArchive` 物件的通訊端，您可以指定參數來建立資料包通訊端，或系結至特定埠以建立伺服器通訊端。 使用用戶端上的 `Connect` 連接到用戶端通訊端，並在伺服器端 `Accept`。 然後建立 `CSocketFile` 物件，並將它與 `CSocketFile` 的函式中的 `CSocket` 物件產生關聯。 接下來，建立一個用於傳送的 `CArchive` 物件，另一個用於接收資料（視需要），然後在 `CArchive` 的函式中將它們與 `CSocketFile` 物件建立關聯。 當通訊完成時，請終結 `CArchive`、`CSocketFile`和 `CSocket` 物件。 SOCKET 資料類型會在[Windows 通訊端：背景](../../mfc/windows-sockets-background.md)一文中說明。

當您使用 `CArchive` 搭配 `CSocketFile` 和 `CSocket`時，您可能會遇到 `CSocket::Receive` 進入迴圈（藉由 `PumpMessages(FD_READ)`）等候要求的位元組數量的情況。 這是因為 Windows 通訊端在每個 FD_READ 通知中只允許一個接收呼叫，但是 `CSocketFile` 和 `CSocket` 允許每個 FD_READ 多個接收呼叫。 如果您在沒有可讀取的資料時收到 FD_READ，應用程式會停止回應。 如果您從未取得另一個 FD_READ，應用程式會停止透過通訊端進行通訊。

您可以解決這個問題，如下所示。 在 socket 類別的 `OnReceive` 方法中，呼叫 `CAsyncSocket::IOCtl(FIONREAD, ...)`，然後在從通訊端讀取預期的資料超過一個 TCP 封包的大小（通常至少是1096個位元組）時呼叫 message 類別的 `Serialize` 方法。 如果可用資料的大小小於所需，請等候所有資料都被接收，然後才啟動讀取作業。

在下列範例中，`m_dwExpected` 是使用者預期接收的大約位元組數目。 假設您在程式碼中的其他位置宣告它。

[!code-cpp[NVC_MFCSocketThread#4](../../mfc/reference/codesnippet/cpp/csocket-class_1.cpp)]

> [!NOTE]
>  在靜態連結 MFC 應用程式的次要執行緒中使用 MFC 通訊端時，您必須在使用通訊端來初始化通訊端程式庫的每個執行緒中，呼叫 `AfxSocketInit`。 根據預設，只會在主要執行緒中呼叫 `AfxSocketInit`。

如需詳細資訊，請參閱[MFC 中的 Windows 通訊端](../../mfc/windows-sockets-in-mfc.md)、 [windows 通訊端：使用具有封存的通訊端](../../mfc/windows-sockets-using-sockets-with-archives.md)、 [windows Socket：具有封存的通訊端運作方式](../../mfc/windows-sockets-how-sockets-with-archives-work.md)、 [windows 套](../../mfc/windows-sockets-sequence-of-operations.md)接字：作業順序、 [Windows 通訊端：使用封存的通訊端範例](../../mfc/windows-sockets-example-of-sockets-using-archives.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CAsyncSocket](../../mfc/reference/casyncsocket-class.md)

`CSocket`

## <a name="requirements"></a>需求

**標頭：** afxsock。h

##  <a name="attach"></a>CSocket：： Attach

呼叫這個成員函式，將 `hSocket` 控制碼附加至 `CSocket` 物件。

```
BOOL Attach(SOCKET hSocket);
```

### <a name="parameters"></a>參數

*hSocket*<br/>
包含通訊端的控制碼。

### <a name="return-value"></a>傳回值

如果函式成功，則為非零。

### <a name="remarks"></a>備註

通訊端控制碼會儲存在物件的[m_hSocket](../../mfc/reference/casyncsocket-class.md#m_hsocket)資料成員中。

如需詳細資訊，請參閱[Windows socket：搭配使用通訊端與](../../mfc/windows-sockets-using-sockets-with-archives.md)封存。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCSocketThread#1](../../mfc/reference/codesnippet/cpp/csocket-class_2.h)]

[!code-cpp[NVC_MFCSocketThread#2](../../mfc/reference/codesnippet/cpp/csocket-class_3.cpp)]

[!code-cpp[NVC_MFCSocketThread#3](../../mfc/reference/codesnippet/cpp/csocket-class_4.cpp)]

##  <a name="cancelblockingcall"></a>CSocket：： CancelBlockingCall

呼叫這個成員函式可取消目前正在進行中的封鎖呼叫。

```
void CancelBlockingCall();
```

### <a name="remarks"></a>備註

此函式會取消此通訊端的任何未完成的封鎖作業。 原始的封鎖呼叫將會儘快終止，並會發生錯誤 WSAEINTR。

在封鎖 `Connect` 作業的情況下，Windows 通訊端執行會儘快終止封鎖呼叫，但可能無法釋放通訊端資源，直到連接完成（然後重設）或計時為止。只有當應用程式立即嘗試開啟新的通訊端（如果沒有可用的通訊端），或連接到相同的對等時，這可能會很明顯。

取消 `Accept` 以外的任何作業都可以讓通訊端處於不定狀態。 如果應用程式取消通訊端上的封鎖作業，應用程式唯一能夠在通訊端上執行的作業就是 `Close`的呼叫，雖然其他操作可能適用于某些 Windows 通訊端程式。 如果您想要讓應用程式具有最大的可攜性，您必須小心不要相依于取消之後執行的作業。

如需詳細資訊，請參閱[Windows socket：搭配使用通訊端與](../../mfc/windows-sockets-using-sockets-with-archives.md)封存。

##  <a name="create"></a>CSocket：： Create

在建立通訊端物件後呼叫**create**成員函式，以建立 Windows 通訊端並加以附加。

```
BOOL Create(
    UINT nSocketPort = 0,
    int nSocketType = SOCK_STREAM,
    LPCTSTR lpszSocketAddress = NULL);
```

### <a name="parameters"></a>參數

*nSocketPort*<br/>
要與通訊端搭配使用的特定埠，如果您想要讓 MFC 選取埠，則為0。

*nSocketType*<br/>
SOCK_STREAM 或 SOCK_DGRAM。

*lpszSocketAddress*<br/>
字串的指標，其中包含已連接之通訊端的網路位址，這是一個點的數位，例如 "128.56.22.8"。 傳遞這個參數的 Null 字串，表示 `CSocket` 實例應該接聽所有網路介面上的用戶端活動。

### <a name="return-value"></a>傳回值

如果函式成功，則為非零;否則，您可以藉由呼叫 `GetLastError`來抓取特定的錯誤碼。

### <a name="remarks"></a>備註

`Create` 接著會呼叫 `Bind`，將通訊端系結至指定的位址。 支援的通訊端類型如下：

- SOCK_STREAM 提供排序、可靠、雙向、以連接為基礎的位元組資料流程。 使用網際網路位址系列的傳輸控制通訊協定（TCP）。

- SOCK_DGRAM 支援資料包，其為固定（通常是小型）最大長度的無連接、不可靠的緩衝區。 使用使用者資料包協定（UDP）作為網際網路位址系列。 若要使用此選項，您不得使用具有 `CArchive` 物件的通訊端。

    > [!NOTE]
    >  `Accept` 成員函式會採用新的空白 `CSocket` 物件的參考做為其參數。 在呼叫 `Accept`之前，您必須先建立此物件。 請記住，如果此通訊端物件超出範圍，連接就會關閉。 請勿呼叫這個新通訊端物件的 `Create`。

如需串流和資料包通訊端的詳細資訊，請參閱[Windows 通訊端：背景](../../mfc/windows-sockets-background.md)、 [windows 通訊端：埠和通訊端位址](../../mfc/windows-sockets-ports-and-socket-addresses.md)和[Windows 通訊端：搭配使用通訊端與](../../mfc/windows-sockets-using-sockets-with-archives.md)封存的文章。

##  <a name="csocket"></a>CSocket：： CSocket

建構 `CSocket` 物件。

```
CSocket();
```

### <a name="remarks"></a>備註

在結構之後，您必須呼叫 `Create` 成員函式。

如需詳細資訊，請參閱[Windows socket：搭配使用通訊端與](../../mfc/windows-sockets-using-sockets-with-archives.md)封存。

##  <a name="fromhandle"></a>CSocket：： FromHandle

傳回 `CSocket` 物件的指標。

```
static CSocket* PASCAL FromHandle(SOCKET hSocket);
```

### <a name="parameters"></a>參數

*hSocket*<br/>
包含通訊端的控制碼。

### <a name="return-value"></a>傳回值

`CSocket` 物件的指標，如果沒有任何 `CSocket` 物件附加至*hSocket*，則為 Null。

### <a name="remarks"></a>備註

當指定通訊端控制碼時，如果 `CSocket` 物件未附加至控制碼，則成員函式會傳回 Null，而且不會建立暫存物件。

如需詳細資訊，請參閱[Windows socket：搭配使用通訊端與](../../mfc/windows-sockets-using-sockets-with-archives.md)封存。

##  <a name="isblocking"></a>CSocket：： IsBlocking

呼叫這個成員函式，以判斷封鎖呼叫是否正在進行中。

```
BOOL IsBlocking();
```

### <a name="return-value"></a>傳回值

如果通訊端正在封鎖，則為非零值;否則為0。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[Windows socket：搭配使用通訊端與](../../mfc/windows-sockets-using-sockets-with-archives.md)封存。

##  <a name="onmessagepending"></a>CSocket：： OnMessagePending

覆寫此成員函式以尋找來自 Windows 的特定訊息，並在您的通訊端中回應它們。

```
virtual BOOL OnMessagePending();
```

### <a name="return-value"></a>傳回值

如果已處理訊息，則為非零。否則為0。

### <a name="remarks"></a>備註

這是一個先進的可覆寫。

當通訊端提取 Windows 訊息時，架構會呼叫 `OnMessagePending`，讓您有機會處理您的應用程式感對的訊息。 如需如何使用 `OnMessagePending`的範例，請參閱[Windows socket：衍生自通訊端類別](../../mfc/windows-sockets-deriving-from-socket-classes.md)一文。

如需詳細資訊，請參閱[Windows socket：搭配使用通訊端與](../../mfc/windows-sockets-using-sockets-with-archives.md)封存。

## <a name="see-also"></a>另請參閱

[CAsyncSocket 類別](../../mfc/reference/casyncsocket-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CAsyncSocket 類別](../../mfc/reference/casyncsocket-class.md)<br/>
[CSocketFile 類別](../../mfc/reference/csocketfile-class.md)
