---
title: "編譯器錯誤 C2015 | Microsoft Docs"
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
  - "C2015"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2015"
ms.assetid: 8f40af0a-3a5a-4d6a-8ed7-125966e6bfed
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2015
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

常數中字元太多  
  
 字元常數包含兩個以上的字元。  標準字元常數的限制是一個字元，而長字元常數的限制是兩個字元。  
  
 逸出序列 \(Escape Sequence，例如 \\t\) 將轉換成單一字元。  
  
## 範例  
 下列範例會產生 C2015：  
  
```  
// C2015.cpp  
// compile with: /c  
  
char test1 = 'error';   // C2015  
char test2 = 'e';   // OK  
```  
  
## 範例  
 使用 Microsoft Extension 而字元常數轉換成整數時，也可能會發生 C2015。下列範例會產生 C2015：  
  
```  
// C2015b.cpp  
#include <stdio.h>  
  
int main()   
{  
    int a = 'abcde';   // C2015  
  
    int b = 'a';   // 'a' = ascii 0x61  
    printf_s("%x\n", b);  
}  
```