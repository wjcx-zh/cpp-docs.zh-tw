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
ms.openlocfilehash: d3fc32d9da54d9cf8c79e9e5de45b81c2ef64a6e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371962"
---
# <a name="windows-sockets-using-class-casyncsocket"></a>Windows Sockets：使用類別 CAsyncSocket

本文介紹如何使用類[CAsyncSocket。](../mfc/reference/casyncsocket-class.md) 請注意,此類在非常低的級別封裝 Windows 套接字 API。 `CAsyncSocket`供程式師使用,他們詳細瞭解網路通信,但希望回撥的便利性用於通知網路事件。 基於此假設,本文僅提供基本說明。 如果您希望 Windows`CAsyncSocket`套 接字在 MFC 應用程式中輕鬆處理多個網路協定,但不想犧牲靈活性,則可能需要考慮使用。 您可能還覺得,通過更直接地程式設計通信,您比使用更通用的類`CSocket`替代模型更直接地程式設計,可以獲得更好的效率。

`CAsyncSocket`記錄在*MFC 參考*中。 可視C++還提供位於Windows SDK中的Windows套接字規範。 詳情將留給你。 可視C++不提供`CAsyncSocket`的範例應用程式。

如果您對網路通訊瞭解不夠,並且想要一個簡單的解決方案,請使用類[CSocket](../mfc/reference/csocket-class.md)與`CArchive`物件。 有關詳細資訊[,請參閱 Windows 通訊卡字:使用帶存檔的 socket](../mfc/windows-sockets-using-sockets-with-archives.md)。

本文將說明：

- 創建和使用`CAsyncSocket`物件。

- [您在 CAsyncSocket 中的職責](#_core_your_responsibilities_with_casyncsocket)。

## <a name="creating-and-using-a-casyncsocket-object"></a><a name="_core_creating_and_using_a_casyncsocket_object"></a>建立與使用 CAsyncSocket 物件

#### <a name="to-use-casyncsocket"></a>使用 CAsyncSocket

1. 建構一個[CAsyncSocket](../mfc/reference/casyncsocket-class.md)物件,並使用 該物件創建基礎**SOCKET**句柄。

   套接字的創建遵循兩階段構造的 MFC 模式。

   例如：

   [!code-cpp[NVC_MFCSimpleSocket#3](../mfc/codesnippet/cpp/windows-sockets-using-class-casyncsocket_1.cpp)]

     -或-

   [!code-cpp[NVC_MFCSimpleSocket#4](../mfc/codesnippet/cpp/windows-sockets-using-class-casyncsocket_2.cpp)]

   上面的第一個構造函數在`CAsyncSocket`堆疊上創建一個物件。 第二個構造函數在`CAsyncSocket`堆上創建 一個。 上面的第一個[創建](../mfc/reference/casyncsocket-class.md#create)調用使用預設參數創建流套接字。 第二`Create`個調用創建具有指定埠和地址的數據報號套接字。 (您可以將任一`Create`版本與任一構造方法一起使用。

   要的`Create`參數是:

   - "埠":短整數。

      對於伺服器套接字,必須指定埠。 對於用戶端套接字,您通常接受此參數的預設值,該值允許 Windows 套接字選擇連接埠。

   - Socket 型**態 :SOCK_STREAM(** 預設值)或**SOCK_DGRAM。**

   - 套接字"位址",如"ftp.microsoft.com"或"128.56.22.8"。

      這是您的互聯網協定 (IP) 位址。 您可能始終依賴於此參數的預設值。

   術語「埠」和「套接字位址」在[Windows 套接字:埠和套接字位址)](../mfc/windows-sockets-ports-and-socket-addresses.md)中解釋。

1. 如果通訊形字是客戶端,請使用[CAsyncSocket::連接](../mfc/reference/casyncsocket-class.md#connect)將套接字物件連線到伺服器套接字:連接 。

     -或-

   如果套接字是伺服器,請將套接字設置為開始偵聽(使用[CAsyncSocket::LISTEN),](../mfc/reference/casyncsocket-class.md#listen)以便從用戶端進行連接嘗試。 收到連線要求後,請使用[CAsyncSocket 接受:接受](../mfc/reference/casyncsocket-class.md#accept)。

   接受連接後,可以執行驗證密碼等任務。

    > [!NOTE]
    >  成員`Accept`函數以引用新的`CSocket`空 物件作為其參數。 在調用`Accept`之前,必須構造此物件。 如果這個通訊端物件超出範圍，連接就會關閉。 不要調用`Create`此新套接字物件。 例如,請參考文章 Windows[通訊元字:操作序列](../mfc/windows-sockets-sequence-of-operations.md)。

1. 通過調用封裝 Windows 套`CAsyncSocket`接字 API 函數的物件成員函數,與其他套接字執行通信。

   請參閱*MFC 參考*中的 Windows 套接字規範和類[CAsyncSocket。](../mfc/reference/casyncsocket-class.md)

1. 銷毀`CAsyncSocket`物件。

   如果在堆疊上創建了套接字物件,則當包含函數超出範圍時,將調用其析構函數。 如果在堆上創建了套接字物件,請使用**新**運算元,則負責使用**delete**運算元銷毀該物件。

   析構函數在銷毀物件之前調用物件的[Close](../mfc/reference/casyncsocket-class.md#close)成員函數。

有關代碼中此序列的範例(實際上對於`CSocket`物件),請參閱 Windows[通訊串: 操作序列](../mfc/windows-sockets-sequence-of-operations.md)。

## <a name="your-responsibilities-with-casyncsocket"></a><a name="_core_your_responsibilities_with_casyncsocket"></a>您對 CAsyncSocket 的責任

創建類[CAsyncSocket](../mfc/reference/casyncsocket-class.md)的物件時,該物件封裝 Windows **SOCKET**句柄,並為此句柄提供操作。 使用`CAsyncSocket`時,必須處理直接使用 API 時可能面臨的所有問題。 例如：

- "阻止"方案。

- 發送和接收計算機之間的位元組訂單差異。

- 在 Unicode 和多位元組位元集 (MBCS) 字串之間進行轉換。

有關這些條款的定義和其他資訊,請參閱[Windows 套接字:阻止](../mfc/windows-sockets-blocking.md)[、Windows 通訊排序](../mfc/windows-sockets-byte-ordering.md)[、Windows 通訊排序、Windows 通訊排序、Windows 通訊排序、轉換字串](../mfc/windows-sockets-converting-strings.md)。

儘管存在這些問題,如果應用程式`CAsycnSocket`需要您可以獲得的所有靈活性和控制,類可能是您的最佳選擇。 如果沒有,則應考慮改用類`CSocket`。 `CSocket`隱藏了很多細節:它在阻止調用期間泵送 Windows 消息,並允許`CArchive`您訪問 ,該消息為您管理位元組順序差異和字串轉換。

如需詳細資訊，請參閱

- [Windows Sockets：背景](../mfc/windows-sockets-background.md)

- [Windows Sockets：資料流通訊端](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets：資料通訊端](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>另請參閱

[MFC 中的 Windows Sockets](../mfc/windows-sockets-in-mfc.md)
