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
ms.openlocfilehash: 66a9ef7fd49ea81ddac4779aa6d1c3f12fbe4c55
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617369"
---
# <a name="accessing-the-embedded-month-calendar-control"></a>存取內嵌月曆控制項

您可以 `CDateTimeCtrl` 呼叫[GetMonthCalCtrl](reference/cdatetimectrl-class.md#getmonthcalctrl)成員函式，從物件存取內嵌月曆控制項物件。

> [!NOTE]
> 只有在日期和時間選擇器控制項未設定**DTS_UPDOWN**樣式時，才會使用內嵌月曆控制項。

如果您要先修改某些屬性再顯示內嵌控制項，這會很有用。 若要完成此動作，請處理**DTN_DROPDOWN**通知、取出月曆控制項（使用[CDateTimeCtrl：： GetMonthCalCtrl](reference/cdatetimectrl-class.md#getmonthcalctrl)），並進行修改。 可惜的是，月曆控制項不是永久性的。

換句話說，當使用者要求顯示月曆控制項時，會建立新的月曆控制項（在**DTN_DROPDOWN**通知之前）。 當使用者關閉控制項時，控制項會損毀（在**DTN_CLOSEUP**通知之後）。 這表示在內嵌控制項顯示之前，您修改的任何屬性都會在內嵌控制項關閉時遺失。

下列範例會使用**DTN_DROPDOWN**通知的處理常式來示範此程式。 程式碼會將月曆控制項的背景色彩變更為灰色，並將[SetMonthCalColor](reference/cdatetimectrl-class.md#setmonthcalcolor)的呼叫。 程式碼如下所示：

[!code-cpp[NVC_MFCControlLadenDialog#5](codesnippet/cpp/accessing-the-embedded-month-calendar-control_1.cpp)]

如先前所述，當內嵌控制項關閉時，會遺失對月曆控制項屬性所做的任何修改，但有兩個例外狀況。 第一個例外狀況是月曆控制項的顏色，先前已經討論過。 第二個例外狀況是月曆控制項所使用的字型。 您可以藉由呼叫[CDateTimeCtrl：： SetMonthCalFont](reference/cdatetimectrl-class.md#setmonthcalfont)來修改預設字型，傳遞現有字型的控制碼。 下列範例 (其中 `m_dtPicker` 是日期和時間控制項物件) 說明一種可能的方法：

[!code-cpp[NVC_MFCControlLadenDialog#6](codesnippet/cpp/accessing-the-embedded-month-calendar-control_2.cpp)]

一旦呼叫 `CDateTimeCtrl::SetMonthCalFont` 變更字型後，下一次月曆便會顯示已儲存並使用的新字型。

## <a name="see-also"></a>另請參閱

[使用 CDateTimeCtrl](using-cdatetimectrl.md)<br/>
[控制項](controls-mfc.md)
