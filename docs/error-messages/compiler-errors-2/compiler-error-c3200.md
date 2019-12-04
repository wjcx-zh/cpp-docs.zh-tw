---
title: 編譯器錯誤 C3200
ms.date: 11/04/2016
f1_keywords:
- C3200
helpviewer_keywords:
- C3200
ms.assetid: 44bb5e77-f0ec-421c-a732-b9ee7c0a3529
ms.openlocfilehash: 7f6b514231bcda18404e891e0acbe457c8f95146
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738774"
---
# <a name="compiler-error-c3200"></a>編譯器錯誤 C3200

' template '：範本參數 ' parameter ' 的樣板引數無效，應為類別樣板

您將不正確引數傳遞至類別樣板。 類別範本需要範本作為參數。 在下列範例中，呼叫 `Y<int, int> aY` 將會產生 C3200。 第一個參數必須是範本，例如 `Y<X, int> aY`。

```cpp
// C3200.cpp
template<typename T>
class X
{
};

template<template<typename U> class T1, typename T2>
class Y
{
};

int main()
{
   Y<int, int> y;   // C3200
}
```
