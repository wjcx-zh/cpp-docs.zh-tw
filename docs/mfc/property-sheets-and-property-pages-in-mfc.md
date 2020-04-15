---
title: MFC 中的屬性工作表和屬性頁
ms.date: 11/04/2016
helpviewer_keywords:
- property pages [MFC], MFC
- controls [MFC], property sheets
- property sheets, MFC
- tab dialog boxes
ms.assetid: e1bede2b-0285-4b88-a052-0f8a372807a2
ms.openlocfilehash: 10fb34c79745e672d30dd2d3c3b97d457583f795
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371176"
---
# <a name="property-sheets-and-property-pages-in-mfc"></a>MFC 中的屬性工作表和屬性頁

屬性表(也稱為選項卡對話方塊)是一個包含屬性頁的對話方塊。 每個屬性頁都基於對話框範本資源,並包含控制項。 它包含在頁面上,上面有一個選項卡。 選項卡命名頁面並指示其用途。 使用者按一下屬性表中的選項卡以選擇一組控制項。

使用頁面將屬性表中的控制件分組到有意義的集中。 包含的屬性表通常具有其自己的多個控制項。 這些適用於所有頁面。

屬性表基於類別[C 屬性表](../mfc/reference/cpropertysheet-class.md)。 屬性頁面基於[類別 CPropertyPage](../mfc/reference/cpropertypage-class.md)。

屬性表是一種特殊的對話框,通常用於修改某些外部物件的屬性,例如視圖中的當前選擇。 屬性表有三個主要部分:包含對話框、一個或多個屬性頁一次顯示一個,以及使用者按一下以選擇該頁面的每個頁面頂部的選項卡。 屬性表可用於您有多個類似的設定組或要更改的選項的情況。 屬性表以易於理解的方式對信息進行分組。

> [!NOTE]
> 當您嘗試使用`CPropertySheet::DoModal`顯示屬性表時,系統可能會生成第一個異常。 發生此例外的原因是系統在建立物件之前試著變更物件[的視窗樣式](../mfc/reference/styles-used-by-mfc.md#window-styles)。 有關此異常的詳細資訊以及如何避免或處理它,請參閱[CPropertySheet::DoModal](../mfc/reference/cpropertysheet-class.md#domodal)。

## <a name="see-also"></a>另請參閱

[屬性表](../mfc/property-sheets-mfc.md)
