---
title: 編譯器錯誤 C2232 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2232
dev_langs:
- C++
helpviewer_keywords:
- C2232
ms.assetid: 76f302b7-30a7-4a81-9a39-b4edde33b54c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c0e7c20de3de097fc09b80459e96158282ef7bba
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46026045"
---
# <a name="compiler-error-c2232"></a>編譯器錯誤 C2232

'->': 左的運算元有 'class 索引鍵 ' 類型，使用' '

`->` 運算子左邊的運算元不是指標。 使用句號 （.） 運算子的類別、 結構或等位。

下列範例會產生 C2232：

```
// C2232.c
struct X {
    int member;
} x, *px;
int main() {
    x->member = 0;   // C2232, x is not a pointer

    px->member = 0;
    x.member = 0;
}
```