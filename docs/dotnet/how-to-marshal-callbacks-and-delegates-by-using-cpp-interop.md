---
title: "如何：使用 C++ Interop 封送處理回呼和委派 | Microsoft Docs"
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
  - "C++ Interop, 回呼和委派"
  - "回呼 [C++], 封送處理"
  - "資料封送處理 [C++], 回呼和委派"
  - "委派 [C++], 封送處理"
  - "Interop [C++], 回呼和委派"
  - "封送處理 [C++], 回呼和委派"
ms.assetid: 2313e9eb-5df9-4367-be0f-14b4712d8d2d
caps.latest.revision: 23
caps.handback.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用 C++ Interop 封送處理回呼和委派
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這個主題示範如何使用 Visual C\+\+，在 Managed 程式碼和 Unmanaged 程式碼之間封送處理 \(Marshalling\) 回呼 \(Callback\) 和委派 \(Delegate\) \(Managed 版本的回呼\)。  
  
 在下列範例中，程式碼會使用 [managed、unmanaged](../preprocessor/managed-unmanaged.md) \#pragma 指示詞，在相同的檔案中實作 Managed 和 Unmanaged 函式，這些函式也可以在不同的檔案中定義。  只包含 Unmanaged 函式的檔案，不需要以 [\/clr \(Common Language Runtime 編譯\)](../build/reference/clr-common-language-runtime-compilation.md) 編譯。  
  
## 範例  
 下列範例會說明如何設定 Unmanaged API 以觸發 \(Trigger\) Managed 委派。  這裡會建立 Managed 委派，並使用其中一個 Interop 方法 \(<xref:System.Runtime.InteropServices.Marshal.GetFunctionPointerForDelegate%2A>\) 來擷取委派的基礎進入點。  接下來，這個位址會被傳遞至 Unmanaged 函式，該函式呼叫此位址時，並不知道它被實作成 Managed 函式。  
  
 請注意，您可以 \(但非必要\) 使用 [pin\_ptr \(C\+\+\/CLI\)](../windows/pin-ptr-cpp-cli.md) Pin 此委派，以防止它遭到記憶體回收行程重新配置 \(Re\-locate\) 或處置 \(Dispose\)。  雖然必須防止提前進行記憶體回收，但是 Pin 會提供過多的保護，因為它雖然防止回收，但也阻礙了重新配置 \(Relocation\)。  
  
 如果委派被記憶體回收重新配置，將不會影響基礎 Managed 回呼，因此會使用 <xref:System.Runtime.InteropServices.GCHandle.Alloc%2A> 在委派中加入參考，可讓委派重新配置而不致於遭到處置。  使用 GCHandle \(而非 pin\_ptr\) 可以降低 Managed 堆積 \(Heap\) 被分割的機會。  
  
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
  
## 範例  
 下列範例與上一個範例類似，只是在這種情況中，提供的函式指標是由 Unmanaged API 儲存，所以可以隨時叫用 \(Invoke\)，但記憶體回收必須停用一段時間。  因此，下列範例會使用 <xref:System.Runtime.InteropServices.GCHandle> 的全域執行個體，在不考慮函式範圍的情況下，防止委派被重新配置。  如第一個範例所述，在這些範例中不需要使用 pin\_ptr，但在此情況中這個準則並不適用，因為 pin\_ptr 的範圍被限制在單一函式之內。  
  
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
  
## 請參閱  
 [使用 C\+\+ Interop \(隱含 PInvoke\)](../dotnet/using-cpp-interop-implicit-pinvoke.md)