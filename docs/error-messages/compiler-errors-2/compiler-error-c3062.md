---
title: 編譯器錯誤 C3062
ms.date: 11/04/2016
f1_keywords:
- C3062
helpviewer_keywords:
- C3062
ms.assetid: 78632e6d-255f-42c3-b124-31a9194ff86d
ms.openlocfilehash: 6f4157db4a2a1b1864446a082deddc73df2e2fe9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406791"
---
# <a name="compiler-error-c3062"></a>編譯器錯誤 C3062

'enum': 列舉值需要值，因為基礎類型是 'type'

您可以指定列舉的基礎型別。 不過，某些類型需要您將值指派給每個列舉值。

如需有關列舉的詳細資訊，請參閱[列舉類別](../../extensions/enum-class-cpp-component-extensions.md)。

下列範例會產生 C3062:

```
// C3062.cpp
// compile with: /clr

enum class MyEnum : bool { a };   // C3062
enum class MyEnum2 : bool { a = true};   // OK
```