---
title: 存取內嵌月曆控制項
ms.date: 11/04/2016
helpviewer_keywords:
- DateTimePicker control [MFC], accessing month calendar
- CDateTimeCtrl class [MFC], accessing embedded control
- month calendar controls [MFC], embedded in date/time picker
- CMonthCalCtrl class [MFC], changing the font
- month calendar controls [MFC], changing the font
- DateTimePicker control [MFC]
ms.assetid: 355e97ed-cf81-4df3-a2f8-9ddbbde93227
ms.openlocfilehash: dfe6fa220e19deebd86e7c8b7bd25dab60165f73
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57292129"
---
# <a name="accessing-the-embedded-month-calendar-control"></a>存取內嵌月曆控制項

您可以從存取內嵌的月曆控制項物件`CDateTimeCtrl`藉由呼叫物件[GetMonthCalCtrl](../mfc/reference/cdatetimectrl-class.md#getmonthcalctrl)成員函式。

> [!NOTE]
>  只有在沒有日期和時間選擇器控制項時，才使用內嵌的月曆控制項**DTS_UPDOWN**樣式集。

如果您要先修改某些屬性再顯示內嵌控制項，這會很有用。 若要完成這項作業，處理**DTN_DROPDOWN**通知，擷取月曆控制項 (使用[cdatetimectrl:: Getmonthcalctrl](../mfc/reference/cdatetimectrl-class.md#getmonthcalctrl))，並進行修改。 可惜的是，月曆控制項不是永久性的。

換句話說，當使用者要求顯示月曆控制項，會建立新的月份行事曆控制項 (之前**DTN_DROPDOWN**通知)。 將控制項終結 (之後**DTN_CLOSEUP**通知) 時使用者關閉。 這表示在內嵌控制項顯示之前，您修改的任何屬性都會在內嵌控制項關閉時遺失。

下列範例示範此程序，使用的處理常式**DTN_DROPDOWN**通知。 程式碼變更月曆控制項，藉由呼叫的背景色彩[SetMonthCalColor](../mfc/reference/cdatetimectrl-class.md#setmonthcalcolor)，設為灰色。 程式碼如下所示：

[!code-cpp[NVC_MFCControlLadenDialog#5](../mfc/codesnippet/cpp/accessing-the-embedded-month-calendar-control_1.cpp)]

如先前所述，當內嵌控制項關閉時，會遺失對月曆控制項屬性所做的任何修改，但有兩個例外狀況。 第一個例外狀況是月曆控制項的顏色，先前已經討論過。 第二個例外狀況是月曆控制項所使用的字型。 您可以藉由呼叫以修改預設字型[cdatetimectrl:: Setmonthcalfont](../mfc/reference/cdatetimectrl-class.md#setmonthcalfont)，傳遞現有字型的控制代碼。 下列範例 (其中 `m_dtPicker` 是日期和時間控制項物件) 說明一種可能的方法：

[!code-cpp[NVC_MFCControlLadenDialog#6](../mfc/codesnippet/cpp/accessing-the-embedded-month-calendar-control_2.cpp)]

一旦呼叫 `CDateTimeCtrl::SetMonthCalFont` 變更字型後，下一次月曆便會顯示已儲存並使用的新字型。

## <a name="see-also"></a>另請參閱

[使用 CDateTimeCtrl](../mfc/using-cdatetimectrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
