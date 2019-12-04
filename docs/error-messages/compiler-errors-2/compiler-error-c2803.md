---
title: 編譯器錯誤 C2803
ms.date: 11/04/2016
f1_keywords:
- C2803
helpviewer_keywords:
- C2803
ms.assetid: 2cdbe374-8cc4-4c4e-ba15-062a7479e937
ms.openlocfilehash: d39f737ba02f3fa9c9d5f61594ddf730db6739a5
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760656"
---
# <a name="compiler-error-c2803"></a>編譯器錯誤 C2803

' operator operator ' 必須至少有一個類別類型的型式參數

多載運算子缺少類別類型的參數。

您必須以傳址方式傳遞至少一個參數（不使用指標，但參考）或值，以寫入 "a < b" （a 和 b 屬於類別 A 的類型）。

如果這兩個參數都是指標，則會單純地比較指標位址，而不會使用使用者定義的轉換。

下列範例會產生 C2803：

```cpp
// C2803.cpp
// compile with: /c
class A{};
bool operator< (const A *left, const A *right);   // C2803
// try the following line instead
// bool operator< (const A& left, const A& right);
```
