---
title: "CAsyncSocket Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CAsyncSocket"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "asynchronous Windows Sockets"
  - "CAsyncSocket class"
  - "通訊 [C++], 網路"
  - "network communications"
  - "sockets [C++], Windows"
  - "Windows Sockets [C++], 非同步"
ms.assetid: cca4d5a1-aa0f-48bd-843e-ef0e2d7fc00b
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CAsyncSocket Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示 Windows Sockets —網路通訊端點。  
  
## 語法  
  
```  
class CAsyncSocket : public CObject  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CAsyncSocket::CAsyncSocket](../Topic/CAsyncSocket::CAsyncSocket.md)|建構 `CAsyncSocket` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CAsyncSocket::Accept](../Topic/CAsyncSocket::Accept.md)|在接受的通訊端連接。|  
|[CAsyncSocket::AsyncSelect](../Topic/CAsyncSocket::AsyncSelect.md)|要求通訊端的事件告知。|  
|[CAsyncSocket::Attach](../Topic/CAsyncSocket::Attach.md)|附加通訊端控制代碼。 `CAsyncSocket` 物件。|  
|[CAsyncSocket::Bind](../Topic/CAsyncSocket::Bind.md)|相關聯的本機位址的通訊端。|  
|[CAsyncSocket::Close](../Topic/CAsyncSocket::Close.md)|關閉通訊端。|  
|[CAsyncSocket::Connect](../Topic/CAsyncSocket::Connect.md)|建立與對等的通訊端連接。|  
|[CAsyncSocket::Create](../Topic/CAsyncSocket::Create.md)|建立通訊端。|  
|[CAsyncSocket::Detach](../Topic/CAsyncSocket::Detach.md)|中斷連結 `CAsyncSocket` 物件的其中一個通訊端控制代碼。|  
|[CAsyncSocket::FromHandle](../Topic/CAsyncSocket::FromHandle.md)|傳回指向 `CAsyncSocket` 物件將通訊端控制代碼。|  
|[CAsyncSocket::GetLastError](../Topic/CAsyncSocket::GetLastError.md)|取得失敗的最後一項作業的錯誤狀態。|  
|[CAsyncSocket::GetPeerName](../Topic/CAsyncSocket::GetPeerName.md)|取得通訊端連接對等的通訊端位址。|  
|[CAsyncSocket::GetPeerNameEx](../Topic/CAsyncSocket::GetPeerNameEx.md)|取得通訊端連接對等的通訊端位址 \(處理 IPv6 位址\)。|  
|[CAsyncSocket::GetSockName](../Topic/CAsyncSocket::GetSockName.md)|取得本機名稱通訊端。|  
|[CAsyncSocket::GetSockNameEx](../Topic/CAsyncSocket::GetSockNameEx.md)|取得本機名稱 \(通訊端控制代碼 IPv6 位址\)。|  
|[CAsyncSocket::GetSockOpt](../Topic/CAsyncSocket::GetSockOpt.md)|擷取通訊端選項。|  
|[CAsyncSocket::IOCtl](../Topic/CAsyncSocket::IOCtl.md)|控制通訊端的方式。|  
|[CAsyncSocket::Listen](../Topic/CAsyncSocket::Listen.md)|建立一個通訊端接聽連入連線要求。|  
|[CAsyncSocket::Receive](../Topic/CAsyncSocket::Receive.md)|從通訊端 \(Socket\) 接收的資料。|  
|[CAsyncSocket::ReceiveFrom](../Topic/CAsyncSocket::ReceiveFrom.md)|接收資料包以及儲存來源位址。|  
|[CAsyncSocket::ReceiveFromEx](../Topic/CAsyncSocket::ReceiveFromEx.md)|接收資料包以及儲存來源位址 \(處理 IPv6 位址\)。|  
|[CAsyncSocket::Send](../Topic/CAsyncSocket::Send.md)|將資料傳送至已連接的通訊端。|  
|[CAsyncSocket::SendTo](../Topic/CAsyncSocket::SendTo.md)|傳送資料至特定目的。|  
|[CAsyncSocket::SendToEx](../Topic/CAsyncSocket::SendToEx.md)|傳送資料至特定目的 \(處理 IPv6 位址\)。|  
|[CAsyncSocket::SetSockOpt](../Topic/CAsyncSocket::SetSockOpt.md)|將通訊端選項。|  
|[CAsyncSocket::ShutDown](../Topic/CAsyncSocket::ShutDown.md)|停用 **傳送** 和\/或通訊端上的 **接收** 呼叫。|  
|[CASyncSocket::Socket](../Topic/CASyncSocket::Socket.md)|配置一個通訊端控制代碼。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CAsyncSocket::OnAccept](../Topic/CAsyncSocket::OnAccept.md)|通知接聽通訊端可以接受暫止連接要求透過呼叫 **接受**。|  
|[CAsyncSocket::OnClose](../Topic/CAsyncSocket::OnClose.md)|告知通訊端 \(Socket\) 連接該管道已經關閉。|  
|[CAsyncSocket::OnConnect](../Topic/CAsyncSocket::OnConnect.md)|告知已連接的通訊端連接嘗試完成，是否成功或錯誤。|  
|[CAsyncSocket::OnOutOfBandData](../Topic/CAsyncSocket::OnOutOfBandData.md)|告知一個收到的通訊端的通訊端上要讀取的 Out\-of\-Band 資料，通常緊急的訊息。|  
|[CAsyncSocket::OnReceive](../Topic/CAsyncSocket::OnReceive.md)|通知接聽通訊端會呼叫將擷取的資料 **接收**。|  
|[CAsyncSocket::OnSend](../Topic/CAsyncSocket::OnSend.md)|告知通訊端就可以呼叫 **傳送**傳送資料。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CAsyncSocket::operator \=](../Topic/CAsyncSocket::operator%20=.md)|指派新值給 `CAsyncSocket` 物件。|  
|[CAsyncSocket::operator SOCKET](../Topic/CAsyncSocket::operator%20SOCKET.md)|使用本運算子的方式擷取 `CAsyncSocket`**SOCKET** 物件的控制代碼。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CAsyncSocket::m\_hSocket](../Topic/CAsyncSocket::m_hSocket.md)|表示要附加的 **SOCKET** 控制代碼傳遞給這個 `CAsyncSocket` 物件。|  
  
## 備註  
 類別 `CAsyncSocket` 封裝 Windows Sockets API 函式，提供物件導向的抽象提供想要與 MFC 一起使用 Windows Sockets 的程式設計人員。  
  
 這個類別會根據假設您已了解網路通訊。  您必須負責處理封鎖，位元組順序差異和呈現在 Unicode 和多位元組字元集 \(MBCS\) 的字串。  如果您要管理這些問題的更方便的介面，請參閱類別 [CSocket](../../mfc/reference/csocket-class.md)。  
  
 使用 `CAsyncSocket` 物件，呼叫它的建構函式，然後呼叫 [建立](../Topic/CAsyncSocket::Create.md) 函式建立基礎通訊端控制代碼 \(型別 `SOCKET`\)，但在接受的通訊端。  對於伺服器通訊端呼叫成員函式， [接聽](../Topic/CAsyncSocket::Listen.md) ，而且用戶端通訊端需要 [連接](../Topic/CAsyncSocket::Connect.md) 成員函式。  伺服器通訊端應要求 [接受](../Topic/CAsyncSocket::Accept.md) 函式接收到連接要求。  使用 \[剩餘 `CAsyncSocket` 函式執行通訊端之間的通訊。  在完成，請 `CAsyncSocket` 終結物件是在堆積上建立，解構函式自動呼叫 [關閉](../Topic/CAsyncSocket::Close.md) 函式。  `SOCKET` 資料型別在文件 [Windows Sockets:背景](../../mfc/windows-sockets-background.md)說明。  
  
> [!NOTE]
>  當使用 MFC 通訊端在靜態連結至 MFC 的應用程式時的次要執行緒，您必須在使用初始化通訊端 \(Socket\) 程式庫中每個執行緒的 `AfxSocketInit` 。  根據預設， `AfxSocketInit` 在主執行緒中呼叫。  
  
 如需詳細資訊，請參閱 [Windows Sockets:使用類別 CAsyncSocket](../../mfc/windows-sockets-using-class-casyncsocket.md) 和相關文件。 [Windows Sockets 2 API](http://msdn.microsoft.com/library/windows/desktop/ms740673)，以及。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CAsyncSocket`  
  
## 需求  
 **標題:** afxsock.h  
  
## 請參閱  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CSocket Class](../../mfc/reference/csocket-class.md)   
 [CSocketFile Class](../../mfc/reference/csocketfile-class.md)