---
title: 編譯器警告 (層級 3) C4570
ms.date: 11/04/2016
f1_keywords:
- C4570
helpviewer_keywords:
- C4570
ms.assetid: feec1225-e6ad-4995-8d96-c22e864a77bd
ms.openlocfilehash: 1c92bd7f632ea6662c3cee1bcaa1dd0c917fb2a1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50661301"
---
# <a name="compiler-warning-level-3-c4570"></a>編譯器警告 (層級 3) C4570

'type': 未明確宣告為抽象，但是擁有抽象函式

包含的類型[抽象](../../windows/abstract-cpp-component-extensions.md)函式應該本身標示為抽象。

## <a name="example"></a>範例

下列範例會產生 C4570。

```
// C4570.cpp
// compile with: /clr /W3 /c
ref struct X {   // C4570
// try the following line instead
// ref class X abstract {
   virtual void f() abstract;
};
```