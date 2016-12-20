---
title: "true (C++) | Microsoft Docs"
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
  - "true_cpp"
  - "true"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "true 關鍵字 [C++]"
ms.assetid: 96be2a70-51c3-4250-9752-874d25a5a11e
caps.latest.revision: 12
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# true (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 語法  
  
```  
  
        bool-identifier = true ;  
bool-expression logical-operator true ;  
```  
  
## 備註  
 這個關鍵字是 [bool](../cpp/bool-cpp.md) 類型變數或條件運算式 \(現為 true 布林運算式的條件運算式\) 的兩個值之中的一個。  如果 `i` 為 `bool` 類型，則陳述式 `i = true;` 會將 **true** 指派給 `i`。  
  
## 範例  
  
```  
// bool_true.cpp  
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