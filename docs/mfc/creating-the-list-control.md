---
title: "建立清單控制項 | Microsoft Docs"
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
  - "CListCtrl 類別, 建立控制項"
  - "清單控制項"
ms.assetid: a4cb1729-31b6-4d2b-a44b-367474848a39
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 建立清單控制項
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

清單控制項 \([CListCtrl](../mfc/reference/clistctrl-class.md)\) 的建立方式取決於您是否直接使用控制項或使用 [CListView](../mfc/reference/clistview-class.md) 類別。  如果您使用 `CListView`，架構會建構檢視做為它的文件\/檢視建立序列的一部分。  建立清單檢視也建立清單控制項 \(兩個是相同的結果\)。  控制項建立至檢視的 [OnCreate](../Topic/CWnd::OnCreate.md) 處理常式函式。  在這種情況下，控制項已經準備好加入項目，透過呼叫 [GetListCtrl](../Topic/CListView::GetListCtrl.md)。  
  
### 直接在對話方塊使用 CListCtrl  
  
1.  在對話方塊編輯器，將清單控制項加入至對話方塊樣板資源。  指定它的控制項 ID.  
  
2.  使用 [加入成員變數精靈](../ide/adding-a-member-variable-visual-cpp.md) 將型別 `CListCtrl` 的成員變數加入至控制項屬性。  您可以使用這個成員呼叫 `CListCtrl` 成員函式。  
  
3.  使用屬性視窗對應至對話方塊類別中處理函式需要處理的所有清單控制項告知訊息 \(請參閱 [對應訊息至函式](../mfc/reference/mapping-messages-to-functions.md)\)。  
  
4.  在 [OnInitDialog](../Topic/CDialog::OnInitDialog.md)中，將 `CListCtrl`的樣式。  請參閱 [變更清單控制項樣式](../mfc/changing-list-control-styles.md)。  這決定您在控制項中取得的檢視類型，不過，您可以在稍後變更檢視。  
  
### 在 nondialog 視窗使用 CListCtrl  
  
1.  在檢視或視窗類別定義控制項。  
  
2.  呼叫控制項的 [建立](../Topic/CListCtrl::Create.md) 成員函式，可能在 [OnInitialUpdate](../Topic/CView::OnInitialUpdate.md)中，可能與父視窗的 [OnCreate](../Topic/CWnd::OnCreate.md) 處理常式函式一樣早 \(如果您繼承控制項\) 。  設定控制項的樣式。  
  
## 請參閱  
 [使用 CListCtrl](../mfc/using-clistctrl.md)   
 [控制項](../mfc/controls-mfc.md)