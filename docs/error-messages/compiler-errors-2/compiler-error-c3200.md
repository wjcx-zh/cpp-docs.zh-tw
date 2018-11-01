---
title: 編譯器錯誤 C3200
ms.date: 11/04/2016
f1_keywords:
- C3200
helpviewer_keywords:
- C3200
ms.assetid: 44bb5e77-f0ec-421c-a732-b9ee7c0a3529
ms.openlocfilehash: 7eb0c00f4f4c5c59766bf305acfef89e12a6cfb1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50505062"
---
# <a name="compiler-error-c3200"></a>編譯器錯誤 C3200

'template': 樣板參數 'parameter' 的無效樣板引數必須是類別樣板

您可以傳遞無效的引數至類別樣板。 類別樣板必須做為參數的範本。 在下列範例中，呼叫`Y<int, int> aY`會產生 C3200。 第一個參數必須是範本，例如`Y<X, int> aY`。

```
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