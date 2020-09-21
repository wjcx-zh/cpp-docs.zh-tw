---
title: 編譯器錯誤 C3412
ms.date: 11/04/2016
f1_keywords:
- C3412
helpviewer_keywords:
- C3412
ms.assetid: aa4dd43b-54ce-4cda-85c1-1a77dd6e34fa
ms.openlocfilehash: 6918e3be0a0288bab50d63a188bc33df87fe7754
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2020
ms.locfileid: "90742888"
---
# <a name="compiler-error-c3412"></a>編譯器錯誤 C3412

' template '：無法在目前的範圍中特殊化範本

範本無法在類別範圍中特製化，只能在全域或命名空間範圍中特製化。

## <a name="examples"></a>範例

下列範例會產生 C3412。

```cpp
// C3412.cpp
template <class T>
struct S {
   template <>
   struct S<int> {};   // C3412 in a class
};
```

下列範例顯示可能的解決方法。

```cpp
// C3412b.cpp
// compile with: /c
template <class T>
struct S {};

template <>
struct S<int> {};
```
