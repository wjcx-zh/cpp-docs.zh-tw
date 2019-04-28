---
title: 編譯器錯誤 C2864
ms.date: 11/04/2016
f1_keywords:
- C2864
helpviewer_keywords:
- C2864
ms.assetid: d0ca2ad9-90a6-4aef-8511-98a3b414c102
ms.openlocfilehash: 9bfc18137df1a54530011a8ec3f7ea50b1d6c86a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62227496"
---
# <a name="compiler-error-c2864"></a>編譯器錯誤 C2864

'variable'：具有類別內初始設定式的靜態資料成員，必須有非動態的 const 整數類型

若要初始化定義為 `static`、非 `volatile` 或不是整數類資料類型的 `const` 資料成員，請使用成員定義陳述式。 這些成員無法在宣告中初始化。

此範例會產生 C2864:

```
// C2864.cpp
// compile with: /c
class B  {
private:
   int a = 3;   // OK
   static int b = 3;   // C2864
   volatile static int c = 3;   // C2864
   volatile static const int d = 3;   // C2864
   const static long long e = 3;   // OK
   static const double f = 3.33;   // C2864
};
```

此範例示範如何修正 C2864：

```
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