---
title: "在 __asm 區塊中存取 C 或 C++ 資料 | Microsoft Docs"
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
  - "__asm 關鍵字 [C++], 資料成員"
  - "資料存取 [C++], 在 __asm 區塊中"
  - "資料成員 [C++], 在 __asm 區塊中"
  - "__asm 區塊中的結構類型"
ms.assetid: e99f5a28-0381-4090-8ece-6af8f2436a49
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 在 __asm 區塊中存取 C 或 C++ 資料
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## Microsoft 特定的  
 內嵌組譯碼的方便之處在於能夠依名稱參考 C 或 C\+\+ 變數。  `__asm` 區塊可以在出現該區塊的範圍內參考任何符號，包括變數名稱。  例如，如果 C 變數 `var` 在範圍之內，指令  
  
```  
__asm mov eax, var  
```  
  
 會將 `var` 的值儲存在 EAX 中。  
  
 如果類別、結構或等位成員具有唯一名稱，`__asm` 區塊可以只使用成員名稱參考該成員，而不在句號 \(**.**\) 運算子之前指定變數或 `typedef` 名稱。  不過，如果成員名稱不是唯一的，您必須在句號運算子之前加上變數或 `typedef` 名稱。  例如，下列範例中的結構類型共用 `same_name` 做為其成員名稱。  
  
 如果您宣告的變數類型為  
  
```  
struct first_type hal;  
struct second_type oat;  
```  
  
 `same_name` 成員的所有參考都必須使用變數名稱，因為 `same_name` 不是唯一的。  不過，`weasel` 成員具有唯一的名稱，因此您可以只使用其成員名稱參考它：  
  
```  
// InlineAssembler_Accessing_C_asm_Blocks.cpp  
// processor: x86  
#include <stdio.h>  
struct first_type  
{  
   char *weasel;  
   int same_name;  
};  
  
struct second_type  
{  
   int wonton;  
   long same_name;  
};  
  
int main()  
{  
   struct first_type hal;  
   struct second_type oat;  
  
   __asm  
   {  
      lea ebx, hal  
      mov ecx, [ebx]hal.same_name ; Must use 'hal'  
      mov esi, [ebx].weasel       ; Can omit 'hal'  
   }  
   return 0;  
}  
```  
  
 請注意，省略變數名稱只是為了方便撰寫程式碼。  無論變數名稱是否存在，都會產生相同的組譯碼指令。  
  
 您可以存取 C\+\+ 的資料成員，不需要考慮存取限制。  不過，您無法呼叫成員函式。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [在 \_\_asm 區塊中使用 C 或 C\+\+](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)