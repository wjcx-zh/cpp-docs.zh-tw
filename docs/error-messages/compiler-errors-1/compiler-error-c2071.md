---
title: 編譯器錯誤 C2071
ms.date: 11/04/2016
f1_keywords:
- C2071
helpviewer_keywords:
- C2071
ms.assetid: f8c09255-a5c4-47e3-8089-3d875ae43cc5
ms.openlocfilehash: 7619d968379bfc35e98bd87071b75296d10c382c
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743278"
---
# <a name="compiler-error-c2071"></a>編譯器錯誤 C2071

'identifier'：儲存類別不合法

`identifier` 宣告的 [儲存類別](../../c-language/c-storage-classes.md)無效。 當指定了一個以上的儲存類別給識別項，或是定義與儲存類別宣告不相容時，可能會造成這個錯誤。

若要修正此問題，請瞭解識別碼的預期儲存類別（例如 **`static`** 或）， **`extern`** 並更正要比對的宣告。

## <a name="examples"></a>範例

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

下列範例會產生 C2071。

```cpp
// C2071_b.cpp
// compile with: /c
typedef int x(int i) { return i; }   // C2071
typedef int (x)(int);   // OK, no local definition in typedef
```
