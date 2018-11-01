---
title: 編譯器錯誤 C2803
ms.date: 11/04/2016
f1_keywords:
- C2803
helpviewer_keywords:
- C2803
ms.assetid: 2cdbe374-8cc4-4c4e-ba15-062a7479e937
ms.openlocfilehash: d20b8dde9f4134273adcba0f947f685f7ce7d213
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50447264"
---
# <a name="compiler-error-c2803"></a>編譯器錯誤 C2803

'operator operator' 必須至少一個類別類型的型式參數

多載的運算子沒有類別類型的參數。

您必須以傳址方式 (不使用指標，而使用參考) 或傳值方式傳遞至少一個參數，才能寫入 "a < b" (a 和 b 屬於類別 A 類型)。

如果這兩個參數是指標，它將純比較的指標位址且不會使用使用者定義的轉換。

下列範例會產生 C2803:

```
// C2803.cpp
// compile with: /c
class A{};
bool operator< (const A *left, const A *right);   // C2803
// try the following line instead
// bool operator< (const A& left, const A& right);
```