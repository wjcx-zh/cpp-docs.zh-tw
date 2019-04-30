---
title: Windows Sockets:使用類別 CAsyncSocket
ms.date: 11/04/2016
f1_keywords:
- CAsyncSocket
helpviewer_keywords:
- CAsyncSocket class [MFC], programming model
- Windows Sockets [MFC], asynchronous
- sockets [MFC], converting between Unicode and MBCS strings
- SOCKET handle
- sockets [MFC], asynchronous operation
- Windows Sockets [MFC], converting Unicode and MBCS strings
ms.assetid: 825dae17-7c1b-4b86-8d6c-da7f1afb5d8d
ms.openlocfilehash: 51274791393d95517bd8de5ae7248dc634018037
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399560"
---
# <a name="windows-sockets-using-class-casyncsocket"></a>Windows Sockets:使用類別 CAsyncSocket

這篇文章說明如何使用類別[CAsyncSocket](../mfc/reference/casyncsocket-class.md)。 請注意，這個類別會封裝 Windows Sockets API，在極低的層級。 `CAsyncSocket` 是以供程式設計人員知道詳細的網路通訊，但是想要的網路事件的通知回呼的便利性。 根據這項假設，本文提供基本的指令。 您可能應該考慮使用`CAsyncSocket`如果您想要處理的 MFC 應用程式中的多個網路通訊協定的 Windows 通訊端的簡易，但不是想要犧牲彈性。 您也可能會認為您可以直接自行比您無法使用類別的較通用的替代模型的程式設計更多通訊來取得較好的效率`CSocket`。

`CAsyncSocket` 記載於*MFC 參考 》*。 視覺化C++也提供 Windows Sockets 規格，位於 Windows SDK。 詳細資料會保留給您。 視覺化C++未提供的範例應用程式`CAsyncSocket`。

如果您不是高了解網路通訊，而且想要一個簡單的解決方案，使用類別[CSocket](../mfc/reference/csocket-class.md)使用`CArchive`物件。 請參閱[Windows Sockets:搭配使用通訊端與封存](../mfc/windows-sockets-using-sockets-with-archives.md)如需詳細資訊。

本文涵蓋：

- 建立和使用`CAsyncSocket`物件。

- [您的責任與 CAsyncSocket](#_core_your_responsibilities_with_casyncsocket)。

##  <a name="_core_creating_and_using_a_casyncsocket_object"></a> 建立和使用 CAsyncSocket 物件

#### <a name="to-use-casyncsocket"></a>若要使用 CAsyncSocket

1. 建構[CAsyncSocket](../mfc/reference/casyncsocket-class.md)物件，並使用物件來建立基礎**通訊端**處理。

   建立通訊端會遵循兩階段建構的 MFC 模式。

   例如：

   [!code-cpp[NVC_MFCSimpleSocket#3](../mfc/codesnippet/cpp/windows-sockets-using-class-casyncsocket_1.cpp)]

     -或-

   [!code-cpp[NVC_MFCSimpleSocket#4](../mfc/codesnippet/cpp/windows-sockets-using-class-casyncsocket_2.cpp)]

   上述的第一個建構函式會建立`CAsyncSocket`堆疊上的物件。 第二個建構函式建立`CAsyncSocket`在堆積上。 第一個[建立](../mfc/reference/casyncsocket-class.md#create)上述的呼叫會使用預設參數建立資料流通訊端。 第二個`Create`呼叫建立資料包通訊端與指定的連接埠和位址。 (您可以使用`Create`使用任一建構方法的版本。)

   參數以`Create`是：

   - 「 連接埠 」: 短整數。

         For a server socket, you must specify a port. For a client socket, you typically accept the default value for this parameter, which lets Windows Sockets select a port.

   - 通訊端類型：**SOCK_STREAM** （預設值） 或**SOCK_DGRAM**。

   - 通訊端 「 地址，「 例如 」 ftp.microsoft.com"或"128.56.22.8 」。

         This is your Internet Protocol (IP) address on the network. You will probably always rely on the default value for this parameter.

   詞彙 「 連接埠 」 和 「 通訊端位址 」 會在說明[Windows Sockets:連接埠和通訊端位址](../mfc/windows-sockets-ports-and-socket-addresses.md)。

1. 如果用戶端通訊端，通訊端物件連接到伺服器通訊端，使用[CAsyncSocket::Connect](../mfc/reference/casyncsocket-class.md#connect)。

     -或-

   如果通訊端是伺服器，設定以開始接聽通訊端 (使用[CAsyncSocket::Listen](../mfc/reference/casyncsocket-class.md#listen)) 從用戶端的連線嘗試。 收到連線要求，請接受它與[CAsyncSocket::Accept](../mfc/reference/casyncsocket-class.md#accept)。

   接受連接之後, 您可以執行像是驗證密碼這類工作。

    > [!NOTE]
    >  `Accept`成員函式會參考新的空白`CSocket`做為其參數的物件。 您必須先建構這個物件，然後再呼叫`Accept`。 如果這個通訊端物件超出範圍，連接就會關閉。 請勿呼叫`Create`這個新的通訊端物件。 如需範例，請參閱文章[Windows Sockets:作業順序](../mfc/windows-sockets-sequence-of-operations.md)。

1. 藉由呼叫完成與其他通訊端通訊`CAsyncSocket`封裝 Windows Sockets API 函式物件的成員函式。

   請參閱 Windows Sockets 規格和類別[CAsyncSocket](../mfc/reference/casyncsocket-class.md)中*MFC 參考 》*。

1. 終結`CAsyncSocket`物件。

   如果您是在堆疊上建立通訊端物件，包含函式超出範圍時，就是會呼叫其解構函式。 如果您在堆積上建立通訊端物件，使用**新**運算子，您必須負責使用**刪除**運算子來終結物件。

   解構函式呼叫物件的[關閉](../mfc/reference/casyncsocket-class.md#close)成員函式，然後再終結物件。

如需範例程式碼中這個序列的 (如實際`CSocket`物件)，請參閱[Windows 通訊端：作業順序](../mfc/windows-sockets-sequence-of-operations.md)。

##  <a name="_core_your_responsibilities_with_casyncsocket"></a> 您的責任與 CAsyncSocket

當您建立類別的物件[CAsyncSocket](../mfc/reference/casyncsocket-class.md)，該物件會封裝 Windows**通訊端**處理，並提供該控制代碼上的作業。 當您使用`CAsyncSocket`，您必須處理所有直接使用 API，可能會面臨的問題。 例如: 

- "中止安裝 」 的案例。

- 傳送及接收的機器之間的位元組順序差異。

- Unicode 及多位元組字元集之間轉換設定 (MBCS) 字串。

如需這些詞彙與其他資訊的定義，請參閱[Windows Sockets:封鎖](../mfc/windows-sockets-blocking.md)， [Windows Sockets:位元組順序](../mfc/windows-sockets-byte-ordering.md)， [Windows Sockets:將字串轉換](../mfc/windows-sockets-converting-strings.md)。

儘管有這些問題中，類別`CAsycnSocket`可能正確的選擇，如果您的應用程式需要所有的彈性和控制您可以取得。 如果沒有，您應該考慮使用類別`CSocket`改。 `CSocket` 會隱藏許多詳細資料，從您： 提取 Windows 訊息期間封鎖呼叫，並可讓您存取權的 it `CArchive`，其可管理位元組順序的差異和為您的字串轉換。

如需詳細資訊，請參閱:

- [Windows Socket：背景](../mfc/windows-sockets-background.md)

- [Windows Socket：資料流通訊端](../mfc/windows-sockets-stream-sockets.md)

- [Windows Socket：資料包通訊端](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>另請參閱

[MFC 中的 Windows Sockets](../mfc/windows-sockets-in-mfc.md)
