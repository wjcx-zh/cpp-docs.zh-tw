---
title: 編譯器錯誤 C3412
ms.date: 11/04/2016
f1_keywords:
- C3412
helpviewer_keywords:
- C3412
ms.assetid: aa4dd43b-54ce-4cda-85c1-1a77dd6e34fa
ms.openlocfilehash: ad241b656464746333760cfcbc134c91e49bf44e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761412"
---
# <a name="compiler-error-c3412"></a>編譯器錯誤 C3412

' template '：無法在目前的範圍中特殊化範本

範本不能在類別範圍中特製化，只會在全域或命名空間範圍中。

## <a name="example"></a>範例

下列範例會產生 C3412。

```cpp
// C3412.cpp
template <class T>
struct S {
   template <>
   struct S<int> {};   // C3412 in a class
};
```

## <a name="example"></a>範例

下列範例顯示可能的解決方式。

```cpp
// C3412b.cpp
// compile with: /c
template <class T>
struct S {};

template <>
struct S<int> {};
```
