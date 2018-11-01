---
title: 編譯器錯誤 C2500
ms.date: 11/04/2016
f1_keywords:
- C2500
helpviewer_keywords:
- C2500
ms.assetid: 6bff8161-dc9a-48ca-91f1-fd2eefdbbc93
ms.openlocfilehash: a5753fc99efcdb1064a21981c62faaba84d44189
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50468363"
---
# <a name="compiler-error-c2500"></a>編譯器錯誤 C2500

'identifier1': 已直接基底類別 'identifier2'。

類別或結構會出現在清單中的基底類別的一次以上。

直接基底可以是其中一個基底清單中所述。 間接基底是其中一個基底清單中的類別的基底類別。

類別不能指定直接基底類別為一次以上。 類別可用來當做間接基底類別一次以上。

下列範例會產生 C2500:

```
// C2500.cpp
// compile with: /c
class A {};
class B : public A, public A {};    // C2500

// OK
class C : public A {};
class D : public A {};
class E : public C, public D {};
```