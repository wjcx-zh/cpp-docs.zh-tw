---
title: Windows Sockets：如何搭配使用通訊端與封存
ms.date: 11/19/2018
helpviewer_keywords:
- Windows Sockets [MFC], synchronous
- sockets [MFC], synchronous operation
- sockets [MFC], with archives
- synchronous state socket
- Windows Sockets [MFC], with archives
- two-state socket object
ms.assetid: d8ae4039-391d-44f0-a19b-558817affcbb
ms.openlocfilehash: f6101193c85e41fbf82681b0b2ae1e09e4162f87
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2018
ms.locfileid: "52174908"
---
# <a name="windows-sockets-how-sockets-with-archives-work"></a>Windows Sockets：如何搭配使用通訊端與封存

這篇文章說明如何[CSocket](../mfc/reference/csocket-class.md)物件， [CSocketFile](../mfc/reference/csocketfile-class.md)物件，並[CArchive](../mfc/reference/carchive-class.md)物件組合來簡化傳送和接收資料，透過 Windows通訊端。

發行項[Windows Sockets： 通訊端使用封存的範例](../mfc/windows-sockets-example-of-sockets-using-archives.md)呈現`PacketSerialize`函式。 中的封存物件`PacketSerialize`範例運作方式十分類似封存物件傳遞至 MFC [Serialize](../mfc/reference/cobject-class.md#serialize)函式。 重要的差異是，通訊端，封存附加不到標準[CFile](../mfc/reference/cfile-class.md)物件 （通常與相關聯的磁碟檔案） 但為`CSocketFile`物件。 而不是連接到磁碟檔案`CSocketFile`物件連接到`CSocket`物件。

A`CArchive`物件會管理一個緩衝區。 儲存 （傳送） 的封存的緩衝區已滿時，相關聯`CFile`物件寫出緩衝區的內容。 排清的封存檔附加到通訊端緩衝區就相當於傳送訊息。 當載入 （接收） 封存的緩衝區已滿，`CFile`物件會停止讀取，直到緩衝區恢復可用性為止。

類別`CSocketFile`衍生自`CFile`，但它不支援[CFile](../mfc/reference/cfile-class.md)成員函式，例如定位函式 (`Seek`， `GetLength`，`SetLength`等等)，鎖定函式 （`LockRange`， `UnlockRange`)，或`GetPosition`函式。 所有[CSocketFile](../mfc/reference/csocketfile-class.md)必須在執行物件會寫入或讀取或從相關聯的位元組序列`CSocket`物件。 因為未牽涉到的檔案作業，例如`Seek`和`GetPosition`沒有意義。 `CSocketFile` 衍生自`CFile`，因此它通常會繼承所有這些成員函式。 若要避免此情形，不支援`CFile`中的成員函式會覆寫`CSocketFile`擲回[CNotSupportedException](../mfc/reference/cnotsupportedexception-class.md)。

`CSocketFile`物件，呼叫成員函式及其`CSocket`傳送或接收資料的物件。

下圖顯示這些物件之間的關聯性兩端的通訊。

![CArchive、 CSocketFile 和 CSocket](../mfc/media/vc38ia1.gif "CArchive、 CSocketFile 和 CSocket") <br/>
CArchive、CSocketFile 和 CSocket

這明顯的目的是複雜性的免除您需要自行管理的通訊端詳細資料。 建立通訊端、 檔案和封存，並將其插入至封存，或從封存中解壓縮，然後開始傳送或接收資料。 [CArchive](../mfc/reference/carchive-class.md)， [CSocketFile](../mfc/reference/csocketfile-class.md)，以及[CSocket](../mfc/reference/csocket-class.md)管理背後的運作的詳細資料。

A`CSocket`物件是一個兩階段物件： 有時候非同步 （一般狀態） 和有時同步。 在其非同步狀態，通訊端可以從 framework 接收非同步通知。 不過，例如接收或傳送的資料作業期間的通訊端會變成同步。 這表示同步作業完成之前，通訊端會收到任何進一步的非同步通知。 因為它切換模式，比方說，您可以像下面這樣：

[!code-cpp[NVC_MFCSimpleSocket#2](../mfc/codesnippet/cpp/windows-sockets-how-sockets-with-archives-work_1.cpp)]

如果`CSocket`不是實作為兩個狀態物件時，可能會收到其他相同種類的事件通知，您已處理的上一個通知時。 例如，您可能會收到`OnReceive`處理時的通知`OnReceive`。 在上述程式碼片段中，擷取`str`從封存可能會導致遞迴。 藉由切換狀態，`CSocket`會遞迴防止藉由避免額外的通知。 一般規則是在通知內的任何通知。

> [!NOTE]
> A`CSocketFile`也可用來當做 （有限制） 的檔案，而不`CArchive`物件。 根據預設，`CSocketFile`建構函式*bArchiveCompatible*參數**TRUE**。 這會指定 「 檔案 」 物件是用於封存。 若要使用 「 檔案 」 物件但未封存，傳遞**假**中*bArchiveCompatible*參數。

在 「 封存相容 」 模式下，`CSocketFile`物件提供更佳的效能，並減少產生風險的 < 死結 >。 當您等候彼此，或等待的常見資源傳送和接收通訊端時，就會發生死結。 如果發生這種情況，可能`CArchive`物件所從事`CSocketFile`一樣的方式`CFile`物件。 使用`CFile`，封存會假設它收到較少的位元組，比要求時，如果有已到達檔案結尾。 使用`CSocketFile`，不過，資料為基礎的訊息緩衝區中可以包含多個訊息，因此接收少於所要求的位元組數目，並不表示檔案結尾。 應用程式不會封鎖在此情況下，它可能與`CFile`，因此能夠繼續從緩衝區讀取訊息，直到緩衝區是空的。 [IsBufferEmpty](../mfc/reference/carchive-class.md#isbufferempty)函式中`CArchive`適合用來監視這種情況的封存的緩衝區的狀態。

如需詳細資訊，請參閱[Windows Sockets： 使用通訊端與封存](../mfc/windows-sockets-using-sockets-with-archives.md)

## <a name="see-also"></a>另請參閱

[MFC 中的 Windows Sockets](../mfc/windows-sockets-in-mfc.md)<br/>
[Cobject:: Serialize](../mfc/reference/cobject-class.md#serialize)
