---
title: 編譯器警告 （層級 1） C4369 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4369
dev_langs:
- C++
helpviewer_keywords:
- C4369
ms.assetid: ade87e84-36be-4e00-be99-2930af848feb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9c8b292717168f7f6ead676528a5b7769b7c8ec4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024147"
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