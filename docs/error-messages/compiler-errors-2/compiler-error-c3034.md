---
title: 編譯器錯誤 C3034 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3034
dev_langs:
- C++
helpviewer_keywords:
- C3034
ms.assetid: 49db8bac-2720-4622-94e3-7988f1603fa3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6e3d96e975450241a5baae60758beadfe40dbe5e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46091454"
---
# <a name="compiler-error-c3034"></a>編譯器錯誤 C3034

OpenMP 'directive1' 指示詞不能直接以巢狀方式置於 'directive2' 指示詞中

部分指示詞不可以是巢狀。 若要修正這個錯誤，您可以將這兩個指示詞的陳述式合併成一個指示詞的區塊，也可以建構連續性指示詞。

下列範例會產生 C3034：

```
// C3034.cpp
// compile with: /openmp /link vcomps.lib
int main() {

   #pragma omp single
   {
      #pragma omp single   // C3034
      {
      ;
      }
   }

   // Two consecutive single clauses are OK.
   #pragma omp single
   {
   }

   #pragma omp single
   {
   }
}
```