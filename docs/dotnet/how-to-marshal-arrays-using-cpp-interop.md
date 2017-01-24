---
title: "如何：使用 C++ Interop 封送處理陣列 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "陣列 [C++], 封送處理"
  - "C++ Interop, 陣列"
  - "資料封送處理 [C++], 陣列"
  - "Interop [C++], 陣列"
  - "封送處理 [C++], 陣列"
ms.assetid: c2b37ab1-8acf-4855-ad3c-7d2864826b14
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用 C++ Interop 封送處理陣列
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主題將示範 Visual C\+\+ 互通性的一個 Facet。  如需詳細資訊，請參閱[使用 C\+\+ Interop \(隱含 PInvoke\)](../dotnet/using-cpp-interop-implicit-pinvoke.md)。  
  
 在下列範例中，程式碼會使用 [managed、unmanaged](../preprocessor/managed-unmanaged.md) \#pragma 指示詞，在相同的檔案中實作 Managed 和 Unmanaged 函式，這些函式即使在不同的檔案中定義，也會以相同的方式互相溝通。  只包含 Unmanaged 函式的檔案，不需要以 [\/clr \(Common Language Runtime 編譯\)](../build/reference/clr-common-language-runtime-compilation.md) 編譯。  
  
## 範例  
 下列程式碼範例會示範如何將 Managed 陣列傳遞至 Unmanaged 函式。  Managed 函式會使用 [pin\_ptr \(C\+\+\/CLI\)](../windows/pin-ptr-cpp-cli.md)，在呼叫 Unmanaged 函式之前禁止陣列的記憶體回收。  將指向 GC 堆積 \(Heap\) 的 Pin 指標提供給 Unmanaged 函式，可以避免複製陣列的額外負荷。  為了示範 Unmanaged 函式會存取 GC 堆積記憶體，此函式會修改陣列的內容，而且當 Managed 函式重新取得控制時，就會反映變更。  
  
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
  
## 範例  
 下列程式碼範例會示範將 Unmanaged 陣列傳遞至 Managed 函式。  Managed 函式會直接存取陣列記憶體 \(相對於建立 Managed 陣列並複製陣列內容\)，在 Unmanaged 函式重新取得控制時可以反映 Managed 函式所做的變更。  
  
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
  
## 請參閱  
 [使用 C\+\+ Interop \(隱含 PInvoke\)](../dotnet/using-cpp-interop-implicit-pinvoke.md)