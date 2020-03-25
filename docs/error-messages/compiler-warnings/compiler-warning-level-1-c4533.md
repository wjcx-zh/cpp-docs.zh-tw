---
title: 編譯器警告 (層級 1) C4533
ms.date: 11/04/2016
f1_keywords:
- C4533
helpviewer_keywords:
- C4533
ms.assetid: 359fecda-d540-46e5-b214-dbabe9ef50d2
ms.openlocfilehash: 20637dc23e13031b4199298a3374825062ce40da
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186422"
---
# <a name="compiler-warning-level-1-c4533"></a>編譯器警告 (層級 1) C4533

' ' 指令 ' 已略過 ' variable ' 的初始化

程式中的指示已變更控制流程，因此未執行初始化變數的指令。 下列範例會產生 C4533：

```cpp
// C4533.cpp
// compile with: /W1
#include <stdio.h>

struct A
{
   int m_data;
};

int main()
{
   if (1)
   {
      goto Label;
   }

   A a = { 100 };

   Label:   // C4533
      printf("\n%d", a.m_data);   // prints an uninitialized value
}
```
