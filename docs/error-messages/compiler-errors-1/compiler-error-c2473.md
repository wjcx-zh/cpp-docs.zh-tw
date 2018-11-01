---
title: 編譯器錯誤 C2473
ms.date: 11/04/2016
f1_keywords:
- C2473
helpviewer_keywords:
- C2473
ms.assetid: 6bb7dbf5-b198-490f-860e-fd64d0c2a284
ms.openlocfilehash: 232f89a714d70c6914b73a370c5f658ff4283ab4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50631786"
---
# <a name="compiler-error-c2473"></a>編譯器錯誤 C2473

'identifier': 類似函式定義，但沒有型式參數清單。

編譯器偵測到與函式類似的項目，但沒有參數清單。

## <a name="example"></a>範例

下列範例會產生 C2473。

```
// C2473.cpp
// compile with: /clr /c
class A {
   int i {}   // C2473
};

class B {
   int i() {}   // OK
};
```