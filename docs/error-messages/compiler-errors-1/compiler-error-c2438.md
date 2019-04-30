---
title: 編譯器錯誤 C2438
ms.date: 11/04/2016
f1_keywords:
- C2438
helpviewer_keywords:
- C2438
ms.assetid: 3a0ab3ba-d0e4-4d8f-971d-e503397cc827
ms.openlocfilehash: b2861090b5f7629c7f0cd94ea38a99e888909258
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62375752"
---
# <a name="compiler-error-c2438"></a>編譯器錯誤 C2438

'identifier': 無法初始化靜態類別資料，透過建構函式

建構函式用來初始化類別的靜態成員。 在類別宣告之外定義中，必須先初始化靜態成員。

下列範例會產生 C2438:

```
// C2438.cpp
struct X {
   X(int i) : j(i) {}   // C2438
   static int j;
};

int X::j;

int main() {
   X::j = 1;
}
```