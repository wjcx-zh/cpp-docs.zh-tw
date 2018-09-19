---
title: 編譯器錯誤 C2250 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2250
dev_langs:
- C++
helpviewer_keywords:
- C2250
ms.assetid: f990986f-5c7d-4af4-a25c-b35540f1e217
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bee638b3e716460f54def3dc347810c874706708
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46070128"
---
# <a name="compiler-error-c2250"></a>編譯器錯誤 C2250

'identifier': 模稜兩可的 'class::member' 的繼承

在衍生的類別繼承虛擬基底類別虛擬函式的多個覆的寫。 這些覆寫會模稜兩可的衍生類別中。

下列範例會產生 C2286：

```
// C2250.cpp
// compile with: /c
// C2250 expected
struct V {
   virtual void vf();
};

struct A : virtual V {
   void vf();
};

struct B : virtual V {
   void vf();
};

struct D : A, B {
   // Uncomment the following line to resolve.
   // void vf();
};
```