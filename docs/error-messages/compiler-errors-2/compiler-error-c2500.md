---
title: 編譯器錯誤 C2500 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2500
dev_langs:
- C++
helpviewer_keywords:
- C2500
ms.assetid: 6bff8161-dc9a-48ca-91f1-fd2eefdbbc93
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9b7e24ca520796b63171fe63c2bf841fe8776845
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46026669"
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