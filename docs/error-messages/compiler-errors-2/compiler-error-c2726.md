---
title: 編譯器錯誤 C2726
ms.date: 11/04/2016
f1_keywords:
- C2726
helpviewer_keywords:
- C2726
ms.assetid: f0191bb7-c175-450b-bf09-a3213db96d09
ms.openlocfilehash: d0ade9317c996bb3432e7a4626fc930a3d5df349
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50575639"
---
# <a name="compiler-error-c2726"></a>編譯器錯誤 C2726

'gcnew' 只可用來建立具有 Managed 或 WinRT 類型的物件

您無法在記憶體回收堆積上建立原生類型的執行個體。

下列範例會產生 C2726，並說明如何加以修正：

```
// C2726.cpp
// compile with: /clr
using namespace System;
class U {};
ref class V {};
value class W {};

int main() {
   U* pU = gcnew U;    // C2726
   U* pU2 = new U;   // OK
   V^ p2 = gcnew V;   // OK
   W p3;   // OK

}
```
