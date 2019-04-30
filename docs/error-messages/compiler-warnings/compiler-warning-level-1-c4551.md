---
title: 編譯器警告 (層級 1) C4551
ms.date: 11/04/2016
f1_keywords:
- C4551
helpviewer_keywords:
- C4551
ms.assetid: 458b59bd-e2d7-425f-9ba6-268ff200424f
ms.openlocfilehash: 8a30ad5622d8e889a7f3ec64b73ead7c63f65b48
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397350"
---
# <a name="compiler-warning-level-1-c4551"></a>編譯器警告 (層級 1) C4551

函式呼叫遺漏引數清單

函式呼叫必須在函式名稱之後包含左右括弧，即使函式不接受任何參數。

下列範例會產生 C4551:

```
// C4551.cpp
// compile with: /W1
void function1() {
}

int main() {
   function1;   // C4551
   function1();   // OK
}
```