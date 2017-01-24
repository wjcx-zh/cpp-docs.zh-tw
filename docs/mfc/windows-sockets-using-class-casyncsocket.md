---
title: "Windows Sockets：使用類別 CAsyncSocket | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CAsyncSocket"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAsyncSocket 類別, 程式設計模型"
  - "SOCKET 控制代碼"
  - "通訊端 [C++], 非同步作業"
  - "通訊端 [C++], 在 Unicode 和 MBCS 字串之間轉換"
  - "Windows Sockets [C++], 非同步"
  - "Windows Sockets [C++], 轉換 Unicode 和 MBCS 字串"
ms.assetid: 825dae17-7c1b-4b86-8d6c-da7f1afb5d8d
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Windows Sockets：使用類別 CAsyncSocket
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文說明如何使用 [CAsyncSocket](../mfc/reference/casyncsocket-class.md)類別。  請注意這個類別會封裝 Windows Sockets API 在較低層級。  `CAsyncSocket` 是供詳細知道網路通訊的程式設計人員使用，但想要回呼便利 Web 事件的告知。  根據這個假設，本文僅提供基本命令。  您可能要考慮使用 `CAsyncSocket` ，如果您想要 Windows Sockets 的方便處理 MFC 應用程式的多個網路通訊協定，但不想要犧牲彈性。  您可能也會認為您比您在使用 `CSocket`類別可以直接進行通訊得到更好的效率你詳細一般的選取模型。  
  
 `CAsyncSocket`詳細說明於 *MFC Reference* 中。  Visual C\+\+ 也提供 Windows Sockets 規格，位於 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]。  詳細資料保留給您。  Visual C\+\+ 不提供 `CAsyncSocket`的應用程式。  
  
 如果您不是高度平台學習的有關網路通訊並不想要的簡單方案，與 `CArchive` 物件的使用 [CSocket](../mfc/reference/csocket-class.md) 類別。  請參閱 [Windows Sockets:使用已封存的通訊端](../mfc/windows-sockets-using-sockets-with-archives.md) 以取得詳細資訊。  
  
 本文包括:  
  
-   建立和使用 `CAsyncSocket` 物件。  
  
-   [將 CAsyncSocket 的責任](#_core_your_responsibilities_with_casyncsocket)。  
  
##  <a name="_core_creating_and_using_a_casyncsocket_object"></a> 建立和使用 CAsyncSocket 物件  
  
#### 使用 CAsyncSocket  
  
1.  [CAsyncSocket](../mfc/reference/casyncsocket-class.md) 建構物件並使用物件建立基本的 **SOCKET** 控制代碼。  
  
     通訊端的建立遵循兩階段建構的 MFC 形式。  
  
     例如：  
  
     [!code-cpp[NVC_MFCSimpleSocket#3](../mfc/codesnippet/CPP/windows-sockets-using-class-casyncsocket_1.cpp)]  
  
     \-或\-  
  
     [!code-cpp[NVC_MFCSimpleSocket#4](../mfc/codesnippet/CPP/windows-sockets-using-class-casyncsocket_2.cpp)]  
  
     第一個建構函式不會在堆疊上的 `CAsyncSocket` 物件。  第二個建構函式會在堆積上配置 `CAsyncSocket` 。  上面第一個 [建立](../Topic/CAsyncSocket::Create.md) 呼叫使用預設參數建立資料流通訊端。  第二個 **Create** 呼叫會以指定的通訊埠和位址建立資料包通訊端。\(您可以使用任一建構方法的任何 **Create** 版本\)。  
  
     對 **Create** 的參數:  
  
    -   「Port」:短整數。  
  
         對於伺服器通訊，您必須指定通訊埠。  對於用戶端通訊端，通常會接受這個參數的預設值，讓 Windows Sockets 選取通訊埠。  
  
    -   通訊端類型: **SOCK\_STREAM** \(預設值\) 或 **SOCK\_DGRAM**。  
  
    -   通訊端位址「，例如「ftp.microsoft.com」或「128.56.22.8」。  
  
         這是您的網路上的 Internet Protocol \(IP\) 位址。  您可能永遠依賴此參數的預設值。  
  
     詞彙「Port」和「通訊端位址 [Windows Sockets:通訊埠和通訊端位址。](../mfc/windows-sockets-ports-and-socket-addresses.md)主題中說明。  
  
2.  如果通訊是用戶端，使用 [CAsyncSocket::Connect](../Topic/CAsyncSocket::Connect.md)，請連接至伺服器通訊端的通訊端，物件。  
  
     \-或\-  
  
     如果通訊是伺服器，請將通訊端開始接聽 \(以 [CAsyncSocket::Listen](../Topic/CAsyncSocket::Listen.md)\) 來自用戶端的連接嘗試。  當接收到連接要求後，接受它與 [CAsyncSocket::Accept](../Topic/CAsyncSocket::Accept.md)。  
  
     在接受連線建立之後，您可以執行這類工作與驗證密碼。  
  
    > [!NOTE]
    >  **Accept** 成員函式會取得新的，空的 `CSocket` 物件的參考做為它的參數。  在您呼叫 **Accept**之前，您必須建構此物件。  如果這個通訊端物件超出範圍，關閉連接。  不要呼叫這個新物件的通訊端 **Create** 。  如需範例，請參閱本文件的 [Windows Sockets:作業序列](../mfc/windows-sockets-sequence-of-operations.md)。  
  
3.  藉由呼叫 `CAsyncSocket` 物件成員執行與封裝 Windows Sockets API 函式的其他通訊端的通訊運作。  
  
     如需 Windows 《 *MFC 參考》中的*通訊端規格和 [CAsyncSocket](../mfc/reference/casyncsocket-class.md) 類別。  
  
4.  終結 `CAsyncSocket` 物件。  
  
     如果您在堆疊上建立通訊端物件，它的解構函式，在包含的函式超出範圍時。  使用 **new** 運算子，如果在堆積上的通訊端，物件，您必須負責使用 **delete** 運算子終結物件。  
  
     解構函式在終結物件前呼叫物件的 [關閉](../Topic/CAsyncSocket::Close.md) 成員函式。  
  
 如需這個序列的範例程式碼 \(實際上為 `CSocket` 物件\)，請參閱 [Windows Sockets:作業序列](../mfc/windows-sockets-sequence-of-operations.md)。  
  
##  <a name="_core_your_responsibilities_with_casyncsocket"></a> 您對 CAsyncSocket 的責任。  
 當您建立類別 [CAsyncSocket](../mfc/reference/casyncsocket-class.md)物件時，物件會封裝 Windows **SOCKET** 控制代碼並提供該控制代碼的作業。  當您使用 `CAsyncSocket`時，您必須處理可能會面臨，如果直接使用應用程式開發介面的問題。  例如：  
  
-   「封鎖」情節。  
  
-   傳送和接收的電腦之間的位元組順序差異。  
  
-   將以 Unicode 和多位元組字元集 \(MBCS\) 字串。  
  
 如需這些詞彙和其他資訊的定義，請參閱 [Windows Sockets:封鎖](../mfc/windows-sockets-blocking.md)， [Windows Sockets:位元組順序](../mfc/windows-sockets-byte-ordering.md)， [Windows Sockets:將字串轉換](../mfc/windows-sockets-converting-strings.md)。  
  
 儘管這些問題，類別 **CAsycnSocket** 可能就是正確的選擇，如果您的應用程式要求所有彈性和控制項可以取得。  否則，請考慮使用類別 `CSocket` 。  `CSocket` 隱藏您的許多詳細資料:它提取 Windows 訊息在封鎖呼叫期間讓您對 `CArchive`的存取，處理位元組順序差異字串轉換您的。  
  
 如需詳細資訊，請參閱：  
  
-   [Windows Sockets：背景](../mfc/windows-sockets-background.md)  
  
-   [Windows Sockets：資料流通訊端](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows Sockets：資料包通訊端](../mfc/windows-sockets-datagram-sockets.md)  
  
## 請參閱  
 [MFC 中的 Windows Sockets](../mfc/windows-sockets-in-mfc.md)