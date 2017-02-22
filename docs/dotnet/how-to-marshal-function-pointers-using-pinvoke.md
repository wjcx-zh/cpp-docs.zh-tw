---
title: "如何：使用 PInvoke 封送處理函式指標 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "資料封送處理 [C++], 回呼和委派"
  - "Interop [C++], 回呼和委派"
  - "封送處理 [C++], 回呼和委派"
  - "平台叫用 [C++], 回呼和委派"
ms.assetid: dcf396fd-a91d-49c0-ab0b-1ea160668a89
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# 如何：使用 PInvoke 封送處理函式指標
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主題會說明在使用 .NET Framework P\/Invoke 功能與 Unmanaged 函式互通時，Managed 委派 \(Delegate\) 如何代替函式指標。  但是，我們鼓勵 Visual C\+\+ 程式設計人員盡可能改用 C\+\+ Interop 功能，因為 P\/Invoke 提供極少的編譯時期錯誤報告，不具型別安全，而且實作時很瑣碎無聊。  如果 Unmanaged API 封裝為 DLL，而且沒有原始程式碼，則 P\/Invoke 是唯一的選擇。  否則請參閱下列主題：  
  
-   [使用 C\+\+ Interop \(隱含 PInvoke\)](../dotnet/using-cpp-interop-implicit-pinvoke.md)  
  
-   [如何：使用 C\+\+ Interop 封送處理回呼和委派](../dotnet/how-to-marshal-callbacks-and-delegates-by-using-cpp-interop.md)  
  
 使用函式指標做為引數的 Unmanaged API，可以從 Managed 程式碼中呼叫，並使用 Managed 委派取代原生 \(Native\) 函式指標。  編譯器 \(Compiler\) 會自動將委派封送處理至 Unmanaged 函式做為函式指標，並插入必要的 Managed\/Unmanaged 轉換程式碼。  
  
## 範例  
 下列程式碼由 Unmanaged 和 Managed 的模組所組成。  Unmanaged 模組是 DLL，定義名稱為 TakesCallback 且可接受函式指標的函式。  這個位址會用來執行函式。  
  
 Managed 模組會定義委派，而委派會封裝處理至機器碼做為函式指標，並使用 <xref:System.Runtime.InteropServices.DllImportAttribute> 屬性 \(Attribute\) 來將原生的 TakesCallback 函式公開 \(Expose\) 給 Managed 程式碼。  在 main 函式中，會建立委派的執行個體 \(Instance\) 並傳遞至 TakesCallback 函式。  程式輸出會示範原生的 TakesCallback 函式執行這個函式。  
  
 Managed 函式會禁止 Managed 委派的記憶體回收，以避免 .NET Framework 記憶體回收在原生函式執行時重新配置委派。  
  
 Managed 模組是使用 \/clr 編譯的，但是 \/clr:pure 也一樣可以執行。  
  
```  
// TraditionalDll5.cpp  
// compile with: /LD /EHsc  
#include <iostream>  
#define TRADITIONALDLL_EXPORTS  
#ifdef TRADITIONALDLL_EXPORTS  
#define TRADITIONALDLL_API __declspec(dllexport)  
#else  
#define TRADITIONALDLL_API __declspec(dllimport)  
#endif  
  
extern "C" {  
   /* Declare an unmanaged function type that takes two int arguments  
      Note the use of __stdcall for compatibility with managed code */  
   typedef int (__stdcall *CALLBACK)(int);  
   TRADITIONALDLL_API int TakesCallback(CALLBACK fp, int);  
}  
  
int TakesCallback(CALLBACK fp, int n) {  
   printf_s("[unmanaged] got callback address, calling it...\n");  
   return fp(n);  
}  
```  
  
```  
// MarshalDelegate.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
public delegate int GetTheAnswerDelegate(int);  
public value struct TraditionalDLL {  
   [DllImport("TraditionalDLL5.dll")]  
   static public int TakesCallback(GetTheAnswerDelegate^ pfn, int n);  
};  
  
int GetNumber(int n) {  
   Console::WriteLine("[managed] callback!");  
   static int x = 0;  
   ++x;  
   return x + n;  
}  
  
int main() {  
   GetTheAnswerDelegate^ fp = gcnew GetTheAnswerDelegate(GetNumber);  
   pin_ptr<GetTheAnswerDelegate^> pp = &fp;  
   Console::WriteLine("[managed] sending delegate as callback...");  
  
   int answer = TraditionalDLL::TakesCallback(fp, 42);  
}  
```  
  
 請注意，DLL 的任何部分不會都公開給使用傳統 \#include 指示詞的 Managed 程式碼。  事實上，DLL 只會在執行階段存取，所以使用 <xref:System.Runtime.InteropServices.DllImportAttribute> 匯入之函式所產生的問題，不會在編譯時期偵測出來。  
  
## 請參閱  
 [在 C\+\+ 中使用明確的 PInvoke \(DllImport 屬性\)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)