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
ms.openlocfilehash: 0ccf71d40db0bc6989620d2ca126ce74311805da
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2020
ms.locfileid: "91413823"
---
# <a name="how-to-marshal-arrays-using-c-interop"></a>如何：使用 C++ Interop 封送處理陣列

本主題將示範 Visual C++ 互通性的一個 facet。 如需詳細資訊，請參閱 [使用 c + + Interop (隱含的 PInvoke) ](../dotnet/using-cpp-interop-implicit-pinvoke.md)。

下列程式碼範例使用 [managed、非](../preprocessor/managed-unmanaged.md) 受控 #pragma 指示詞，在相同的檔案中執行 managed 和非受控函式，但這些函式在個別檔案中定義時，會以相同的方式相交互操作。 只包含非受控函式的檔案不需要使用 [/clr (Common Language Runtime 編譯) ](../build/reference/clr-common-language-runtime-compilation.md)來進行編譯。

## <a name="example-pass-managed-array-to-unmanaged-function"></a>範例：將受控陣列傳遞至非受控函式

下列範例示範如何將 managed 陣列傳遞至非受控函數。 Managed 函式在呼叫非受控函式之前，會使用 [pin_ptr (c + +/cli) ](../extensions/pin-ptr-cpp-cli.md) 來隱藏陣列的垃圾收集。 藉由提供未受管理的函式與 GC 堆積的固定指標，可避免複製陣列的額外負荷。 為了示範非受控函式正在存取 GC 堆積記憶體，它會修改陣列的內容，並在 managed 函式繼續控制時反映變更。

```cpp
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

## <a name="example-pass-unmanaged-array-to-managed-function"></a>範例：傳遞非受控陣列至 managed 函數

下列範例示範如何將非受控陣列傳遞至 managed 函數。 Managed 函式會直接存取陣列記憶體 (而不是建立 managed 陣列並複製陣列內容) ，這樣可讓 managed 函式所做的變更在未受管理的函式重新取得控制權時反映在該函式中。

```cpp
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

[使用 c + + Interop (隱含 PInvoke) ](../dotnet/using-cpp-interop-implicit-pinvoke.md)
