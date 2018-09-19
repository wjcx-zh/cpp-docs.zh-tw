---
title: 編譯器錯誤 C2765 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2765
dev_langs:
- C++
helpviewer_keywords:
- C2765
ms.assetid: 47ad86f3-a7e0-47ad-85ff-0f5534458cb9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 708a4c326e87cf580208e26ef5ffe540afd52f95
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46085130"
---
# <a name="compiler-error-c2765"></a>編譯器錯誤 C2765

'function': 函式樣板的明確特製化不能有任何預設引數

在函式樣板的明確特製化上不允許預設引數。 如需詳細資訊，請參閱 <<c0> [ 明確樣板的特製化函式](../../cpp/explicit-specialization-of-function-templates.md)。

下列範例會產生 C2765:

```
// C2765.cpp
template<class T> void f(T t) {};

template<> void f<char>(char c = 'a') {}   // C2765
// try the following line instead
// template<> void f<char>(char c) {}
```