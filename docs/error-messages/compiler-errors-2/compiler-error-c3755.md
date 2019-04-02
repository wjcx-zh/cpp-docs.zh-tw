---
title: 編譯器錯誤 C3755
ms.date: 11/04/2016
f1_keywords:
- C3755
helpviewer_keywords:
- C3755
ms.assetid: 9317b55e-a52e-4b87-b915-5a208d6eda38
ms.openlocfilehash: 5d1260138bfdbc318817c336077eef326b62f8b8
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58767427"
---
# <a name="compiler-error-c3755"></a>編譯器錯誤 C3755

'delegate': 不可定義委派

A[委派 （c + + 元件延伸模組）](../../extensions/delegate-cpp-component-extensions.md)可以宣告但未定義。

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