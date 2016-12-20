---
title: "如何：使用 C++ Interop 封送處理 ANSI 字串 | Microsoft Docs"
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
  - "ANSI [C++], 封送處理字串"
  - "C++ Interop, 字串"
  - "資料封送處理 [C++], 字串"
  - "Interop [C++], 字串"
  - "封送處理 [C++], 字串"
ms.assetid: 5eda2eb6-5140-40f0-82cf-7ce171fffb45
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用 C++ Interop 封送處理 ANSI 字串
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主題會示範如何使用 C\+\+ Interop 傳遞 ANSI 字串，不過 .NET Framework 的 <xref:System.String> 是以 Unicode 格式表示字串，所以轉換至 ANSI 需要額外的步驟。  如需與其他字串型別互相溝通的資訊，請參閱下列主題：  
  
-   [如何：使用 C\+\+ Interop 封送處理 Unicode 字串](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)  
  
-   [如何：使用 C\+\+ Interop 封送處理 COM 字串](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)  
  
 在下列範例中，程式碼會使用 [managed、unmanaged](../preprocessor/managed-unmanaged.md) \#pragma 指示詞，在相同的檔案中實作 Managed 和 Unmanaged 函式，這些函式即使在不同的檔案中定義，也會以相同的方式互相溝通。  因為只包含 Unmanaged 函式的檔案不需要使用 [\/clr \(Common Language Runtime 編譯\)](../build/reference/clr-common-language-runtime-compilation.md) 進行編譯，所以檔案可以保留其執行特性。  
  
## 範例  
 範例會示範使用 <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A> 從 Managed 函式將 ANSI 字串傳遞至 Unmanaged 函式。  這個方法會在 Unmanaged 堆積 \(Heap\) 上配置記憶體，並在執行轉換後將位址傳回。  這表示不需要 Pin 動作 \(因為 GC 堆積上的記憶體不會傳遞至 Unmanaged 函式\)，而且必須明確釋放從 <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A> 傳回的 IntPtr，否則會產生記憶體遺漏 \(Memory Leak\)。  
  
```  
// MarshalANSI1.cpp  
// compile with: /clr  
#include <iostream>  
#include <stdio.h>  
  
using namespace std;  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
#pragma unmanaged  
  
void NativeTakesAString(const char* p) {  
   printf_s("(native) received '%s'\n", p);  
}  
  
#pragma managed  
  
int main() {  
   String^ s = gcnew String("sample string");  
   IntPtr ip = Marshal::StringToHGlobalAnsi(s);  
   const char* str = static_cast<const char*>(ip.ToPointer());  
  
   Console::WriteLine("(managed) passing string...");  
   NativeTakesAString( str );  
  
   Marshal::FreeHGlobal( ip );  
}  
```  
  
## 範例  
 下列範例會示範在 Managed 函式 \(由 Unmanaged 函式所呼叫\) 中存取 ANSI 字串時必要的資料封送處理 \(Marshaling\)。  Managed 函式在接收原生 \(Native\) 字串時，可以直接使用字串或使用 <xref:System.Runtime.InteropServices.Marshal.PtrToStringAnsi%2A> 方法將字串轉換為 Managed 字串，如以下所示。  
  
```  
// MarshalANSI2.cpp  
// compile with: /clr  
#include <iostream>  
#include <vcclr.h>  
  
using namespace std;  
  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
#pragma managed  
  
void ManagedStringFunc(char* s) {  
   String^ ms = Marshal::PtrToStringAnsi(static_cast<IntPtr>(s));  
   Console::WriteLine("(managed): received '{0}'", ms);  
}  
  
#pragma unmanaged  
  
void NativeProvidesAString() {  
   cout << "(native) calling managed func...\n";  
   ManagedStringFunc("test string");  
}  
  
#pragma managed  
  
int main() {  
   NativeProvidesAString();  
}  
```  
  
## 請參閱  
 [使用 C\+\+ Interop \(隱含 PInvoke\)](../dotnet/using-cpp-interop-implicit-pinvoke.md)