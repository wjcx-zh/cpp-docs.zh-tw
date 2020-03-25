---
title: 編譯器警告（層級1） C4172
ms.date: 11/04/2016
f1_keywords:
- C4172
helpviewer_keywords:
- C4172
ms.assetid: a8d2bf65-d8b1-4fe3-8340-a223d7e7fde6
ms.openlocfilehash: 7258172c00b1ff4aebb18fa2c715559fd82a2180
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163542"
---
# <a name="compiler-warning-level-1-c4172"></a>編譯器警告（層級1） C4172

傳回本機變數或暫存的位址

函式會傳回本機變數或暫存物件的位址。 當函式傳回時，會終結本機變數和暫存物件，因此傳回的位址無效。

重新設計函數，使其不會傳回本機物件的位址。

下列範例會產生 C4172：

```cpp
// C4172.cpp
// compile with: /W1 /LD
float f = 10;

const double& bar() {
// try the following line instead
// const float& bar() {
   return f;   // C4172
}
```
