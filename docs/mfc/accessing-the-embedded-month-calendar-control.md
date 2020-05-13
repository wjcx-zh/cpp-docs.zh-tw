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
ms.openlocfilehash: 69270cc5663406f2c5d38ffccdbd35f39298a3d5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354188"
---
# <a name="accessing-the-embedded-month-calendar-control"></a>存取內嵌月曆控制項

可以通過調用[GetMonthCalCtrl](../mfc/reference/cdatetimectrl-class.md#getmonthcalctrl)成員`CDateTimeCtrl`函數從 物件存取嵌入的月曆控制物件。

> [!NOTE]
> 僅當日期和時間選取器控制項沒有**設定DTS_UPDOWN**樣式時,才使用嵌入的月曆控制件。

如果您要先修改某些屬性再顯示內嵌控制項，這會很有用。 為此,請處理**DTN_DROPDOWN**通知,檢索月曆控件(使用[CDateTimeCtrl::getMonthCalCtrl),](../mfc/reference/cdatetimectrl-class.md#getmonthcalctrl)然後進行修改。 可惜的是，月曆控制項不是永久性的。

換句話說,當使用者請求顯示月曆控件時,將創建新的月日曆控件(**在通知DTN_DROPDOWN**之前)。 當用戶拒絕時,控件將銷毀 **(DTN_CLOSEUP**通知后)。 這表示在內嵌控制項顯示之前，您修改的任何屬性都會在內嵌控制項關閉時遺失。

下面的示例演示了此過程,使用**處理程式執行DTN_DROPDOWN**通知。 代碼將月曆控制件的背景顏色更改為灰色,調用[SetMonthCalColor。](../mfc/reference/cdatetimectrl-class.md#setmonthcalcolor) 程式碼如下所示：

[!code-cpp[NVC_MFCControlLadenDialog#5](../mfc/codesnippet/cpp/accessing-the-embedded-month-calendar-control_1.cpp)]

如先前所述，當內嵌控制項關閉時，會遺失對月曆控制項屬性所做的任何修改，但有兩個例外狀況。 第一個例外狀況是月曆控制項的顏色，先前已經討論過。 第二個例外狀況是月曆控制項所使用的字型。 您可以通過調用[CDateTimeCtrl::setMonthCalFont](../mfc/reference/cdatetimectrl-class.md#setmonthcalfont)來修改預設字體,傳遞現有字體的句柄。 下列範例 (其中 `m_dtPicker` 是日期和時間控制項物件) 說明一種可能的方法：

[!code-cpp[NVC_MFCControlLadenDialog#6](../mfc/codesnippet/cpp/accessing-the-embedded-month-calendar-control_2.cpp)]

一旦呼叫 `CDateTimeCtrl::SetMonthCalFont` 變更字型後，下一次月曆便會顯示已儲存並使用的新字型。

## <a name="see-also"></a>另請參閱

[使用 CDateTimeCtrl](../mfc/using-cdatetimectrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
