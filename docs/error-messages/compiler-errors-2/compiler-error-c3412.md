---
title: 編譯器錯誤 C3412 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3412
dev_langs:
- C++
helpviewer_keywords:
- C3412
ms.assetid: aa4dd43b-54ce-4cda-85c1-1a77dd6e34fa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f6a04de132c85cb09a960d3a0edfcb3b07127119
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054565"
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