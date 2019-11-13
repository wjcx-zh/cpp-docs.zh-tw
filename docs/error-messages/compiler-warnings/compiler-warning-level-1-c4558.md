---
title: 編譯器警告（層級1） C4558
ms.date: 11/04/2016
f1_keywords:
- C4558
helpviewer_keywords:
- C4558
ms.assetid: 52bb0324-7bec-468c-b35b-13a08d38e578
ms.openlocfilehash: d47e2a619cb84838144b3be6fd45d1f79ecc8661
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966007"
---
# <a name="compiler-warning-level-1-c4558"></a>編譯器警告（層級1） C4558

運算元 ' value ' 的值超出範圍 ' lowerbound-界 '

傳遞給元件語言指令的值超出為參數指定的範圍。 此值將會被截斷。

下列範例會產生 C4558：

```cpp
// C4558.cpp
// compile with: /W1
// processor: x86
void asm_test() {
   __asm pinsrw   mm1, eax, 8;   // C4558
}

int main() {
}
```