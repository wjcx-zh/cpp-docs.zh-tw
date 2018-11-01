---
title: 編譯器錯誤 C2078
ms.date: 11/04/2016
f1_keywords:
- C2078
helpviewer_keywords:
- C2078
ms.assetid: 9bead850-4123-46cf-a634-5c77ba974b2b
ms.openlocfilehash: 413d1215b7d69af738b5b4ad99206e4d6135980e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50569763"
---
# <a name="compiler-error-c2078"></a>編譯器錯誤 C2078

初始設定式太多

初始設定式數目超過要初始化的物件數目。

從初始設定式清單中省略內部大括號時，編譯器可以推算正確指派給物件和內部物件的初始設定式。 使用完整括號也能避免模稜兩可，產生正確的指派。 使用局部括號會造成 C2078，因為指派給初始設定式給物件時會模稜兩可。

下列範例會產生 C2078，並示範如何修正此問題：

```
// C2078.cpp
// Compile by using: cl /c /W4 C2078.cpp
struct S {
   struct {
      int x, y;
   } z[2];
};

int main() {
   int d[2] = {1, 2, 3};   // C2078
   int e[2] = {1, 2};      // OK

   char a[] = {"a", "b"};  // C2078
   char *b[] = {"a", "b"}; // OK
   char c[] = {'a', 'b'};  // OK

   S s1{1, 2, 3, 4};       // OK
   S s2{{1, 2}, {3, 4}};   // C2078
   S s3{{1, 2, 3, 4}};     // OK
   S s4{{{1, 2}, {3, 4}}}; // OK
}

```