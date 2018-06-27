---
title: 設定月份日期狀態月曆控制項 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- MCN_GETDAYSTATE
dev_langs:
- C++
helpviewer_keywords:
- CMonthCalCtrl class [MFC], setting day state info
- MCN_GETDAYSTATE notification [MFC]
- month calendar controls [MFC], day state info
ms.assetid: 435d1b11-ec0e-4121-9e25-aaa6af812a3c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6d4254448e3f8f5a23acd9a303788fd13afb2f84
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2018
ms.locfileid: "36950791"
---
# <a name="setting-the-day-state-of-a-month-calendar-control"></a>設定月曆控制項的日期狀態
月曆控制項的其中一個屬性是針對該月份的每一天儲存資訊的能力，稱為控制項的日期狀態。 這項資訊可用來強調目前顯示的月份中某些特別的日期。  
  
> [!NOTE]
>  `CMonthCalCtrl`物件必須具有 MCS_DAYSTATE 樣式來顯示日期狀態資訊。  
  
 日期狀態資訊以 32 位元資料類型，表示**MONTHDAYSTATE**。 中的每個位元**MONTHDAYSTATE**位元欄位 (1 到 31) 表示一個月中每天的狀態。 如果位元是開啟的，則對應的日期會以粗體顯示；否則就不會強調其顯示。  
  
 有兩種方法來設定月曆控制項的日期狀態： 明確地透過呼叫[cmonthcalctrl:: Setdaystate](../mfc/reference/cmonthcalctrl-class.md#setdaystate)或藉由處理 MCN_GETDAYSTATE 通知訊息。  
  
## <a name="handling-the-mcngetdaystate-notification-message"></a>處理 MCN_GETDAYSTATE 通知訊息  
 MCN_GETDAYSTATE 訊息是由控制項傳送，以判斷顯示月份的日期應如何顯示。  
  
> [!NOTE]
>  因為控制項會快取之前和之後的月份 (相對於可見的月份)，所以您會在選擇新的月份時接收到這個通知。  
  
 為了適當處理此訊息，您必須決定多少月份日期狀態資訊已針對要求，會初始化陣列**MONTHDAYSTATE**具有適當的值，初始化相關的結構成員的結構以新的資訊。 下列程序，並詳細說明必要的步驟，假設您有`CMonthCalCtrl`呼叫物件*m_monthcal*和陣列**MONTHDAYSTATE**物件*mdState*.  
  
#### <a name="to-handle-the-mcngetdaystate-notification-message"></a>處理 MCN_GETDAYSTATE 通知訊息  
  
1.  使用 [屬性] 視窗中，加入 MCN_GETDAYSTATE 訊息的通知處理常式*m_monthcal*物件 (請參閱[訊息對應到函式](../mfc/reference/mapping-messages-to-functions.md))。  
  
2.  在處理常式的主體中，加入下列程式碼：  
  
     [!code-cpp[NVC_MFCControlLadenDialog#26](../mfc/codesnippet/cpp/setting-the-day-state-of-a-month-calendar-control_1.cpp)]  
  
     範例會將轉換*pNMHDR*指向適當的類型，然後判斷所要求的幾個月的資訊 (`pDayState->cDayState`)。 對於每個月份，目前的位元欄位 (`pDayState->prgDayState[i]`) 會初始化為零，同時會設定需要的日期 (在這個情況中為每個月的第 15 天)。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)   
 [控制項](../mfc/controls-mfc.md)

