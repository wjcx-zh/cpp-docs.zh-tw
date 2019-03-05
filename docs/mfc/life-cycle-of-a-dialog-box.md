---
title: 對話方塊的生命週期
ms.date: 11/04/2016
helpviewer_keywords:
- dialog boxes [MFC], life cycle
- modal dialog boxes [MFC], life cycle
- modeless dialog boxes [MFC], life cycle
- MFC dialog boxes [MFC], life cycle
- life cycle of dialog boxes [MFC]
ms.assetid: e16fd78e-238d-4f31-8c9d-8564f3953bd9
ms.openlocfilehash: a3772a180e35a57c997446fcf2268d84bec2daa5
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57291102"
---
# <a name="life-cycle-of-a-dialog-box"></a>對話方塊的生命週期

在對話方塊的生命週期中，使用者叫用對話方塊中，通常內，建立並初始化對話方塊物件的命令處理常式，使用者所互動的對話方塊中，並關閉對話方塊。

對於強制回應對話方塊，您的處理常式會收集任何使用者輸入 對話方塊關閉後的資料。 因為其對話方塊視窗已關閉之後，就會有對話方塊物件，您可以只使用對話方塊類別的成員變數，擷取的資料。

非強制回應對話方塊，您可能會經常擷取資料從對話方塊物件仍然可見的對話方塊時。 在某些時候，會終結對話方塊物件;當發生這種情況，取決於您的程式碼。

## <a name="what-do-you-want-to-know-more-about"></a>您想要深入了解什麼

- [建立和顯示對話方塊](../mfc/creating-and-displaying-dialog-boxes.md)

- [建立強制回應對話方塊](../mfc/creating-modal-dialog-boxes.md)

- [建立非強制回應對話方塊](../mfc/creating-modeless-dialog-boxes.md)

- [在記憶體中使用的對話方塊範本](../mfc/using-a-dialog-template-in-memory.md)

- [設定對話方塊的背景色彩](../mfc/setting-the-dialog-boxs-background-color.md)

- [初始化對話方塊](../mfc/initializing-the-dialog-box.md)

- [在對話方塊中的處理 Windows 訊息](../mfc/handling-windows-messages-in-your-dialog-box.md)

- [從對話方塊物件擷取資料](../mfc/retrieving-data-from-the-dialog-object.md)

- [關閉對話方塊](../mfc/closing-the-dialog-box.md)

- [終結對話方塊](../mfc/destroying-the-dialog-box.md)

- [對話方塊資料交換 (DDX) 和驗證 (DDV)](../mfc/dialog-data-exchange-and-validation.md)

- [屬性工作表對話方塊](../mfc/property-sheets-and-property-pages-mfc.md)

## <a name="see-also"></a>另請參閱

[對話方塊](../mfc/dialog-boxes.md)
