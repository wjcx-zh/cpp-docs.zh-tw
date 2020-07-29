---
title: Windows Sockets：使用封存的通訊端範例
ms.date: 11/04/2016
helpviewer_keywords:
- sockets [MFC], with archives
- examples [MFC], Windows Sockets
- Windows Sockets [MFC], with archives
ms.assetid: 2e3c9bb2-7e7b-4f28-8dc5-6cb7a484edac
ms.openlocfilehash: 275a6c274648225fedcec9d42c280f77af68158e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226772"
---
# <a name="windows-sockets-example-of-sockets-using-archives"></a>Windows Sockets：使用封存的通訊端範例

本文提供使用 [類別[CSocket](../mfc/reference/csocket-class.md)] 的範例。 此範例會運用 `CArchive` 物件，透過通訊端來序列化資料。 請注意，這不會對檔案進行檔序列化。

下列範例說明如何使用封存，透過物件來傳送和接收資料 `CSocket` 。 此範例的設計目的是要讓應用程式的兩個實例（位於相同的電腦上，或在網路上的不同電腦上）交換資料。 一個實例會傳送資料，而另一個實例會接收並認可。 任一應用程式都可以起始交換，而且可以做為伺服器，或做為另一個應用程式的用戶端。 下列函式定義于應用程式的 view 類別中：

[!code-cpp[NVC_MFCSimpleSocket#1](../mfc/codesnippet/cpp/windows-sockets-example-of-sockets-using-archives_1.cpp)]

這個範例最重要的一點，就是它的結構與 MFC 函式的 `Serialize` 功能類似。 `PacketSerialize`成員函式是由 **`if`** 具有子句的語句所組成 **`else`** 。 函式會接收兩個[CArchive](../mfc/reference/carchive-class.md)參考做為參數： *arData*和*arAck*。 如果已設定*arData*封存物件來儲存（傳送），則 **`if`** 分支會執行; 否則，如果已設定*arData*進行載入（接收），則函式會採用 **`else`** 分支。 如需 MFC 序列化的詳細資訊，請參閱[序列化](../mfc/how-to-make-a-type-safe-collection.md)。

> [!NOTE]
> *ArAck* archive 物件會假設為*arData*的相反。 如果*arData*是用於傳送， *arAck*會接收，而反向則是 true。

針對傳送，範例函式會針對指定的次數進行迴圈，每次產生一些亂數據以供示範之用。 您的應用程式會從某個來源取得實際的資料，例如檔案。 *ArData*封存的插入運算子（ **<<** ）是用來傳送三個連續資料區塊的資料流程：

- 指定資料性質的「標頭」（在此案例中，*其中 bvalue system.boolean.true*變數的值和要傳送的複本數目）。

   這個範例會隨機產生這兩個專案。

- 指定的資料複本數目。

   內部 **`for`** 迴圈會將*其中 bvalue system.boolean.true*傳送到指定的次數。

- 接收者會向使用者顯示的字串，稱為*strText* 。

針對接收，函式的運作方式類似，不同之處在于它會使用封存的抽取運算子（ **>>** ）來取得封存的資料。 接收端應用程式會驗證它所收到的資料，並顯示最後的「已接收」訊息，然後傳回訊息，指出「已傳送」要顯示的送出應用程式。

在此通訊模型中，「已接收」一詞（在*strText*變數中傳送的訊息）是為了在通訊的另一端顯示，因此它會指定接收的使用者已收到特定數目的資料封包。 接收者會使用類似的字串回復，顯示「已傳送」，以便在原始寄件者的畫面上顯示。 同時接收兩個字串，表示已成功進行通訊。

> [!CAUTION]
> 如果您要撰寫 MFC 用戶端程式與所建立的 (非 MFC) 伺服器進行通訊，請不要透過封存傳送 C++ 物件。 除非伺服器是瞭解您想要傳送之物件種類的 MFC 應用程式，否則將無法接收和還原序列化物件。 [Windows socket： Byte 順序](../mfc/windows-sockets-byte-ordering.md)一文中的範例會顯示此類型的通訊。

如需詳細資訊，請參閱 Windows 通訊端規格： **htonl**、 **htons**、 **ntohl**、 **ntohs**。 此外，如需詳細資訊，請參閱：

- [Windows 通訊端：衍生自通訊端類別](../mfc/windows-sockets-deriving-from-socket-classes.md)

- [Windows 通訊端：通訊端與封存的工作方式](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows Socket：背景](../mfc/windows-sockets-background.md)

## <a name="see-also"></a>另請參閱

[MFC 中的 Windows Sockets](../mfc/windows-sockets-in-mfc.md)<br/>
[CArchive：： IsStoring](../mfc/reference/carchive-class.md#isstoring)<br/>
[CArchive：： operator <<](../mfc/reference/carchive-class.md#operator_lt_lt)<br/>
[CArchive：： operator >>](../mfc/reference/carchive-class.md#operator_lt_lt)<br/>
[CArchive：： Flush](../mfc/reference/carchive-class.md#flush)<br/>
[CObject：：序列化](../mfc/reference/cobject-class.md#serialize)
