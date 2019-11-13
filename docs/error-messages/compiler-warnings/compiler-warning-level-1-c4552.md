---
title: 編譯器警告（層級1） C4552
ms.date: 11/04/2016
f1_keywords:
- C4552
helpviewer_keywords:
- C4552
ms.assetid: ebbbb5ee-1c19-45bd-b386-41a19630fc76
ms.openlocfilehash: b9f7fcd5a1949082aad75407f230db2e32dddd67
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966349"
---
# <a name="compiler-warning-level-1-c4552"></a>編譯器警告（層級1） C4552

' operator '：運算子沒有作用;具有副作用的預期運算子

如果運算式語句的運算子沒有任何副作用做為運算式的頂端，可能就會發生錯誤。

若要覆寫這個警告，請將運算式放在括弧中。

下列範例會產生 C4552：

```cpp
// C4552.cpp
// compile with: /W1
int main() {
   int i, j;
   i + j;   // C4552
   // try the following line instead
   // (i + j);
}
```