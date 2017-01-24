---
title: "從對話方塊物件擷取資料 | Microsoft Docs"
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
  - "擷取使用者輸入"
  - "資料 [MFC], 對話方塊"
  - "資料 [MFC], 擷取"
  - "資料擷取 [C++], 對話方塊"
  - "DDX (對話方塊資料交換) [C++]"
  - "DDX (對話方塊資料交換) [C++], 關於 DDX"
  - "DDX (對話方塊資料交換) [C++], 從 Dialog 物件擷取資料"
  - "對話方塊控制項 [C++], 初始化值"
  - "對話方塊資料 [C++]"
  - "對話方塊資料 [C++], 擷取"
  - "對話方塊 [C++], 擷取使用者資料"
  - "GetDlgItemText 方法"
  - "GetWindowText 方法"
  - "MFC 對話方塊, 擷取使用者輸入"
  - "擷取資料"
  - "SetDlgItemText 方法"
  - "SetWindowText 方法"
  - "使用者輸入 [C++], 從 MFC 對話方塊擷取"
ms.assetid: bdca2b61-6b53-4c2e-b426-8712c7a38ec0
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 從對話方塊物件擷取資料
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

架構提供簡易的方法會初始化控制項的值在對話方塊及擷取控制項的值。  這種比較耗費強制的手動方法將呼叫函式 \(例如類別 `CWnd`的 `SetDlgItemText` 和 `GetDlgItemText` 成員函式，套用至控制項的視窗。  這些函式，您個別存取的每個控制項設定或取得其值，呼叫函式 \(例如 `SetWindowText` 和 `GetWindowText`。  框架的方法自動初始化和擷取。  
  
 對話資料交換 \(Dialog Data Exchange，DDX\) 可讓您在對話方塊的變數更輕鬆地物件的控制項在對話方塊和成員間交換資料。  這個切換運作兩個方式。  若要在對話方塊的控制項，您可以設定資料成員值對話方塊物件的，因此，架構會將值加入至控制項，在對話方塊顯示之前。  然後您可以隨時更新具有使用者輸入的資料的對話資料成員。  此時，您可以參考資料成員變數使用資料。  
  
 您可以為對話方塊控制項的值會自動驗證的同時設定與對話資料驗證 \(DDV\)。  
  
 DDX 和 DDV [對話資料交換和驗證](../mfc/dialog-data-exchange-and-validation.md)中詳細說明。  
  
 對於強制回應對話方塊，也就是說，當，但是被終結時，擷取所有資料使用者輸入在對話方塊物件前的 `DoModal` 傳回 **IDOK** 。  對於非強制回應對話方塊，從對話方塊物件隨時擷取資料藉由使用引數呼叫 **TRUE** 的 `UpdateData` 然後存取對話方塊類別成員變數。  這個主題 [對話資料交換和驗證](../mfc/dialog-data-exchange-and-validation.md)中詳細討論。  
  
## 請參閱  
 [對話方塊的生命週期](../mfc/life-cycle-of-a-dialog-box.md)