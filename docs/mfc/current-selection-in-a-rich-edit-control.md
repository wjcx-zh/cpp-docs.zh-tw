---
title: Rich Edit 控制項中目前的選取範圍
ms.date: 11/04/2016
helpviewer_keywords:
- current selection in CRichEditCtrls
- CRichEditCtrl class [MFC], current selection in
- rich edit controls [MFC], current selection in
- selection, current in CRichEditCtrl
ms.assetid: f6b2a2b6-5481-4ad3-9720-6dd772ea6fc8
ms.openlocfilehash: e493f46e2a2b5bec695177e8c8da9c09de13376d
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916458"
---
# <a name="current-selection-in-a-rich-edit-control"></a>Rich Edit 控制項中目前的選取範圍

使用者可以使用滑鼠或鍵盤, 在 rich edit 控制項 ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) 中選取文字。 目前的選取範圍是所選字元的範圍, 如果未選取任何字元, 則為插入點的位置。 應用程式可以取得目前選取範圍的相關資訊、設定目前的選取範圍、判斷目前的選取範圍何時變更, 以及顯示或隱藏選取範圍醒目提示。

若要判斷 rich edit 控制項中目前的選取範圍, 請使用[GetSel](../mfc/reference/cricheditctrl-class.md#getsel)成員函式。 若要設定目前的選取範圍, 請使用[SetSel](../mfc/reference/cricheditctrl-class.md#setsel)成員函式。 [CHARRANGE](/windows/desktop/api/richedit/ns-richedit-charrange)結構會與這些函數搭配使用, 以指定字元範圍。 若要取得目前選取範圍內容的相關資訊, 您可以使用[GetSelectionType](../mfc/reference/cricheditctrl-class.md#getselectiontype)成員函式。

根據預設, rich edit 控制項會在取得並失去焦點時, 顯示並隱藏選取專案反白顯示。 您可以使用[HideSelection](../mfc/reference/cricheditctrl-class.md#hideselection)成員函式, 隨時顯示或隱藏選取專案醒目提示。 例如, 應用程式可能會提供 [搜尋] 對話方塊, 以在 rich edit 控制項中尋找文字。 應用程式可能會選取相符的文字而不關閉對話方塊, 在此情況下, `HideSelection`它必須使用來反白顯示選取專案。

若要取得 rich edit 控制項中選取的文字, 請使用[GetSelText](../mfc/reference/cricheditctrl-class.md#getseltext)成員函式。 文字會複製到指定的字元陣列。 您必須確定陣列夠大, 足以容納選取的文字加上終止的 null 字元。

您可以使用[FindText](../mfc/reference/cricheditctrl-class.md#findtext)成員函式來搜尋 rich edit 控制項中的字串, 此函式與此函式搭配使用的[FINDTEXTEX](/windows/desktop/api/richedit/ns-richedit-findtextexa)結構會指定要搜尋的文字範圍和要搜尋的字串。 您也可以指定這些選項, 如同搜尋是否區分大小寫。

## <a name="see-also"></a>另請參閱

[使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
