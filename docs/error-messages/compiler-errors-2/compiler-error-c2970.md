---
title: 編譯器錯誤 C2970
ms.date: 11/04/2016
f1_keywords:
- C2970
helpviewer_keywords:
- C2970
ms.assetid: 21d90348-20d3-438c-b278-efdbfb93a7d2
ms.openlocfilehash: 425d1bf50d56c4455ccd9292b300e744625d34c7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50638408"
---
# <a name="compiler-error-c2970"></a>編譯器錯誤 C2970

'class': 樣板參數 'param': 'arg': 運算式包含具有內部連結的物件不能當做非類型引數

您無法使用的名稱或位址的靜態變數，做為範本引數。 此範本類別必須要有一個可以在編譯時期評估的常數值。

下列範例會產生 C2970:

```
// C2970.cpp
// compile with: /c
static int si;
// could declare nonstatic to resolve all errors
// int si;

template <int i>
class X {};

template <int *pi>
class Y {};

X<si> anX;   // C2970 cannot use static variable in templates

// this would also work
const int i = 10;
X<i> anX2;
```