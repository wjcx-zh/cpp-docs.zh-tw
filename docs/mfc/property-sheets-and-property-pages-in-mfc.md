---
title: 屬性工作表和 MFC 中的屬性頁 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- property pages [MFC], MFC
- controls [MFC], property sheets
- property sheets, MFC
- tab dialog boxes
ms.assetid: e1bede2b-0285-4b88-a052-0f8a372807a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f35282ce46aff3a3f0fba5fca505653cd892a392
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46430033"
---
# <a name="property-sheets-and-property-pages-in-mfc"></a>MFC 中的屬性工作表和屬性頁

屬性工作表，也稱為索引標籤對話方塊中，會包含屬性頁的對話方塊。 每個屬性頁對話方塊範本資源為基礎，並包含控制項。 它會以頁面上，最上層顯示 索引標籤。 [] 索引標籤命名頁面，並指出其用途。 使用者按一下來選取一組控制項的屬性工作表中的索引標籤。

您可以使用頁面屬性工作表中的這些控制項聚集成有意義的集合。 包含的屬性工作表通常會有自己的數個控制項。 這些適用於所有頁面。

以類別為基礎的屬性工作表[CPropertySheet](../mfc/reference/cpropertysheet-class.md)。 屬性頁面會以類別為基礎[CPropertyPage](../mfc/reference/cpropertypage-class.md)。

屬性工作表是一種特殊的對話方塊中，通常用來修改某些外部物件，例如目前的選取範圍，在檢視中的屬性。 屬性工作表有三個主要部分: [包含] 對話方塊中，一或多個屬性頁，顯示的一次，並在使用者按一下以選取該頁面的每個頁面頂端的索引標籤。 屬性工作表可用於當您具有數個類似的群組，設定或變更的選項。 屬性工作表，以易於了解的方式分組的資訊。

> [!NOTE]
>  當您嘗試使用顯示屬性工作表`CPropertySheet::DoModal`，系統可能會產生 first-chance 例外狀況。 因為系統嘗試變更，就會發生這個例外狀況[的視窗樣式](../mfc/reference/styles-used-by-mfc.md#window-styles)之前已建立物件的物件。 如需有關此例外狀況，以及如何避免它，或處理的詳細資訊，請參閱[cpropertysheet:: Setwizardmode](../mfc/reference/cpropertysheet-class.md#domodal)。

## <a name="see-also"></a>另請參閱

[屬性工作表](../mfc/property-sheets-mfc.md)

