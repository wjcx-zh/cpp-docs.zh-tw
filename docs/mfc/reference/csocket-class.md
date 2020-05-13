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
ms.openlocfilehash: 730bea34354b008d641ecc28e7368f79efad12a7
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751162"
---
# <a name="csocket-class"></a>CSocket 類別

派生自`CAsyncSocket`繼承其 Windows 套接字 API 的封`CAsyncSocket`裝,並且表示比 物件更高的抽象級別。

## <a name="syntax"></a>語法

```
class CSocket : public CAsyncSocket
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[Socket::socket](#csocket)|建構 `CSocket` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[Socket::連線](#attach)|將 SOCKET 句柄`CSocket`附加到 物件。|
|[套接字::取消封鎖呼叫](#cancelblockingcall)|取消當前正在進行的阻塞呼叫。|
|[Socket::建立](#create)|創建套接字。|
|[套接字::從手柄](#fromhandle)|返回指向`CSocket`物件的指標,給定一個 SOCKET 句柄。|
|[套接字::正在阻塞](#isblocking)|確定阻止呼叫是否正在進行。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[Socket::開啟訊息掛起](#onmessagepending)|在等待阻塞調用完成時調用以處理掛起的消息。|

## <a name="remarks"></a>備註

`CSocket`與類`CSocketFile`一起`CArchive`工作 ,並管理數據的發送和接收。

物件`CSocket`還提供阻塞,這`CArchive`對於的同步操作至關重要。 `Receive`阻止函數,如`Send``ReceiveFrom`,`SendTo``Accept`、 和`CAsyncSocket`(全部繼承`WSAEWOULDBLOCK`自`CSocket`), 不會在 中返回錯誤。 相反,這些函數等待操作完成。 此外,如果`CancelBlockingCall`在這些函數之一處於阻塞時調用,則原始調用將終止與錯誤 WSAEINTR。

要使用`CSocket`物件,請調用建構函數,然後調`Create`用 以創建基礎 SOCKET 句柄(類型 SOCKET)。 建立流套接字`Create`的預設參數,但如果不將套接字`CArchive`與 物件一起使用,則可以指定一個參數來改為創建 datagram 套接字,或者綁定到特定埠以創建伺服器套接字。 使用`Connect`用戶端和`Accept`伺服器端連接到用戶端套接字。 然後創建一`CSocketFile`個物件並將其關聯到`CSocket`建構函數`CSocketFile`中的物件。 接下來,創建用於`CArchive`發送的物件和用於接收數據的物件(根據需要),然後將它們與`CSocketFile``CArchive`構造函數中的對象相關聯。 通信完成後,銷毀`CArchive`、`CSocketFile`物件`CSocket`。 在[Windows 套接字:背景](../../mfc/windows-sockets-background.md)) 一文中介紹了 SOCKET 數據類型。

使用`CArchive``CSocketFile``CSocket`和 時,`CSocket::Receive`可能會遇到 輸入`PumpMessages(FD_READ)`迴圈 (由 ) 等待請求的位元組數的情況。 這是因為 Windows 套接字僅允許每個FD_READ通知一個`CSocketFile``CSocket`recv 調用,並且允許每個FD_READ多個 recv 調用。 如果在沒有要讀取的數據時獲得FD_READ,應用程式將掛起。 如果您從未獲得另一個FD_READ,應用程式將停止通過套接字進行通信。

您可以按照如下方式解決此問題。 在`OnReceive`套接字類中,當`CAsyncSocket::IOCtl(FIONREAD, ...)`從套接字讀`Serialize`取的預期數據超過一個 TCP 數據包(網路介質的最大傳輸單元,通常至少 1096 位元組)時,在調用消息類的方法之前調用。 如果可用數據的大小小於所需大小,請等待接收所有數據,然後僅啟動讀取操作。

在下面的範例中,`m_dwExpected`是使用者希望接收的大約位元組數。 假定您在代碼的其他位置聲明它。

[!code-cpp[NVC_MFCSocketThread#4](../../mfc/reference/codesnippet/cpp/csocket-class_1.cpp)]

> [!NOTE]
> 在靜態連結的 MFC 應用程式中的輔助線程中使用 MFC`AfxSocketInit`套接字時,必須呼叫使用 socket 初始化套接字型檔的每個線程。 預設情況下,`AfxSocketInit`僅在主線程中呼叫。

有關詳細資訊,請參閱 MFC 中的[Windows 套接字](../../mfc/windows-sockets-in-mfc.md)[、Windows 套接字:使用帶存檔的套接字](../../mfc/windows-sockets-using-sockets-with-archives.md)[、Windows 套接字:具有存檔的 socket 的工作原理](../../mfc/windows-sockets-how-sockets-with-archives-work.md)[、Windows 套接字:操作順序](../../mfc/windows-sockets-sequence-of-operations.md)[、Windows 套接字:使用存檔的套接字示例](../../mfc/windows-sockets-example-of-sockets-using-archives.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CAsyncSocket](../../mfc/reference/casyncsocket-class.md)

`CSocket`

## <a name="requirements"></a>需求

**標題:** afxsock.h

## <a name="csocketattach"></a><a name="attach"></a>Socket::連線

調用此成員函數以將`hSocket`句柄附加到`CSocket`物件。

```
BOOL Attach(SOCKET hSocket);
```

### <a name="parameters"></a>參數

*hSocket*<br/>
包含套接字的句柄。

### <a name="return-value"></a>傳回值

如果函式成功，則為非零。

### <a name="remarks"></a>備註

SOCKET 句柄存儲在物件的[m_hSocket](../../mfc/reference/casyncsocket-class.md#m_hsocket)數據成員中。

有關詳細資訊,請參閱[Windows 通訊卡字:使用帶存檔的通訊字](../../mfc/windows-sockets-using-sockets-with-archives.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCSocketThread#1](../../mfc/reference/codesnippet/cpp/csocket-class_2.h)]

[!code-cpp[NVC_MFCSocketThread#2](../../mfc/reference/codesnippet/cpp/csocket-class_3.cpp)]

[!code-cpp[NVC_MFCSocketThread#3](../../mfc/reference/codesnippet/cpp/csocket-class_4.cpp)]

## <a name="csocketcancelblockingcall"></a><a name="cancelblockingcall"></a>套接字::取消封鎖呼叫

調用此成員函數以取消當前正在進行的阻塞呼叫。

```cpp
void CancelBlockingCall();
```

### <a name="remarks"></a>備註

此功能取消此套接字的任何未完成的阻塞操作。 原始阻塞調用將儘快終止與錯誤 WSAEINTR。

在阻塞`Connect`操作的情況下,Windows Sockets 實現將儘快終止阻塞調用,但在連接完成(然後重置)或超時之前,可能無法釋放套接字資源。僅當應用程式立即嘗試打開新套接字(如果沒有可用套接字)或連接到同一對等體時,這才可能明顯。

取消除任外的任何操作`Accept`都會使套接字處於不確定狀態。 如果應用程式取消對套接字的阻塞操作,則應用程式可以依賴於對套接字執行的唯一操作是調用`Close`,儘管其他操作可能在某些 Windows 套接字實現上工作。 如果希望應用程式具有最大可移植性,則必須小心不要依賴於取消後執行的操作。

有關詳細資訊,請參閱[Windows 通訊卡字:使用帶存檔的通訊字](../../mfc/windows-sockets-using-sockets-with-archives.md)。

## <a name="csocketcreate"></a><a name="create"></a>Socket::建立

在建構套接字物件後調用 **「創建**成員」函數以創建 Windows 套接字並附加它。

```
BOOL Create(
    UINT nSocketPort = 0,
    int nSocketType = SOCK_STREAM,
    LPCTSTR lpszSocketAddress = NULL);
```

### <a name="parameters"></a>參數

*nSocket連接埠*<br/>
要與套接字一起使用的特定埠,如果希望 MFC 選擇埠,則為 0。

*nSocket 類型*<br/>
SOCK_STREAM或SOCK_DGRAM。

*lpszSocket位址*<br/>
指向包含連接套接字的網路位址的字串的指標,虛線數位,如"128.56.22.8"。 傳遞此參數的 NULL 字串`CSocket`指示 實例應偵聽所有網路介面上的用戶端活動。

### <a name="return-value"></a>傳回值

如果函數成功,則非零;否則 0,可以通過`GetLastError`調用 檢索特定的錯誤代碼。

### <a name="remarks"></a>備註

`Create`然後調用`Bind`將套接字綁定到指定的位址。 支援以下通訊型態:

- SOCK_STREAM 提供序列化、可靠、雙向、基於連接的位元組流。 對互聯網位址系列使用傳輸控制協定 (TCP)。

- SOCK_DGRAM支援數據圖,這是固定(通常較小)最大長度的無連接不可靠的緩衝區。 對 Internet 位址系列使用使用者數據圖協定 (UDP)。 要使用此選項,不得將套接字與物件一`CArchive`起使用。

    > [!NOTE]
    >  成員`Accept`函數以引用新的`CSocket`空 物件作為其參數。 在調用`Accept`之前,必須構造此物件。 請記住,如果此套接字物件超出範圍,連接將關閉。 不要調用`Create`此新套接字物件。

有關串流和資料報 socket 的詳細資訊,請參閱[文章 Windows 套接字:背景](../../mfc/windows-sockets-background.md)[、Windows 通訊形字:連接埠和 socket 位址](../../mfc/windows-sockets-ports-and-socket-addresses.md),以及[Windows socket:使用帶存檔的 socket](../../mfc/windows-sockets-using-sockets-with-archives.md)。

## <a name="csocketcsocket"></a><a name="csocket"></a>Socket::socket

建構 `CSocket` 物件。

```
CSocket();
```

### <a name="remarks"></a>備註

構造後,必須調用`Create`成員函數。

有關詳細資訊,請參閱[Windows 通訊卡字:使用帶存檔的通訊字](../../mfc/windows-sockets-using-sockets-with-archives.md)。

## <a name="csocketfromhandle"></a><a name="fromhandle"></a>套接字::從手柄

返回指向`CSocket`物件的指標。

```
static CSocket* PASCAL FromHandle(SOCKET hSocket);
```

### <a name="parameters"></a>參數

*hSocket*<br/>
包含套接字的句柄。

### <a name="return-value"></a>傳回值

指向`CSocket`物件的指標,如果沒有附加到`CSocket`*hSocket*的物件,則為 NULL。

### <a name="remarks"></a>備註

當給定一個 SOCKET`CSocket`句柄 時,如果物件未附加到句柄,成員函數將返回 NULL,並且不創建臨時物件。

有關詳細資訊,請參閱[Windows 通訊卡字:使用帶存檔的通訊字](../../mfc/windows-sockets-using-sockets-with-archives.md)。

## <a name="csocketisblocking"></a><a name="isblocking"></a>套接字::正在阻塞

調用此成員函數以確定阻止呼叫是否正在進行。

```
BOOL IsBlocking();
```

### <a name="return-value"></a>傳回值

如果套接字阻塞,則非零;否則 0。

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[Windows 通訊卡字:使用帶存檔的通訊字](../../mfc/windows-sockets-using-sockets-with-archives.md)。

## <a name="csocketonmessagepending"></a><a name="onmessagepending"></a>Socket::開啟訊息掛起

重寫此成員函數以查找 Windows 中的特定消息,並在套接字中回應它們。

```
virtual BOOL OnMessagePending();
```

### <a name="return-value"></a>傳回值

處理消息時非零;否則 0。

### <a name="remarks"></a>備註

這是一個高級的可重寫。

框架在套`OnMessagePending`接字正在泵送 Windows 消息時調用,以便您有機會處理應用程式感興趣的消息。 有關如何使用`OnMessagePending`的示例,請參閱[Windows 套接字:從套接字類派生](../../mfc/windows-sockets-deriving-from-socket-classes.md)的文章。

有關詳細資訊,請參閱[Windows 通訊卡字:使用帶存檔的通訊字](../../mfc/windows-sockets-using-sockets-with-archives.md)。

## <a name="see-also"></a>另請參閱

[CAsyncSocket 類別](../../mfc/reference/casyncsocket-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CAsyncSocket 類別](../../mfc/reference/casyncsocket-class.md)<br/>
[CSocketFile 類別](../../mfc/reference/csocketfile-class.md)
