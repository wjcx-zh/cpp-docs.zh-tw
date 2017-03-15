---
title: "在日期時間選擇器控制項中使用回呼欄位 | Microsoft Docs"
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
  - "DTN_FORMATQUERY"
  - "DTN_FORMAT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDateTimeCtrl 類別中的回呼欄位"
  - "CDateTimeCtrl 類別, 回呼欄位"
  - "CDateTimeCtrl 類別, 處理 DTN_FORMAT 和 DTN_FORMATQ"
  - "DateTimePicker 控制項 [MFC]"
  - "DateTimePicker 控制項 [MFC], 回呼欄位"
  - "DTN_FORMAT 告知"
  - "DTN_FORMATQUERY 告知"
ms.assetid: 404f4ba9-cba7-4718-9faa-bc6b274a723f
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 在日期時間選擇器控制項中使用回呼欄位
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

除了定義日期和時間選擇器欄位的標準格式字元以外，您也可以指定自訂字串的某些部分以自訂輸出，做為回呼欄位。  若要宣告回呼欄位，請在格式字串的主體的任何位置包含一個或多個「X」字元 \(ASCII 碼 88\)。  例如，下列字串「'Today is: 'yy'\/'MM'\/'dd' \(Day 'X'\)'」讓日期和時間選擇控制項以年、月、日期、年的天數顯示目前的值。  
  
> [!NOTE]
>  回呼欄位的 X 數值不會對應至要顯示的字元數值。  
  
 您可以重複「X」字元，以區別自訂字串的多個回呼欄位。  因此，格式字串「XXddddMMMdd', 'yyyXXX」包含兩個唯一的回呼欄位， 「XX」和「XXX」。  
  
> [!NOTE]
>  回呼欄位視為有效欄位，因此您的應用程式必須準備處理 **DTN\_WMKEYDOWN**  通知訊息。  
  
 實作日期和時間選擇器控制項的回呼欄位，包含三個部分：  
  
-   初始化自訂格式字串  
  
-   處理 **DTN\_FORMATQUERY** 通知  
  
-   處理 **DTN\_FORMAT** 通知  
  
## 初始化自訂格式字串  
 呼叫 `CDateTimeCtrl::SetFormat` 初始化自訂字串。  如需詳細資訊，請參閱 [在日期和時間選擇器控制項使用自訂格式字串](../mfc/using-custom-format-strings-in-a-date-and-time-picker-control.md)。  設定自訂格式字串的位置通常是在包含對話方塊類別的 `OnInitDialog` 函式，或是包含檢視類別的 `OnInitialUpdate` 函式。  
  
## 處理 DTN\_FORMATQUERY 通知  
 當控制項剖析格式字串並遇到回呼欄位時，應用程式會傳送 **DTN\_FORMAT** 和 **DTN\_FORMATQUERY** 通知訊息。  回呼欄位字串包含通知，讓您可判斷哪一個回呼欄位正在進行查詢。  
  
 會傳送 **DTN\_FORMATQUERY** 通知以擷取目前回呼欄位中顯示字串之像素的最大容許大小。  
  
 若要適當地計算這個值，您必須使用控制項顯示字型，計算要被替代給欄位的字串之高度和寬度。  字串的實際計算可以呼叫 [GetTextExtentPoint32](http://msdn.microsoft.com/library/windows/desktop/dd144938) Win32 函式輕鬆達成。  一旦大小決定後，請將值傳遞至應用程式並結束處理函式。  
  
 下列範例是提供回呼字串的大小的一個方法：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#8](../mfc/codesnippet/CPP/using-callback-fields-in-a-date-and-time-picker-control_1.cpp)]  
  
 一旦目前回呼欄位的大小被計算後，您必須為欄位提供值。  這會在 **DTN\_FORMAT**  通知的處理常式進行。  
  
## 處理 DTN\_FORMAT 通知  
 應用程式使用 **DTN\_FORMAT** 通知來要求會被取代的字串。  下列範例示範可能的一個方法：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#9](../mfc/codesnippet/CPP/using-callback-fields-in-a-date-and-time-picker-control_2.cpp)]  
  
> [!NOTE]
>  轉換通知處理常式的第一個參數至適當的型別，可以找到對 **NMDATETIMEFORMAT**  結構的指標。  
  
## 請參閱  
 [使用 CDateTimeCtrl](../mfc/using-cdatetimectrl.md)   
 [控制項](../mfc/controls-mfc.md)