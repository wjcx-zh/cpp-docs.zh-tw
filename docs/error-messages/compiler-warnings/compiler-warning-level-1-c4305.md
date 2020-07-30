---
title: 編譯器警告 (層級 1) C4305
ms.date: 01/17/2018
f1_keywords:
- C4305
helpviewer_keywords:
- C4305
ms.openlocfilehash: 567442bc48487e4f7d1f905f871d15f913646e87
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233284"
---
# <a name="compiler-warning-level-1-c4305"></a>編譯器警告 (層級 1) C4305

> '*coNtext*'：從 '*type1*' 截斷為 '*type2*'

## <a name="remarks"></a>備註

當值在初始化中轉換成較小的類型，或做為函式引數，而導致資訊遺失時，就會發出這個警告。

## <a name="example"></a>範例

此範例顯示兩種您可能會看到此警告的方式：

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

若要修正此問題，請使用正確類型的值進行初始化，或使用明確轉換成正確的類型。 例如，使用 **`float`** 常值（例如 2.71828 f），而不是 **`double`** （浮點常值的預設類型）來初始化 **`float`** 變數，或傳遞至接受 **`float`** 引數的函式。
