---
title: 編譯器錯誤 C2786
ms.date: 11/04/2016
f1_keywords:
- C2786
helpviewer_keywords:
- C2786
ms.assetid: 6676d8c0-86dd-4a39-bdda-b75a35f4d137
ms.openlocfilehash: ba5d05e9c7cc702509144fb876a1301bfc8bf3d4
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74739606"
---
# <a name="compiler-error-c2786"></a>編譯器錯誤 C2786

' type '： __uuidof 的運算元無效

[__Uuidof](../../cpp/uuidof-operator.md)運算子會使用已附加 GUID 的使用者自訂類型，或此類使用者定義類型的物件。  可能的原因:

1. 引數不是使用者定義型別。

1. `__uuidof` 無法從引數解壓縮 GUID。

下列範例會產生 C2786：

```cpp
// C2786.cpp
struct __declspec(uuid("00000000-0000-0000-0000-000000000000")) A {};

int main() {
   __uuidof(int);   // C2786
   __uuidof(int *);   // C2786
   __uuidof(A **);   // C2786

   // no error
   __uuidof(A);
   __uuidof(A *);
   __uuidof(A &);
   __uuidof(A[]);

   int i;
   int *pi;
   A **ppa;

   __uuidof(i);      // C2786
   __uuidof(pi);     // C2786
   __uuidof(ppa);    // C2786
}
```
