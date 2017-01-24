---
title: "建立月曆控制項 | Microsoft Docs"
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
  - "CMonthCalCtrl 類別, 建立"
  - "月曆控制項"
  - "月曆控制項, 建立"
ms.assetid: 185cc642-85e9-4365-8a4c-d90b75b010f7
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 建立月曆控制項
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

月曆控制項的建立方式，取決於您是在對話方塊中使用控制項或在 nondialog 視窗建立它。  
  
### 直接在對話方塊使用 CMonthCalCtrl  
  
1.  在對話方塊編輯器，將月曆控制項加入至對話方塊樣板資源。  指定它的控制項 ID.  
  
2.  指定使用月曆控制項的屬性對話方塊，需要的所有樣式。  
  
3.  使用 [加入成員變數精靈](../ide/adding-a-member-variable-visual-cpp.md) 將型別 [CMonthTimeCtrl](../mfc/reference/cmonthcalctrl-class.md) 的成員變數加入至控制項屬性。  您可以使用這個成員呼叫 `CMonthCalCtrl` 成員函式。  
  
4.  使用屬性視窗對應至對話方塊類別中處理函式需要處理的所有月曆控制項告知訊息 \(請參閱 [對應訊息至函式](../mfc/reference/mapping-messages-to-functions.md)\)。  
  
5.  在 [OnInitDialog](../Topic/CDialog::OnInitDialog.md)中，加入額外的樣式至 `CMonthCalCtrl` 物件。  
  
### 在 nondialog 視窗使用 CMonthCalCtrl  
  
1.  在檢視或視窗類別定義控制項。  
  
2.  呼叫控制項的 [建立](../Topic/CMonthCalCtrl::Create.md) 成員函式 \(可能在 [OnInitialUpdate](../Topic/CView::OnInitialUpdate.md) 中\)，並且盡可能的與父視窗的 [OnCreate](../Topic/CWnd::OnCreate.md) 處理常式函式一樣早 \(如果您是繼承控制項\) 。  設定控制項的樣式。  
  
## 請參閱  
 [使用 CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)   
 [控制項](../mfc/controls-mfc.md)