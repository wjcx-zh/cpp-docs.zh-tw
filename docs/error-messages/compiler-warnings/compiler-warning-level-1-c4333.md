---
title: 編譯器警告 (層級 1) C4333
ms.date: 11/04/2016
f1_keywords:
- C4333
helpviewer_keywords:
- C4333
ms.assetid: d3763c52-6110-4da0-84db-5264e3f3f166
ms.openlocfilehash: b0f87b5d839dcfbb577af567a1a51a95daf716f0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50557348"
---
# <a name="compiler-warning-level-1-c4333"></a>編譯器警告 (層級 1) C4333

'operator': 向右位移量太大，資料遺失

向右移位作業已量太大。  所有重要的位元移位出，而且結果一律為零。

## <a name="example"></a>範例

下列範例會產生 C4333。

```
// C4333.cpp
// compile with: /c /W1
unsigned shift8 (unsigned char c) {
   return c >> 8;   // C4333

   // try the following line instead
   // return c >> 4;   // OK
}
```