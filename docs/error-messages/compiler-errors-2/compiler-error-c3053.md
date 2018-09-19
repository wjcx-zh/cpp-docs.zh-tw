---
title: 編譯器錯誤 C3053 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3053
dev_langs:
- C++
helpviewer_keywords:
- C3053
ms.assetid: ab9a25f3-e341-4f6e-8e69-069b4a963a64
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c50112be2650c4b379b6de93acaa73a9cb285687
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46112027"
---
# <a name="compiler-error-c3053"></a>編譯器錯誤 C3053

'symbol': 'threadprivate' 只對全域或靜態資料項目有效

傳遞至 [threadprivate](../../parallel/openmp/reference/threadprivate.md) 的符號必須是全域或靜態的。

下列範例會產生 C3053：

```
// C3053.cpp
// compile with: /openmp
void Test() {
   int x, y;
   #pragma omp threadprivate(x, y)   // C3053
   #pragma omp parallel copyin(x, y)
   {
      x = y;
   }
}
```

可能的解決方式：

```
// C3053b.cpp
// compile with: /openmp /LD
int x, y;
#pragma omp threadprivate(x, y)

void Test() {
   #pragma omp parallel copyin(x, y)
   {
      x = y;
   }
}
```