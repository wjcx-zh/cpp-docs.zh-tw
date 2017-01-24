---
title: "設定月曆控制項的日期狀態 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MCN_GETDAYSTATE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMonthCalCtrl 類別, 設定日期狀態資訊"
  - "MCN_GETDAYSTATE 告知"
  - "月曆控制項, 日期狀態資訊"
ms.assetid: 435d1b11-ec0e-4121-9e25-aaa6af812a3c
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 設定月曆控制項的日期狀態
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

月曆控制項的其中一個屬性是能夠儲存資訊，參考至該月份每天控制項狀態的日期。  這個資訊可用來強調目前顯示的月份中某些特別的日期。  
  
> [!NOTE]
>  `CMonthCalCtrl` 物件必須有 **MCS\_DAYSTATE** 樣式，以顯示日期狀態資訊。  
  
 日期狀態資訊是 32 位元資料型別， **MONTHDAYSTATE**。  **MONTHDAYSTATE** 位元欄位 \(從 1 到 31\) 的每個位元表示一個月裡一天的狀態。  如果位元是開啟的，則對應的日期會以粗體顯示；否則其顯示不會有任何強調。  
  
 有兩種方法可以設定月曆控制項上的日期狀態：明確呼叫 [CMonthCalCtrl::SetDayState](../Topic/CMonthCalCtrl::SetDayState.md) 或處理 **MCN\_GETDAYSTATE** 通知訊息。  
  
## 處理 MCN\_GETDAYSTATE 通知訊息  
 **MCN\_GETDAYSTATE** 資訊由控制項傳送，以判斷顯示月份中的日期應該如何顯示。  
  
> [!NOTE]
>  因為控制項會快取之前和之後的月份，如需可見的月份，您會在新的月份被選取時接收這個告知。  
  
 若要適當地處理這個訊息，您必須判斷多少個月份日狀態資訊正在被要求，初始化一個具有適當值的 **MONTHDAYSTATE** 結構之陣列，並以新的資訊初始化相關的結構成員。  下列程序列出詳細的必要步驟，假設您有一個名為 `m_monthcal` 的 `CMonthCalCtrl` 物件，和一個 **MONTHDAYSTATE** 物件的陣列 `mdState`。  
  
#### 若要處理 MCN\_GETDAYSTATE 通知訊息  
  
1.  使用屬性視窗，將 **MCN\_GETDAYSTATE** 訊息的通知處理常式加入至 `m_monthcal` 物件 \(請參閱 [對應訊息至函式](../mfc/reference/mapping-messages-to-functions.md)\)。  
  
2.  在處理常式的的主體，加入下列程式碼：  
  
     [!code-cpp[NVC_MFCControlLadenDialog#26](../mfc/codesnippet/CPP/setting-the-day-state-of-a-month-calendar-control_1.cpp)]  
  
     這個範例會將 `pNMHDR` 指標轉換為適當的型別，然後判斷多少月份的資訊正在被要求 \(`pDayState->cDayState`\)。  對於每個月份，目前的位元欄位 \(`pDayState->prgDayState[i]`\) 初始化為零，而需要的日期已設定 \(在這個情況中為，每個月的第 15 天\)。  
  
## 請參閱  
 [使用 CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)   
 [控制項](../mfc/controls-mfc.md)