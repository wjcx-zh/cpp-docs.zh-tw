---
title: 處理日期時間選擇器控制項中的通知訊息
ms.date: 11/04/2016
f1_keywords:
- DTN_CLOSEUP
- DTN_DATETIMECHANGE
- DTN_DROPDOWN
helpviewer_keywords:
- DTN_DROPDOWN notification [MFC]
- DTN_DATETIMECHANGE notification [MFC]
- DTN_CLOSEUP notification [MFC]
- DateTimePicker control [MFC], handling notifications
- CDateTimeCtrl class [MFC], handling notifications
- DTN_FORMAT notification [MFC]
- DateTimePicker control [MFC]
ms.assetid: ffbe29ab-ff80-4609-89f7-260b404439c4
ms.openlocfilehash: 3c568d231cc02b2529a4d97ab7faed51c1737b19
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620996"
---
# <a name="processing-notification-messages-in-date-and-time-picker-controls"></a>處理日期時間選擇器控制項中的通知訊息

當使用者與日期和時間選擇器控制項互動時，控制項（ `CDateTimeCtrl` ）會將通知訊息傳送至其父視窗，通常是 view 或 dialog 物件。 如果您想要執行動作以作為回應，請處理這些訊息。 例如，當使用者開啟日期和時間選擇器以顯示內嵌月曆控制項時，就會傳送 DTN_DROPDOWN 通知。

使用 [[類別] [Wizard]](reference/mfc-class-wizard.md) ，將通知處理常式新增至您要執行之訊息的父類別。

下列清單描述日期和時間選擇器控制項所傳送的各種通知。

- DTN_DROPDOWN 通知父系即將顯示內嵌月曆控制項。 只有在尚未設定 DTS_UPDOWN 樣式時，才會傳送此通知。 如需有關此通知的詳細資訊，請參閱[存取內嵌月曆控制項](accessing-the-embedded-month-calendar-control.md)。

- DTN_CLOSEUP 通知父系，即將關閉內嵌月曆控制項。 只有在尚未設定 DTS_UPDOWN 樣式時，才會傳送此通知。

- DTN_DATETIMECHANGE 會通知父系控制項中已發生變更。

- DTN_FORMAT 通知父系需要在回呼欄位中顯示文字。 如需有關此通知和回呼欄位的詳細資訊，請參閱[在日期和時間選擇器控制項中使用回呼欄位](using-callback-fields-in-a-date-and-time-picker-control.md)。

- DTN_FORMATQUERY 要求父系提供將在回呼欄位中顯示之字串的允許大小上限。 處理此通知可讓控制項隨時正確地顯示輸出，減少控制項顯示內的閃爍。 如需有關此通知的詳細資訊，請參閱[在日期和時間選擇器控制項中使用回呼欄位](using-callback-fields-in-a-date-and-time-picker-control.md)。

- DTN_USERSTRING 會通知父系，表示使用者已完成編輯日期和時間選擇器控制項的內容。 只有在已設定 DTS_APPCANPARSE 樣式時，才會傳送此通知。

- 當使用者在回呼欄位中輸入時，DTN_WMKEYDOWN 通知父系。 處理此通知，以模擬日期和時間選擇器控制項中，非回呼欄位支援的相同鍵盤回應。 如需有關此通知的詳細資訊，請參閱 Windows SDK 中的[DTP 控制項支援回呼欄位](/windows/win32/Controls/date-and-time-picker-controls)。

## <a name="see-also"></a>另請參閱

[使用 CDateTimeCtrl](using-cdatetimectrl.md)<br/>
[控制項](controls-mfc.md)
