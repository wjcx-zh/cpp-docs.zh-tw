---
title: "Windows Sockets： 從通訊端類別衍生 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- derived classes [MFC], from socket classes
- Windows Sockets [MFC], deriving from socket classes
- sockets [MFC], deriving from socket classes
ms.assetid: 3a26e67a-e323-433b-9b05-eca018799801
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 63f8b8f735b62c1cbfedd50320bf65cec5905632
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="windows-sockets-deriving-from-socket-classes"></a>Windows Sockets：從通訊端類別衍生
本文將說明一些您可以藉由從其中一個通訊端類別衍生您自己的類別取得的功能。  
  
 您可以將您自己的通訊端類別衍生自[CAsyncSocket](../mfc/reference/casyncsocket-class.md)或[CSocket](../mfc/reference/csocket-class.md)加入您自己的功能。 特別是，這些類別會提供一些您可以覆寫虛擬成員函式。 這些函數包括[OnReceive](../mfc/reference/casyncsocket-class.md#onreceive)， [OnSend](../mfc/reference/casyncsocket-class.md#onsend)， [OnAccept](../mfc/reference/casyncsocket-class.md#onaccept)， [OnConnect](../mfc/reference/casyncsocket-class.md#onconnect)，和[OnClose](../mfc/reference/casyncsocket-class.md#onclose)。 您可以利用它們提供網路事件發生時通知您衍生通訊端類別中覆寫函式。 架構會呼叫以通知您重要的通訊端事件，例如接收的資料，您可以開始讀取這些通知回撥函式。 如需通知函式的詳細資訊，請參閱[Windows Sockets： 通訊端告知](../mfc/windows-sockets-socket-notifications.md)。  
  
 此外，類別`CSocket`提供[OnMessagePending](../mfc/reference/csocket-class.md#onmessagepending)成員函式 (進階可覆寫)。 通訊端會提取 windows 訊息時，MFC 會呼叫此函式。 您可以覆寫`OnMessagePending`至從 Windows 中尋找特定的訊息，並予以回應。  
  
 預設版本`OnMessagePending`類別中提供`CSocket`會檢查訊息佇列`WM_PAINT`等候完成的封鎖呼叫時的訊息。 它會分派改善顯示品質的 [小畫家] 訊息。 除了用這種有用的項目，說明您可能會覆寫函式的其中一種方式自己。 另舉一例，請考慮使用`OnMessagePending`下列工作。 假設您在等候網路異動完成時顯示非強制回應對話方塊。 此對話方塊包含 [取消] 按鈕，使用者可使用取消花太長時間封鎖交易。 您`OnMessagePending`覆寫可能幫浦與這個非強制回應對話方塊相關的訊息。  
  
 在您`OnMessagePending`覆寫，傳回**TRUE**或呼叫的基底類別版本傳回`OnMessagePending`。 如果您仍然想要完成的工作執行，請呼叫基底類別版本。  
  
 如需詳細資訊，請參閱:  
  
-   [Windows Sockets：搭配使用通訊端與封存](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
-   [Windows Sockets：使用類別 CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Windows Sockets：封鎖](../mfc/windows-sockets-blocking.md)  
  
-   [Windows Sockets：位元組順序](../mfc/windows-sockets-byte-ordering.md)  
  
-   [Windows Sockets：轉換字串](../mfc/windows-sockets-converting-strings.md)  
  
## <a name="see-also"></a>請參閱  
 [MFC 中的 Windows Sockets](../mfc/windows-sockets-in-mfc.md)

