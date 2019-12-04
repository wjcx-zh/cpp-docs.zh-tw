---
title: 編譯器錯誤 C2897
ms.date: 11/04/2016
f1_keywords:
- C2897
helpviewer_keywords:
- C2897
ms.assetid: a88349e2-823f-42a0-8660-0653b677afa4
ms.openlocfilehash: 1433faade0a41ad8b63a3b40cb5d02f724bde658
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760770"
---
# <a name="compiler-error-c2897"></a>編譯器錯誤 C2897

析構函數/完成項不能是函式樣板

無法多載析構函數或完成項，因此不允許將析構函式宣告為範本（這會定義一組析構函數）。

下列範例會產生 C2897：

## <a name="example"></a>範例

下列範例會產生 C2897。

```cpp
// C2897.cpp
// compile with: /c
class X {
public:
   template<typename T> ~X() {}   // C2897
};
```

## <a name="example"></a>範例

下列範例會產生 C2897。

```cpp
// C2897_b.cpp
// compile with: /c /clr
ref struct R2 {
protected:
   template<typename T> !R2(){}   // C2897 error
};
```
