---
title: "在日期時間選擇器控制項中使用自訂格式字串 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDateTimeCtrl 類別, 顯示樣式"
  - "DateTimePicker 控制項 [MFC]"
  - "DateTimePicker 控制項 [MFC], 顯示樣式"
ms.assetid: 7d577f03-6ca0-4597-9093-50b78f304719
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 在日期時間選擇器控制項中使用自訂格式字串
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

根據預設，日期時間選擇器控制項用來顯示目前日期提供三個格式類型 \(與唯一樣式對應的每個格式\) 或逾時:  
  
-   **DTS\_LONGDATEFORMAT** 顯示長格式的日期，會產生如「 2000 年 1 月 3 日 星期三」的輸出。  
  
-   **DTS\_SHORTDATEFORMAT** 顯示簡短日期，會產生與「1\/3\/00 」的輸出。  
  
-   **DTS\_TIMEFORMAT** 顯示長格式的時間，產生像「5:31: 42 PM」的輸出。  
  
 不過，您可以使用自訂格式字串，您可以自訂日期或時間的外觀。  這個自訂字串組合現有的格式字元，內部格式字元或兩者的混合。  一旦自訂字串已建置，請呼叫將您的自訂字串的 [CDateTimeCtrl::SetFormat](../Topic/CDateTimeCtrl::SetFormat.md) 。  使用您的自訂格式字串，日期時間選擇器控制項會顯示目前的值。  
  
 下列範例程式碼 \(其中 `m_dtPicker` 是 `CDateTimeCtrl` 物件\) 會示範一個可行的解決方法:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#7](../mfc/codesnippet/CPP/using-custom-format-strings-in-a-date-and-time-picker-control_1.cpp)]  
  
 除了自訂格式字串之外，日期時間選擇器控制項也支援 [回呼欄位](../mfc/using-callback-fields-in-a-date-and-time-picker-control.md)。  
  
## 請參閱  
 [使用 CDateTimeCtrl](../mfc/using-cdatetimectrl.md)   
 [控制項](../mfc/controls-mfc.md)