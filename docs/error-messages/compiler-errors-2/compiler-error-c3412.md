---
title: 編譯器錯誤 C3412
ms.date: 11/04/2016
f1_keywords:
- C3412
helpviewer_keywords:
- C3412
ms.assetid: aa4dd43b-54ce-4cda-85c1-1a77dd6e34fa
ms.openlocfilehash: 7c16ffa37f4d7192956afae26c825b63add1bfdd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50540241"
---
# <a name="compiler-error-c3412"></a>編譯器錯誤 C3412

'template': 無法特製化目前的領域中的範本

在類別範圍內，只能在全域或命名空間範圍內，不能特製化樣板。

## <a name="example"></a>範例

下列範例會產生 C3412。

```
// C3412.cpp
template <class T>
struct S {
   template <>
   struct S<int> {};   // C3412 in a class
};
```

## <a name="example"></a>範例

下列範例顯示可能的解決方式。

```
// C3412b.cpp
// compile with: /c
template <class T>
struct S {};

template <>
struct S<int> {};
```