---
title: 編譯器錯誤 C2765
ms.date: 11/04/2016
f1_keywords:
- C2765
helpviewer_keywords:
- C2765
ms.assetid: 47ad86f3-a7e0-47ad-85ff-0f5534458cb9
ms.openlocfilehash: 7b34bd8b352e8872722e9402d8d0113ae6157292
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62257643"
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