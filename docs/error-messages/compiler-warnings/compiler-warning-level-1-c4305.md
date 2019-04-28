---
title: 編譯器警告 (層級 1) C4305
ms.date: 1/17/2018
f1_keywords:
- C4305
helpviewer_keywords:
- C4305
ms.openlocfilehash: 3f9116b0e7bdd9ee13c42b48f44da4b090f41ccd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62327466"
---
# <a name="compiler-warning-level-1-c4305"></a>編譯器警告 (層級 1) C4305

> '*內容*': 從'*type1*'to'*type2*'

## <a name="remarks"></a>備註

值，轉換成較小的類型在初始化期間或建構函式引數，導致資訊遺失時，會發出這個警告。

## <a name="example"></a>範例

此範例會示範兩種方式，您可能會看到這個警告：

```cpp
// C4305.cpp
// Compile by using: cl /EHsc /W4 C4305.cpp

struct item
{
    item(float) {}
};

int main()
{
    float f = 2.71828;          // C4305 'initializing'
    item i(3.14159);            // C4305 'argument'
    return static_cast<int>(f);
}
```

若要修正此問題，藉由使用的值為正確的型別，初始化，或使用明確轉換成正確的型別。 比方說，使用**浮點數**例如 2.71828f 而不是常值**double** （浮點常值的預設類型） 來初始化**float**變數，或要傳遞至使用建構函式**浮點數**引數。
