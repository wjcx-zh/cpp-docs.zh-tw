---
title: 編譯器錯誤 C3755
ms.date: 11/04/2016
f1_keywords:
- C3755
helpviewer_keywords:
- C3755
ms.assetid: 9317b55e-a52e-4b87-b915-5a208d6eda38
ms.openlocfilehash: 0150693ae84b45dc62c11cfdc59369eb25a819cd
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757276"
---
# <a name="compiler-error-c3755"></a>編譯器錯誤 C3755

' delegate '：委派可能未定義

[委派（C++元件延伸模組）](../../extensions/delegate-cpp-component-extensions.md)可以宣告但不能定義。

## <a name="example"></a>範例

下列範例會產生 C3755。

```cpp
// C3755.cpp
// compile with: /clr /c
delegate void MyDel() {};   // C3755
```

## <a name="example"></a>範例

如果您嘗試建立委派範本，也可能會發生 C3755。 下列範例會產生 C3755。

```cpp
// C3755_b.cpp
// compile with: /clr /c
ref struct R {
   template<class T>
   delegate void D(int) {}   // C3755
};
```
