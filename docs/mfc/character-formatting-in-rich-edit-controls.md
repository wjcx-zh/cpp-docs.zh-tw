---
title: Rich Edit 控制項中的字元格式化
ms.date: 11/04/2016
helpviewer_keywords:
- formatting [MFC], characters
- rich edit controls [MFC], character formatting in
- CRichEditCtrl class [MFC], character formatting in
ms.assetid: c80f4305-75ad-45f9-8d17-d83d0fe79be5
ms.openlocfilehash: 0b9d925b6ba3157177b7012d1e303ef7b7ddab46
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624940"
---
# <a name="character-formatting-in-rich-edit-controls"></a>Rich Edit 控制項中的字元格式化

您可以使用 rich edit 控制項（[CRichEditCtrl](reference/cricheditctrl-class.md)）的成員函式來格式化字元，並取出格式資訊。 針對字元，您可以指定字樣、大小、色彩和效果，例如粗體、斜體和 protected。

您可以使用[SetSelectionCharFormat](reference/cricheditctrl-class.md#setselectioncharformat)和[SetWordCharFormat](reference/cricheditctrl-class.md#setwordcharformat)成員函式來套用字元格式。 若要判斷所選取文字的目前字元格式，請使用[GetSelectionCharFormat](reference/cricheditctrl-class.md#getselectioncharformat)成員函式。 [CHARFORMAT](/windows/win32/api/richedit/ns-richedit-charformata)結構會與這些成員函式搭配使用，以指定字元屬性。 **CHARFORMAT**的其中一個重要成員是**dwMask**。 在 `SetSelectionCharFormat` 和中 `SetWordCharFormat` ， **dwMask**會指定要由這個函式呼叫設定哪些字元屬性。 `GetSelectionCharFormat`報告選取範圍中第一個字元的屬性;**dwMask**會指定在整個選取範圍中一致的屬性。

您也可以取得並設定「預設字元格式」，這是套用至任何後續插入字元的格式。 例如，如果應用程式將預設字元格式設定為粗體，而使用者接著輸入字元，則該字元會是粗體。 若要取得和設定預設字元格式，請使用[GetDefaultCharFormat](reference/cricheditctrl-class.md#getdefaultcharformat)和[SetDefaultCharFormat](reference/cricheditctrl-class.md#setdefaultcharformat)成員函式。

「Protected」字元屬性不會變更文字的外觀。 如果使用者嘗試修改受保護的文字，rich edit 控制項會將**EN_PROTECTED**通知訊息傳送給其父視窗，允許父視窗允許或防止變更。 若要接收此通知訊息，您必須使用[SetEventMask](reference/cricheditctrl-class.md#seteventmask)成員函式來加以啟用。 如需事件遮罩的詳細資訊，請參閱本主題稍後的[來自 Rich Edit 控制項的通知](notifications-from-a-rich-edit-control.md)。

前景色彩是字元屬性，但背景色彩是 rich edit 控制項的屬性。 若要設定背景色彩，請使用[SetBackgroundColor](reference/cricheditctrl-class.md#setbackgroundcolor)成員函式。

## <a name="see-also"></a>另請參閱

[使用 CRichEditCtrl](using-cricheditctrl.md)<br/>
[控制項](controls-mfc.md)
