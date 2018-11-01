---
title: Rich Edit 控制項中目前的選取範圍
ms.date: 11/04/2016
helpviewer_keywords:
- current selection in CRichEditCtrls
- CRichEditCtrl class [MFC], current selection in
- rich edit controls [MFC], current selection in
- selection, current in CRichEditCtrl
ms.assetid: f6b2a2b6-5481-4ad3-9720-6dd772ea6fc8
ms.openlocfilehash: 4b4b4d0b3419201cd1243bf6f846ab0e1b5ed686
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50636499"
---
# <a name="current-selection-in-a-rich-edit-control"></a>Rich Edit 控制項中目前的選取範圍

使用者可以選取 rich edit 控制項中的文字 ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) 使用滑鼠或鍵盤。 目前的選取範圍的所選的字元範圍或插入點，如果沒有任何字元的位置選取。 應用程式可以取得目前的選取範圍的相關資訊，設定目前的選取項目，判斷當目前的選取項目變更和顯示或隱藏選取反白顯示。

若要判斷 rich edit 控制項中目前的選取範圍，請使用[GetSel](../mfc/reference/cricheditctrl-class.md#getsel)成員函式。 若要設定目前的選取範圍，請使用[SetSel](../mfc/reference/cricheditctrl-class.md#setsel)成員函式。 [CHARRANGE](/windows/desktop/api/richedit/ns-richedit-_charrange)結構來使用這些函式指定的字元範圍。 若要擷取目前的選取範圍的內容的相關資訊，您可以使用[GetSelectionType](../mfc/reference/cricheditctrl-class.md#getselectiontype)成員函式。

根據預設，rich edit 控制項顯示，並獲得和失去焦點時，會隱藏反白顯示的選取項目。 您可以顯示或隱藏在任何時間的反白顯示的選取項目，使用[HideSelection](../mfc/reference/cricheditctrl-class.md#hideselection)成員函式。 例如，應用程式可能會提供在 rich edit 控制項中尋找文字的 [搜尋] 對話方塊。 應用程式可能會選取相符的文字，而不需要關閉對話方塊時，它必須在此情況下使用`HideSelection`反白顯示選取項目。

若要選取的文字在 rich edit 控制項中，使用[GetSelText](../mfc/reference/cricheditctrl-class.md#getseltext)成員函式。 將文字複製到指定的字元陣列。 您必須確定陣列足以容納選取的文字，再加上結束的 null 字元。

您可以使用 rich edit 控制項中的字串搜尋[FindText](../mfc/reference/cricheditctrl-class.md#findtext)成員函式[FINDTEXTEX](/windows/desktop/api/richedit/ns-richedit-_findtextexa)搭配此函式的結構指定的文字範圍搜尋及要搜尋的字串。 您也可以指定這些選項做為搜尋是否區分大小寫。

## <a name="see-also"></a>另請參閱

[使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)

