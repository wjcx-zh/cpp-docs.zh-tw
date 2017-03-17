---
title: "CSocket 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- WinSock CSocket class
- CSocket class
- SOCKET handle
- sockets classes
ms.assetid: 7f23c081-d24d-42e3-b511-8053ca53d729
caps.latest.revision: 30
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 451ea100dbf02e365204fe4fdf1c380e855d8231
ms.lasthandoff: 02/24/2017

---
# <a name="csocket-class"></a>CSocket 類別
衍生自`CAsyncSocket`、 繼承其封裝的 Windows Sockets api，並代表較高的抽象層級`CAsyncSocket`物件。  
  
## <a name="syntax"></a>語法  
  
```  
class CSocket : public CAsyncSocket  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CSocket::CSocket](#csocket)|建構 `CSocket` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CSocket::Attach](#attach)|附加**通訊端**的控制代碼`CSocket`物件。|  
|[CSocket::CancelBlockingCall](#cancelblockingcall)|取消目前正在進行封鎖呼叫。|  
|[CSocket::Create](#create)|建立通訊端。|  
|[CSocket::FromHandle](#fromhandle)|傳回的指標`CSocket`物件，指定**通訊端**處理。|  
|[CSocket::IsBlocking](#isblocking)|決定是否封鎖呼叫正在進行中。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CSocket::OnMessagePending](#onmessagepending)|等候鎖定的呼叫完成時呼叫擱置中訊息的程序。|  
  
## <a name="remarks"></a>備註  
 `CSocket`類別會搭配`CSocketFile`和`CArchive`管理傳送和接收資料。  
  
 A`CSocket`物件也會提供封鎖，因為這是同步作業的`CArchive`。 封鎖函式，例如`Receive`， `Send`， `ReceiveFrom`， `SendTo`，和`Accept`(全都繼承自`CAsyncSocket`)，不會傳回`WSAEWOULDBLOCK`錯誤`CSocket`。 相反地，這些函式會等候直到作業完成為止。 此外，原始的呼叫會終止，且錯誤`WSAEINTR`如果`CancelBlockingCall`時封鎖了其中一個這些函式會呼叫。  
  
 若要使用`CSocket`物件，請呼叫建構函式，然後呼叫`Create`建立基礎`SOCKET`處理 (型別`SOCKET`)。 預設參數`Create`建立資料流通訊端，但如果您不想要使用的通訊端與`CArchive`物件，您可以指定參數，以建立資料包通訊端，相反地，或繫結至特定連接埠，建立伺服器通訊端。 連接到用戶端通訊端使用`Connect`在用戶端和`Accept`伺服器端上。 然後建立`CSocketFile`物件，並將它來建立關聯`CSocket`物件存放至`CSocketFile`建構函式。 接下來，建立`CArchive`物件以傳送和接收資料 （視需要），然後將它們與`CSocketFile`物件存放至`CArchive`建構函式。 通訊完成時，終結`CArchive`， `CSocketFile`，和`CSocket`物件。 `SOCKET`文中所述的資料型別[Windows Sockets︰ 背景](../../mfc/windows-sockets-background.md)。  
  
 當您使用`CArchive`與`CSocketFile`和`CSocket`，您可能會發生的情況其中`CSocket::Receive`進入迴圈 (由`PumpMessages(FD_READ)`) 等待要求的位元組數量。 這是因為 Windows 通訊端可以只有一個接收呼叫每個 FD_READ 通知，但`CSocketFile`和`CSocket`允許每個 FD_READ 的多個接收呼叫。 如果您收到 FD_READ 可讀取的資料時，應用程式停止回應。 如果您永遠不會收到另一個 FD_READ，應用程式停止通訊端進行通訊。  
  
 您可以解決這個問題，如下所示。 在`OnReceive`您通訊端類別方法，呼叫`CAsyncSocket::IOCtl(FIONREAD, ...)`之前先呼叫`Serialize`訊息類別時從通訊端讀取預期的資料超過一個 TCP 封包 （最大傳輸單位網路中通常至少 1096 個位元組） 的大小的方法。 如果少於所需的可用的資料大小，等待接收，然後才開始讀取的作業的所有資料。  
  
 在下列範例中，`m_dwExpected`是近似的使用者希望接收的位元組數目。 假設您宣告它在其他地方在程式碼中。  
  
 [!code-cpp[NVC_MFCSocketThread #&4;](../../mfc/reference/codesnippet/cpp/csocket-class_1.cpp)]  
  
> [!NOTE]
>  當使用靜態連結的 MFC 應用程式中的次要執行緒中的 MFC 通訊端，您必須呼叫`AfxSocketInit`中使用通訊端初始化通訊端程式庫的每個執行緒。 根據預設，`AfxSocketInit`只能在主執行緒中呼叫。  
  
 如需詳細資訊，請參閱[MFC 中的 Windows Sockets](../../mfc/windows-sockets-in-mfc.md)， [Windows Sockets︰ 使用通訊端與封存](../../mfc/windows-sockets-using-sockets-with-archives.md)， [Windows Sockets︰ 如何使用通訊端與封存工作](../../mfc/windows-sockets-how-sockets-with-archives-work.md)， [Windows Sockets︰ 作業的順序](../../mfc/windows-sockets-sequence-of-operations.md)， [Windows Sockets︰ 通訊端使用封存的範例](../../mfc/windows-sockets-example-of-sockets-using-archives.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CAsyncSocket](../../mfc/reference/casyncsocket-class.md)  
  
 `CSocket`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxsock.h  
  
##  <a name="attach"></a>CSocket::Attach  
 呼叫此成員函式附加`hSocket`的控制代碼`CSocket`物件。  
  
```  
BOOL Attach(SOCKET hSocket);
```  
  
### <a name="parameters"></a>參數  
 `hSocket`  
 包含通訊端的控制代碼。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功，則為非零。  
  
### <a name="remarks"></a>備註  
 **通訊端**控制代碼會儲存在物件的[m_hSocket](../../mfc/reference/casyncsocket-class.md#m_hsocket)資料成員。  
  
 如需詳細資訊，請參閱[Windows Sockets︰ 使用通訊端與封存](../../mfc/windows-sockets-using-sockets-with-archives.md)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCSocketThread #&1;](../../mfc/reference/codesnippet/cpp/csocket-class_2.h)]  
  
 [!code-cpp[NVC_MFCSocketThread #&2;](../../mfc/reference/codesnippet/cpp/csocket-class_3.cpp)]  
  
 [!code-cpp[NVC_MFCSocketThread #&3;](../../mfc/reference/codesnippet/cpp/csocket-class_4.cpp)]  
  
##  <a name="cancelblockingcall"></a>CSocket::CancelBlockingCall  
 呼叫此成員函式取消正在進行中的封鎖呼叫。  
  
```  
void CancelBlockingCall();
```  
  
### <a name="remarks"></a>備註  
 此函式會取消任何未處理的封鎖作業，此通訊端。 原始的封鎖呼叫會儘速終止，且錯誤**WSAEINTR**。  
  
 在封鎖的情況下**連接**作業，Windows Sockets 實作會封鎖呼叫時終止，不過它可能不會釋放，直到連接已完成 （並再重設） 的通訊端資源或逾時。 這很可能會很明顯，只有當應用程式立即嘗試開啟新的通訊端 （如果沒有通訊端有的話），或連接到相同的對等。  
  
 取消任何作業以外的其他**接受**可能會讓通訊端處於不定狀態。 如果應用程式取消封鎖通訊端上的作業，唯一可能取決於應用程式可以在通訊端上執行的作業是呼叫**關閉**，不過其他作業可能在某些 Windows Sockets 實作上運作。 如果您的應用程式的最大的可攜性，您必須小心，不要在取消後執行作業而定。  
  
 如需詳細資訊，請參閱[Windows Sockets︰ 使用通訊端與封存](../../mfc/windows-sockets-using-sockets-with-archives.md)。  
  
##  <a name="create"></a>CSocket::Create  
 呼叫**建立**之後建構建立 Windows 通訊端，並將它附加到通訊端物件的成員函式。  
  
```  
BOOL Create(
    UINT nSocketPort = 0,  
    int nSocketType = SOCK_STREAM,  
    LPCTSTR lpszSocketAddress = NULL);
```  
  
### <a name="parameters"></a>參數  
 `nSocketPort`  
 如果您想選取的連接埠的 MFC 通訊端或 0 搭配使用特定通訊埠。  
  
 `nSocketType`  
 **SOCK_STREAM**或**SOCK_DGRAM**。  
  
 `lpszSocketAddress`  
 包含連線的通訊端，小數點的數字，例如 「&128;.56.22.8 」 的網路位址的字串指標。 傳遞**NULL**此參數表示的字串**CSocket**應接聽所有網路介面上的用戶端活動的執行個體。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功則為非零否則為 0 和特定的錯誤碼可以擷取藉由呼叫`GetLastError`。  
  
### <a name="remarks"></a>備註  
 **建立**接著會呼叫**繫結**繫結至指定的位址的通訊端。 支援下列通訊端類型︰  
  
- **SOCK_STREAM**來排序，提供可靠、 雙向、 連接為基礎的位元組資料流。 使用網際網路通訊協定家族的傳輸控制通訊協定 (TCP)。  
  
- **SOCK_DGRAM**支援資料流，也就是無連線、 不可靠的固定 （通常很小） 的最大長度的緩衝區。 使用使用者資料包通訊協定 (UDP) 的網際網路通訊協定家族。 若要使用此選項，您必須使用與通訊端`CArchive`物件。  
  
    > [!NOTE]
    >  **接受**成員函式會採用新的空白參考`CSocket`物件做為其參數。 您必須先建構這個物件，才能呼叫**接受**。 請記住，如果這個通訊端物件超出範圍，連接會關閉。 請勿呼叫**建立**對這個新通訊端物件。  
  
 如需資料流和資料包通訊端的詳細資訊，請參閱文章[Windows Sockets︰ 背景](../../mfc/windows-sockets-background.md)， [Windows Sockets︰ 連接埠和通訊端位址](../../mfc/windows-sockets-ports-and-socket-addresses.md)，和[Windows Sockets︰ 使用通訊端與封存](../../mfc/windows-sockets-using-sockets-with-archives.md)。  
  
##  <a name="csocket"></a>CSocket::CSocket  
 建構 `CSocket` 物件。  
  
```  
CSocket();
```  
  
### <a name="remarks"></a>備註  
 建構完成之後，您必須呼叫**建立**成員函式。  
  
 如需詳細資訊，請參閱[Windows Sockets︰ 使用通訊端與封存](../../mfc/windows-sockets-using-sockets-with-archives.md)。  
  
##  <a name="fromhandle"></a>CSocket::FromHandle  
 若要將指標傳回`CSocket`物件。  
  
```  
static CSocket* PASCAL FromHandle(SOCKET hSocket);
```  
  
### <a name="parameters"></a>參數  
 `hSocket`  
 包含通訊端的控制代碼。  
  
### <a name="return-value"></a>傳回值  
 指標`CSocket`物件，或**NULL**如果沒有任何`CSocket`物件附加至`hSocket`。  
  
### <a name="remarks"></a>備註  
 當指定時**通訊端**處理，如果`CSocket`物件沒有附加至控制代碼，成員函式會傳回**NULL**並不會建立暫存物件。  
  
 如需詳細資訊，請參閱[Windows Sockets︰ 使用通訊端與封存](../../mfc/windows-sockets-using-sockets-with-archives.md)。  
  
##  <a name="isblocking"></a>CSocket::IsBlocking  
 呼叫此成員函式，來判斷是否封鎖的呼叫正在進行中。  
  
```  
BOOL IsBlocking();
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果會封鎖通訊端。否則為 0。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[Windows Sockets︰ 使用通訊端與封存](../../mfc/windows-sockets-using-sockets-with-archives.md)。  
  
##  <a name="onmessagepending"></a>CSocket::OnMessagePending  
 若要從 Windows 尋找特定的訊息，並在您的通訊端回應此成員函式會覆寫。  
  
```  
virtual BOOL OnMessagePending();
```  
  
### <a name="return-value"></a>傳回值  
 已處理的訊息; 如果為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 這是進階可覆寫。  
  
 這個架構會呼叫`OnMessagePending`時通訊端會提取 Windows 訊息，讓您有機會處理您的應用程式的感興趣的訊息。 如需範例，您可以使用`OnMessagePending`，請參閱文章[Windows Sockets︰ 衍生自通訊端類別](../../mfc/windows-sockets-deriving-from-socket-classes.md)。  
  
 如需詳細資訊，請參閱[Windows Sockets︰ 使用通訊端與封存](../../mfc/windows-sockets-using-sockets-with-archives.md)。  
  
## <a name="see-also"></a>另請參閱  
 [CAsyncSocket 類別](../../mfc/reference/casyncsocket-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CAsyncSocket 類別](../../mfc/reference/casyncsocket-class.md)   
 [CSocketFile 類別](../../mfc/reference/csocketfile-class.md)

