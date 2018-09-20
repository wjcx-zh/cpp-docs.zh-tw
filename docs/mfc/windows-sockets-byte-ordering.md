---
title: Windows Sockets： 位元組順序 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- byte order issues in sockets programming
- sockets [MFC], byte order issues
- Windows Sockets [MFC], byte order issues
ms.assetid: 8a787a65-f9f4-4002-a02f-ac25a5dace5d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: feaf2c02dbb17272696571ba27a077e6e99836b0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46377177"
---
# <a name="windows-sockets-byte-ordering"></a>Windows Sockets：位元組順序

本文和兩個方針手冊說明了 Windows Sockets 程式設計的幾個問題。 本文章涵蓋位元組順序。 文章中所涵蓋的其他問題： [Windows Sockets： 封鎖](../mfc/windows-sockets-blocking.md)並[Windows Sockets： 轉換字串](../mfc/windows-sockets-converting-strings.md)。

如果您使用或衍生自類別[CAsyncSocket](../mfc/reference/casyncsocket-class.md)，您必須自行管理這些問題。 如果您使用或衍生自類別[CSocket](../mfc/reference/csocket-class.md)，MFC 會為您管理它們。

## <a name="byte-ordering"></a>位元組順序

不同的電腦架構有時會儲存使用不同的位元組順序的資料。 比方說，Intel 為基礎的機器會將資料儲存在 Macintosh (Motorola) 機器的反向順序。 Intel 位元組順序，稱為 「 由小到大，」 也是網路標準"Big-endian"順序相反。 下表說明這些詞彙。

### <a name="big--and-little-endian-byte-ordering"></a>大型-和位元組由小到大位元組順序

|位元組順序|意義|
|-------------------|-------------|
|Big Endian|最大顯著性位元組是文字的左邊。|
|Little Endian|最大顯著性位元組位於右端的文字。|

一般而言，您不必擔心資料傳送，並透過網路接收的位元組順序轉換，但在其中，您必須轉換的位元組順序的情況下。

## <a name="when-you-must-convert-byte-orders"></a>當您必須將位元組順序的轉換

要轉換的位元組順序，在下列情況：

- 您傳遞解譯網路，而不是您要傳送給另一部電腦的資料所需的資訊。 例如，您可能會通過連接埠和位址，必須了解網路。

- 您要與其通訊的伺服器應用程式不是 MFC 應用程式 （和它沒有原始碼）。 這會呼叫位元組順序轉換如果兩部電腦不會共用相同的位元組順序。

## <a name="when-you-do-not-have-to-convert-byte-orders"></a>當您沒有轉換的位元組順序

您可以避免轉換在下列情況中的位元組順序的工作：

- 兩端的機器可以接受未交換位元組為單位，這兩部電腦使用相同的位元組順序。

- MFC 應用程式的伺服器正在與通訊。

- 因此您可以分辨明確是否您就必須轉換的位元組順序，或不，您會有您要通訊之伺服器的原始程式碼。

- 您可以移植到 MFC 伺服器。 這很容易進行，而結果通常是較小、 更快速的程式碼。

使用[CAsyncSocket](../mfc/reference/casyncsocket-class.md)，您必須自行管理任何所需的位元組順序轉換。 Windows 通訊端標準化"Big-endian"位元組順序模型，並提供此順序和其他項目之間進行轉換的函式。 [CArchive](../mfc/reference/carchive-class.md)，不過可以搭配[CSocket](../mfc/reference/csocket-class.md)，使用完全相反的 ("Big-endian") 順序，但`CArchive`負責為您的位元組順序轉換的詳細資料。 使用這個標準的順序，在您的應用程式，或使用 Windows 通訊端的位元組順序轉換函式，您可以讓程式碼的可攜性。

使用 MFC 通訊端的理想案例是當您撰寫的通訊兩端： 在兩端使用 MFC。 如果您正在撰寫的應用程式，將通訊與非 MFC 應用程式，例如 FTP 伺服器，您可能需要管理位元組-交換自行之前，您將資料傳遞至封存物件，使用 Windows 通訊端轉換常式**ntohs**， **ntohl**， **htons**，和**htonl**。 非 MFC 應用程式與通訊中使用這些函式的範例則顯示在本文稍後。

> [!NOTE]
>  如果另一端的通訊不是 MFC 應用程式，您也必須避免 c + + 物件衍生自資料流處理`CObject`封存到因為接收者無法處理它們。 請參閱中的附註[Windows Sockets： 使用通訊端與封存](../mfc/windows-sockets-using-sockets-with-archives.md)。

如需有關位元組順序的詳細資訊，請參閱 Windows 通訊端規格，可在 Windows SDK。

## <a name="a-byte-order-conversion-example"></a>位元組順序轉換範例

下列範例示範序列化函式，以`CSocket`使用封存的物件。 它也會說明 Windows 通訊端 API 中使用的位元組順序轉換函式。

此範例中呈現您撰寫的原始程式碼無法存取非 MFC 伺服器應用程式與通訊的用戶端的案例。 在此案例中，您必須假設非 MFC 伺服器會使用標準的網路位元組順序。 相反地，會使用用戶端應用程式 MFC`CArchive`物件`CSocket`物件，和`CArchive`使用"little Endian"的位元組順序，網路標準的相反。

假設您計劃與其進行通訊的非 MFC 伺服器已建立的通訊協定的訊息封包，如下所示：

[!code-cpp[NVC_MFCSimpleSocket#5](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_1.cpp)]

MFC 而言，這就表示，如下所示：

[!code-cpp[NVC_MFCSimpleSocket#6](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_2.cpp)]

C + +**結構**是類別基本上相同的動作。 `Message`結構可以具有成員函式，例如`Serialize`成員函式宣告上方。 `Serialize`成員函式可能會看起來像這樣：

[!code-cpp[NVC_MFCSimpleSocket#7](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_3.cpp)]

這個範例會呼叫位元組順序轉換的資料，因為不清楚相符之間非 MFC 伺服器應用程式，一端的位元組順序和`CArchive`另一端的 MFC 用戶端應用程式中使用。 此範例會說明數個 Windows 通訊端提供的位元組順序轉換函式。 下表描述這些函式。

### <a name="windows-sockets-byte-order-conversion-functions"></a>Windows 通訊端的位元組順序轉換函式

|功能|用途|
|--------------|-------------|
|**ntohs**|將 16 位元數量從網路位元組順序轉換為主機位元組順序 (big Endian 到 little Endian)。|
|**ntohl**|將 32 位元數量從網路位元組順序轉換為主機位元組順序 (big Endian 到 little Endian)。|
|**Htons**|將 16 位元數量從主機位元組順序轉換為網路位元組順序 （由小到大到 big Endian）。|
|**Htonl**|將 32 位元數量從主機位元組順序轉換為網路位元組順序 （由小到大到 big Endian）。|

此範例中的另一個重點是非 MFC 應用程式通訊的另一端的通訊端應用程式時，您必須避免執行像下面這樣：

`ar << pMsg;`

何處`pMsg`是衍生自類別的 c + + 物件的指標`CObject`。 這會傳送物件和伺服器相關聯的額外 MFC 資訊不會了解它，就好像 MFC 應用程式一樣。

如需詳細資訊，請參閱:

- [Windows Sockets：使用類別 CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets：背景](../mfc/windows-sockets-background.md)

- [Windows Sockets：資料流通訊端](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets：資料通訊端](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>另請參閱

[MFC 中的 Windows Sockets](../mfc/windows-sockets-in-mfc.md)

