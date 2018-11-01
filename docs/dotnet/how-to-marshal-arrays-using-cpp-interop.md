---
title: 如何：使用 C++ Interop 封送處理陣列
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- arrays [C++], marshaling
- marshaling [C++], arrays
- interop [C++], arrays
- C++ Interop, arrays
- data marshaling [C++], arrays
ms.assetid: c2b37ab1-8acf-4855-ad3c-7d2864826b14
ms.openlocfilehash: 10cf89d0f14a072318e6b1ef743f386e6ba914cd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50441661"
---
# <a name="how-to-marshal-arrays-using-c-interop"></a>如何：使用 C++ Interop 封送處理陣列

本主題會示範一個 facet 的 Visual c + + 的互通性。 如需詳細資訊，請參閱 <<c0> [ 使用 c + + Interop (隱含 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)。

下列程式碼範例使用[managed、 unmanaged](../preprocessor/managed-unmanaged.md) #pragma 指示詞來實作 managed 和 unmanaged 函式在相同的檔案，但如果在不同的檔案中定義這些函式交互操作方式相同。 包含 unmanaged 的函式的檔案不需要進行編譯[/clr （Common Language Runtime 編譯）](../build/reference/clr-common-language-runtime-compilation.md)。

## <a name="example"></a>範例

下列範例示範如何將 managed 的陣列傳遞至 unmanaged 函式。 受管理的函式會使用[pin_ptr (C + + /cli CLI)](../windows/pin-ptr-cpp-cli.md)隱藏記憶體回收陣列呼叫 unmanaged 函式之前。 藉由提供使用 pin 指標的 unmanaged 函式，GC 堆積，您可以避免建立陣列的複本的額外負荷。 若要示範 unmanaged 函式會存取 GC 堆積記憶體，它會修改陣列的內容與所做的變更會反映當 managed 函式會繼續控制。

```
// PassArray1.cpp
// compile with: /clr
#ifndef _CRT_RAND_S
#define _CRT_RAND_S
#endif

#include <iostream>
#include <stdlib.h>
using namespace std;

using namespace System;

#pragma unmanaged

void TakesAnArray(int* a, int c) {
   cout << "(unmanaged) array received:\n";
   for (int i=0; i<c; i++)
      cout << "a[" << i << "] = " << a[i] << "\n";

   unsigned int number;
   errno_t err;

   cout << "(unmanaged) modifying array contents...\n";
   for (int i=0; i<c; i++) {
      err = rand_s( &number );
      if ( err == 0 )
         a[i] = number % 100;
   }
}

#pragma managed

int main() {
   array<int>^ nums = gcnew array<int>(5);

   nums[0] = 0;
   nums[1] = 1;
   nums[2] = 2;
   nums[3] = 3;
   nums[4] = 4;

   Console::WriteLine("(managed) array created:");
   for (int i=0; i<5; i++)
      Console::WriteLine("a[{0}] = {1}", i, nums[i]);

   pin_ptr<int> pp = &nums[0];
   TakesAnArray(pp, 5);

   Console::WriteLine("(managed) contents:");
   for (int i=0; i<5; i++)
      Console::WriteLine("a[{0}] = {1}", i, nums[i]);
}
```

## <a name="example"></a>範例

下列範例示範如何將未受管理的陣列傳遞至 managed 函式。 Managed 函式會存取陣列的記憶體直接 （而不是建立 managed 的陣列，並複製的陣列內容），可讓 managed 函式所做變更才能重新取得控制項時，會反映在 unmanaged 函式。

```
// PassArray2.cpp
// compile with: /clr
#include <iostream>
using namespace std;

using namespace System;

#pragma managed

void ManagedTakesAnArray(int* a, int c) {
   Console::WriteLine("(managed) array received:");
   for (int i=0; i<c; i++)
      Console::WriteLine("a[{0}] = {1}", i, a[i]);

   cout << "(managed) modifying array contents...\n";
   Random^ r = gcnew Random(DateTime::Now.Second);
   for (int i=0; i<c; i++)
      a[i] = r->Next(100);
}

#pragma unmanaged

void NativeFunc() {
   int nums[5] = { 0, 1, 2, 3, 4 };

   printf_s("(unmanaged) array created:\n");
   for (int i=0; i<5; i++)
      printf_s("a[%d] = %d\n", i, nums[i]);

   ManagedTakesAnArray(nums, 5);

   printf_s("(ummanaged) contents:\n");
   for (int i=0; i<5; i++)
      printf_s("a[%d] = %d\n", i, nums[i]);
}

#pragma managed

int main() {
   NativeFunc();
}
```

## <a name="see-also"></a>另請參閱

[使用 C++ Interop (隱含 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)