---
title: 編譯器錯誤 C3037
ms.date: 11/04/2016
f1_keywords:
- C3037
helpviewer_keywords:
- C3037
ms.assetid: 9ba8a890-d3c7-4cce-93c5-d358e2bfad28
ms.openlocfilehash: a022cfe6057f9ea518664090b5842faf4e822cb5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62350201"
---
# <a name="compiler-error-c3037"></a>編譯器錯誤 C3037

'var': 'reduction' 子句中的變數在封入內容中必須為共用

[reduction](../../parallel/openmp/reference/reduction.md) 子句中指定的變數，對內容中的每個執行緒而言可能都不是私用。

下列範例會產生 C3037：

```
// C3037.cpp
// compile with: /openmp /c
int g_i;

int main() {
   int i;

   #pragma omp parallel private(g_i)
   // try the following line instead
   // #pragma omp parallel
   {
      #pragma omp for reduction(+:g_i)   // C3037
      for (i = 0 ; i < 10 ; ++i) {
         g_i += i;
      }
   }
}
```