---
title: 編譯器錯誤 C2045
ms.date: 11/04/2016
f1_keywords:
- C2045
helpviewer_keywords:
- C2045
ms.assetid: 2fca668e-9b20-4933-987a-18c0fd0187df
ms.openlocfilehash: 55eccbae84fb7f700c3ac9fdf6721d3f25582862
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50581879"
---
# <a name="compiler-error-c2045"></a>編譯器錯誤 C2045

'identifier': 已重新定義標籤

在相同的函式中，標籤會出現在多個陳述式之前。

下列範例會產生 C2045：

```
// C2045.cpp
int main() {
   label: {
   }
   goto label;
   label: {}   // C2045
}
```