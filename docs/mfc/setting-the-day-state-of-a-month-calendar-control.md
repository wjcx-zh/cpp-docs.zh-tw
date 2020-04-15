---
title: 設定月曆控制項的日期狀態
ms.date: 11/04/2016
f1_keywords:
- MCN_GETDAYSTATE
helpviewer_keywords:
- CMonthCalCtrl class [MFC], setting day state info
- MCN_GETDAYSTATE notification [MFC]
- month calendar controls [MFC], day state info
ms.assetid: 435d1b11-ec0e-4121-9e25-aaa6af812a3c
ms.openlocfilehash: 9892f2d853687787dd76428fc9bc95f3a4f74565
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365434"
---
# <a name="setting-the-day-state-of-a-month-calendar-control"></a>設定月曆控制項的日期狀態

月曆控制項的其中一個屬性是針對該月份的每一天儲存資訊的能力，稱為控制項的日期狀態。 這項資訊可用來強調目前顯示的月份中某些特別的日期。

> [!NOTE]
> 對`CMonthCalCtrl`象 必須具有MCS_DAYSTATE樣式才能顯示日狀態資訊。

紀錄顯示為 32 位元資料類型 **,MONTHDAYSTATE**。 **MONTHDAYSTATE**位欄位中的每個位(1 到 31)表示一個月內一天的狀態。 如果位元是開啟的，則對應的日期會以粗體顯示；否則就不會強調其顯示。

有兩種方法可以設置月份日曆控件的日狀態:顯式調用[CMonthCalCtrl::setDayState](../mfc/reference/cmonthcalctrl-class.md#setdaystate)或通過處理MCN_GETDAYSTATE通知消息。

## <a name="handling-the-mcn_getdaystate-notification-message"></a>處理 MCN_GETDAYSTATE 通知訊息

MCN_GETDAYSTATE 資訊是由控制項傳送，以判斷顯示月份中的日期應該如何顯示。

> [!NOTE]
> 因為控制項會快取之前和之後的月份 (相對於可見的月份)，所以您會在選擇新的月份時接收到這個通知。

要正確處理此消息,您必須確定要為其請求多少天狀態資訊,使用正確的值初始化**MONTHSDAYSTATE**結構陣列,以及使用新資訊初始化相關結構成員。 以下過程詳細說明了必要的步驟,假定您有一`CMonthCalCtrl`個稱為*m_monthcal*的物件和一個**monthDAYSTATE**物件陣*列 mdState*。

#### <a name="to-handle-the-mcn_getdaystate-notification-message"></a>處理 MCN_GETDAYSTATE 通知訊息

1. 使用[類嚮導](reference/mfc-class-wizard.md),將MCN_GETDAYSTATE消息的通知處理程式添加到*m_monthcal*物件(請參閱[將消息映射到函數](../mfc/reference/mapping-messages-to-functions.md))。

1. 在處理常式的主體中，加入下列程式碼：

   [!code-cpp[NVC_MFCControlLadenDialog#26](../mfc/codesnippet/cpp/setting-the-day-state-of-a-month-calendar-control_1.cpp)]

   該範例將*pNMHDR*指標轉換為正確的類型,然後確定請求的資訊月數`pDayState->cDayState`( 。 對於每個月份，目前的位元欄位 (`pDayState->prgDayState[i]`) 會初始化為零，同時會設定需要的日期 (在這個情況中為每個月的第 15 天)。

## <a name="see-also"></a>另請參閱

[使用 CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
