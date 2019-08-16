---
title: Rich Edit 控制項中的剪貼簿流作業
ms.date: 11/04/2016
helpviewer_keywords:
- pasting Clipboard data
- CRichEditCtrl class [MFC], paste operation
- cut operation in CRichEditCtrl class [MFC]
- CRichEditCtrl class [MFC], Clipboard operations
- copy operations in rich edit controls
- Clipboard, operations in CRichEditCtrl
- rich edit controls [MFC], Clipboard operations
ms.assetid: 15ce66bc-2636-4a35-a2ae-d52285dc1af6
ms.openlocfilehash: e232010b443ace245844f1c28649477cccc8e9e4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508965"
---
# <a name="clipboard-operations-in-rich-edit-controls"></a>Rich Edit 控制項中的剪貼簿流作業

您的應用程式可以使用最適用的剪貼簿格式或特定的剪貼簿格式, 將剪貼簿的內容貼入 rich edit 控制項 ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) 中。 您也可以判斷 Rich Edit 控制項是否可以貼上剪貼簿格式。

您可以使用 [[複製](../mfc/reference/cricheditctrl-class.md#copy)] 或 [[剪](../mfc/reference/cricheditctrl-class.md#cut)下] 成員函式來複製或剪下目前選取範圍的內容。 同樣地, 您可以使用 [[貼](../mfc/reference/cricheditctrl-class.md#paste)上] 成員函式, 將剪貼簿的內容貼入 rich edit 控制項。 控制項會先貼上其所辨識的第一個可用的格式，這大概會是最具描述性的格式。

若要貼上特定的剪貼簿格式, 您可以使用[PasteSpecial](../mfc/reference/cricheditctrl-class.md#pastespecial)成員函式。 這個函式對於提供 Paste Special 命令，讓使用者選取剪貼簿格式的應用程式非常有幫助。 您可以使用[CanPaste](../mfc/reference/cricheditctrl-class.md#canpaste)成員函式來判斷控制項是否能辨識給定的格式。

您也可以使用 `CanPaste` 來判斷 Rich Edit 控制項是否已辨識出可用的剪貼簿格。 這個函式適用於 `OnInitMenuPopup` 處理常式。 應用程式可能會根據控制項是否可貼上任何可用的格式來啟用或停用其貼上命令。

Rich Edit 控制項會註冊兩種剪貼簿格式：RTF 格式和所呼叫 RichEdit 文字和物件的格式。 應用程式可以使用[RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)函數來註冊這些格式, 並指定**CF_RTF**和**CF_RETEXTOBJ**值。

## <a name="see-also"></a>另請參閱

[使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
