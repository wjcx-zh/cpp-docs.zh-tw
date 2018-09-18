---
title: 編譯器錯誤 C3200 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3200
dev_langs:
- C++
helpviewer_keywords:
- C3200
ms.assetid: 44bb5e77-f0ec-421c-a732-b9ee7c0a3529
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 77be23b92d5237d2fa65557bdf36de31cd27d9d3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062633"
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