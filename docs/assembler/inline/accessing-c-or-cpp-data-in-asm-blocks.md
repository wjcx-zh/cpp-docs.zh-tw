---
title: 存取 C 或 c + + 在 __asm 區塊中的資料 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- data members [C++], in __asm blocks
- data access [C++], in __asm blocks
- __asm keyword [C++], data members
- structure types in __asm blocks
ms.assetid: e99f5a28-0381-4090-8ece-6af8f2436a49
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9631db3c09c19e38791a6c909be02acd1c91601b
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="accessing-c-or-c-data-in-asm-blocks"></a>在 __asm 區塊中存取 C 或 C++ 資料
## <a name="microsoft-specific"></a>Microsoft 特定的  
 內嵌組譯碼的方便之處在於能夠依名稱參考 C 或 C++ 變數。 `__asm` 區塊可以在出現該區塊的範圍內參考任何符號，包括變數名稱。 例如，如果 C 變數 `var` 在範圍之內，指令  
  
```  
__asm mov eax, var  
```  
  
 會將 `var` 的值儲存在 EAX 中。  
  
 如果類別、 結構或等位成員都有唯一的名稱，`__asm`區塊可以參考使用只有成員名稱，但未指定變數或`typedef`期間之前的名稱 (**。**) 運算子。 不過，如果成員名稱不是唯一的，您必須在句號運算子之前加上變數或 `typedef` 名稱。 例如，下列範例中的結構類型共用 `same_name` 做為其成員名稱。  
  
 如果您宣告的變數類型為  
  
```  
struct first_type hal;  
struct second_type oat;  
```  
  
 `same_name` 成員的所有參考都必須使用變數名稱，因為 `same_name` 不是唯一的。 不過，`weasel` 成員具有唯一的名稱，因此您可以只使用其成員名稱參考它：  
  
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
  
 請注意，省略變數名稱只是為了方便撰寫程式碼。 無論變數名稱是否存在，都會產生相同的組譯碼指令。  
  
 您可以存取 C++ 的資料成員，不需要考慮存取限制。 不過，您無法呼叫成員函式。  
  
 **結束 Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [在 __asm 區塊中使用 C 或 C++](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)