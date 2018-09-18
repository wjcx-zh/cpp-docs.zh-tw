---
title: 編譯器錯誤 C2231 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2231
dev_langs:
- C++
helpviewer_keywords:
- C2231
ms.assetid: 677c5c66-d30f-4c3b-bbb9-760858d56477
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cd6cd35d20f4ce0377aa5ae5cd66cd8c08004fb8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46021666"
---
# <a name="compiler-error-c2231"></a>編譯器錯誤 C2231

'。 ': 左運算元指向 ' 類別索引鍵 '，請使用 '->'

成員選取運算子 （.） 左邊的運算元是而不是類別、 結構或等位的指標。

下列範例會產生 C2231：

```
// C2231.c
struct S {
   int member;
} s, *ps = &s;
int main() {
   ps.member = 0;   // C2231

   // OK
   ps->member = 0;   // crash
   s.member = 0;
}
```