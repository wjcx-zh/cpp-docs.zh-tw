---
title: 屬性工作表和屬性頁 (MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], tabs
- property pages [MFC], property sheets
- CPropertyPage class [MFC], property sheets and pages
- CPropertySheet class [MFC], property sheets and pages
- property sheets, propert pages
ms.assetid: de8fea12-6c35-4cef-8625-b8073a379446
ms.openlocfilehash: 5d4fd1c957b7f4d0d6ad10379a448309743aa11a
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685074"
---
# <a name="property-sheets-and-property-pages-mfc"></a>屬性工作表和屬性頁 (MFC)

[MFC [] 對話方塊](../mfc/dialog-boxes.md)可以藉由整合屬性工作表和屬性頁來執行 [索引標籤對話方塊]。 在 MFC 中稱為「屬性工作表」，這種對話方塊與 Microsoft Word、Excel 和視覺效果C++中的許多對話方塊類似，似乎包含一堆索引標籤式工作表，非常類似從前端到後端的檔案資料夾堆疊，或一組串聯的視窗。 [Front] 索引標籤上的控制項可見;在後端索引標籤上，只會顯示 [已標記] 索引標籤。 屬性工作表特別適合用來管理大量內容或設定，而這些屬性或設定相當整齊地分成數個群組。 一般來說，一個屬性工作表可以藉由取代數個不同的對話方塊來簡化使用者介面。

從 MFC 版本4.0 開始，屬性工作表和屬性頁會使用 Windows 95 和 Windows NT 3.51 版和更新版本隨附的通用控制項來執行。

屬性工作表會使用[CPropertySheet](../mfc/reference/cpropertysheet-class.md)和[CPropertyPage](../mfc/reference/cpropertypage-class.md)類別來執行（如*MFC 參考*中所述）。 `CPropertySheet` 定義整體對話方塊，其中可以包含以 `CPropertyPage` 為基礎的多個「頁面」。

如需建立和使用屬性工作表的詳細資訊，請參閱主題[屬性工作表](../mfc/property-sheets-mfc.md)。

## <a name="see-also"></a>另請參閱

[對話方塊](../mfc/dialog-boxes.md)<br/>
[在 MFC 中使用對話方塊](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[MFC 中的屬性工作表和屬性頁](../mfc/property-sheets-and-property-pages-in-mfc.md)<br/>
[交換資料](../mfc/exchanging-data.md)<br/>
[建立非強制回應屬性工作表](../mfc/creating-a-modeless-property-sheet.md)<br/>
[處理套用按鈕](../mfc/handling-the-apply-button.md)
