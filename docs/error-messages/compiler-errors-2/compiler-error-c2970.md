---
title: 編譯器錯誤 C2970
ms.date: 11/04/2016
f1_keywords:
- C2970
helpviewer_keywords:
- C2970
ms.assetid: 21d90348-20d3-438c-b278-efdbfb93a7d2
ms.openlocfilehash: af30ccc4a71c51d042d6f7807a648a1eef066a70
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74742661"
---
# <a name="compiler-error-c2970"></a>編譯器錯誤 C2970

' class '：樣板參數 ' param '： ' arg '：牽涉到具有內部連結之物件的運算式不能當做非類型引數使用

您不能使用靜態變數的名稱或位址做為樣板引數。 樣板類別預期可以在編譯時期評估的 const 值。

下列範例會產生 C2970：

```cpp
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
