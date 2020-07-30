---
title: Windows Sockets：位元組順序
ms.date: 11/04/2016
helpviewer_keywords:
- byte order issues in sockets programming
- sockets [MFC], byte order issues
- Windows Sockets [MFC], byte order issues
ms.assetid: 8a787a65-f9f4-4002-a02f-ac25a5dace5d
ms.openlocfilehash: f00936f3de07df8c1e4d9df1c678b2cfd5f3e3ad
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226798"
---
# <a name="windows-sockets-byte-ordering"></a>Windows Sockets：位元組順序

本文和兩個方針手冊說明了 Windows Sockets 程式設計的幾個問題。 本文涵蓋位元組順序。 其他問題會在文章： [Windows socket：封鎖](../mfc/windows-sockets-blocking.md)和[Windows 通訊端：轉換字串](../mfc/windows-sockets-converting-strings.md)中討論。

如果您使用或衍生自類別[CAsyncSocket](../mfc/reference/casyncsocket-class.md)，您就必須自行管理這些問題。 如果您使用或衍生自類別[CSocket](../mfc/reference/csocket-class.md)，MFC 會為您管理這些專案。

## <a name="byte-ordering"></a>位元組順序

不同的電腦架構有時候會使用不同的位元組順序來儲存資料。 例如，Intel 電腦會依照 Macintosh （Motorola）電腦的反向順序來儲存資料。 Intel 位元組順序（稱為「小位元組序」）也是網路標準「位元組由小到大」順序的反向。 下表說明這些詞彙。

### <a name="big--and-little-endian-byte-ordering"></a>以大到小的位元組序排序

|位元組順序|意義|
|-------------------|-------------|
|位元組由大到小|最重要的位元組是在單字的左邊。|
|位元組由大到小|最重要的位元組是在單字的右端。|

一般來說，您不需要擔心您透過網路傳送和接收之資料的位元組順序轉換，但在某些情況下，您必須轉換位元組順序。

## <a name="when-you-must-convert-byte-orders"></a>當您必須轉換位元組順序時

在下列情況下，您必須轉換位元組順序：

- 您所傳遞的資訊必須由網路來解讀，而不是您要傳送至另一部電腦的資料。 例如，您可能會傳遞網路必須瞭解的埠和位址。

- 您用來通訊的伺服器應用程式不是 MFC 應用程式（而且您沒有它的原始程式碼）。 如果這兩部電腦不會共用相同的位元組順序，這會呼叫位元組順序轉換。

## <a name="when-you-do-not-have-to-convert-byte-orders"></a>當您不需要轉換位元組順序時

在下列情況下，您可以避免轉換位元組順序的工作：

- 兩端的機器可以同意不要交換位元組，而且這兩部電腦都使用相同的位元組順序。

- 您要與之通訊的伺服器是 MFC 應用程式。

- 您有正在進行通訊之伺服器的原始程式碼，因此您可以明確地判斷是否必須轉換位元組順序。

- 您可以將伺服器移植到 MFC。 這相當容易，而且結果通常較小，程式碼更快。

使用[CAsyncSocket](../mfc/reference/casyncsocket-class.md)時，您必須自行管理任何必要的位元組順序轉換。 Windows 通訊端會標準化「位元組由大到小」的位元組順序模型，並提供可在此順序和其他專案之間轉換的函式。 但是，您與[CSocket](../mfc/reference/csocket-class.md)搭配使用的[CArchive](../mfc/reference/carchive-class.md)會使用相反的（「不是位元組）」順序，但 `CArchive` 會為您處理位元組順序轉換的詳細資料。 藉由在您的應用程式中使用此標準順序，或使用 Windows 通訊端位元組順序轉換函式，您就可以使程式碼更具可攜性。

使用 MFC 通訊端的理想情況是，當您撰寫兩個通訊端點時：在兩端使用 MFC。 如果您撰寫的應用程式將與非 MFC 應用程式（例如 FTP 伺服器）通訊，您可能需要在使用 Windows 通訊端轉換常式**ntohs**、 **ntohl**、 **htons**和**htonl**之前，自行管理位元組交換，然後再將資料傳遞給封存物件。 本文稍後會顯示這些用來與非 MFC 應用程式通訊的函式範例。

> [!NOTE]
> 當通訊的另一端不是 MFC 應用程式時，您也必須避免將衍生自的 c + + 物件串流 `CObject` 至您的封存，因為接收者將無法處理它們。 請參閱[Windows socket：使用具有封存的通訊端](../mfc/windows-sockets-using-sockets-with-archives.md)中的附注。

如需有關位元組訂單的詳細資訊，請參閱 Windows SDK 中提供的 Windows 通訊端規格。

## <a name="a-byte-order-conversion-example"></a>位元組順序轉換範例

下列範例顯示使用封存之物件的序列化函 `CSocket` 式。 它也會說明如何在 Windows 通訊端 API 中使用位元組順序轉換函式。

這個範例會示範您撰寫的用戶端，其與非 MFC 伺服器應用程式進行通訊，但您沒有原始程式碼的存取權。 在此案例中，您必須假設非 MFC 伺服器使用標準網路位元組順序。 相反地，您的 MFC 用戶端應用程式會使用 `CArchive` 物件搭配 `CSocket` 物件，並使用「位元組由小到大」 `CArchive` 位元組順序，與網路標準相反。

假設您計畫用來進行通訊的非 MFC 伺服器，已為訊息封包建立通訊協定，如下所示：

[!code-cpp[NVC_MFCSimpleSocket#5](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_1.cpp)]

在 MFC 詞彙中，這會以下列方式表示：

[!code-cpp[NVC_MFCSimpleSocket#6](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_2.cpp)]

在 c + + 中，和 **`struct`** 類別基本上是相同的事物。 `Message`結構可以有成員函式，例如上方宣告的成員函式 `Serialize` 。 成員函式 `Serialize` 看起來可能像這樣：

[!code-cpp[NVC_MFCSimpleSocket#7](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_3.cpp)]

這個範例會呼叫資料的位元組順序轉換，因為一個端的非 MFC 伺服器應用程式的位元組順序與 `CArchive` 另一端的 mfc 用戶端應用程式中所使用的不相符。 此範例說明 Windows 通訊端提供的數個位元組順序轉換函式。 下表描述這些功能。

### <a name="windows-sockets-byte-order-conversion-functions"></a>Windows 通訊端位元組順序轉換函式

|函式|用途|
|--------------|-------------|
|**ntohs**|將16位的數量從網路位元組順序轉換為主機位元組順序（以大到小到小型位元組）。|
|**ntohl**|將32位的數量從網路位元組順序轉換為主機位元組順序（從大到小到小型位元組）。|
|**Htons**|將16位的數量從主機位元組順序轉換成網路位元組順序（以小到大為位元組，並以位元組為單位）。|
|**Htonl**|將32位的數量從主機位元組順序轉換為網路位元組順序（以小到大為位元組，並以位元組為單位）。|

這個範例的另一個重點是，當通訊另一端的通訊端應用程式為非 MFC 應用程式時，您必須避免執行如下所示的作業：

`ar << pMsg;`

其中 `pMsg` ，是衍生自類別之 c + + 物件的指標 `CObject` 。 這會傳送與物件相關聯的額外 MFC 資訊，而伺服器將不會瞭解它，因為它是 MFC 應用程式。

如需詳細資訊，請參閱

- [Windows 通訊端：使用類別 CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Socket：背景](../mfc/windows-sockets-background.md)

- [Windows 通訊端：資料流程通訊端](../mfc/windows-sockets-stream-sockets.md)

- [Windows 通訊端：資料包通訊端](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>另請參閱

[MFC 中的 Windows Sockets](../mfc/windows-sockets-in-mfc.md)
