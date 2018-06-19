---
title: 月曆控制項在月份中的處理通知訊息 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CMonthCalCtrl class [MFC], notifications
- CMonthCalCtrl class [MFC], day states
- month calendar controls [MFC], notification messages
- notifications [MFC], for CMonthCalCtrl
- notifications [MFC], month calendar control
ms.assetid: 607c3e90-0756-493b-9503-ce835a50c7ab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 26b4d73284b0cff362ba16248e0906b76c7f52a1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33346909"
---
# <a name="processing-notification-messages-in-month-calendar-controls"></a>處理月曆控制項中的通知訊息
當使用者月曆控制項 （選取日期和/或檢視不同的月份），與控制項互動 (`CMonthCalCtrl`) 會傳送通知訊息至其父視窗，通常是檢視或對話方塊物件。 如果您想要執行動作以作為回應，請處理這些訊息。 比方說，當使用者選取新的月份，若要檢視，您可以提供一組應該反白的日期。  
  
 使用 [屬性] 視窗，將通知處理常式加入您想要實作之這些訊息的父類別。  
  
 下表描述月曆控制項所傳送的各種通知。  
  
-   **MCN_GETDAYSTATE**要求資訊應該以粗體顯示的天數。 在處理此通知的資訊，請參閱[設定月曆控制項的日期狀態](../mfc/setting-the-day-state-of-a-month-calendar-control.md)。  
  
-   **MCN_SELCHANGE**時告知父選取的日期的範圍已變更。  
  
-   **MCN_SELECT**通知已明確選取日期的父系。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)   
 [控制項](../mfc/controls-mfc.md)

