---
title: 編譯器錯誤 C2758
ms.date: 11/04/2016
f1_keywords:
- C2758
helpviewer_keywords:
- C2758
ms.assetid: 1d273034-194c-4926-9869-142d1b219cbe
ms.openlocfilehash: c3a86b8b8c7f122929a52221d4f01a17c50395be
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62257656"
---
# <a name="compiler-error-c2758"></a>編譯器錯誤 C2758

'member'：必須初始化參考類型的成員

當建構函式未初始化初始設定式清單中參考類型的成員時，會產生編譯器錯誤 C2758。 編譯器會將成員保持未定義的狀態。 在建構函式的初始化清單中宣告參考成員變數或提供值時，必須初始化。

下列範例會產生 C2758：

```
// C2758.cpp
// Compile by using: cl /W3 /c C2758.cpp
struct A {
   const int i;

   A(int n) { };   // C2758
   // try the following line instead
   // A(int n) : i{n} {};
};
```