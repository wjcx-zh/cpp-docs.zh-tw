---
title: "編譯器錯誤 C2457 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2457"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2457"
ms.assetid: 347e169d-23ad-434f-8836-5b09b53980ff
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# 編譯器錯誤 C2457
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'macro': 預先定義的巨集不可以出現在函式主體之外  
  
 您嘗試在全域空間中使用預先定義的巨集，例如 [\_\_FUNCTION\_\_](../../preprocessor/predefined-macros.md)。  
  
## 範例  
 下列範例會產生 C2457：  
  
```  
// C2457.cpp  
#include <stdio.h>  
  
__FUNCTION__;   // C2457, cannot be global  
  
int main()   
{  
    printf_s("\n%s",__FUNCTION__);   // OK  
}  
```