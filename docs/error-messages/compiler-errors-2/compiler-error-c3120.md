---
title: 編譯器錯誤 C3120
ms.date: 11/04/2016
f1_keywords:
- C3120
helpviewer_keywords:
- C3120
ms.assetid: 9b6b210f-9948-4517-a4cc-b4aaadebde68
ms.openlocfilehash: ced859be68f780d0f0dee31e31d80b994ee73404
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74740945"
---
# <a name="compiler-error-c3120"></a>編譯器錯誤 C3120

' method_name '：介面方法無法接受可變引數清單

介面方法不能接受可變的引數清單。 例如，下列介面定義會產生 C3120：

```cpp
// C3120.cpp
__interface A {
int X(int i, ...);    // C3120
};

int main(void) { return(0); }
```
