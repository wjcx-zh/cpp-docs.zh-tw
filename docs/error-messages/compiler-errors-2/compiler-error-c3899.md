---
title: 編譯器錯誤 C3899
ms.date: 11/04/2016
f1_keywords:
- C3899
helpviewer_keywords:
- C3899
ms.assetid: 14e07e4a-f7a7-4309-baaa-649d69e12e23
ms.openlocfilehash: 022bc1a37f7d9cfdb2c206592dd303a9c3c95080
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74749109"
---
# <a name="compiler-error-c3899"></a>編譯器錯誤 C3899

' var '：不允許直接在類別 ' class ' 的平列區域內使用 initonly 資料成員的左值

[Initonly （C++/cli）](../../dotnet/initonly-cpp-cli.md)資料成員無法在[平行](../../parallel/openmp/reference/parallel.md)區域中的函式的該部分內初始化。  這是因為編譯器會執行該程式碼的內部重新配置，因此它實際上不再是此函式的一部分。

若要解決此問題，請在函式中初始化 initonly 資料成員，但在平列區域之外。

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
