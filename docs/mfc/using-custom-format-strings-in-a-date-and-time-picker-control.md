---
title: 在日期時間選擇器控制項中使用自訂格式字串
ms.date: 11/04/2016
helpviewer_keywords:
- CDateTimeCtrl class [MFC], display styles
- DateTimePicker control [MFC], display styles
- DateTimePicker control [MFC]
ms.assetid: 7d577f03-6ca0-4597-9093-50b78f304719
ms.openlocfilehash: 2e3e980649264a6842abcc9491171e5105dbab17
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50557482"
---
# <a name="using-custom-format-strings-in-a-date-and-time-picker-control"></a>在日期時間選擇器控制項中使用自訂格式字串

根據預設，日期時間選擇器控制項會以三種格式類型 (每種格式對應一獨特的樣式) 顯示目前的日期或時間：

- **DTS_LONGDATEFORMAT**以長格式，產生如"Wednesday，January 3，2000"的輸出中顯示的日期。

- **DTS_SHORTDATEFORMAT**簡短格式，產生如 「 1/3/00 」 的輸出中顯示的日期。

- **DTS_TIMEFORMAT**以長格式，產生如 「 5:31:42 PM 」 輸出中顯示的時間。

不過，您可以使用自訂格式字串，自訂日期或時間的顯示外觀。 這個自訂字串由現有的格式字元、非格式字元組成或混合兩者。 一旦建立自訂的字串，請呼叫[cdatetimectrl:: Setformat](../mfc/reference/cdatetimectrl-class.md#setformat)傳入您的自訂字串。 日期和時間選擇器控制項會使用您的自訂格式字串顯示目前的值。

下列範例程式碼 (其中*這裡，m_dtPicker*是`CDateTimeCtrl`物件) 示範一個可行的解決方案：

[!code-cpp[NVC_MFCControlLadenDialog#7](../mfc/codesnippet/cpp/using-custom-format-strings-in-a-date-and-time-picker-control_1.cpp)]

除了自訂格式字串的日期和時間選擇器控制項也支援[回呼欄位](../mfc/using-callback-fields-in-a-date-and-time-picker-control.md)。

## <a name="see-also"></a>另請參閱

[使用 CDateTimeCtrl](../mfc/using-cdatetimectrl.md)<br/>
[控制項](../mfc/controls-mfc.md)

