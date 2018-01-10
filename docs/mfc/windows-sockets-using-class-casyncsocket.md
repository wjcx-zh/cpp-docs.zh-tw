---
title: "Windows Sockets： 使用類別 CAsyncSocket |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CAsyncSocket
dev_langs: C++
helpviewer_keywords:
- CAsyncSocket class [MFC], programming model
- Windows Sockets [MFC], asynchronous
- sockets [MFC], converting between Unicode and MBCS strings
- SOCKET handle
- sockets [MFC], asynchronous operation
- Windows Sockets [MFC], converting Unicode and MBCS strings
ms.assetid: 825dae17-7c1b-4b86-8d6c-da7f1afb5d8d
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 41a1bf9e7b162ecfe9724f22996f8883d95cce72
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="windows-sockets-using-class-casyncsocket"></a>Windows Sockets：使用類別 CAsyncSocket
這篇文章說明如何使用類別[CAsyncSocket](../mfc/reference/casyncsocket-class.md)。 請注意，這個類別會封裝 Windows Sockets API，在非常低的層級。 `CAsyncSocket`是以供程式設計人員清楚詳細資料中的網路通訊，但想回呼的方便性，不論網路事件的通知。 根據這項假設，本文章提供基本的指令。 您可能應該考慮使用`CAsyncSocket`如果您想要處理的 MFC 應用程式中的多個網路通訊協定的 Windows Sockets 簡易，但不是想要犠牲彈性。 您也可能會認為可以直接自行比您無法使用模型類別的程式設計詳細的通訊，以取得更好的效率`CSocket`。  
  
 `CAsyncSocket`記載於*MFC 參考*。 Visual c + + 也提供 Windows Sockets 規格，位於 Windows SDK。 詳細資料會保留給您。 Visual c + + 不提供的範例應用程式`CAsyncSocket`。  
  
 如果您不是高了解網路通訊，而且需要較簡單的解決方案，使用類別[CSocket](../mfc/reference/csocket-class.md)與`CArchive`物件。 請參閱[Windows Sockets： 使用通訊端與封存](../mfc/windows-sockets-using-sockets-with-archives.md)如需詳細資訊。  
  
 本文涵蓋：  
  
-   建立和使用`CAsyncSocket`物件。  
  
-   [您的責任與 CAsyncSocket](#_core_your_responsibilities_with_casyncsocket)。  
  
##  <a name="_core_creating_and_using_a_casyncsocket_object"></a>建立和使用 CAsyncSocket 物件  
  
#### <a name="to-use-casyncsocket"></a>若要使用 CAsyncSocket  
  
1.  建構[CAsyncSocket](../mfc/reference/casyncsocket-class.md)物件，並使用物件來建立基礎**通訊端**處理。  
  
     建立通訊端的遵循兩階段建構的 MFC 模式。  
  
     例如:   
  
     [!code-cpp[NVC_MFCSimpleSocket#3](../mfc/codesnippet/cpp/windows-sockets-using-class-casyncsocket_1.cpp)]  
  
     -或-  
  
     [!code-cpp[NVC_MFCSimpleSocket#4](../mfc/codesnippet/cpp/windows-sockets-using-class-casyncsocket_2.cpp)]  
  
     上述第一個建構函式建立`CAsyncSocket`堆疊上的物件。 第二個建構函式建立`CAsyncSocket`在堆積上。 第一個[建立](../mfc/reference/casyncsocket-class.md#create)上述的呼叫會使用預設參數建立資料流通訊端。 第二個**建立**呼叫會使用指定的連接埠和位址建立資料包通訊端。 (您可以使用**建立**使用何種建構方法的版本。)  
  
     參數**建立**是：  
  
    -   「 連接埠 」: 短整數。  
  
         伺服器通訊端中，您必須指定連接埠。 用戶端通訊端中，您通常會接受此參數，可讓 Windows 通訊端選取的連接埠的預設值。  
  
    -   通訊端類型： **SOCK_STREAM** （預設值） 或**SOCK_DGRAM**。  
  
    -   通訊端 「 地址 」"ftp.microsoft.com"或"128.56.22.8"等。  
  
         這是您網路上的網際網路通訊協定 (IP) 位址。 您可能永遠會依賴預設值，這個參數。  
  
     詞彙 「 連接埠 」 和 「 通訊端位址 」 說明，請參閱[Windows Sockets： 連接埠和通訊端位址](../mfc/windows-sockets-ports-and-socket-addresses.md)。  
  
2.  如果用戶端通訊端，通訊端物件連接到伺服器通訊端，使用[CAsyncSocket::Connect](../mfc/reference/casyncsocket-class.md#connect)。  
  
     -或-  
  
     如果伺服器通訊端，設定要開始接聽通訊端 (使用[CAsyncSocket::Listen](../mfc/reference/casyncsocket-class.md#listen)) 從用戶端的連線嘗試。 在收到連線要求時，接受使用[CAsyncSocket::Accept](../mfc/reference/casyncsocket-class.md#accept)。  
  
     接受連接之後, 您可以執行像是驗證密碼這類工作。  
  
    > [!NOTE]
    >  **接受**成員函式會採用新的空白參考`CSocket`做為其參數的物件。 您必須先建構這個物件，才能呼叫**接受**。 如果這個通訊端物件超出範圍，連接就會關閉。 請勿呼叫**建立**對這個新通訊端物件。 如需範例，請參閱文章[Windows Sockets： 作業的順序](../mfc/windows-sockets-sequence-of-operations.md)。  
  
3.  藉由呼叫完成與其他通訊端通訊`CAsyncSocket`封裝 Windows Sockets API 函式物件的成員函式。  
  
     請參閱 Windows Sockets 規格和類別[CAsyncSocket](../mfc/reference/casyncsocket-class.md)中*MFC 參考*。  
  
4.  終結`CAsyncSocket`物件。  
  
     如果您是在堆疊上建立通訊端物件，包含函式超出範圍時呼叫其解構函式。 如果您在堆積上建立通訊端物件，使用**新**運算子，您必須負責使用**刪除**運算子終結物件。  
  
     解構函式呼叫物件的[關閉](../mfc/reference/casyncsocket-class.md#close)成員函式，然後再終結物件。  
  
 如需程式碼在此順序中的範例 (實際的`CSocket`物件)，請參閱[Windows Sockets： 作業的順序](../mfc/windows-sockets-sequence-of-operations.md)。  
  
##  <a name="_core_your_responsibilities_with_casyncsocket"></a>您的責任與 CAsyncSocket  
 當您建立類別的物件[CAsyncSocket](../mfc/reference/casyncsocket-class.md)，物件會封裝 Windows**通訊端**控制代碼並提供該控制代碼上的作業。 當您使用`CAsyncSocket`，您必須處理則可能會面臨如果直接使用 API 的所有問題。 例如:   
  
-   「 封鎖 」 的案例。  
  
-   在傳送與接收電腦之間的位元組順序差異。  
  
-   Unicode 及多位元組字元間的轉換設定 (MBCS) 字串。  
  
 如需這些詞彙與其他資訊的定義，請參閱[Windows Sockets： 封鎖](../mfc/windows-sockets-blocking.md)， [Windows Sockets： 位元組順序](../mfc/windows-sockets-byte-ordering.md)， [Windows Sockets： 轉換字串](../mfc/windows-sockets-converting-strings.md).  
  
 儘管有這些問題，類別**CAsycnSocket**可能會為您是適當的選擇，如果您的應用程式需要所有的彈性和您可以取得的控制項。 如果沒有，您應該考慮使用類別`CSocket`改為。 `CSocket`隱藏許多從您的詳細資料： it 提取 Windows 訊息期間封鎖呼叫，並可讓您存取`CArchive`，它負責管理位元組順序的差異，並為您的字串轉換。  
  
 如需詳細資訊，請參閱:  
  
-   [Windows Sockets：背景](../mfc/windows-sockets-background.md)  
  
-   [Windows Sockets：資料流通訊端](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows Sockets：資料通訊端](../mfc/windows-sockets-datagram-sockets.md)  
  
## <a name="see-also"></a>請參閱  
 [MFC 中的 Windows Sockets](../mfc/windows-sockets-in-mfc.md)

