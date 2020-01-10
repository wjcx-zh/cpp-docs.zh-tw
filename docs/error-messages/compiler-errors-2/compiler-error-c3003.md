---
title: 編譯器錯誤 C3003
ms.date: 11/04/2016
f1_keywords:
- C3003
helpviewer_keywords:
- C3003
ms.assetid: 22e74f99-bb7f-4518-ab0d-934d5d49bcc7
ms.openlocfilehash: 2f7b645f0b76f500502faea86a9fe20bb8eb5a62
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75298892"
---
# <a name="compiler-error-c3003"></a>編譯器錯誤 C3003

'directive': OpenMP 指示詞名稱不能在指示詞子句後面

OpenMP 指示詞名稱不能在 OpenMP 指示詞子句後面。

下列範例會產生 C3003：

```c
// C3003.c
// compile with: /openmp
int main()
{
   int x, y, z;
   #pragma omp parallel shared(x, y, z) for   // C3003
}
```
