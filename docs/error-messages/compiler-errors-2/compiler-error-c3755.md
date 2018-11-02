---
title: 編譯器錯誤 C3755
ms.date: 11/04/2016
f1_keywords:
- C3755
helpviewer_keywords:
- C3755
ms.assetid: 9317b55e-a52e-4b87-b915-5a208d6eda38
ms.openlocfilehash: 90dc3b7a0e1dbc4e0dc6c42ca722ca1db462fca9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50558206"
---
# <a name="compiler-error-c3755"></a>編譯器錯誤 C3755

'delegate': 不可定義委派

A[委派 （c + + 元件延伸模組）](../../windows/delegate-cpp-component-extensions.md)可以宣告但未定義。

## <a name="example"></a>範例

下列範例會產生 C3755。

```
// C3755.cpp
// compile with: /clr /c
delegate void MyDel() {};   // C3755
```

## <a name="example"></a>範例

如果您嘗試建立委派的範本，也會發生 C3755。 下列範例會產生 C3755。

```
// C3755_b.cpp
// compile with: /clr /c
ref struct R {
   template<class T>
   delegate void D(int) {}   // C3755
};
```