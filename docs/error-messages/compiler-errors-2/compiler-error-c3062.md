---
title: 編譯器錯誤 C3062
ms.date: 11/04/2016
f1_keywords:
- C3062
helpviewer_keywords:
- C3062
ms.assetid: 78632e6d-255f-42c3-b124-31a9194ff86d
ms.openlocfilehash: 9b1fbc8f4ca2ce3434a30e833f4741bc17015bbb
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74749525"
---
# <a name="compiler-error-c3062"></a>編譯器錯誤 C3062

' enum '：枚舉器需要值，因為基礎類型是 ' type '

您可以指定列舉的基礎類型。 不過，某些類型會要求您將值指派給每個枚舉器。

如需有關列舉的詳細資訊，請參閱[enum 類別](../../extensions/enum-class-cpp-component-extensions.md)。

下列範例會產生 C3062：

```cpp
// C3062.cpp
// compile with: /clr

enum class MyEnum : bool { a };   // C3062
enum class MyEnum2 : bool { a = true};   // OK
```
