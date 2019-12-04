---
title: 編譯器錯誤 C3222
ms.date: 11/04/2016
f1_keywords:
- C3222
helpviewer_keywords:
- C3222
ms.assetid: 5624bde8-2fd0-4b8b-92ce-5dfbaf91cf93
ms.openlocfilehash: 96a6b1b81d2d82328dcb4ceaca376f247f785c13
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74737942"
---
# <a name="compiler-error-c3222"></a>編譯器錯誤 C3222

'parameter'：無法對 Managed 或 WinRT 類型或泛型函式的成員函式宣告預設引數

不允許宣告具有預設引數的方法參數。 方法的多載形式是解決這個問題的一種方法。 也就是說，定義不含參數的同名方法，然後在方法主體中初始化變數。

下列範例會產生 C3222：

```cpp
// C3222_2.cpp
// compile with: /clr
public ref class G {
   void f( int n = 0 );   // C3222
};
```
