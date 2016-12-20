---
title: "編譯器錯誤 C2180 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2180"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2180"
ms.assetid: ea71b39e-b977-48a7-b7bd-af68ef5e263b
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2180
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

控制運算式具有類型 'type'  
  
 `if`、`while`、`for` 或 `do` 陳述式中的控制運算式，是轉換成 `void` 的運算式。  若要修正此問題，請將控制運算式變更為會產生 `bool` 的運算式或可轉換成 `bool` 的類型。  
  
 下列範例會產生 C2180：  
  
```  
// C2180.c  
  
int main() {  
   while ((void)1)   // C2180  
      return 1;  
   while (1)         // OK  
      return 0;  
}  
```