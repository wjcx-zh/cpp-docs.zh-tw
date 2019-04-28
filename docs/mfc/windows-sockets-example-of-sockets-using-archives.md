---
title: Windows Sockets:使用封存的通訊端範例
ms.date: 11/04/2016
helpviewer_keywords:
- sockets [MFC], with archives
- examples [MFC], Windows Sockets
- Windows Sockets [MFC], with archives
ms.assetid: 2e3c9bb2-7e7b-4f28-8dc5-6cb7a484edac
ms.openlocfilehash: 4ea1e2911b156066360da09993fa7302db79f12b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62305290"
---
# <a name="windows-sockets-example-of-sockets-using-archives"></a>Windows Sockets:使用封存的通訊端範例

本文提供使用類別的範例[CSocket](../mfc/reference/csocket-class.md)。 此範例會採用`CArchive`將透過通訊端的資料序列化的物件。 請注意，這不是文件序列化到或檔案。

下列範例說明如何傳送和接收資料，透過使用封存`CSocket`物件。 範例的設計，讓兩個執行個體 （在相同電腦上或在網路上的不同電腦上） 的應用程式交換資料。 一個執行個體傳送資料，而另一個執行個體接收和認可。 其中一個應用程式可以起始交換，而且其中一個可做為伺服器或另一個應用程式的用戶端。 下列函式定義於應用程式的檢視類別：

[!code-cpp[NVC_MFCSimpleSocket#1](../mfc/codesnippet/cpp/windows-sockets-example-of-sockets-using-archives_1.cpp)]

最重要的事有關這個範例是其結構平行的 MFC`Serialize`函式。 `PacketSerialize`成員函式所組成**如果**陳述式搭配**其他**子句。 此函式會接收兩個[CArchive](../mfc/reference/carchive-class.md)做為參數的參考： *arData*並*arAck*。 如果*arData*來儲存 （傳送），已設定封存物件**如果**分支便會執行; 否則如果*arData*設定載入 （接收） 的函式會採用**其他**分支。 如需在 MFC 中序列化的詳細資訊，請參閱[序列化](../mfc/how-to-make-a-type-safe-collection.md)。

> [!NOTE]
>  *ArAck*封存物件會被假設為相對於*arData*。 如果*arData*適用於傳送， *arAck*收到，且反之則為 true。

進行傳送，範例函式執行迴圈的次數，每次產生一些隨機的資料，供示範之用的指定數目。 您的應用程式會從某些來源，例如檔案中取得實際資料。 *ArData*封存的插入運算子 (**<<**) 用來傳送資料的三個連續區塊的資料流：

- "header"，指定資料的本質 (在此案例中的值*bValue*變數，並將傳送多少複本)。

   兩個項目會隨機產生，此範例中。

- 指定的資料複本數目。

   內部**for**迴圈傳送*bValue*指定重試次數。

- 字串，呼叫*strText*接收者顯示給使用者。

接收函式的運作方式類似，不同之處在於它會使用封存的擷取運算子 (**>>**) 以取得從封存的資料。 接收應用程式會確認它接收的資料，會顯示最後一個 「 接收 」 的訊息，然後送回訊息指出 「 已傳送 」 傳送的應用程式，才能顯示。

在此通訊模型中，「 已接收 」 這個字，訊息傳送*strText*變數，並不是位於另一端的通訊，因此它會指定要接收的使用者特定數目的資料封包已被收到。 接收者會以類似的字串，表示在原始寄件者 畫面上的 「 傳送 」，以顯示回覆。 兩個字串的回條指出發生成功進行通訊。

> [!CAUTION]
>  如果您要撰寫 MFC 用戶端程式與所建立的 (非 MFC) 伺服器進行通訊，請不要透過封存傳送 C++ 物件。 除非伺服器是 MFC 應用程式了解您想要傳送的物件類型，它將無法接收和還原序列化物件。 一文中的舉例[Windows Sockets:位元組順序](../mfc/windows-sockets-byte-ordering.md)顯示此類型的通訊。

如需詳細資訊，請參閱 Windows Sockets 規格： **htonl**， **htons**， **ntohl**， **ntohs**。 此外，如需詳細資訊，請參閱：

- [Windows Socket：從通訊端類別衍生](../mfc/windows-sockets-deriving-from-socket-classes.md)

- [Windows Socket：如何搭配使用通訊端與封存](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows Socket：背景](../mfc/windows-sockets-background.md)

## <a name="see-also"></a>另請參閱

[MFC 中的 Windows Sockets](../mfc/windows-sockets-in-mfc.md)<br/>
[CArchive::IsStoring](../mfc/reference/carchive-class.md#isstoring)<br/>
[CArchive::operator <<](../mfc/reference/carchive-class.md#operator_lt_lt)<br/>
[CArchive::operator >>](../mfc/reference/carchive-class.md#operator_lt_lt)<br/>
[CArchive::Flush](../mfc/reference/carchive-class.md#flush)<br/>
[CObject::Serialize](../mfc/reference/cobject-class.md#serialize)
