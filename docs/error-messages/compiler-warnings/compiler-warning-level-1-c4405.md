---
title: 編譯器警告（層級1） C4405
ms.date: 11/04/2016
f1_keywords:
- C4405
helpviewer_keywords:
- C4405
ms.assetid: 155c64d6-58ae-4455-b61f-ccd711c5da96
ms.openlocfilehash: 182f9ff061fd2a8ebe5ea0046545412fca5f646a
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73965579"
---
# <a name="compiler-warning-level-1-c4405"></a>編譯器警告（層級1） C4405

' identifier '：識別碼是保留字

保留給內嵌組解碼的字會當做變數名稱使用。 這可能會導致無法預期的結果。 若要修正這個警告，請避免使用保留給內嵌組解碼的字組來命名變數。 下列範例會產生 C4405：

```cpp
// C4405.cpp
// compile with: /W1
// processor: x86
void func1() {
   int mov = 0, i = 0;
   _asm {
      mov mov, 0;   // C4405
      // instead, try ..
      // mov i, 0;
   }
}

int main() {
}
```