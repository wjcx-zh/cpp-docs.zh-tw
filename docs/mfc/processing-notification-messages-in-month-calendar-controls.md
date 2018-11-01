---
title: 處理月曆控制項中的通知訊息
ms.date: 11/04/2016
helpviewer_keywords:
- CMonthCalCtrl class [MFC], notifications
- CMonthCalCtrl class [MFC], day states
- month calendar controls [MFC], notification messages
- notifications [MFC], for CMonthCalCtrl
- notifications [MFC], month calendar control
ms.assetid: 607c3e90-0756-493b-9503-ce835a50c7ab
ms.openlocfilehash: 3dbf50080bea59c4df4a9c92a135a65b093f7674
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50511926"
---
# <a name="processing-notification-messages-in-month-calendar-controls"></a>處理月曆控制項中的通知訊息

當使用者月曆控制項 （選取的日期和/或檢視不同的月份），與控制項互動 (`CMonthCalCtrl`) 傳送通知訊息至其父視窗，通常是檢視或對話方塊物件。 如果您想要執行動作以作為回應，請處理這些訊息。 例如，當使用者選取新的月份，若要檢視，您可以提供一組應該要強調的一點的日期。

使用 [屬性] 視窗，將通知處理常式加入您想要實作之這些訊息的父類別。

下列清單描述月曆控制項所傳送的各種通知。

- 了解哪種日期應該以粗體顯示的 MCN_GETDAYSTATE 要求資訊。 如需處理這項通知的詳細資訊，請參閱[設定月曆控制項的日期狀態](../mfc/setting-the-day-state-of-a-month-calendar-control.md)。

- MCN_SELCHANGE 告知父代的所選取的日期範圍已變更。

- MCN_SELECT 告知父代已明確選取日期。

## <a name="see-also"></a>另請參閱

[使用 CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)

