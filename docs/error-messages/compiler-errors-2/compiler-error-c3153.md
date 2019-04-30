---
title: 編譯器錯誤 C3153
ms.date: 11/04/2016
f1_keywords:
- C3153
helpviewer_keywords:
- C3153
ms.assetid: d775d97e-2480-484f-81f1-88406b10f947
ms.openlocfilehash: 62b9e7499c52153183f14eae47c488da6a59b458
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62374868"
---
# <a name="compiler-error-c3153"></a>編譯器錯誤 C3153

'interface': 您無法建立介面的執行個體

介面無法具現化。 若要使用的介面成員，衍生自介面類別、 實作介面成員，然後再使用的成員。

下列範例會產生 C3153:

```
// C3153.cpp
// compile with: /clr
interface class A {
};

int main() {
   A^ a = gcnew A;   // C3153
}
```
