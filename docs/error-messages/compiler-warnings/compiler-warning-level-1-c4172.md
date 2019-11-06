---
title: 編譯器警告（層級1） C4172
ms.date: 11/04/2016
f1_keywords:
- C4172
helpviewer_keywords:
- C4172
ms.assetid: a8d2bf65-d8b1-4fe3-8340-a223d7e7fde6
ms.openlocfilehash: 7d53972dbcb2e3ab6a95b0b874cc6bb98cd66840
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2019
ms.locfileid: "73624819"
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