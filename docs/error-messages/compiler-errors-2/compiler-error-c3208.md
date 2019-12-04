---
title: 編譯器錯誤 C3208
ms.date: 11/04/2016
f1_keywords:
- C3208
helpviewer_keywords:
- C3208
ms.assetid: 6d060bfe-52cf-4599-8f70-bdeb5a670df3
ms.openlocfilehash: 61577ac4f28b8432a4425a76002ed5ad83186419
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761890"
---
# <a name="compiler-error-c3208"></a>編譯器錯誤 C3208

'function': 類別樣板 'class' 的樣板參數清單不符合樣板類樣板參數 'parameter' 的樣板參數清單

樣板類樣板參數沒有與所提供類別樣板相同的樣板參數數目。

下列範例會產生 C3208：

```cpp
// C3208.cpp
template <template <class T> class TT >
int f();

template <class T1, class T2>
struct S;

template <class T1>
struct R;

int i = f<S>();   // C3208
// try the following line instead
// int i = f<R>();
```
