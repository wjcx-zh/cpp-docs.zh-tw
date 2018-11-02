---
title: 編譯器錯誤 C3892
ms.date: 11/04/2016
f1_keywords:
- C3892
helpviewer_keywords:
- C3892
ms.assetid: 83fff42c-ea48-442f-bc2e-b33a6b99d890
ms.openlocfilehash: 07f34efa4ecf1445665fccf60dba10ea12dbff3f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50468662"
---
# <a name="compiler-error-c3892"></a>編譯器錯誤 C3892

'var': 您無法指派給為 const 變數

它會宣告並初始化之後，就無法變更 const 變數。

下列範例會產生 C3892:

```
// C3892.cpp
// compile with: /clr
ref struct Y1 {
   static const int staticConst = 9;
};

int main() {
   Y1::staticConst = 0;   // C3892
}
```