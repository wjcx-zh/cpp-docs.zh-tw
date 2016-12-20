---
title: "存取內嵌月曆控制項 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDateTimeCtrl 類別, 存取內嵌控制項"
  - "CMonthCalCtrl 類別, 變更字型"
  - "DateTimePicker 控制項 [MFC]"
  - "DateTimePicker 控制項 [MFC], 存取月曆"
  - "月曆控制項, 變更字型"
  - "月曆控制項, 內嵌於日期/時間選擇器中"
ms.assetid: 355e97ed-cf81-4df3-a2f8-9ddbbde93227
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 存取內嵌月曆控制項
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

內嵌月曆控制項物件可以呼叫 [GetMonthCalCtrl](../Topic/CDateTimeCtrl::GetMonthCalCtrl.md) 成員函式，從 `CDateTimeCtrl` 物件存取。  
  
> [!NOTE]
>  內嵌月曆控制項，只有在日期和時間選擇器控制項尚未有 **DTS\_UPDOWN**  模式時使用。  
  
 如果您要在內嵌控制項顯示之前修改某些屬性，這會很有用。  若要完成這項作業，請處理 **DTN\_DROPDOWN** 通知，擷取月曆控制項 \(使用 [CDateTimeCtrl::GetMonthCalCtrl](../Topic/CDateTimeCtrl::GetMonthCalCtrl.md)\)，並進行修改。  可惜的是，月曆控制項不是永久性的。  
  
 換句話說，當使用者要求顯示月曆控制項時，會建立新的月曆控制項 \(在 **DTN\_DROPDOWN** 告知之前\)。  當使用者關閉後控制項會被終結 \(在 **DTN\_CLOSEUP** 告知後\)。  這表示在內嵌控制項顯示之前，您修改的任何屬性會在當內嵌控制項關閉時遺失。  
  
 使用 **DTN\_DROPDOWN** 通知的處理常式，下列範例示範這個程序。  程式碼以呼叫 [SetMonthCalColor](../Topic/CDateTimeCtrl::SetMonthCalColor.md)，變更月曆控制項的背景色彩為灰色。  程式碼如下：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#5](../mfc/codesnippet/CPP/accessing-the-embedded-month-calendar-control_1.cpp)]  
  
 如前面所述，當內嵌控制項關閉時，會遺失對月曆控制項屬性所做的任何修改，但有兩個例外狀況。  第一個例外狀況，這個月曆控制項的顏色，已經討論過。  第二個例外狀況，是月曆控制項所使用的字型。  您可以藉由呼叫 [CDateTimeCtrl::SetMonthCalFont](../Topic/CDateTimeCtrl::SetMonthCalFont.md)，修改預設字型，傳遞現有字型的控制代碼。  下列範例 \(其中 `m_dtPicker` 是日期和時間的物件\) 示範了可能的方法：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#6](../mfc/codesnippet/CPP/accessing-the-embedded-month-calendar-control_2.cpp)]  
  
 一旦呼叫 `CDateTimeCtrl::SetMonthCalFont` 變更字型後，下次月曆會顯示已儲存並使用的新字型。  
  
## 請參閱  
 [使用 CDateTimeCtrl](../mfc/using-cdatetimectrl.md)   
 [控制項](../mfc/controls-mfc.md)