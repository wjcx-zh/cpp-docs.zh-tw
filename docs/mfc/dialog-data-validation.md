---
title: "對話方塊資料驗證 | Microsoft Docs"
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
  - "資料驗證 [C++], 對話方塊"
  - "資料驗證 [C++], 訊息方塊"
  - "DDV (對話方塊資料驗證) [C++]"
  - "對話方塊 [C++], 驗證資料"
  - "驗證資料 [C++], 對話方塊資料輸入"
  - "驗證資料 [C++], 訊息方塊"
ms.assetid: f070c309-2044-4ff2-8c92-1ec1ea84af58
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 對話方塊資料驗證
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以指定要刪除資料交換之外呼叫 DDV 函式，如下列範例所示的 [對話資料交換](../mfc/dialog-data-exchange.md)。  這個範例會驗證的 `DDV_MaxChars` 呼叫在 TextBox 控制項中輸入的字串超過 20 個字元的長度不是。  DDV 函式在違規的控制項通常會有警告訊息方塊的使用者，則驗證會失敗並將焦點，因此使用者可以重新輸入資料。  必須呼叫特定控制項的 DDV 函式，在相同的控制項之後 DDX 函式。  
  
 您也可以定義自訂 DDX 和 DDV 常式。  如需這個與 DDX 和 DDV 的其他方面的詳細資訊，請參閱 [MFC 技術提示 26](../mfc/tn026-ddx-and-ddv-routines.md)。  
  
 [加入成員變數精靈](../ide/add-member-variable-wizard.md) 會將所有 DDX 和 DDV 呼叫資料對應您的。  
  
## 請參閱  
 [對話方塊資料交換和驗證](../mfc/dialog-data-exchange-and-validation.md)   
 [對話方塊的生命週期](../mfc/life-cycle-of-a-dialog-box.md)   
 [對話方塊資料交換](../mfc/dialog-data-exchange.md)