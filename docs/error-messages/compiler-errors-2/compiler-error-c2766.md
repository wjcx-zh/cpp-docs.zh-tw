---
title: 編譯器錯誤 C2766
ms.date: 11/04/2016
f1_keywords:
- C2766
helpviewer_keywords:
- C2766
ms.assetid: 8032f4ca-6827-4f04-9c61-c44643c85cc4
ms.openlocfilehash: 48faee02bba18754972954a2ca464417bd552758
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759798"
---
# <a name="compiler-error-c2766"></a>編譯器錯誤 C2766

明確特製化;' 特製化 ' 已經定義過了

不允許重複的明確特製化。 如需詳細資訊，請參閱函式樣板[的明確特製化](../../cpp/explicit-specialization-of-function-templates.md)。

下列範例會產生 C2766：

```cpp
// C2766.cpp
// compile with: /c
template<class T>
struct A {};

template<>
struct A<int> {};

template<>
struct A<int> {};   // C2766
// try the following line instead
// struct A<char> {};
```
