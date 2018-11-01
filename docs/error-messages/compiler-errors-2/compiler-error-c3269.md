---
title: 編譯器錯誤 C3269
ms.date: 11/04/2016
f1_keywords:
- C3269
helpviewer_keywords:
- C3269
ms.assetid: c575f067-244d-4dd5-bf58-9e7630ea58b7
ms.openlocfilehash: 406b388460b3d449471c884dd6461f2ce59a10f6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50622946"
---
# <a name="compiler-error-c3269"></a>編譯器錯誤 C3269

'function': managed 或 WinRTtype 成員函式不可以宣告使用 '...'

Managed 和 WinRT 類別成員函式不能宣告可變長度參數清單。

下列範例會產生 C3269，並示範如何修正此問題：

```
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
