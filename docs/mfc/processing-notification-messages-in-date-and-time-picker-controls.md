---
title: "處理日期時間選擇器控制項中的通知訊息 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DTN_CLOSEUP"
  - "DTN_DATETIMECHANGE"
  - "DTN_DROPDOWN"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDateTimeCtrl 類別, 處理告知"
  - "DateTimePicker 控制項 [MFC]"
  - "DateTimePicker 控制項 [MFC], 處理告知"
  - "DTN_CLOSEUP 告知"
  - "DTN_DATETIMECHANGE 告知"
  - "DTN_DROPDOWN 告知"
  - "DTN_FORMAT 告知"
ms.assetid: ffbe29ab-ff80-4609-89f7-260b404439c4
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 處理日期時間選擇器控制項中的通知訊息
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當使用者使用日期時間選擇器控制項互動，控制項 \(`CDateTimeCtrl`\) 傳送通知訊息至其父視窗，通常檢視或對話物件。  如果您想要執行某個動作以回應，請處理這些訊息。  例如，在中，當使用者開啟日期時間選擇器顯示內嵌月曆控制項時， **DTN\_DROPDOWN** 通知傳送。  
  
 使用屬性視窗將告知處理常式到您要實作的訊息的父類別。  
  
 下列清單描述日期時間選擇器控制項傳送的各種告知。  
  
-   **DTN\_DROPDOWN** 告知父嵌入月曆控制項中顯示。  當 **DTS\_UPDOWN** 樣式未設定時，這個告知只傳送。  如需這個告知的詳細資訊，請參閱 [存取內嵌月份行事曆控制項](../mfc/accessing-the-embedded-month-calendar-control.md)。  
  
-   **DTN\_CLOSEUP** 告知父嵌入月曆控制項將會關閉。  當 **DTS\_UPDOWN** 樣式未設定時，這個告知只傳送。  
  
-   **DTN\_DATETIMECHANGE** 告知父代變更在控制項中發生。  
  
-   **DTN\_FORMAT** 告知父文字需要在回呼欄位中顯示。  如需這個告知和回呼欄位的詳細資訊，請參閱 [使用日期時間選擇器控制項的回呼欄位](../mfc/using-callback-fields-in-a-date-and-time-picker-control.md)。  
  
-   **DTN\_FORMATQUERY** 要求父提供在回呼欄位中顯示字串的最大容許大小。  處理這個告知允許控制項一直正確顯示輸出，以減少控制項的顯示中的重繪。  如需這個告知的詳細資訊，請參閱 [使用日期時間選擇器控制項的回呼欄位](../mfc/using-callback-fields-in-a-date-and-time-picker-control.md)。  
  
-   **DTN\_USERSTRING** 告知父使用者完成編輯日期時間選擇器控制項的內容。  當 **DTS\_APPCANPARSE** 樣式設定時，這個告知只傳送。  
  
-   當使用者輸入回呼欄位時，**DTN\_WMKEYDOWN** 告知父代。  處理這個告知模擬為日期時間選擇器控制項的非回呼欄位支援的同一個鍵盤回應。  如需這個告知的詳細資訊，請參閱 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]的 [支援 DTP 控制項的回呼欄位](http://msdn.microsoft.com/library/windows/desktop/bb761726) 。  
  
## 請參閱  
 [使用 CDateTimeCtrl](../mfc/using-cdatetimectrl.md)   
 [控制項](../mfc/controls-mfc.md)