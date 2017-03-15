---
title: "Default Control Events | Microsoft Docs"
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
  - "Dialog editor, default control events"
  - "controls [C++], default control events"
  - "events [C++], controls"
  - "dialog box controls, events"
ms.assetid: 75556b23-18f5-4390-97a4-2ecad3309741
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Default Control Events
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下列控制項名稱具有預設事件：  
  
|控制項名稱|預設事件|  
|-----------|----------|  
|Animate|**ACN\_START**|  
|Check box|**BN\_CLICKED**|  
|Combo box|**CBN\_SELCHANGE**|  
|Custom|**TTN\_GETDISPINFO**|  
|Date time picker|**DTN\_DATETIMECHANGE**|  
|Edit box|**EN\_CHANGE**|  
|Group Box|\(不適用\)|  
|Hot key|**NM\_OUTOFMEMORY**|  
|IP 位址|**IPN\_FIELDCHANGED**|  
|List|**LVN\_ITEMCHANGE**|  
|List box|**LBN\_SELCHANGE**|  
|Month calendar|**MCN\_SELCHANGE**|  
|Picture Control|\(不適用\)|  
|Progress|**NM\_CUSTOMDRAW**|  
|Push button|**BN\_CLICKED**|  
|Radio button|**BN\_CLICKED**|  
|Rich Edit|**EN\_CHANGE**|  
|Scroll bar|**NM\_THEMECHANGED**|  
|Slider|**NM\_CUSTOMDRAW**|  
|Spin|**UDN\_DELTAPOS**|  
|Static Text|\(不適用\)|  
|Tab|**TCN\_SELCHANGE**|  
|Tree|**TVN\_SELCHANGE**|  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
## 需求  
 Win32  
  
## 請參閱  
 [Defining Member Variables for Dialog Controls](../mfc/defining-member-variables-for-dialog-controls.md)   
 [與使用者介面物件關聯的訊息類型](../mfc/reference/message-types-associated-with-user-interface-objects.md)   
 [編輯訊息處理常式](../mfc/reference/editing-a-message-handler.md)   
 [定義反映訊息的訊息處理常式](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md)   
 [根據新控制項類別來宣告變數](../mfc/reference/declaring-a-variable-based-on-your-new-control-class.md)   
 [覆寫 Virtual 函式](../ide/overriding-a-virtual-function-visual-cpp.md)