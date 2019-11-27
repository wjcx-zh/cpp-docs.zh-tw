---
title: 編譯器警告 (層級 3) C4570
ms.date: 11/04/2016
f1_keywords:
- C4570
helpviewer_keywords:
- C4570
ms.assetid: feec1225-e6ad-4995-8d96-c22e864a77bd
ms.openlocfilehash: fd144847ce6c4f8697cd866d304c23cb9b2be408
ms.sourcegitcommit: 217fac22604639ebd62d366a69e6071ad5b724ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/19/2019
ms.locfileid: "74188882"
---
# <a name="compiler-warning-level-3-c4570"></a>編譯器警告 (層級 3) C4570

' type '：未明確宣告為抽象，但有抽象函數

包含[抽象](../../extensions/abstract-cpp-component-extensions.md)函數的類型本身應該標記為抽象。

## <a name="example"></a>範例

下列範例會產生 C4570。

```cpp
// C4570.cpp
// compile with: /clr /W3 /c
ref struct X {   // C4570
// try the following line instead
// ref class X abstract {
   virtual void f() abstract;
};
```