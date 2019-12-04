---
title: 編譯器錯誤 C2768
ms.date: 11/04/2016
f1_keywords:
- C2768
helpviewer_keywords:
- C2768
ms.assetid: a7f6047a-6a80-4737-ad5c-c12868639fb5
ms.openlocfilehash: bcc801bb5802598e936d577f08729214bb7e13a1
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759785"
---
# <a name="compiler-error-c2768"></a>編譯器錯誤 C2768

' function '：明確樣板引數的使用不合法

編譯器無法判斷函式定義是否應該是函式樣板的明確特製化，或者，如果函式定義應該是用於新函數，則為。

此錯誤是在 Visual Studio .NET 2003 中引進，做為編譯器一致性增強功能的一部分。

下列範例會產生 C2768：

```cpp
// C2768.cpp
template<typename T>
void f(T) {}

void f<int>(int) {}   // C2768

// an explicit specialization
template<>
void f<int>(int) {}

// global nontemplate function overload
void f(int) {}
```
