---
title: 編譯器警告 （層級 4） C4754 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4754
dev_langs:
- C++
helpviewer_keywords:
- C4754
ms.assetid: e0e4606a-754a-4f42-a274-21a34978d21d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c7681f78812ef33dce5bd6d7792f8158a8f35ce3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118657"
---
# <a name="compiler-warning-level-4-c4754"></a>編譯器警告 (層級 4) C4754

比較中有算術運算的轉換規則，表示有一個分支無法執行到。

因為比較結果永遠相同，所以發出 C4754 警告。 這表示一個條件分支從未執行，很可能是因為關聯的整數運算式不正確。 這個程式碼缺失常發生於 64 位元架構的錯誤整數溢位檢查。

整數轉換規則很複雜，而且有許多微妙的陷阱。 修正每個 C4754 警告的替代方案，您可以更新程式碼以使用[SafeInt 程式庫](../../windows/safeint-library.md)。

## <a name="example"></a>範例

此範例會產生 C4754:

```cpp
// C4754a.cpp
// Compile with: /W4 /c
#include "errno.h"

int sum_overflow(unsigned long a, unsigned long b)
{
   unsigned long long x = a + b; // C4754

   if (x > 0xFFFFFFFF)
   {
      // never executes!
      return EOVERFLOW;
   }
   return 0;
}
```

在結果向上轉型成 64 位元值和指派給 64 位元變數 `a + b` 之前，加法 `x` 可能造成算術溢位。 這表示在 `x` 中檢查是多餘的，永遠不會攔截溢位。 在這種情況下，編譯器就會發出這個警告：

```Output
Warning C4754: Conversion rules for arithmetic operations in the comparison at C4754a.cpp (7) mean that one branch cannot be executed. Cast '(a + ...)' to 'ULONG64' (or similar type of 8 bytes).
```

若要排除警告，您可以變更指派陳述式，將運算元轉型為 8 位元組值：

```cpp
// Casting one operand is sufficient to force all the operands in
// the addition be upcast according to C/C++ conversion rules, but
// casting both is clearer.
unsigned long long x =
   (unsigned long long)a + (unsigned long long)b;
```

## <a name="example"></a>範例

接下來的範例也會產生 C4754。

```cpp
// C4754b.cpp
// Compile with: /W4 /c
#include "errno.h"

int wrap_overflow(unsigned long a)
{
   if (a + sizeof(unsigned long) < a) // C4754
   {
      // never executes!
      return EOVERFLOW;
   }
   return 0;
}
```

`sizeof()` 運算子會傳回 `size_t`，其大小為架構相依。 範例程式碼可在 32 位元架構上運作，其中 `size_t` 是 32 位元類型。 不過，在 64 位元架構上，`size_t` 是 64 位元類型。 整數的轉換規則表示 `a` 會向上轉型成運算式 `a + b < a` 的 64 位元值，如同寫成 `(size_t)a + (size_t)b < (size_t)a`。 當 `a` 和 `b` 都是 32 位元整數時，64 位元加法運算永不溢位，且限制式永不成立。 因此，程式碼永不會偵測到 64 位元架構的整數溢位狀況。 這個範例會使編譯器發出這個警告：

```Output
Warning C4754: Conversion rules for arithmetic operations in the comparison at C4754b.cpp (7) mean that one branch cannot be executed. Cast '4' to 'ULONG' (or similar type of 4 bytes).
```

請注意，這個警告訊息明確列出常數值 4，而不是原始來源字串—當警告分析遇到違規的程式碼時，`sizeof(unsigned long)` 已轉換為常數。 因此，您可能必須追蹤原始程式碼中哪個運算式與警告訊息的常數值相關聯。 最常解析成 C4754 警告訊息中之常數的原始程式碼是 `sizeof(TYPE)` 和 `strlen(szConstantString)` 等運算式。

在這種情況下，已修正的程式碼會看起來像這樣：

```cpp
// Casting the result of sizeof() to unsigned long ensures
// that all the addition operands are 32-bit, so any overflow
// is detected by the check.
if (a + (unsigned long)sizeof(unsigned long) < a)

```

**請注意**指編譯器警告的行號是陳述式的最後一行。 在分佈於多行的複雜條件陳述式的警告訊息，程式碼缺失可能是在報告行的幾行之前。 例如: 

```cpp
unsigned long a;

if (a + sizeof(unsigned long) < a || // incorrect check
    condition1() ||
    a == 0) {    // C4754 warning reported on this line
         // never executes!
         return INVALID_PARAMETER;
}
```