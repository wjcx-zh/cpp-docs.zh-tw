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
ms.openlocfilehash: ce84863744629d30248f94b94448d776177f9841
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57292883"
---
# <a name="processing-notification-messages-in-date-and-time-picker-controls"></a>處理日期時間選擇器控制項中的通知訊息

當使用者與日期和時間選擇器控制項、 控制項互動 (`CDateTimeCtrl`) 傳送通知訊息至其父視窗，通常是檢視或對話方塊物件。 如果您想要執行動作以作為回應，請處理這些訊息。 例如，當使用者開啟以顯示內嵌的月曆控制項的日期和時間選擇器時，會傳送 DTN_DROPDOWN 告知。

使用 [屬性] 視窗，將通知處理常式加入您想要實作之這些訊息的父類別。

下列清單將描述各種日期和時間選擇器控制項所傳送的通知。

- DTN_DROPDOWN 告知在即將顯示內嵌月曆控制項的父代。 尚未設定 DTS_UPDOWN 樣式時，才會傳送此通知。 如需有關這項通知的詳細資訊，請參閱 <<c0> [ 存取內嵌月曆控制項](../mfc/accessing-the-embedded-month-calendar-control.md)。

- DTN_CLOSEUP 告知內嵌月曆控制項的父代即將關閉。 尚未設定 DTS_UPDOWN 樣式時，才會傳送此通知。

- DTN_DATETIMECHANGE 告知已發生變更，在控制項中的父代。

- DTN_FORMAT 告知在回呼欄位會顯示所需的文字是父代。 如需有關此通知和回呼欄位的詳細資訊，請參閱 <<c0> [ 日期和時間選擇器控制項中使用回呼欄位](../mfc/using-callback-fields-in-a-date-and-time-picker-control.md)。

- DTN_FORMATQUERY 要求提供在字串中會顯示在回呼欄位的允許大小上限的父代。 處理此通知可讓控制項正確地顯示在任何時間，減少重繪閃動內控制項的顯示的輸出。 如需有關這項通知的詳細資訊，請參閱 <<c0> [ 日期和時間選擇器控制項中使用回呼欄位](../mfc/using-callback-fields-in-a-date-and-time-picker-control.md)。

- DTN_USERSTRING 通知使用者已完成編輯的日期和時間選擇器內容的父控制項。 當已設定了 DTS_APPCANPARSE 樣式時，才會傳送此通知。

- 當使用者輸入的回呼欄位中時，DTN_WMKEYDOWN 會告知父代。 處理這個通知可模擬相同的鍵盤回應的日期和時間選擇器控制項中的非回呼欄位的支援。 如需有關這項通知的詳細資訊，請參閱 < [DTP 控制項支援回呼欄位](/windows/desktop/Controls/date-and-time-picker-controls)Windows SDK 中。

## <a name="see-also"></a>另請參閱

[使用 CDateTimeCtrl](../mfc/using-cdatetimectrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
