---
title: "auto 儲存類別規範 | Microsoft Docs"
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
ms.assetid: 8e73f57e-aa92-4e41-91ea-5c8ad2a2b332
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# auto 儲存類別規範
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**auto** 儲存類別指定名稱會宣告自動變數，也就是具有本機存留期的變數。  **auto** 變數只能在其宣告所在的區塊中看見。  **auto** 變數的宣告可以包含初始設定式，如[初始化](../c-language/initialization.md)中所述。  由於具有 **auto** 儲存類別的變數不會自動初始化，因此您應在宣告這些變數時加以明確初始化，或者在區塊內的陳述式中為它們指派初始值。  未初始化的 **auto** 變數值為未定義 \(如果已指定初始設定式，則 **auto** 或 **register** 儲存類別的區域變數會在每次進入範圍時初始化\)。  
  
 內部 **static** 變數 \(具有區域或區塊範圍的靜態變數\) 可以使用任何外部或 **static** 項目的位址初始化，但是不可使用另一個 **auto** 項目的位址初始化，因為 **auto** 項目的位址不是常數。  
  
## 請參閱  
 [auto 關鍵字](../cpp/auto-keyword.md)