---
title: "如何：使用 C++ Interop 封送處理 Unicode 字串 | Microsoft Docs"
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
  - "C++ Interop, 字串"
  - "資料封送處理 [C++], 字串"
  - "Interop [C++], 字串"
  - "封送處理 [C++], 字串"
  - "Unicode, 封送處理字串"
ms.assetid: 96c2141d-6c5d-43ef-a1aa-5785afb9a9aa
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用 C++ Interop 封送處理 Unicode 字串
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主題將示範 Visual C\+\+ 互通性的一個 Facet。  如需詳細資訊，請參閱[使用 C\+\+ Interop \(隱含 PInvoke\)](../dotnet/using-cpp-interop-implicit-pinvoke.md)。  
  
 在下列範例中，程式碼會使用 [managed、unmanaged](../preprocessor/managed-unmanaged.md) \#pragma 指示詞，在相同的檔案中實作 Managed 和 Unmanaged 函式，這些函式即使在不同的檔案中定義，也會以相同的方式互相溝通。  只包含 Unmanaged 函式的檔案，不需要以 [\/clr \(Common Language Runtime 編譯\)](../build/reference/clr-common-language-runtime-compilation.md) 編譯。  
  
 本主題會示範如何在 Managed 函式和 Unmanaged 函式之間傳遞 Unicode 字串。  如需與其他字串型別互通的資訊，請參閱下列主題：  
  
-   [如何：使用 C\+\+ Interop 封送處理 ANSI 字串](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)  
  
-   [如何：使用 C\+\+ Interop 封送處理 COM 字串](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)  
  
## 範例  
 若要將 Unicode 字串從 Managed 函式傳遞至 Unmanaged 函式，PtrToStringChars 函式 \(在 Vcclr.h 中宣告\) 可以用來存取 Managed 字串在記憶體中儲存的位置。  因為這個位址會傳遞至原生 \(Native\) 函式，您必須使用 [pin\_ptr \(C\+\+\/CLI\)](../windows/pin-ptr-cpp-cli.md) 對記憶體進行 Pin 動作，以避免記憶體回收循環在 Unmanaged 函式執行時介入，導致字串資料重新配置。  
  
```  
// MarshalUnicode1.cpp  
// compile with: /clr  
#include <iostream>  
#include <stdio.h>  
#include <vcclr.h>  
  
using namespace std;  
  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
#pragma unmanaged  
  
void NativeTakesAString(const wchar_t* p) {  
   printf_s("(native) received '%S'\n", p);  
}  
  
#pragma managed  
  
int main() {  
   String^ s = gcnew String("test string");  
   pin_ptr<const wchar_t> str = PtrToStringChars(s);  
  
   Console::WriteLine("(managed) passing string to native func...");  
   NativeTakesAString( str );  
}  
```  
  
## 範例  
 下列範例會示範在 Managed 函式 \(由 Unmanaged 函式所呼叫\) 中存取 Unicode 字串時必要的資料封送處理 \(Marshaling\)。  Managed 函式在收到原生 Unicode 字串時，會使用 <xref:System.Runtime.InteropServices.Marshal.PtrToStringUni%2A> 方法將字串轉換為 Managed 字串。  
  
```  
// MarshalUnicode2.cpp  
// compile with: /clr  
#include <iostream>  
  
using namespace std;  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
#pragma managed  
  
void ManagedStringFunc(wchar_t* s) {  
   String^ ms = Marshal::PtrToStringUni((IntPtr)s);  
   Console::WriteLine("(managed) received '{0}'", ms);  
}  
  
#pragma unmanaged  
  
void NativeProvidesAString() {  
   cout << "(unmanaged) calling managed func...\n";  
   ManagedStringFunc(L"test string");  
}  
  
#pragma managed  
  
int main() {  
   NativeProvidesAString();  
}  
```  
  
## 請參閱  
 [使用 C\+\+ Interop \(隱含 PInvoke\)](../dotnet/using-cpp-interop-implicit-pinvoke.md)