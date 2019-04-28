---
title: Windows Sockets:Stream 通訊端
ms.date: 11/04/2016
helpviewer_keywords:
- Windows Sockets [MFC], stream sockets
- sockets [MFC], stream sockets
- stream sockets [MFC]
ms.assetid: 31faaa34-a995-493f-a30b-b8115293d619
ms.openlocfilehash: 91f06c4a36e76638708edf085987e51418913fd6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62337826"
---
# <a name="windows-sockets-stream-sockets"></a>Windows Sockets:Stream 通訊端

本文說明資料流通訊端 (其中一種可以使用的 Windows Socket 類型)。 (另一個型別是[資料包通訊端](../mfc/windows-sockets-datagram-sockets.md)。)

資料流通訊端提供不含記錄界限的資料流：可以是雙向的位元組資料流 (應用程式是全雙工的：它可以透過通訊端進行傳送和接收)。 資料流可以是循序傳送的不重複的資料。 (「循序」表示封包會依傳送的順序傳送。 「不重複」是指您一次只能取得一個特定封包)。其中保證會收到資料流訊息的回應，因此資料流相當適合處理大量的資料。

網路傳輸層可能會將資料拆開或分組為適當大小的封包。 `CSocket` 類別會為您處理封裝和解除封裝的步驟。

資料流採用明確的連線：通訊端 A 要求與通訊端 B 進行連線，通訊端 B 接受或拒絕連線要求。

撥打電話可以做為資料流的範例。 在一般情況下，接收的一方會依您所說出的順序聽到所說的內容，而不會重複或遺失。 例如，若要實作檔案傳輸通訊協定 (FTP)，其中會傳送任意大小的 ASCII 或二進位檔案，則可以使用資料流通訊端。

當必須確定資料抵達且當資料大小很大時，使用資料流通訊端會比使用資料包通訊端更好。 如需資料流通訊端的詳細資訊，請參閱 Windows Sockets 規格。 使用 Windows SDK 中的規格。

使用資料流通訊端可能會優於設計為使用資料包通訊端廣播給網路上所有接收通訊端的應用程式，因為

- 廣播模型受限於網路氾濫 (或「風暴」) 的問題。

- 之後採用的主從模型會比較有效率。

- 資料流模型提供可靠的資輸，而資料包模型則沒有。

- 最終的模型是採用 Unicode 和 ANSI 通訊端應用程式間的通訊能力，將 CArchive 類別提供給 CSocket 類別使用。

    > [!NOTE]
    >  如果您使用 `CSocket` 類別，則必須使用資料流。 如果您指定做為通訊端類型，就會失敗，MFC 判斷提示**SOCK_DGRAM**。

## <a name="see-also"></a>另請參閱

[MFC 中的 Windows Sockets](../mfc/windows-sockets-in-mfc.md)<br/>
[Windows Socket：背景](../mfc/windows-sockets-background.md)
