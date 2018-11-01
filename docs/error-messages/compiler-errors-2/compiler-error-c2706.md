---
title: 編譯器錯誤 C2706
ms.date: 11/04/2016
f1_keywords:
- C2706
helpviewer_keywords:
- C2706
ms.assetid: e18da924-c42d-4b09-8e29-f4e0382d7dc6
ms.openlocfilehash: 9767d36d44b99423d600d299d0803901d3dbfec5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50472506"
---
# <a name="compiler-error-c2706"></a>編譯器錯誤 C2706

不合法的 __except 沒有相符\__finally (遺漏 '}' 中\__finally 區塊？)

編譯器找不到的右大括號`__try`區塊。

下列範例會產生 C2706:

```
// C2706.cpp
int main() {
   __try {
      void f();
   // C2706  } missing here
   __except(GetExceptionCode() == 0x0) {
   }
}
```