---
title: 編譯器警告 (層級 4) C4937
ms.date: 11/04/2016
f1_keywords:
- C4937
helpviewer_keywords:
- C4937
ms.assetid: 2bb9f0e7-bbd6-4697-84de-95955e32ae29
ms.openlocfilehash: dd7a7f9ac3d0ce0798a88f753cb0ccb4addbd5bc
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988750"
---
# <a name="compiler-warning-level-4-c4937"></a>編譯器警告 (層級 4) C4937

難以辨別 'text1' 和 'text2' 是否為 'directive' 的引數

因為編譯器處理指示詞引數的方式，無法辨別對編譯器有意義的名稱，例如有多種文字涵義的關鍵字 (單和雙底線格式)。

這類字串的範例 __cdecl 和 \__forceinline。  請注意，/Za 中只會啟用雙底線格式。

下列範例會產生 C4937：

```cpp
// C4937.cpp
// compile with: /openmp /W4
#include "omp.h"
int main() {
   #pragma omp critical ( __leave )   // C4937
   ;

   // OK
   #pragma omp critical ( leave )
   ;
}
```
