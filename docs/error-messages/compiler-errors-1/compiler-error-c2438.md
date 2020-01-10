---
title: 編譯器錯誤 C2438
ms.date: 11/04/2016
f1_keywords:
- C2438
helpviewer_keywords:
- C2438
ms.assetid: 3a0ab3ba-d0e4-4d8f-971d-e503397cc827
ms.openlocfilehash: da6443f3f319c864b53f6d077e8bf99faffc5888
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74744312"
---
# <a name="compiler-error-c2438"></a>編譯器錯誤 C2438

' identifier '：無法透過函式初始化靜態類別資料

函式是用來初始化類別的靜態成員。 靜態成員必須在類別宣告之外的定義中初始化。

下列範例會產生 C2438：

```cpp
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
