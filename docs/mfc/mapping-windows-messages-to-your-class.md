---
title: 將 Windows 訊息對應到您的類別
ms.date: 09/06/2019
helpviewer_keywords:
- MFC dialog boxes [MFC], Windows messages
- message maps [MFC], in dialog class
- Windows messages [MFC], mapping in dialog classes
- messages to dialog class [MFC]
- mappings [MFC], messages to dialog class [MFC]
- message maps [MFC], mapping Windows messages to classes
- messages to dialog class [MFC], mapping
- Class Wizard [MFC]
ms.assetid: a4c6fd1f-1d33-47c9-baa0-001755746d6d
ms.openlocfilehash: 6b1155945c4248c5ac2755d60d8887f890e6d324
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618292"
---
# <a name="mapping-windows-messages-to-your-class"></a>將 Windows 訊息對應到您的類別

如果您需要對話方塊來處理 Windows 訊息，請覆寫適當的處理常式函式。 若要這麼做，請選擇**方案總管**中的 [**類別檢視**] 索引標籤，以滑鼠右鍵按一下代表此對話方塊的類別，然後選擇 [[類別] [Wizard]](reference/mfc-class-wizard.md)。 使用 wizard 將[訊息對應](reference/mapping-messages-to-functions.md)至對話方塊類別。 這會寫入每個訊息的訊息對應專案，並將訊息處理常式成員函式新增至類別。 使用程式碼編輯器，在訊息處理常式中撰寫程式碼。

您也可以覆寫[CDialog](reference/cdialog-class.md)及其基類的成員函式，特別是[CWnd](reference/cwnd-class.md)。

## <a name="what-do-you-want-to-know-more-about"></a>您想要深入瞭解的內容

- [訊息處理和對應](message-handling-and-mapping.md)

- [經常覆寫的成員函式](commonly-overridden-member-functions.md)

- [常加入的成員函式](commonly-added-member-functions.md)

## <a name="see-also"></a>另請參閱

[對話方塊](dialog-boxes.md)<br/>
[在 MFC 中使用對話方塊](life-cycle-of-a-dialog-box.md)
