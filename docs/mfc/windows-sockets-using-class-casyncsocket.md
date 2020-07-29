---
title: Windows Sockets：使用類別 CAsyncSocket
ms.date: 11/04/2016
helpviewer_keywords:
- CAsyncSocket class [MFC], programming model
- Windows Sockets [MFC], asynchronous
- sockets [MFC], converting between Unicode and MBCS strings
- SOCKET handle
- sockets [MFC], asynchronous operation
- Windows Sockets [MFC], converting Unicode and MBCS strings
ms.assetid: 825dae17-7c1b-4b86-8d6c-da7f1afb5d8d
ms.openlocfilehash: 6a3b3469b908eaf6f8062b8db7fc4287606b7f02
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228501"
---
# <a name="windows-sockets-using-class-casyncsocket"></a>Windows Sockets：使用類別 CAsyncSocket

本文說明如何使用 [類別[CAsyncSocket](../mfc/reference/casyncsocket-class.md)]。 請注意，這個類別會以非常低的層級封裝 Windows 通訊端 API。 `CAsyncSocket`適用于詳細瞭解網路通訊的程式設計人員，但想要回呼以取得網路事件通知的便利性。 根據這項假設，本文只提供基本的指示。 `CAsyncSocket`如果您想要讓 Windows 通訊端輕鬆處理 MFC 應用程式中的多個網路通訊協定，但不想犧牲彈性，您應該考慮使用。 您可能也覺得您可以更直接地對通訊進行程式設計，而不是使用更通用的類別替代模型，以獲得更好的效率 `CSocket` 。

`CAsyncSocket`已記載于*MFC 參考*中。 Visual C++ 也會提供位於 Windows SDK 的 Windows 通訊端規格。 詳細資料會留給您。 Visual C++ 不會提供的範例應用程式 `CAsyncSocket` 。

如果您不太熟悉網路通訊，而且想要簡單的解決方案，請使用類別[CSocket](../mfc/reference/csocket-class.md)搭配 `CArchive` 物件。 如需詳細資訊，請參閱[Windows 通訊端：使用具有封存的通訊端](../mfc/windows-sockets-using-sockets-with-archives.md)。

本文將說明：

- 建立和使用 `CAsyncSocket` 物件。

- [您對 CAsyncSocket 的責任](#_core_your_responsibilities_with_casyncsocket)。

## <a name="creating-and-using-a-casyncsocket-object"></a><a name="_core_creating_and_using_a_casyncsocket_object"></a>建立和使用 CAsyncSocket 物件

#### <a name="to-use-casyncsocket"></a>若要使用 CAsyncSocket

1. 建立[CAsyncSocket](../mfc/reference/casyncsocket-class.md)物件，並使用物件來建立基礎**通訊端**控制碼。

   建立通訊端時，會遵循兩階段結構的 MFC 模式。

   例如：

   [!code-cpp[NVC_MFCSimpleSocket#3](../mfc/codesnippet/cpp/windows-sockets-using-class-casyncsocket_1.cpp)]

     -或-

   [!code-cpp[NVC_MFCSimpleSocket#4](../mfc/codesnippet/cpp/windows-sockets-using-class-casyncsocket_2.cpp)]

   上述第一個函式會 `CAsyncSocket` 在堆疊上建立物件。 第二個函式會 `CAsyncSocket` 在堆積上建立。 上述第一個[Create](../mfc/reference/casyncsocket-class.md#create)呼叫會使用預設參數來建立資料流程通訊端。 第二個 `Create` 呼叫會使用指定的埠和位址來建立資料包通訊端。 （您可以使用任一 `Create` 版本搭配任一種結構方法）。

   的參數為 `Create` ：

   - 「埠」：短整數。

      若為伺服器通訊端，您必須指定埠。 針對用戶端通訊端，您通常會接受此參數的預設值，這可讓 Windows Socket 選取埠。

   - 通訊端類型： **SOCK_STREAM** （預設值）或**SOCK_DGRAM**。

   - 通訊端「位址」，例如 "ftp.microsoft.com" 或 "128.56.22.8"。

      這是您網路上的網際網路通訊協定（IP）位址。 您可能一律會依賴此參數的預設值。

   「埠」和「通訊端位址」等詞彙會在[Windows socket：埠和通訊端位址](../mfc/windows-sockets-ports-and-socket-addresses.md)中說明。

1. 如果通訊端是用戶端，請使用[CAsyncSocket：： connect](../mfc/reference/casyncsocket-class.md#connect)，將通訊端物件連接到伺服器通訊端。

     -或-

   如果通訊端是伺服器，請設定通訊端以開始接聽來自用戶端的連接嘗試（使用[CAsyncSocket：：接聽](../mfc/reference/casyncsocket-class.md#listen)）。 收到連線要求時，請使用[CAsyncSocket：： accept](../mfc/reference/casyncsocket-class.md#accept)接受它。

   接受連線之後，您可以執行這類工作來驗證密碼。

    > [!NOTE]
    >  成員函式 `Accept` 會採用新的空白物件的參考 `CSocket` 做為其參數。 在呼叫之前，您必須先建立這個物件 `Accept` 。 如果這個通訊端物件超出範圍，連接就會關閉。 請勿呼叫 `Create` 這個新通訊端物件的。 如需範例，請參閱[Windows socket：作業序列一](../mfc/windows-sockets-sequence-of-operations.md)文。

1. 藉由呼叫 `CAsyncSocket` 封裝 Windows 通訊端 API 函式的物件成員函式，執行與其他通訊端的通訊。

   請參閱*MFC 參考*中的 Windows 通訊端規格和類別[CAsyncSocket](../mfc/reference/casyncsocket-class.md) 。

1. 終結 `CAsyncSocket` 物件。

   如果您在堆疊上建立了通訊端物件，當包含的函式超出範圍時，就會呼叫其析構函數。 如果您使用運算子在堆積上建立通訊端物件， **`new`** 您必須負責使用 **`delete`** 運算子來終結物件。

   在終結物件之前，此析構函數會呼叫物件的[Close](../mfc/reference/casyncsocket-class.md#close)成員函式。

如需程式碼中此順序的範例（實際用於 `CSocket` 物件），請參閱[Windows Socket：作業順序](../mfc/windows-sockets-sequence-of-operations.md)。

## <a name="your-responsibilities-with-casyncsocket"></a><a name="_core_your_responsibilities_with_casyncsocket"></a>您的 CAsyncSocket 責任

當您建立[CAsyncSocket](../mfc/reference/casyncsocket-class.md)類別的物件時，物件會封裝 Windows**通訊端**控制碼，並在該控制碼上提供作業。 當您使用時 `CAsyncSocket` ，如果您直接使用 API，就必須處理您可能面臨的所有問題。 例如：

- 「封鎖」案例。

- 傳送和接收電腦之間的位元組順序差異。

- 在 Unicode 和多位元組字元集（MBCS）字串之間轉換。

如需這些詞彙和其他資訊的定義，請參閱[Windows 通訊端：封鎖](../mfc/windows-sockets-blocking.md)、 [windows 通訊端：位元組順序](../mfc/windows-sockets-byte-ordering.md)、 [Windows 通訊端：轉換字串](../mfc/windows-sockets-converting-strings.md)。

雖然有這些問題，但 `CAsycnSocket` 如果您的應用程式需要所有的彈性和控制能力，類別可能是正確的選擇。 如果不是，您應該考慮改為使用 class `CSocket` 。 `CSocket`從您隱藏許多詳細資料：它會在封鎖呼叫期間提取 Windows 訊息，並讓您存取 `CArchive` ，這會為您管理位元組順序差異和字串轉換。

如需詳細資訊，請參閱

- [Windows Socket：背景](../mfc/windows-sockets-background.md)

- [Windows 通訊端：資料流程通訊端](../mfc/windows-sockets-stream-sockets.md)

- [Windows 通訊端：資料包通訊端](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>另請參閱

[MFC 中的 Windows Sockets](../mfc/windows-sockets-in-mfc.md)
