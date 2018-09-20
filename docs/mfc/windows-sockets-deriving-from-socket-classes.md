---
title: Windows Sockets： 從通訊端類別衍生 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- derived classes [MFC], from socket classes
- Windows Sockets [MFC], deriving from socket classes
- sockets [MFC], deriving from socket classes
ms.assetid: 3a26e67a-e323-433b-9b05-eca018799801
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c562a8d6bf1c3f00f3812f6c25a4afd70276c64f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46418953"
---
# <a name="windows-sockets-deriving-from-socket-classes"></a>Windows Sockets：從通訊端類別衍生

本文說明一些您可以取得其中一個通訊端類別衍生您自己的類別的功能。

您可以將您自己的通訊端類別衍生自[CAsyncSocket](../mfc/reference/casyncsocket-class.md)或是[CSocket](../mfc/reference/csocket-class.md)新增您自己的功能。 特別是，這些類別會提供一些您可以覆寫的虛擬成員函式。 這些函式包含[OnReceive](../mfc/reference/casyncsocket-class.md#onreceive)， [OnSend](../mfc/reference/casyncsocket-class.md#onsend)， [OnAccept](../mfc/reference/casyncsocket-class.md#onaccept)， [OnConnect](../mfc/reference/casyncsocket-class.md#onconnect)，以及[OnClose](../mfc/reference/casyncsocket-class.md#onclose)。 您可以在您的衍生通訊端類別，以善用網路事件發生時提供通知，以覆寫函式。 架構會呼叫以通知您重要的通訊端的事件，例如收到資料，您可以開始讀取這些通知回撥函式。 如需通知函式的詳細資訊，請參閱[Windows Sockets： 通訊端告知](../mfc/windows-sockets-socket-notifications.md)。

此外，類別`CSocket`提供[OnMessagePending](../mfc/reference/csocket-class.md#onmessagepending)成員函式 (一種進階可覆寫)。 MFC 通訊端會提取 Windows 為基礎的訊息時，呼叫此函式。 您可以覆寫`OnMessagePending`從 Windows 中尋找特定的訊息並加以回應。

預設版本`OnMessagePending`類別中提供`CSocket`等待封鎖的呼叫完成時檢查 WM_PAINT 訊息的訊息佇列。 它會分派改善顯示品質的繪製訊息。 除了執行一些有用的事，這說明您可能會覆寫函式的其中一個方法您自己。 另舉一例，請考慮使用`OnMessagePending`下列工作。 假設您在等候網路異動完成時顯示非強制回應對話方塊。 對話方塊會包含使用者可用來取消花太多時間的封鎖交易 [取消] 按鈕。 您`OnMessagePending`覆寫可能會提取與這個非強制回應對話方塊中的訊息。

在您`OnMessagePending`覆寫，傳回 **，則為 TRUE**或呼叫的基底類別版本傳回`OnMessagePending`。 如果它不會執行您仍想完成的工作，請呼叫基底類別版本。

如需詳細資訊，請參閱:

- [Windows Sockets：搭配使用通訊端與封存](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows Sockets：使用類別 CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets：封鎖](../mfc/windows-sockets-blocking.md)

- [Windows Sockets：位元組順序](../mfc/windows-sockets-byte-ordering.md)

- [Windows Sockets：轉換字串](../mfc/windows-sockets-converting-strings.md)

## <a name="see-also"></a>另請參閱

[MFC 中的 Windows Sockets](../mfc/windows-sockets-in-mfc.md)

