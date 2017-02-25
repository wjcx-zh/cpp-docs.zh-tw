---
title: "處理月曆控制項中的通知訊息 | Microsoft Docs"
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
  - "CMonthCalCtrl 類別, 日期狀態"
  - "CMonthCalCtrl 類別, 告知"
  - "月曆控制項, 通知訊息"
  - "告知, CMonthCalCtrl 的"
  - "告知, 月曆控制項"
ms.assetid: 607c3e90-0756-493b-9503-ce835a50c7ab
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 處理月曆控制項中的通知訊息
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當使用者與月曆控制項互動 \(選取日期和\/或檢視不同的月份\)，控制項 \(`CMonthCalCtrl`\) 傳送通知訊息至其父視窗，通常為檢視或對話物件。  如果您想要執行某個動作以回應，請處理這些訊息。  例如，當使用者選取新的月份檢視時，您可以提供一組應該被強調的日期。  
  
 使用屬性視窗加入通知處理常式到您要實作的訊息的父類別。  
  
 下列清單說明月曆控制項傳送的各種通知。  
  
-   **MCN\_GETDAYSTATE** 要求應顯示的天數資訊為粗體。  如需處理這個通知的詳細資訊，請參閱 [設定月份行事曆控制項的狀態](../mfc/setting-the-day-state-of-a-month-calendar-control.md)。  
  
-   **MCN\_SELCHANGE** 通知父日期選取的日期或日期範圍發生變更。  
  
-   **MCN\_SELECT** 通知父已明確選取日期。  
  
## 請參閱  
 [使用 CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)   
 [控制項](../mfc/controls-mfc.md)