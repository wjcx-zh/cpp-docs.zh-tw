---
title: 編譯器錯誤 C3899
ms.date: 11/04/2016
f1_keywords:
- C3899
helpviewer_keywords:
- C3899
ms.assetid: 14e07e4a-f7a7-4309-baaa-649d69e12e23
ms.openlocfilehash: f3650d994e3102f71ab1d3598a4d1482f50b3334
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91510036"
---
# <a name="compiler-error-c3899"></a>編譯器錯誤 C3899

' var '： initonly 資料成員的左值使用不能直接在類別 ' class ' 的平列區域內使用

[Initonly (c + +/cli) ](../../dotnet/initonly-cpp-cli.md)資料成員無法在位於[平行](../../parallel/openmp/reference/openmp-directives.md#parallel)區域之函式的該部分內初始化。  這是因為編譯器會執行該程式碼的內部重新配置，因此它實際上不是此程式碼的一部分。

若要解決此問題，請初始化函式中的 initonly 資料成員，但在平列區域以外。

## <a name="example"></a>範例

下列範例會產生 C3899。

```cpp
// C3899.cpp
// compile with: /clr /openmp
#include <omp.h>

public ref struct R {
   initonly int x;
   R() {
      x = omp_get_thread_num() + 1000;   // OK
      #pragma omp parallel num_threads(5)
      {
         // cannot assign to 'x' here
         x = omp_get_thread_num() + 1000;   // C3899
         System::Console::WriteLine("thread {0}", omp_get_thread_num());
      }
      x = omp_get_thread_num() + 1000;   // OK
   }
};

int main() {
   R^ r = gcnew R;
   System::Console::WriteLine(r->x);
}
```
