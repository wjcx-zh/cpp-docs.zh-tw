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
ms.openlocfilehash: 452d24bf1ffd157366f357a510e8c8cfaad28d91
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908085"
---
# <a name="processing-notification-messages-in-month-calendar-controls"></a>處理月曆控制項中的通知訊息

當使用者與月曆控制項互動（選取日期和/或查看不同的月份）時，控制項（`CMonthCalCtrl`）會將通知訊息傳送至其父視窗，通常是 view 或 dialog 物件。 如果您想要執行動作以作為回應，請處理這些訊息。 例如，當使用者選取要觀看的新月份時，您可以提供一組應該強調的日期。

使用 [[類別] [Wizard]](reference/mfc-class-wizard.md) ，將通知處理常式新增至您要執行之訊息的父類別。

下列清單描述月曆控制項所傳送的各種通知。

- MCN_GETDAYSTATE 會要求應以粗體顯示哪幾天的相關資訊。 如需處理此通知的詳細資訊，請參閱[設定月曆控制項的日期狀態](../mfc/setting-the-day-state-of-a-month-calendar-control.md)。

- MCN_SELCHANGE 會通知父系選取的日期或日期範圍已變更。

- MCN_SELECT 會通知父系已進行明確的選取日期。

## <a name="see-also"></a>另請參閱

[使用 CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
