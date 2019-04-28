---
title: 將 Windows 訊息對應到您的類別
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], Windows messages
- message maps [MFC], in dialog class
- Windows messages [MFC], mapping in dialog classes
- messages to dialog class [MFC]
- mappings [MFC], messages to dialog class [MFC]
- message maps [MFC], mapping Windows messages to classes
- messages to dialog class [MFC], mapping
ms.assetid: a4c6fd1f-1d33-47c9-baa0-001755746d6d
ms.openlocfilehash: 7e15f52e41d4ac91a839629342258128db86e2d5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62363839"
---
# <a name="mapping-windows-messages-to-your-class"></a>將 Windows 訊息對應到您的類別

如果您需要您的對話方塊中，以處理 Windows 訊息時，會覆寫適當的處理常式函式。 若要這樣做，請使用 [屬性] 視窗[對應的訊息](../mfc/reference/mapping-messages-to-functions.md)至對話方塊類別。 這會寫入每個訊息的訊息對應項目，並將訊息處理常式成員函式加入類別。 使用視覺效果C++中的訊息處理常式撰寫程式碼的原始程式碼編輯器。

您也可以覆寫的成員函式[CDialog](../mfc/reference/cdialog-class.md)和其基底類別，尤其是[CWnd](../mfc/reference/cwnd-class.md)。

## <a name="what-do-you-want-to-know-more-about"></a>您想要深入了解什麼

- [訊息處理和對應](../mfc/message-handling-and-mapping.md)

- [常被覆寫的成員函式](../mfc/commonly-overridden-member-functions.md)

- [常加入的成員函式](../mfc/commonly-added-member-functions.md)

## <a name="see-also"></a>另請參閱

[對話方塊](../mfc/dialog-boxes.md)<br/>
[對話方塊的生命週期](../mfc/life-cycle-of-a-dialog-box.md)
