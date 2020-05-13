---
title: Windows Sockets：位元組順序
ms.date: 11/04/2016
helpviewer_keywords:
- byte order issues in sockets programming
- sockets [MFC], byte order issues
- Windows Sockets [MFC], byte order issues
ms.assetid: 8a787a65-f9f4-4002-a02f-ac25a5dace5d
ms.openlocfilehash: 50548202483c4d9d4471ad2c600270c4df4503e7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371053"
---
# <a name="windows-sockets-byte-ordering"></a>Windows Sockets：位元組順序

本文和兩個方針手冊說明了 Windows Sockets 程式設計的幾個問題。 本文介紹位元組排序。 其他問題在文章中介紹[:Windows套接字:阻止](../mfc/windows-sockets-blocking.md)和[Windows 套接字:轉換字串](../mfc/windows-sockets-converting-strings.md)。

如果您使用或派生自類[CAsyncSocket,](../mfc/reference/casyncsocket-class.md)則需要自己管理這些問題。 如果您使用或派生自[CSocket](../mfc/reference/csocket-class.md)類,MFC 會為您管理它們。

## <a name="byte-ordering"></a>位元組順序

不同的機器體系結構有時使用不同的位元組順序儲存數據。 例如,基於英特爾的機器以 Macintosh (摩托羅拉) 機器的相反順序存儲數據。 英特爾位元組順序稱為"小 Endian",也是網路標準"大Endian"訂單的反面。 下表解釋了這些術語。

### <a name="big--and-little-endian-byte-ordering"></a>大和小恩地位元組訂購

|位元組順序|意義|
|-------------------|-------------|
|大恩迪安|最重要的位元組位於單詞的左端。|
|小恩迪安|最重要的位元組位於單詞的右端。|

通常,您不必擔心通過網路發送和接收的數據的位元組順序轉換,但在某些情況下必須轉換位元組訂單。

## <a name="when-you-must-convert-byte-orders"></a>當您必須轉換位元組訂單時

您需要在以下情況下轉換位元組訂單:

- 您傳遞的資訊需要由網路解釋,而不是您發送到另一台計算機的數據。 例如,您可以傳遞埠和位址,而網路必須瞭解這些埠和位址。

- 與您通訊的伺服器應用程式不是 MFC 應用程式(並且您沒有它的原始程式碼)。 如果兩台電腦不共用相同的位元組順序,則這將調用位元組訂單轉換。

## <a name="when-you-do-not-have-to-convert-byte-orders"></a>當您不必轉換位元組訂單時

在以下情況下,可以避免轉換位元組訂單的工作:

- 兩端的計算機可以同意不交換位元組,並且兩台電腦使用相同的位元組順序。

- 您要通訊的伺服器是 MFC 應用程式。

- 您擁有要通訊的伺服器的原始程式碼,因此您可以顯式判斷是否必須轉換位元組訂單。

- 您可以將伺服器移植到 MFC。 這是相當容易做到的,結果通常是更小,更快的代碼。

使用[CAsyncSocket,](../mfc/reference/casyncsocket-class.md)您必須自己管理任何必要的位元組順序轉換。 Windows 套接字可標準化「大 Endian」位元組順序模型,並提供在此順序和其他訂單之間轉換的功能。 [但是,CArchive,](../mfc/reference/carchive-class.md)你與[CSocket](../mfc/reference/csocket-class.md)一起使用,使用相反(「小Endian」)順序`CArchive`,但 會為您處理位元順序轉換的詳細資訊。 通過在應用程式中使用此標準排序或使用 Windows 套接字位元組順序轉換功能,可以使代碼更加便攜。

使用 MFC 套接字的理想情況是,當您寫入通信的兩端時:在兩端使用 MFC。 如果您正在編寫一個將與非 MFC 應用程式(如 FTP 伺服器)通信的應用程式,則可能需要在將數據傳遞到存檔物件之前,使用 Windows Sockets 轉換例程**ntohs、ntohl、htons**和**ntohs****htonl**來管理**htons**位元組交換。 本文後面會介紹與非 MFC 應用程式通信中使用的這些函數的示例。

> [!NOTE]
> 當通信的另一端不是 MFC 應用程式時,還必須避免將派生`CObject`C++ 物件流式傳輸到存檔中,因為接收方將無法處理它們。 請參考 Windows[通訊中註解:使用帶存檔的 socket](../mfc/windows-sockets-using-sockets-with-archives.md)。

有關位元組訂單的詳細資訊,請參閱 Windows SDK 中可用的 Windows 套接字規範。

## <a name="a-byte-order-conversion-example"></a>位元組順序轉換範例

下面的範例顯示了使用存檔`CSocket`的物件的序列化函數。 它還說明瞭在 Windows 套接字 API 中使用位元組順序轉換功能。

此示例介紹一個方案,其中您編寫的用戶端與無法訪問原始程式碼的非 MFC 伺服器應用程式進行通訊。 在這種情況下,您必須假定非 MFC 伺服器使用標準網路位元組順序。 相反,MFC 客戶端`CArchive`應用程式使用`CSocket`物件與`CArchive`物件,並使用 「小 Endian」位元組順序,這與網路標準相反。

假設您計劃與其通訊的非 MFC 伺服器具有消息資料套件的已建立協定,如下所示:

[!code-cpp[NVC_MFCSimpleSocket#5](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_1.cpp)]

用MFC的術語,這將表達如下:

[!code-cpp[NVC_MFCSimpleSocket#6](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_2.cpp)]

在C++中,**結構**本質上與類是一回事。 結構`Message`可以具有成員函數,如上面`Serialize`聲明 的成員函數。 成員`Serialize`函數可能如下所示:

[!code-cpp[NVC_MFCSimpleSocket#7](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_3.cpp)]

此示例要求資料位元組順序轉換,因為一端的非 MFC 伺服器應用程式的位元組排序與另一端`CArchive`MFC 用戶端應用程式中使用的字節排序之間存在明顯的不匹配。 該示例說明了 Windows 套接字提供的幾個位元組順序轉換功能。 下表描述了這些功能。

### <a name="windows-sockets-byte-order-conversion-functions"></a>Windows 通訊端組順序轉換功能

|函式|目的|
|--------------|-------------|
|**ntohs**|將 16 位數量從網路位元組順序轉換為主機位元組順序(大 Endian 到小 Endian)。|
|**ntohl**|將 32 位數量從網路位元組順序轉換為主機位元組順序(大 Endian 到小 Endian)。|
|**霍頓斯**|將 16 位數量從主機位元組順序轉換為網路位元組順序(小 Endian 到大 Endian)。|
|**赫托恩**|將 32 位數量從主機位元組順序轉換為網路位元組順序(小 Endian 到大 Endian)。|

此示例的另一點是,當通訊另一端的套接字應用程式是非 MFC 應用程式時,必須避免執行以下操作:

`ar << pMsg;`

其中`pMsg`是指向從`CObject`類 派生C++對象的指標。 這將發送與物件關聯的額外 MFC 資訊,伺服器將無法理解它,就像它是 MFC 應用程式一樣。

如需詳細資訊，請參閱

- [Windows Sockets：使用類別 CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets：背景](../mfc/windows-sockets-background.md)

- [Windows Sockets：資料流通訊端](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets：資料通訊端](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>另請參閱

[MFC 中的 Windows Sockets](../mfc/windows-sockets-in-mfc.md)
