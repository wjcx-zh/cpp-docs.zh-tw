---
title: "開發您自己的 Helper 函式 | Microsoft Docs"
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
  - "Helper 函式"
ms.assetid: a845429d-68b1-4e14-aa88-f3f5343bd490
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 開發您自己的 Helper 函式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

您可能會希望提供自己的常式版本，根據 DLL 或匯入的名稱來進行特定的處理。  有兩種方法可以完成這項工作：根據提供的程式碼自己編寫程式，或是使用之前說明的告知攔截來攔截所提供的版本。  
  
 自己編寫程式  
 由於本質上您可以利用提供的程式碼做為新常式的方針，因此這是相當簡單的方法。  當然，它必須遵守呼叫慣例；如果它會返回連結器產生的 Thunk，也必須傳回適當的函式指標。  在您的程式碼中，可以執行任何希望執行的動作來滿足呼叫或離開呼叫。  
  
 使用啟動處理告知攔截  
 最簡單的方法可能是只提供新指標給使用者提供的告知攔截函式，此函式接收與 dliStartProcessing 告知中的預設 Helper 相同的值。  此時，攔截函式本質上已經變成新的 Helper 函式，成功地回到預設的 Helper 將會忽略預設 Helper 中所有的進一步的處理。  
  
## 請參閱  
 [延遲載入 DLL 的連結器支援](../../build/reference/linker-support-for-delay-loaded-dlls.md)