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
ms.openlocfilehash: b8a91c8b0c3bdef9256628b9226c5f3ff154ed7d
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907531"
---
# <a name="setting-the-day-state-of-a-month-calendar-control"></a>設定月曆控制項的日期狀態

月曆控制項的其中一個屬性是針對該月份的每一天儲存資訊的能力，稱為控制項的日期狀態。 這項資訊可用來強調目前顯示的月份中某些特別的日期。

> [!NOTE]
>  `CMonthCalCtrl`物件必須具有 MCS_DAYSTATE 樣式，才能顯示日期狀態資訊。

日期狀態資訊會以32位資料類型（ **MONTHDAYSTATE**）表示。 **MONTHDAYSTATE**位欄位中的每個位（1到31）代表一個月中某一天的狀態。 如果位元是開啟的，則對應的日期會以粗體顯示；否則就不會強調其顯示。

有兩種方法可設定月曆控制項的日期狀態：明確地呼叫[CMonthCalCtrl：： SetDayState](../mfc/reference/cmonthcalctrl-class.md#setdaystate) ，或藉由處理 MCN_GETDAYSTATE 通知訊息。

## <a name="handling-the-mcn_getdaystate-notification-message"></a>處理 MCN_GETDAYSTATE 通知訊息

MCN_GETDAYSTATE 訊息會由控制項傳送，以決定應該如何顯示可見月份中的天數。

> [!NOTE]
>  因為控制項會快取之前和之後的月份 (相對於可見的月份)，所以您會在選擇新的月份時接收到這個通知。

若要適當地處理此訊息，您必須判斷要求的月份日期狀態資訊有多少、使用適當的值初始化**MONTHDAYSTATE**結構的陣列，以及使用新的來初始化相關的結構成員。更多資訊. 下列程式詳述必要的步驟，假設您有`CMonthCalCtrl`一個稱為*m_monthcal*的物件，以及一個**MONTHDAYSTATE**物件*mdState*的陣列。

#### <a name="to-handle-the-mcn_getdaystate-notification-message"></a>處理 MCN_GETDAYSTATE 通知訊息

1. 使用[類別 Wizard](reference/mfc-class-wizard.md)，將 MCN_GETDAYSTATE 訊息的通知處理常式新增至*m_monthcal*物件（請參閱將[訊息對應至](../mfc/reference/mapping-messages-to-functions.md)函式）。

1. 在處理常式的主體中，加入下列程式碼：

   [!code-cpp[NVC_MFCControlLadenDialog#26](../mfc/codesnippet/cpp/setting-the-day-state-of-a-month-calendar-control_1.cpp)]

   這個範例會將*pNMHDR*指標轉換成適當的類型，然後決定要要求多少月的資訊（`pDayState->cDayState`）。 對於每個月份，目前的位元欄位 (`pDayState->prgDayState[i]`) 會初始化為零，同時會設定需要的日期 (在這個情況中為每個月的第 15 天)。

## <a name="see-also"></a>另請參閱

[使用 CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
