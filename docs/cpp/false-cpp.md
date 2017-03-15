---
title: "false (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "false_cpp"
  - "false"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "false 關鍵字 [C++]"
ms.assetid: cc13aec5-1f02-4d38-8dbf-5473ea2b354f
caps.latest.revision: 11
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# false (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

關鍵字是類型為 [bool](../cpp/bool-cpp.md) 之變數或條件運算式 \(現為 **true** 之布林運算式的條件運算式\) 的兩個值當中的一個值。  例如，如果 `i` 是類型為 `bool` 的變數，`i = false;` 陳述式就會將 **false** 指派給 `i`。  
  
## 範例  
  
```  
// bool_false.cpp  
#include <stdio.h>  
  
int main()  
{  
    bool bb = true;  
    printf_s("%d\n", bb);  
    bb = false;  
    printf_s("%d\n", bb);  
}  
```  
  
  **1**  
**0**   
## 請參閱  
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)