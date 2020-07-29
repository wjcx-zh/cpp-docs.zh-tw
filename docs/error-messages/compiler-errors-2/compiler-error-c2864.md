---
title: 編譯器錯誤 C2864
ms.date: 10/04/2019
f1_keywords:
- C2864
helpviewer_keywords:
- C2864
ms.assetid: d0ca2ad9-90a6-4aef-8511-98a3b414c102
ms.openlocfilehash: cfa928c84fbf6c841e3caaf51dda526a7ae184fa
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212653"
---
# <a name="compiler-error-c2864"></a>編譯器錯誤 C2864

> '*member name*'：具有類別初始化運算式的靜態資料成員，必須具有非暫時性 const 整數類型

## <a name="remarks"></a>備註

若要初始化 **`static`** 定義為 **`volatile`** 、非 **`const`** 或不是整數類型的資料成員，請使用成員定義語句。 它們無法在宣告中初始化。

## <a name="example"></a>範例

這個範例會產生 C2864：

```cpp
// C2864.cpp
// compile with: /c
class B  {
private:
   int a = 3;   // OK
   static int b = 3;   // C2864
   volatile static int c = 3;   // C2864
   volatile static const int d = 3;   // C2864
   static const long long e = 3;   // OK
   static const double f = 3.33;   // C2864
};
```

此範例示範如何修正 C2864：

```cpp
// C2864b.cpp
// compile with: /c
class C  {
private:
   int a = 3;
   static int b; // = 3; C2864
   volatile static int c; // = 3; C2864
   volatile static const int d; // = 3; C2864
   static const long long e = 3;
   static const double f; // = 3.33; C2864
};

// Initialize static volatile, non-const, or non-integral
// data members when defined, not when declared:
int C::b = 3;
volatile int C::c = 3;
volatile const int C::d = 3;
const double C::f = 3.33;
```
