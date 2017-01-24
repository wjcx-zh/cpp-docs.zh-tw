---
title: "CSocket Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CSocket"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSocket class"
  - "SOCKET handle"
  - "sockets classes"
  - "WinSock CSocket class"
ms.assetid: 7f23c081-d24d-42e3-b511-8053ca53d729
caps.latest.revision: 30
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSocket Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

從 `CAsyncSocket`相比衍生，會繼承其 Windows Sockets API 的套件，並代表較高層級的抽象 `CAsyncSocket` 物件。  
  
## 語法  
  
```  
class CSocket : public CAsyncSocket  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CSocket::CSocket](../Topic/CSocket::CSocket.md)|建構 `CSocket` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CSocket::Attach](../Topic/CSocket::Attach.md)|附加 **SOCKET** 控制代碼 `CSocket` 物件。|  
|[CSocket::CancelBlockingCall](../Topic/CSocket::CancelBlockingCall.md)|取消目前正在進行中的一個封鎖的呼叫。|  
|[CSocket::Create](../Topic/CSocket::Create.md)|建立通訊端。|  
|[CSocket::FromHandle](../Topic/CSocket::FromHandle.md)|傳回的指標 `CSocket` 物件將 **SOCKET** 控制代碼。|  
|[CSocket::IsBlocking](../Topic/CSocket::IsBlocking.md)|判斷一個封鎖的呼叫是否正在進行中。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CSocket::OnMessagePending](../Topic/CSocket::OnMessagePending.md)|呼叫處理等待訊息，當等候一個封鎖呼叫完成時。|  
  
## 備註  
 `CSocket` 與類別一起使用 `CSocketFile` 和 `CArchive` 處理傳送和接收資料。  
  
 `CSocket` 物件也提供封鎖，對 `CArchive`的同步處理作業是非常重要的。  封鎖運作，例如 `Receive`， `Send`， `ReceiveFrom`， `SendTo`，因此， `Accept` \(所有繼承自 `CAsyncSocket`\)，不會在 `CSocket`的 `WSAEWOULDBLOCK` 錯誤。  相反地，這些函式等候，直到作業完成為止。  此外，原始呼叫會終止錯誤 `WSAEINTR` ，如果 `CancelBlockingCall` ，會呼叫這些函式之封鎖時。  
  
 若要使用 `CSocket` 物件，請呼叫建構函式，然後呼叫 `Create` 建立基本的 `SOCKET` 控制代碼 \(型別 `SOCKET`\)。  `Create` 預設參數建立資料流通訊端，，但是，如果您不使用有 `CArchive` 物件的通訊端，可以指定參數建立資料包通訊端，或是繫結至特定通訊埠建立伺服器通訊端。  用來在用戶端的在伺服器端，的 `Connect` 和 `Accept` 連接到用戶端通訊。  然後建立 `CSocketFile` 物件並將它設為 `CSocketFile` 建構函式的 `CSocket` 物件。  接下來，建立傳送的 `CArchive` 物件和一個收到的資料 \(視需要而定\)，然後讓它們與在 `CArchive` 建構函式的 `CSocketFile` 物件。  通訊物件完成後，將終結 `CArchive`、 `CSocketFile`和 `CSocket` 物件。  `SOCKET` 資料型別在文件 [Windows Sockets:背景](../../mfc/windows-sockets-background.md)說明。  
  
 當您使用 `CArchive` 和 `CSocketFile` 和 `CSocket`時，可能會遇到 `CSocket::Receive` 進入迴圈的條件 \( `PumpMessages(FD_READ)`\) 等待要求的數量 \(以位元組為單位\)。  這是因為， Windows Sockets 只允許每 FD\_READ 告知一個 recv 呼叫，不過， `CSocketFile` 和 `CSocket` 允許每 FD\_READ 的多個 recv 呼叫。  如果您取得 FD\_READ，當沒有讀取資料時，應用程式無回應。  如果您未從取得另一個 FD\_READ，應用程式會停止通訊的通訊端。  
  
 您可以下列方式來解決此問題。  在您的通訊端類別 `OnReceive` 方法，呼叫 `CAsyncSocket::IOCtl(FIONREAD, ...)` …\)，再呼叫您的訊息類別之前 `Serialize` 方法，當從通訊端要讀取的預期的資料超過一 TCP 封包 \(網路媒體，通常至少 1096 位元組的最大傳輸單位表示的大小\)。  如果可用資料的大小小於必要，請等候所有資料接收和該點開始讀取作業。  
  
 在下列範例中， `m_dwExpected` 是使用者所接收的大約位元組數目。  舉例來說，假設您在其他位置宣告它用於您的程式碼。  
  
 [!CODE [NVC_MFCSocketThread#4](../CodeSnippet/VS_Snippets_Cpp/NVC_MFCSocketThread#4)]  
  
> [!NOTE]
>  當使用 MFC 通訊端位於靜態連結至 MFC 應用程式的次要執行緒，您必須在使用通訊端初始化通訊端程式庫的每個執行緒的 `AfxSocketInit` 。  根據預設， `AfxSocketInit` 在主執行緒呼叫。  
  
 如需詳細資訊，請參閱 [在 MFC 中的 Windows Sockets](../../mfc/windows-sockets-in-mfc.md)，[Windows Sockets:使用具有檔案的通訊端](../../mfc/windows-sockets-using-sockets-with-archives.md)， [Windows Sockets:取得檔案的通訊端的運作方式](../../mfc/windows-sockets-how-sockets-with-archives-work.md)， [Windows Sockets:作業順序](../../mfc/windows-sockets-sequence-of-operations.md)， [Windows Sockets:通訊端的範例會使用檔案](../../mfc/windows-sockets-example-of-sockets-using-archives.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CAsyncSocket](../../mfc/reference/casyncsocket-class.md)  
  
 `CSocket`  
  
## 需求  
 **標題:** afxsock.h  
  
## 請參閱  
 [CAsyncSocket Class](../../mfc/reference/casyncsocket-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CAsyncSocket Class](../../mfc/reference/casyncsocket-class.md)   
 [CSocketFile Class](../../mfc/reference/csocketfile-class.md)