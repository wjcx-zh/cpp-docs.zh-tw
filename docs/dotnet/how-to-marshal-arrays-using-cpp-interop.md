---
title: 如何： 使用 c + + Interop 封送處理陣列 |Microsoft 文件
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- arrays [C++], marshaling
- marshaling [C++], arrays
- interop [C++], arrays
- C++ Interop, arrays
- data marshaling [C++], arrays
ms.assetid: c2b37ab1-8acf-4855-ad3c-7d2864826b14
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: ebc54832c86ede92cd6bd3f2ee8b36288d06b895
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33130207"
---
# <a name="how-to-marshal-arrays-using-c-interop"></a>如何：使用 C++ Interop 封送處理陣列
本主題會示範一個 facet 的 Visual c + + 的互通性。 如需詳細資訊，請參閱[使用 c + + Interop (隱含 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)。  
  
 下列程式碼範例使用[managed、 unmanaged](../preprocessor/managed-unmanaged.md) #pragma 指示詞來實作 managed 和 unmanaged 函式在相同的檔案，但如果在不同的檔案中定義這些函式交互操作的方式相同。 檔案，其中包含只在 unmanaged 函式不需要進行編譯[/clr （Common Language Runtime 編譯）](../build/reference/clr-common-language-runtime-compilation.md)。  
  
## <a name="example"></a>範例  
 下列範例會示範如何將 managed 的陣列傳遞至 unmanaged 函式。 Managed 函式會使用[pin_ptr (C + + /CLI)](../windows/pin-ptr-cpp-cli.md)隱藏陣列的記憶體回收集合，然後再呼叫 unmanaged 函式。 藉由提供 pin 指標的 unmanaged 函式 GC 堆積，您可以避免建立陣列的複本的額外負荷。 若要示範 GC 堆積記憶體存取 unmanaged 函式，它會修改陣列的內容和的變更會反映 managed 函式會繼續控制項時。  
  
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
 下列範例示範如何將未受管理的陣列傳遞至 managed 函式。 Managed 函式存取陣列記憶體直接 （相對於建立 managed 的陣列，並將複製的陣列內容），可讓 managed 函式所做變更才能反映在 unmanaged 函式，當它重新取得控制。  
  
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