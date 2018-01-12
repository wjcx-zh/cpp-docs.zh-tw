---
title: "如何： 封送處理回呼和委派使用 c + + Interop |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
helpviewer_keywords:
- data marshaling [C++], callbacks and delegates
- C++ Interop, callbacks and delegates
- interop [C++], callbacks and delegates
- delegates [C++], marshaling
- marshaling [C++], callbacks and delegates
- callbacks [C++], marshaling
ms.assetid: 2313e9eb-5df9-4367-be0f-14b4712d8d2d
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: dbae96aeb7b11105a1a2aa30aa513c8d94011a91
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-marshal-callbacks-and-delegates-by-using-c-interop"></a>如何：使用 C++ Interop 封送處理回呼和委派
本主題示範回呼的封送處理，並使用 Visual c + + 中的 managed 和 unmanaged 程式碼之間委派 （回呼的受管理的版本）。  
  
 下列程式碼範例使用[managed、 unmanaged](../preprocessor/managed-unmanaged.md) #pragma 指示詞來實作 managed 和 unmanaged 函式在相同的檔案，但也無法在不同的檔案定義函式。 檔案，其中包含只在 unmanaged 函式不需要進行編譯[/clr （Common Language Runtime 編譯）](../build/reference/clr-common-language-runtime-compilation.md)。  
  
## <a name="example"></a>範例  
 下列範例會示範如何設定 unmanaged 的 API，以觸發程序之 managed 的委派。 建立受管理的委派和 interop 方法的其中一個<xref:System.Runtime.InteropServices.Marshal.GetFunctionPointerForDelegate%2A>，用來擷取基礎的進入點的委派。 此位址再傳遞至 unmanaged 函式，不需要知道的情況，它會實作為 managed 函式會呼叫它。  
  
 請注意，它是可行的但並非必要，釘選使用委派[pin_ptr (C + + /CLI)](../windows/pin-ptr-cpp-cli.md)可防止它們被重新位於或處置記憶體回收行程。 防止過早記憶體回收，但是 pin 會提供更多的保護，而不是必要的因為它會讓集合，但是也會防止重新配置。  
  
 如果記憶體回收，位於重新委派，它將不會影響 underlaying managed 回撥，因此<xref:System.Runtime.InteropServices.GCHandle.Alloc%2A>用來將參考加入委派，讓重新配置的委派，但無法處置。 使用而不 pin_ptr GCHandle 可減少片段可能會在 managed 堆積。  
  
```  
// MarshalDelegate1.cpp  
// compile with: /clr  
#include <iostream>  
  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
#pragma unmanaged  
  
// Declare an unmanaged function type that takes two int arguments  
// Note the use of __stdcall for compatibility with managed code  
typedef int (__stdcall *ANSWERCB)(int, int);  
  
int TakesCallback(ANSWERCB fp, int n, int m) {  
   printf_s("[unmanaged] got callback address, calling it...\n");  
   return fp(n, m);  
}  
  
#pragma managed  
  
public delegate int GetTheAnswerDelegate(int, int);  
  
int GetNumber(int n, int m) {  
   Console::WriteLine("[managed] callback!");  
   return n + m;  
}  
  
int main() {  
   GetTheAnswerDelegate^ fp = gcnew GetTheAnswerDelegate(GetNumber);  
   GCHandle gch = GCHandle::Alloc(fp);  
   IntPtr ip = Marshal::GetFunctionPointerForDelegate(fp);  
   ANSWERCB cb = static_cast<ANSWERCB>(ip.ToPointer());  
   Console::WriteLine("[managed] sending delegate as callback...");  
  
// force garbage collection cycle to prove  
// that the delegate doesn't get disposed  
   GC::Collect();  
  
   int answer = TakesCallback(cb, 243, 257);  
  
// release reference to delegate  
   gch.Free();  
}  
```  
  
## <a name="example"></a>範例  
 下列範例類似上述範例中，但在此情況下提供的函式指標會儲存由 unmanaged 的 API，讓它可以叫用在任何時間，需要回收 2aa 任意長度的時間。 因此，下列範例會使用的全域執行個體<xref:System.Runtime.InteropServices.GCHandle>以防止委派重新配置、 獨立的函式範圍。 第一個範例中所述，使用 pin_ptr 不需要為這些範例中，但在此情況下不會運作，如 pin_ptr 的範圍僅限於單一函式。  
  
```  
// MarshalDelegate2.cpp  
// compile with: /clr   
#include <iostream>  
  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
#pragma unmanaged  
  
// Declare an unmanaged function type that takes two int arguments  
// Note the use of __stdcall for compatibility with managed code  
typedef int (__stdcall *ANSWERCB)(int, int);  
static ANSWERCB cb;  
  
int TakesCallback(ANSWERCB fp, int n, int m) {  
   cb = fp;  
   if (cb) {  
      printf_s("[unmanaged] got callback address (%d), calling it...\n", cb);  
      return cb(n, m);  
   }  
   printf_s("[unmanaged] unregistering callback");  
   return 0;  
}  
  
#pragma managed  
  
public delegate int GetTheAnswerDelegate(int, int);  
  
int GetNumber(int n, int m) {  
   Console::WriteLine("[managed] callback!");  
   static int x = 0;  
   ++x;  
  
   return n + m + x;  
}  
  
static GCHandle gch;  
  
int main() {  
   GetTheAnswerDelegate^ fp = gcnew GetTheAnswerDelegate(GetNumber);  
  
   gch = GCHandle::Alloc(fp);  
  
   IntPtr ip = Marshal::GetFunctionPointerForDelegate(fp);  
   ANSWERCB cb = static_cast<ANSWERCB>(ip.ToPointer());  
   Console::WriteLine("[managed] sending delegate as callback...");  
  
   int answer = TakesCallback(cb, 243, 257);  
  
   // possibly much later (in another function)...  
  
   Console::WriteLine("[managed] releasing callback mechanisms...");  
   TakesCallback(0, 243, 257);  
   gch.Free();  
}  
```  
  
## <a name="see-also"></a>請參閱  
 [使用 C++ Interop (隱含 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)