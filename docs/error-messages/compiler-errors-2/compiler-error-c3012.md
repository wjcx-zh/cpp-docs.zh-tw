---
title: 編譯器錯誤 C3012
ms.date: 11/04/2016
f1_keywords:
- C3012
helpviewer_keywords:
- C3012
ms.assetid: cc7040b1-b3fb-4da6-a474-877914d30332
ms.openlocfilehash: 9fe0ac7d3637cad3a5571c4631345dac1a0021bb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50503077"
---
# <a name="compiler-error-c3012"></a>編譯器錯誤 C3012

> '*內建*': 不允許直接放在平行區域內的內建函式

[](../../intrinsics/compiler-intrinsics.md) 區域中不允許 `omp parallel` 函式。 若要修正此問題，將內建函式移出區域，或取代非內建的對等項目。

## <a name="example"></a>範例

下列範例會產生 C3012，並示範修正此問題的一種方法：

```cpp
// C3012.cpp
// compile with: /openmp
#ifdef __cplusplus
extern "C" {
#endif
void* _ReturnAddress();
#ifdef __cplusplus
}
#endif

int main()
{
   #pragma omp parallel
   {
      _ReturnAddress();   // C3012
   }
   _ReturnAddress();      // OK
}
```