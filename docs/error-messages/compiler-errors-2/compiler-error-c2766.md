---
title: 編譯器錯誤 C2766 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2766
dev_langs:
- C++
helpviewer_keywords:
- C2766
ms.assetid: 8032f4ca-6827-4f04-9c61-c44643c85cc4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ee59a8ebc0de3c539d1c9b775dcf06525b1a77fa
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46051525"
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