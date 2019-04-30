---
title: 編譯器錯誤 C2231
ms.date: 11/04/2016
f1_keywords:
- C2231
helpviewer_keywords:
- C2231
ms.assetid: 677c5c66-d30f-4c3b-bbb9-760858d56477
ms.openlocfilehash: 0d6519bd12cdb5ee5a86fa4a6915b51b0dc59fc5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383304"
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