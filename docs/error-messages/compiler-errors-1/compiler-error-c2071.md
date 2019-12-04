---
title: 編譯器錯誤 C2071
ms.date: 11/04/2016
f1_keywords:
- C2071
helpviewer_keywords:
- C2071
ms.assetid: f8c09255-a5c4-47e3-8089-3d875ae43cc5
ms.openlocfilehash: 1dc9781bc0cf1bc6c7f879cc3971828983471c6f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757744"
---
# <a name="compiler-error-c2071"></a>編譯器錯誤 C2071

'identifier'：儲存類別不合法

已使用不正確[儲存類別](../../c-language/c-storage-classes.md)宣告 `identifier`。 當指定了一個以上的儲存類別給識別項，或是定義與儲存類別宣告不相容時，可能會造成這個錯誤。

若要修正此問題，請瞭解識別碼的預定儲存類別（例如 `static` 或 `extern`），並更正宣告以符合。

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
