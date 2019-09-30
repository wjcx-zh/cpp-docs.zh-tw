---
title: 在 MFC 中使用對話方塊
ms.date: 09/27/2019
helpviewer_keywords:
- dialog boxes [MFC], life cycle
- modal dialog boxes [MFC], life cycle
- modeless dialog boxes [MFC], life cycle
- MFC dialog boxes [MFC], life cycle
- life cycle of dialog boxes [MFC]
ms.assetid: e16fd78e-238d-4f31-8c9d-8564f3953bd9
ms.openlocfilehash: ad15250cf9a8dd663072cf9423263260bbb40a0e
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685722"
---
# <a name="working-with-dialog-boxes-in-mfc"></a>在 MFC 中使用對話方塊

在對話方塊的生命週期內，使用者會叫用對話方塊，通常是在建立和初始化對話方塊物件的命令處理常式內，使用者會與對話方塊互動，然後對話方塊會關閉。

對於強制回應對話方塊，您的處理常式會在對話方塊關閉後，收集使用者所輸入的任何資料。 由於對話方塊物件在對話方塊視窗已關閉之後就存在，因此您可以直接使用對話方塊類別的成員變數來解壓縮資料。

對於非強制回應對話方塊，您通常可能會在對話方塊仍然可見時，從對話方塊物件中解壓縮資料。 在某個時間點，對話方塊物件已終結;發生這種情況時，會視您的程式碼而定。

## <a name="what-do-you-want-to-know-more-about"></a>您想要深入瞭解的內容

- [建立和顯示對話方塊](../mfc/creating-and-displaying-dialog-boxes.md)

- [建立強制回應對話方塊](../mfc/creating-modal-dialog-boxes.md)

- [建立非強制回應對話方塊](../mfc/creating-modeless-dialog-boxes.md)

- [使用記憶體中的對話方塊範本](../mfc/using-a-dialog-template-in-memory.md)

- [設定對話方塊的背景色彩](../mfc/setting-the-dialog-boxs-background-color.md)

- [初始化對話方塊](../mfc/initializing-the-dialog-box.md)

- [處理對話方塊中的 Windows 訊息](../mfc/handling-windows-messages-in-your-dialog-box.md)

- [正在從 dialog 物件中抓取資料](../mfc/retrieving-data-from-the-dialog-object.md)

- [關閉對話方塊](../mfc/closing-the-dialog-box.md)

- [終結對話方塊](../mfc/destroying-the-dialog-box.md)

- [對話方塊資料交換（DDX）和驗證（DDV）](../mfc/dialog-data-exchange-and-validation.md)

- [屬性工作表對話方塊](../mfc/property-sheets-and-property-pages-mfc.md)

## <a name="see-also"></a>另請參閱

[對話方塊](../mfc/dialog-boxes.md)
