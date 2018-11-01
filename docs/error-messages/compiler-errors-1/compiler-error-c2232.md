---
title: 編譯器錯誤 C2232
ms.date: 11/04/2016
f1_keywords:
- C2232
helpviewer_keywords:
- C2232
ms.assetid: 76f302b7-30a7-4a81-9a39-b4edde33b54c
ms.openlocfilehash: f1478c2d06ab535a532b1be45c2db69050afe7b4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50665383"
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