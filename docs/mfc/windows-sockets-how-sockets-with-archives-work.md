---
title: Windows Sockets： 通訊端與封存的運作方式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Windows Sockets [MFC], synchronous
- sockets [MFC], synchronous operation
- sockets [MFC], with archives
- synchronous state socket
- Windows Sockets [MFC], with archives
- two-state socket object
ms.assetid: d8ae4039-391d-44f0-a19b-558817affcbb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c03ae586e346be2ba1e7c71475b69318ded0dd18
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33385212"
---
# <a name="windows-sockets-how-sockets-with-archives-work"></a>Windows Sockets：如何搭配使用通訊端與封存
這篇文章說明如何[CSocket](../mfc/reference/csocket-class.md)物件[CSocketFile](../mfc/reference/csocketfile-class.md)物件，和[CArchive](../mfc/reference/carchive-class.md)物件會結合，以便簡化傳送和接收資料透過 Windows通訊端。  
  
 發行項[Windows Sockets： 通訊端使用封存的範例](../mfc/windows-sockets-example-of-sockets-using-archives.md)呈現**PacketSerialize**函式。 中的封存物件**PacketSerialize**範例的作用很像傳遞至 MFC 的封存物件[序列化](../mfc/reference/cobject-class.md#serialize)函式。 基本的差異是，通訊端，封存附加不到標準[CFile](../mfc/reference/cfile-class.md)物件 （通常與相關聯的磁碟檔案），但`CSocketFile`物件。 不必連線到磁碟檔案，`CSocketFile`物件連接`CSocket`物件。  
  
 A`CArchive`物件管理的緩衝區。 儲存 （傳送） 的保存的緩衝區已滿時，相關聯`CFile`物件寫出緩衝區的內容。 排清的封存附加到通訊端緩衝區就相當於傳送訊息。 當載入 （接收） 封存的緩衝區已滿，`CFile`物件停止讀取，直到緩衝區恢復可用性為止。  
  
 類別`CSocketFile`衍生自`CFile`，但不支援[CFile](../mfc/reference/cfile-class.md)成員函式，例如定位函式 (`Seek`， `GetLength`，`SetLength`等等)，鎖定函式 （`LockRange`， `UnlockRange`)，或`GetPosition`函式。 所有[CSocketFile](../mfc/reference/csocketfile-class.md)物件必須執行動作會寫入或讀取的位元組或從相關聯的序列`CSocket`物件。 因為未牽涉到檔案作業，例如`Seek`和`GetPosition`沒有意義。 `CSocketFile` 衍生自`CFile`，因此它通常會繼承所有這些成員函式。 若要避免此情形，不支援`CFile`成員函式會覆寫中`CSocketFile`擲回[CNotSupportedException](../mfc/reference/cnotsupportedexception-class.md)。  
  
 `CSocketFile`物件，呼叫成員函式其`CSocket`傳送或接收資料的物件。  
  
 下圖顯示這些物件之間的關聯性兩端的通訊。  
  
 ![CArchive、 CSocketFile 和 CSocket](../mfc/media/vc38ia1.gif "vc38ia1")  
CArchive、CSocketFile 和 CSocket  
  
 這種明顯的目的是複雜性的免除您自行管理的詳細資料，通訊端的必要性。 建立通訊端、 檔案和封存，並插入至封存或從封存中加以擷取，然後開始傳送或接收資料。 [CArchive](../mfc/reference/carchive-class.md)， [CSocketFile](../mfc/reference/csocketfile-class.md)，和[CSocket](../mfc/reference/csocket-class.md)管理背後的運作原理的詳細資料。  
  
 A`CSocket`物件是一個兩階段物件： 有時非同步 （一般狀態） 和有時同步。 在其非同步狀態，通訊端可以從 framework 接收非同步通知。 不過，如接收或傳送資料等作業期間，通訊端會變成同步。 這表示通訊端將會收到非同步告知，直到同步作業完成為止。 因為它切換模式，例如，您可以像下面這樣：  
  
 [!code-cpp[NVC_MFCSimpleSocket#2](../mfc/codesnippet/cpp/windows-sockets-how-sockets-with-archives-work_1.cpp)]  
  
 如果`CSocket`不是實作為兩個狀態物件時，可能會接收其他相同的事件通知，而您在處理之前通知。 例如，您可能會收到`OnReceive`時處理通知`OnReceive`。 在上述程式碼片段中，擷取`str`從封存檔，可能會造成遞迴。 藉由切換狀態，`CSocket`防止遞迴藉由防止其他通知。 一般規則是在通知中的任何通知。  
  
> [!NOTE]
>  A`CSocketFile`也可用以 （有限制） 的檔案，而不做`CArchive`物件。 根據預設，`CSocketFile`建構函式的`bArchiveCompatible`參數是**TRUE**。 這會指定 「 檔案 」 物件是用於封存。 若要使用 「 檔案 」 物件，但未封存，傳遞**FALSE**中`bArchiveCompatible`參數。  
  
 在 「 封存相容 」 模式下，`CSocketFile`物件提供更佳的效能並減少的 < 死結 >。 傳送和接收通訊端進行等候，或等候一般資源時，就會發生死結。 如果發生這種情況，可能會`CArchive`物件使用過`CSocketFile`中一樣的方式`CFile`物件。 與`CFile`，封存可以假設如果收到比要求的位元組更少，具有已到達檔案結尾。 與`CSocketFile`，不過，資料為基礎的訊息; 緩衝區中可以包含多個訊息，因此接收要求的位元組數目少於並不表示的檔案結尾。 應用程式不會封鎖在此情況下可能與`CFile`，而且可以繼續從緩衝區讀取訊息，直到緩衝區是空的。 [IsBufferEmpty](../mfc/reference/carchive-class.md#isbufferempty)函式在`CArchive`有助於監視這種情況的封存的緩衝區的狀態。  
  
 如需詳細資訊，請參閱[Windows Sockets： 使用通訊端與封存](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
## <a name="see-also"></a>另請參閱  
 [MFC 中的 Windows Sockets](../mfc/windows-sockets-in-mfc.md)   
 [Cobject:: Serialize](../mfc/reference/cobject-class.md#serialize)

