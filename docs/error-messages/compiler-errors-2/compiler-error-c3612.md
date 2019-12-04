---
title: 編譯器錯誤 C3612
ms.date: 11/04/2016
f1_keywords:
- C3612
helpviewer_keywords:
- C3612
ms.assetid: aa6e3a2b-4afa-481c-98c1-1b6d1f82f869
ms.openlocfilehash: 499c31b0c02bd72695cd6118612609a70316f0ae
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755742"
---
# <a name="compiler-error-c3612"></a>編譯器錯誤 C3612

' type '：密封的類別不能是抽象的

根據預設，使用 `value` 所定義的類型會密封，而類別則是抽象的，除非它會執行其基底的所有方法。 密封的抽象類別不能是基類，也不能具現化。

如需詳細資訊，請參閱[類別與結構](../../extensions/classes-and-structs-cpp-component-extensions.md)。

## <a name="example"></a>範例

下列範例會產生 C3612：

```cpp
// C3612.cpp
// compile with: /clr /c
value struct V: public System::ICloneable {};   // C3612

// OK
value struct V2: public System::ICloneable {
   Object^ Clone();
};
```
