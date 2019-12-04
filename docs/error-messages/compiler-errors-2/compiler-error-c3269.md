---
title: 編譯器錯誤 C3269
ms.date: 11/04/2016
f1_keywords:
- C3269
helpviewer_keywords:
- C3269
ms.assetid: c575f067-244d-4dd5-bf58-9e7630ea58b7
ms.openlocfilehash: 95f71c9312faaf5c14bd8990898257002c528c0e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754013"
---
# <a name="compiler-error-c3269"></a>編譯器錯誤 C3269

' function '： managed 或 WinRTtype 的成員函式不能以 ' ... ' 宣告

Managed 和 WinRT 類別成員函式不能宣告可變長度參數清單。

下列範例會產生 C3269，並示範如何修正此問題：

```cpp
// C3269_2.cpp
// compile with: /clr

ref struct A
{
   void func(int i, ...)   // C3269
   // try the following line instead
   // void func(int i )
   {
   }
};

int main()
{
}
```
