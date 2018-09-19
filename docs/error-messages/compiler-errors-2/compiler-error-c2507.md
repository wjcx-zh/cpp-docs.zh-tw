---
title: 編譯器錯誤 C2507 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2507
dev_langs:
- C++
helpviewer_keywords:
- C2507
ms.assetid: f102aff5-de7d-4c3f-9cac-2ddf9ce02b14
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 16cc9c5f21618f3b681fbefbfadfd66b0219d5ac
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46022717"
---
# <a name="compiler-error-c2507"></a>編譯器錯誤 C2507

'identifier': 基底類別上的太多虛擬修飾詞

類別或結構宣告為`virtual`一次以上。 只有一個`virtual`修飾符可以出現在清單中每個類別的基底類別。

下列範例會產生 C2507:

```
// C2507.cpp
// compile with: /c
class A {};
class B : virtual virtual public A {};   // C2507
class C : virtual public A {};   // OK
```