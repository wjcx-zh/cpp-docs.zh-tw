---
title: 編譯器錯誤 C2071
ms.date: 11/04/2016
f1_keywords:
- C2071
helpviewer_keywords:
- C2071
ms.assetid: f8c09255-a5c4-47e3-8089-3d875ae43cc5
ms.openlocfilehash: cd815bf90b135f65072a56911c7c4b0f054fcfec
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87210068"
---
# <a name="compiler-error-c2071"></a>編譯器錯誤 C2071

'identifier'：儲存類別不合法

`identifier`以不正確[儲存類別](../../c-language/c-storage-classes.md)宣告。 當指定了一個以上的儲存類別給識別項，或是定義與儲存類別宣告不相容時，可能會造成這個錯誤。

若要修正此問題，請瞭解識別碼的預定儲存類別，例如或， **`static`** **`extern`** 並更正宣告以符合。

## <a name="example"></a>範例

下列範例會產生 C2071。

```cpp
// C2071.cpp
// compile with: /c
struct C {
   extern int i;   // C2071
};
struct D {
   int i;   // OK, no extern on an automatic
};
```

## <a name="example"></a>範例

下列範例會產生 C2071。

```cpp
// C2071_b.cpp
// compile with: /c
typedef int x(int i) { return i; }   // C2071
typedef int (x)(int);   // OK, no local definition in typedef
```
