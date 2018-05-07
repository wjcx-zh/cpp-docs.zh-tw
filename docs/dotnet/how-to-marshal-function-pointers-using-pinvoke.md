---
title: 如何： 使用 PInvoke 封送處理函式指標 |Microsoft 文件
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- data marshaling [C++], callbacks and delegates
- interop [C++], callbacks and delegates
- platform invoke [C++], callbacks and delegates
- marshaling [C++], callbacks and delegates
ms.assetid: dcf396fd-a91d-49c0-ab0b-1ea160668a89
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 1aa8da5e5b6931fb46ff283a5be15da5b2c7325d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-marshal-function-pointers-using-pinvoke"></a>如何：使用 PInvoke 封送處理函式指標
本主題說明如何在受管理的委派時與互通 unmanaged 函式使用.NET Framework P/Invoke 功能可用來代替函式指標。 不過，Visual c + + 程式設計人員會建議 （自動），而是使用 c + + Interop 功能，因為 P/Invoke 提供極少的編譯時間錯誤報告，不是類型安全，就必須等待冗長實作。 如果未受管理的應用程式開發介面會封裝為 DLL 不是可用的原始程式碼，P/Invoke 是唯一的選項。 否則，請參閱下列主題：  
  
-   [使用 C++ Interop (隱含 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)  
  
-   [如何：使用 C++ Interop 封送處理回呼和委派](../dotnet/how-to-marshal-callbacks-and-delegates-by-using-cpp-interop.md)  
  
 Unmanaged 的 Api 的需要函式指標，可以從呼叫的引數，因為 managed 與原生函式指標取代之 managed 委派的程式碼。 編譯器會自動封送處理至 unmanaged 函式委派，函式指標，並將插入的必要轉換 managed/unmanaged 程式碼。  
  
## <a name="example"></a>範例  
 下列程式碼是由 unmanaged 和 managed 的模組所組成。 未受管理的模組會定義稱為 TakesCallback 可接受函式指標的函式的 DLL。 此位址用來執行該函式。  
  
 受管理的模組定義委派，其中會以原生程式碼，函式指標封送處理，並使用<xref:System.Runtime.InteropServices.DllImportAttribute>公開 managed 程式碼的原生 TakesCallback 函式的屬性。 在 main 函式，是建立委派的執行個體，並將其傳遞給 TakesCallback 函式中。 程式輸出會示範執行此函式時，取得原生 TakesCallback 函式。  
  
 Managed 函式會抑制受管理的委派，若要避免.NET Framework 記憶體回收重新配置委派，而原生函式會執行記憶體回收。  
  
```cpp  
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
  
```cpp  
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
  
 請注意，DLL 的任何部分公開給 managed 程式碼使用的傳統 #include 指示詞。 事實上，DLL 會在執行階段存取，因此問題函式匯入與<xref:System.Runtime.InteropServices.DllImportAttribute>將不會在編譯時期偵測。  
  
## <a name="see-also"></a>另請參閱  
 [在 C++ 中使用明確的 PInvoke (DllImport 屬性)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)