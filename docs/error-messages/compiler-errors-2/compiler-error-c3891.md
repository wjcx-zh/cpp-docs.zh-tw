---
title: 編譯器錯誤 C3891
ms.date: 11/04/2016
f1_keywords:
- C3891
helpviewer_keywords:
- C3891
ms.assetid: 6e1a9458-97f5-4580-bc0f-aa97a1bfd20d
ms.openlocfilehash: 67d12984a32998c244bcd04f99a5f2200a192974
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50524562"
---
# <a name="compiler-error-c3891"></a>編譯器錯誤 C3891

'var': 常值資料成員不能做為左值

A[常值](../../windows/literal-cpp-component-extensions.md)變數是常數，而且無法變更其值，在初始化之後，在宣告中。

下列範例會產生 C3891:

```
// C3891.cpp
// compile with: /clr
ref struct Y1 {
   literal int staticConst = 9;
};

int main() {
   Y1::staticConst = 0;   // C3891
}
```