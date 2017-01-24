---
title: "建立日期時間選擇器控制項 | Microsoft Docs"
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
  - "CDateTimeCtrl 類別, 建立"
  - "DateTimePicker 控制項 [MFC], 建立"
ms.assetid: 764ec2fb-98cd-478b-a5f2-d63f0bb12279
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 建立日期時間選擇器控制項
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

日期時間選擇器控制項的建立方式取決於您是否在對話方塊中使用控制項或將它建立在 nondialog 視窗。  
  
### 直接在對話方塊使用 CDateTimeCtrl  
  
1.  在對話方塊編輯器，將日期時間選擇器控制項加入至對話方塊樣板資源。  指定它的控制項 ID.  
  
2.  需要的所有樣式以指定使用日期時間選擇器控制項的屬性對話方塊。  
  
3.  使用 [加入成員變數精靈](../ide/adding-a-member-variable-visual-cpp.md) 將型別 [CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md) 的成員變數加入至控制項屬性。  您可以使用這個成員呼叫 `CDateTimeCtrl` 成員函式。  
  
4.  使用屬性視窗對應至對話方塊類別中處理函式需要處理的所有清單控制項[告知訊息](../mfc/processing-notification-messages-in-date-and-time-picker-controls.md) \(請參閱 [對應訊息至函式](../mfc/reference/mapping-messages-to-functions.md)\)。  
  
5.  在 [OnInitDialog](../Topic/CDialog::OnInitDialog.md)中，加入額外的樣式至 `CDateTimeCtrl` 物件。  
  
### 在 nondialog 視窗使用 CDateTimeCtrl  
  
1.  在檢視或視窗類別聲明控制項。  
  
2.  呼叫控制項的 [建立](../Topic/CTabCtrl::Create.md) 成員函式 \(可能在 [OnInitialUpdate](../Topic/CView::OnInitialUpdate.md) 中\)，並且盡可能的與父視窗的 [OnCreate](../Topic/CWnd::OnCreate.md) 處理常式函式一樣早 \(如果您是繼承控制項\) 。  設定控制項的樣式。  
  
## 請參閱  
 [使用 CDateTimeCtrl](../mfc/using-cdatetimectrl.md)   
 [控制項](../mfc/controls-mfc.md)