---
title: 編譯器錯誤 C3062
ms.date: 11/04/2016
f1_keywords:
- C3062
helpviewer_keywords:
- C3062
ms.assetid: 78632e6d-255f-42c3-b124-31a9194ff86d
ms.openlocfilehash: ac45847c94e7d2dc731eba71b0a38105eb915e53
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50590407"
---
# <a name="compiler-error-c3062"></a>編譯器錯誤 C3062

'enum': 列舉值需要值，因為基礎類型是 'type'

您可以指定列舉的基礎型別。 不過，某些類型需要您將值指派給每個列舉值。

如需有關列舉的詳細資訊，請參閱[列舉類別](../../windows/enum-class-cpp-component-extensions.md)。

下列範例會產生 C3062:

```
// C3062.cpp
// compile with: /clr

enum class MyEnum : bool { a };   // C3062
enum class MyEnum2 : bool { a = true};   // OK
```