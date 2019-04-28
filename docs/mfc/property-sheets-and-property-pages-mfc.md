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
ms.openlocfilehash: 7ff2851cc4ed04a64f1a49d68b6e3143b5edccd8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62297017"
---
# <a name="property-sheets-and-property-pages-mfc"></a>屬性工作表和屬性頁 (MFC)

MFC [ 對話方塊](../mfc/dialog-boxes.md)可對透過加入屬性工作表和屬性頁的 「 索引標籤對話方塊 」 的外觀。 稱為 「 屬性工作表 」 在 MFC 中，這種對話方塊中，類似於許多對話方塊在 Microsoft Word、 Excel 和視覺效果C++，可能包含一堆索引標籤式的工作表，如同一堆從前面到後面或一群串聯 windows 看過的檔案資料夾。 在 [前端] 索引標籤上的控制項都是可見的;只加上標籤的索引標籤會顯示在後端的索引標籤上的。 屬性工作表是特別適用於管理大量的屬性或恰當且分為多個群組的設定。 一般而言，一個屬性工作表可以取代數個分開的對話方塊以簡化使用者介面。

根據 MFC 4.0 版，屬性工作表和屬性頁會實作使用隨附於 Windows 95 及 Windows NT 3.51 版及更新版本的通用控制項。

使用類別來實作的屬性工作表[CPropertySheet](../mfc/reference/cpropertysheet-class.md)並[CPropertyPage](../mfc/reference/cpropertypage-class.md) (中所述*MFC 參考 》*)。 `CPropertySheet` 定義整體的對話方塊中，其中可以包含多個 「 頁面 」 根據`CPropertyPage`。

如需建立和使用屬性工作表的詳細資訊，請參閱主題[屬性工作表](../mfc/property-sheets-mfc.md)。

## <a name="see-also"></a>另請參閱

[對話方塊](../mfc/dialog-boxes.md)<br/>
[對話方塊的生命週期](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[MFC 中的屬性工作表和屬性頁](../mfc/property-sheets-and-property-pages-in-mfc.md)<br/>
[交換資料](../mfc/exchanging-data.md)<br/>
[建立非強制回應屬性工作表](../mfc/creating-a-modeless-property-sheet.md)<br/>
[處理套用按鈕](../mfc/handling-the-apply-button.md)
