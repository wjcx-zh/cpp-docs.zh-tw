---
title: "CSocketFile Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CSocketFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "archives [C++], 網路"
  - "CSocketFile class"
  - "networks [C++], archive"
  - "networks [C++], serializing to"
  - "序列化 [C++], 網路"
  - "SOCKET handle"
ms.assetid: 7924c098-5f72-40d6-989d-42800a47958f
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# CSocketFile Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供傳送和接收網路上的資料使用的 `CFile` 物件透過 Windows Sockets。  
  
## 語法  
  
```  
class CSocketFile : public CFile  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CSocketFile::CSocketFile](../Topic/CSocketFile::CSocketFile.md)|建構 `CSocketFile` 物件。|  
  
## 備註  
 您可以 `CSocket` 附加至物件的 `CSocketFile` 物件。  使用 MFC 序列化，您也可以將一般，附加至 `CArchive` 物件的 `CSocketFile` 物件簡化傳送和接收資料。  
  
 若要序列化 \(\) 傳送資料，您可以將該步驟順序插入檔案， `CSocketFile` 呼叫成員函式來 `CSocket` 物件寫入資料。  若要序列化 \(sInk\) 資料，您需要從這個檔案擷取物件。  這會讓此檔案稱為 `CSocketFile` 成員函式讀取 `CSocket` 物件的資料。  
  
> [!TIP]
>  除了使用之外 `CSocketFile` 如下所述，您可以使用它，獨立檔案物件，就可以使用 `CFile`，它的基底類別。  您也可以使用任何檔案架構的 MFC 序列化函式的 `CSocketFile` 。  由於 `CSocketFile` 不支援所有 `CFile` 的功能，某些預設序列化 MFC 函式和 `CSocketFile`相容。  這特別適用的 `CEditView` 類別。  您不應嘗試使用 `CEditView::SerializeRaw`附加至物件的 `CSocketFile` 一 `CArchive` 物件序列化 `CEditView` 資料;使用 **CEditView::Serialize** 。  `SerializeRaw` 函式要求檔案物件的函式，例如 `Seek`， `CSocketFile` 沒有。  
  
 當您使用 `CArchive` 和 `CSocketFile` 和 `CSocket`時，可能會遇到 **CSocket::Receive** 進入迴圈的條件 \( **PumpMessages\(FD\_READ\)**\) 等待要求的數量 \(以位元組為單位\)。  這是因為， Windows Sockets 只允許每 FD\_READ 告知一個 recv 呼叫，不過， `CSocketFile` 和 `CSocket` 允許每個 FD\_READ 的多個 recv 呼叫。  如果您取得 FD\_READ，當無法讀取資料時，應用程式無回應。  如果永遠不會被另一個 FD\_READ，應用程式會透過通訊端。  
  
 您可以依照下列方式來解決此問題。  在您的通訊端類別 `OnReceive` 方法，呼叫 **CAsyncSocket::IOCtl\(FIONREAD, ...\)** ，才能呼叫您的訊息類別之前 `Serialize` 方法，當從通訊端 \(Socket\) 要讀取的預期的資料超過一個 TCP 封包 \(Web 媒體，通常至少 1096 個位元組的最大傳輸單位的大小\)。  如果提供的資料大小比所需的是，請等候所有資料接收和該點開始讀取作業。  
  
 在下列範例中， `m_dwExpected` 是使用者預期收到的多少位元組數目。  舉例來說，假設您在其他位置宣告它用於您的程式碼。  
  
 [!CODE [NVC_MFCSocketThread#4](../CodeSnippet/VS_Snippets_Cpp/NVC_MFCSocketThread#4)]  
  
 如需詳細資訊，請參閱 [在 MFC 中的 Windows Sockets](../../mfc/windows-sockets-in-mfc.md)、 [Windows Sockets:使用具有檔案的通訊端](../../mfc/windows-sockets-using-sockets-with-archives.md)，以及 [Windows Sockets 2 API](http://msdn.microsoft.com/library/windows/desktop/ms740673)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [C 檔案](../../mfc/reference/cfile-class.md)  
  
 `CSocketFile`  
  
## 需求  
 **Header:** afxsock.h  
  
## 請參閱  
 [CFile Class](../../mfc/reference/cfile-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CAsyncSocket Class](../../mfc/reference/casyncsocket-class.md)   
 [CSocket Class](../../mfc/reference/csocket-class.md)