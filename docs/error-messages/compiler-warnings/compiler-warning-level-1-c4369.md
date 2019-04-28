---
title: 編譯器警告 (層級 1) C4369
ms.date: 11/04/2016
f1_keywords:
- C4369
helpviewer_keywords:
- C4369
ms.assetid: ade87e84-36be-4e00-be99-2930af848feb
ms.openlocfilehash: b374b67fa3319be35490358d7664bcb45bc640db
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62207026"
---
# <a name="compiler-warning-level-1-c4369"></a>編譯器警告 (層級 1) C4369

'列舉值': 無法為 'type' 表示列舉值 'value'，值為 'new_value'

列舉值來計算大於指定的基礎類型的最大值。  這會造成溢位和類型的最小可能值列舉值的編譯器包裝。

## <a name="example"></a>範例

下列範例會產生 C4369。

```
// C4369.cpp
// compile with: /W1
int main() {
   enum Color: char { red = 0x7e, green, blue };   // C4369
   enum Color2: char { red2 = 0x7d, green2, blue2};   // OK
}
```