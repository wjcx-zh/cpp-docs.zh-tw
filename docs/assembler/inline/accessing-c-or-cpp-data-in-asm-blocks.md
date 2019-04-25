---
title: 在 __asm 區塊中存取 C 或 C++ 資料
ms.date: 08/30/2018
helpviewer_keywords:
- data members [C++], in __asm blocks
- data access [C++], in __asm blocks
- __asm keyword [C++], data members
- structure types in __asm blocks
ms.assetid: e99f5a28-0381-4090-8ece-6af8f2436a49
ms.openlocfilehash: 1f56cc5c049c1501ea09c76f31be3ab9dea5ed10
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62167604"
---
# <a name="accessing-c-or-c-data-in-asm-blocks"></a>在 __asm 區塊中存取 C 或 C++ 資料

**Microsoft 專屬**

內嵌組譯碼的方便之處在於能夠依名稱參考 C 或 C++ 變數。 `__asm` 區塊可以在出現該區塊的範圍內參考任何符號，包括變數名稱。 例如，如果 C 變數 `var` 在範圍之內，指令

```cpp
__asm mov eax, var
```

會將 `var` 的值儲存在 EAX 中。

如果類別、 結構或等位成員都有唯一的名稱，`__asm`區塊可以參考它只使用成員名稱，但未指定變數或`typedef`名稱句點的前面 (**。**) 運算子。 不過，如果成員名稱不是唯一的，您必須在句號運算子之前加上變數或 `typedef` 名稱。 例如，下列範例中的結構類型共用 `same_name` 做為其成員名稱。

如果您宣告的變數類型為

```cpp
struct first_type hal;
struct second_type oat;
```

`same_name` 成員的所有參考都必須使用變數名稱，因為 `same_name` 不是唯一的。 不過，`weasel` 成員具有唯一的名稱，因此您可以只使用其成員名稱參考它：

```cpp
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

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[在 __asm 區塊中使用 C 或 C++](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)<br/>