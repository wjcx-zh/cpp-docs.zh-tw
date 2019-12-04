---
title: 編譯器錯誤 C2500
ms.date: 11/04/2016
f1_keywords:
- C2500
helpviewer_keywords:
- C2500
ms.assetid: 6bff8161-dc9a-48ca-91f1-fd2eefdbbc93
ms.openlocfilehash: 152546fce8f3ee63f8b95595bff052f18cd4ebda
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74746964"
---
# <a name="compiler-error-c2500"></a>編譯器錯誤 C2500

' identifier1 '： ' identifier2 ' 已經是直接基類

類別或結構在基類清單中出現一次以上。

「直接基底」是基底清單中所述的一個。 間接基底是基底清單中其中一個類別的基類。

無法將類別指定為直接基類多次。 類別可以做為間接基類多次使用。

下列範例會產生 C2500：

```cpp
// C2500.cpp
// compile with: /c
class A {};
class B : public A, public A {};    // C2500

// OK
class C : public A {};
class D : public A {};
class E : public C, public D {};
```
