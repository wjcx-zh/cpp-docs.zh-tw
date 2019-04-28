---
title: 編譯器錯誤 C2071
ms.date: 11/04/2016
f1_keywords:
- C2071
helpviewer_keywords:
- C2071
ms.assetid: f8c09255-a5c4-47e3-8089-3d875ae43cc5
ms.openlocfilehash: 95344b5ef675f566f433dfeaed9dee5c38ef77d4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62303343"
---
# <a name="compiler-error-c2071"></a>編譯器錯誤 C2071

'identifier'：儲存類別不合法

`identifier` 已宣告為無效[儲存類別](../../c-language/c-storage-classes.md)。 當指定了一個以上的儲存類別給識別項，或是定義與儲存類別宣告不相容時，可能會造成這個錯誤。

若要修正此問題，了解識別項的預定的儲存類別，例如`static`或`extern`— 並更正宣告以符合。

## <a name="example"></a>範例

下列範例會產生 C2071。

```
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

```
// C2071_b.cpp
// compile with: /c
typedef int x(int i) { return i; }   // C2071
typedef int (x)(int);   // OK, no local definition in typedef
```