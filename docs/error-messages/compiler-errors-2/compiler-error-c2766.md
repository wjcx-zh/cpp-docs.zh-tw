---
title: 編譯器錯誤 C2766
ms.date: 11/04/2016
f1_keywords:
- C2766
helpviewer_keywords:
- C2766
ms.assetid: 8032f4ca-6827-4f04-9c61-c44643c85cc4
ms.openlocfilehash: 87ea9f693265080d744746c6a8014b2b8b6db13a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50446485"
---
# <a name="compiler-error-c2766"></a>編譯器錯誤 C2766

明確特製化;'specialization' 已經定義

不允許重複的明確特製化。 如需詳細資訊，請參閱 <<c0> [ 明確樣板的特製化函式](../../cpp/explicit-specialization-of-function-templates.md)。

下列範例會產生 C2766:

```
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