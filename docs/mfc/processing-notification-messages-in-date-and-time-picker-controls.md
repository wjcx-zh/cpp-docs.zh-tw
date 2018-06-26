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
ms.openlocfilehash: 630792eb4bdd89cbe8081894c4ee026437568f3b
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930760"
---
# <a name="processing-notification-messages-in-date-and-time-picker-controls"></a>處理日期時間選擇器控制項中的通知訊息
當使用者互動有日期和時間選擇器控制項，控制項 (`CDateTimeCtrl`) 會傳送通知訊息至其父視窗，通常是檢視或對話方塊物件。 如果您想要執行動作以作為回應，請處理這些訊息。 例如，當使用者開啟以顯示內嵌的月曆控制項的日期和時間選擇器時，會傳送 DTN_DROPDOWN 告知。  
  
 使用 [屬性] 視窗，將通知處理常式加入您想要實作之這些訊息的父類別。  
  
 下列清單描述的日期和時間選擇器控制項所傳送的告知。  
  
-   DTN_DROPDOWN 告知內嵌月曆控制項的父項是即將顯示。 DTS_UPDOWN 樣式未設定時，才會傳送這個通知。 如需有關這項通知的詳細資訊，請參閱[存取內嵌月曆控制項](../mfc/accessing-the-embedded-month-calendar-control.md)。  
  
-   DTN_CLOSEUP 告知內嵌月曆控制項的父項是即將關閉。 DTS_UPDOWN 樣式未設定時，才會傳送這個通知。  
  
-   DTN_DATETIMECHANGE 告知父代已經在控制項中發生變更。  
  
-   DTN_FORMAT 通知文字的父代所需的回呼欄位中顯示。 如需有關這個通知和回呼欄位的詳細資訊，請參閱[日期和時間選擇器控制項中使用回呼欄位](../mfc/using-callback-fields-in-a-date-and-time-picker-control.md)。  
  
-   DTN_FORMATQUERY 要求提供之字串將會顯示在回呼欄位的允許大小上限的父系。 處理此通知會讓控制項適當地顯示在任何時間，減少重繪閃動內控制項的顯示的輸出。 如需有關這項通知的詳細資訊，請參閱[日期和時間選擇器控制項中使用回呼欄位](../mfc/using-callback-fields-in-a-date-and-time-picker-control.md)。  
  
-   DTN_USERSTRING 告知父使用者已完成編輯日期和時間選擇器控制項的內容。 未設定 DTS_APPCANPARSE 樣式時，才會傳送這個通知。  
  
-   當使用者輸入的回呼欄位中，DTN_WMKEYDOWN 通知父代。 處理這個通知可模擬支援日期和時間選擇器控制項中的非回呼欄位相同的鍵盤回應。 如需有關這項通知的詳細資訊，請參閱[DTP 控制項中支援回呼欄位](http://msdn.microsoft.com/library/windows/desktop/bb761726)Windows SDK 中。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CDateTimeCtrl](../mfc/using-cdatetimectrl.md)   
 [控制項](../mfc/controls-mfc.md)

