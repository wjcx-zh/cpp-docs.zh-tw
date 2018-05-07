---
title: 處理控制項通知訊息的日期和時間選擇器 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- DTN_CLOSEUP
- DTN_DATETIMECHANGE
- DTN_DROPDOWN
dev_langs:
- C++
helpviewer_keywords:
- DTN_DROPDOWN notification [MFC]
- DTN_DATETIMECHANGE notification [MFC]
- DTN_CLOSEUP notification [MFC]
- DateTimePicker control [MFC], handling notifications
- CDateTimeCtrl class [MFC], handling notifications
- DTN_FORMAT notification [MFC]
- DateTimePicker control [MFC]
ms.assetid: ffbe29ab-ff80-4609-89f7-260b404439c4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 53c45f664dec2a553210187514b28f1ba3c2ed9b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="processing-notification-messages-in-date-and-time-picker-controls"></a>處理日期時間選擇器控制項中的通知訊息
當使用者互動有日期和時間選擇器控制項，控制項 (`CDateTimeCtrl`) 會傳送通知訊息至其父視窗，通常是檢視或對話方塊物件。 如果您想要執行動作以作為回應，請處理這些訊息。 例如，當使用者開啟以顯示內嵌的月曆控制項，日期和時間選擇器**DTN_DROPDOWN**會傳送通知。  
  
 使用 [屬性] 視窗，將通知處理常式加入您想要實作之這些訊息的父類別。  
  
 下列清單描述的日期和時間選擇器控制項所傳送的告知。  
  
-   **DTN_DROPDOWN**告知父代內嵌的月曆控制項即將顯示。 此通知只會傳送時**DTS_UPDOWN**樣式未設定。 如需有關這項通知的詳細資訊，請參閱[存取內嵌月曆控制項](../mfc/accessing-the-embedded-month-calendar-control.md)。  
  
-   **DTN_CLOSEUP**告知父代內嵌的月曆控制項即將關閉。 此通知只會傳送時**DTS_UPDOWN**樣式未設定。  
  
-   **DTN_DATETIMECHANGE**通知已經在控制項中發生變更的父系。  
  
-   **DTN_FORMAT**時告知父文字所顯示的回呼欄位中。 如需有關這個通知和回呼欄位的詳細資訊，請參閱[日期和時間選擇器控制項中使用回呼欄位](../mfc/using-callback-fields-in-a-date-and-time-picker-control.md)。  
  
-   **DTN_FORMATQUERY**要求提供之字串將會顯示在回呼欄位的允許大小上限的父系。 處理此通知會讓控制項適當地顯示在任何時間，減少重繪閃動內控制項的顯示的輸出。 如需有關這項通知的詳細資訊，請參閱[日期和時間選擇器控制項中使用回呼欄位](../mfc/using-callback-fields-in-a-date-and-time-picker-control.md)。  
  
-   **DTN_USERSTRING**時告知父使用者已完成編輯日期和時間選擇器控制項的內容。 此通知只會傳送時**DTS_APPCANPARSE**已設定樣式。  
  
-   **DTN_WMKEYDOWN**時使用者會在回呼欄位輸入通知父代。 處理這個通知可模擬支援日期和時間選擇器控制項中的非回呼欄位相同的鍵盤回應。 如需有關這項通知的詳細資訊，請參閱[DTP 控制項中支援回呼欄位](http://msdn.microsoft.com/library/windows/desktop/bb761726)Windows SDK 中。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CDateTimeCtrl](../mfc/using-cdatetimectrl.md)   
 [控制項](../mfc/controls-mfc.md)

