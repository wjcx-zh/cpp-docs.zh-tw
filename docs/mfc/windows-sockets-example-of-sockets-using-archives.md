---
title: Windows Sockets：使用封存的通訊端範例
ms.date: 11/04/2016
helpviewer_keywords:
- sockets [MFC], with archives
- examples [MFC], Windows Sockets
- Windows Sockets [MFC], with archives
ms.assetid: 2e3c9bb2-7e7b-4f28-8dc5-6cb7a484edac
ms.openlocfilehash: 253a65430ae230fbc4deeb9bd5288f28237310d2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371080"
---
# <a name="windows-sockets-example-of-sockets-using-archives"></a>Windows Sockets：使用封存的通訊端範例

本文提供了使用類[CSocket](../mfc/reference/csocket-class.md)的範例。 該示例使用`CArchive`對象透過套接字對數據進行序列化。 請注意,這不是檔序列化或從檔。

下面的範例說明了如何使用存檔通過`CSocket`物件發送和接收數據。 該示例的設計是使應用程式的兩個實例(在同一台計算機上或網路上的不同計算機上)交換數據。 一個實例發送數據,另一個實例接收和確認這些數據。 任一應用程式都可以啟動交換,也可以充當伺服器或作為另一個應用程式的用戶端。 以下函數在應用程式的檢視類別中定義:

[!code-cpp[NVC_MFCSimpleSocket#1](../mfc/codesnippet/cpp/windows-sockets-example-of-sockets-using-archives_1.cpp)]

此示例中最重要的是其結構與 MFC`Serialize`函數的結構平行。 成員`PacketSerialize`函數由帶**其他**子句的**if**語句組成。 此函數接收兩個[CArchive](../mfc/reference/carchive-class.md)引用參數 *:arData*和*arAck*。 如果*arData*存檔物件設定為存儲(發送),則執行**如果**分支;否則,如果*arData*設置為載入(接收),則函數將採用**其他**分支。 關於 MFC 中序列化的詳細資訊,請參閱[序列化](../mfc/how-to-make-a-type-safe-collection.md)。

> [!NOTE]
> *arAck*存檔物件假定與*arData*相反。 如果*arData*用於發送,*則 arAck*接收,反之亦然。

對於發送,範例函數迴圈指定的次數,每次生成一些隨機數據用於演示目的。 您的應用程式將從某些源(如文件)獲取真實數據。 *arData*存檔的插入運算子**<<**( ) 用於送出三個連續資料塊的流:

- 指定資料性質的"標頭"(在本例中 *,bValue*變數的值和將發送多少個副本)。

   此示例隨機生成這兩個項。

- 資料的副本的指定數量。

   循環的內部**發送** *bValue*指定的次數。

- 接收器向其用戶顯示的名為*strText*的字串。

對於接收,該函數的操作類似,只不過它使用存檔的提取運算符 (**>>**) 從存檔獲取數據。 接收應用程式驗證它接收的數據,顯示最終的"已接收"消息,然後發送回一條消息,顯示"已發送",以便發送應用程式顯示。

在此通信模型中,「接收」一詞(在*strText*變數中發送的消息)用於在通訊的另一端顯示,因此它向接收使用者指定已收到一定數量的資料包。 接收方使用類似字串進行回復,該字串顯示"已發送",以便顯示在原始發件人的螢幕上。 收到兩個字串表示已成功通信。

> [!CAUTION]
> 如果您要撰寫 MFC 用戶端程式與所建立的 (非 MFC) 伺服器進行通訊，請不要透過封存傳送 C++ 物件。 除非伺服器是瞭解要發送的物件類型的 MFC 應用程式,否則它將無法接收和取消序列化物件。 一文中的範例[Windows 套接字:位元組排序](../mfc/windows-sockets-byte-ordering.md)顯示了此類型的通信。

有關詳細資訊,請參閱 Windows 通訊卡字規範 **:htonl、htons、ntohl** **、ntohs**。 **htons** **ntohl** 此外,有關詳細資訊,請參閱:

- [Windows Sockets：從通訊端類別衍生](../mfc/windows-sockets-deriving-from-socket-classes.md)

- [Windows Sockets：如何搭配使用通訊端與封存](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows Sockets：背景](../mfc/windows-sockets-background.md)

## <a name="see-also"></a>另請參閱

[MFC 中的 Windows Sockets](../mfc/windows-sockets-in-mfc.md)<br/>
[C 壓縮檔:正在儲存](../mfc/reference/carchive-class.md#isstoring)<br/>
[C存檔::操作員 <<](../mfc/reference/carchive-class.md#operator_lt_lt)<br/>
[C存檔::操作員 >>](../mfc/reference/carchive-class.md#operator_lt_lt)<br/>
[C存檔:沖洗](../mfc/reference/carchive-class.md#flush)<br/>
[CObject:序列化](../mfc/reference/cobject-class.md#serialize)
