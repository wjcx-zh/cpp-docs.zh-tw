---
title: 編譯器錯誤 C2534
ms.date: 11/04/2016
f1_keywords:
- C2534
helpviewer_keywords:
- C2534
ms.assetid: 481f9f54-5b51-4aa0-8eea-218f10807705
ms.openlocfilehash: e684804ea31b16f31c82e244cb4f9a6aaf2d08c3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386963"
---
# <a name="compiler-error-c2534"></a>編譯器錯誤 C2534

'identifier': 建構函式無法傳回值

建構函式無法傳回值或具有傳回型別 (甚至`void`傳回型別)。

此錯誤可能會修正藉由移除`return`從建構函式定義的陳述式。

下列範例會產生 C2534:

```
// C2534.cpp
class A {
public:
   int i;
   A() { return i; }   // C2534
};
```