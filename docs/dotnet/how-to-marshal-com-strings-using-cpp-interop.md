---
title: "如何：使用 C++ Interop 封送處理 COM 字串 | Microsoft Docs"
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
  - "COM [C++], 封送處理字串"
  - "資料封送處理 [C++], 字串"
  - "Interop [C++], 字串"
  - "封送處理 [C++], 字串"
ms.assetid: 06590759-bf99-4e34-a3a9-4527ea592cc2
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用 C++ Interop 封送處理 COM 字串
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這個主題會示範如何將 BSTR \(COM 程式設計中偏好使用的基本字串格式\) 從 Managed 函式傳遞至 Unmanaged 函式，以及如何從 Unmanaged 函式傳遞至 Managed 函式。  如需與其他字串型別互通的資訊，請參閱下列主題：  
  
-   [如何：使用 C\+\+ Interop 封送處理 Unicode 字串](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)  
  
-   [如何：使用 C\+\+ Interop 封送處理 ANSI 字串](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)  
  
 在下列範例中，程式碼會使用 [managed、unmanaged](../preprocessor/managed-unmanaged.md) \#pragma 指示詞，在相同的檔案中實作 Managed 和 Unmanaged 函式，這些函式即使在不同的檔案中定義，也會以相同的方式互相溝通。  只包含 Unmanaged 函式的檔案，不需要以 [\/clr \(Common Language Runtime 編譯\)](../build/reference/clr-common-language-runtime-compilation.md) 編譯。  
  
## 範例  
 下列範例會示範如何將 BSTR \(COM 程式設計中使用的字串格式\) 從 Managed 函式傳遞至 Unmanaged 函式。  呼叫的 Managed 函式會使用 <xref:System.Runtime.InteropServices.Marshal.StringToBSTR%2A> 來取得 .NET System.String 內容之 BSTR 表示的位址。  這個指標使用 [pin\_ptr \(C\+\+\/CLI\)](../windows/pin-ptr-cpp-cli.md) 來執行 Pin，以確定執行 Unmanaged 函式時，它的實體位址在記憶體回收期間不會改變。  在 [pin\_ptr \(C\+\+\/CLI\)](../windows/pin-ptr-cpp-cli.md) 超出範圍之前，記憶體回收行程都無法移動記憶體。  
  
```  
// MarshalBSTR1.cpp  
// compile with: /clr  
#define WINVER 0x0502  
#define _AFXDLL  
#include <afxwin.h>  
  
#include <iostream>  
using namespace std;  
  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
#pragma unmanaged  
  
void NativeTakesAString(BSTR bstr) {  
   printf_s("%S", bstr);  
}  
  
#pragma managed  
  
int main() {  
   String^ s = "test string";  
  
   IntPtr ip = Marshal::StringToBSTR(s);  
   BSTR bs = static_cast<BSTR>(ip.ToPointer());  
   pin_ptr<BSTR> b = &bs;  
  
   NativeTakesAString( bs );  
   Marshal::FreeBSTR(ip);  
}  
```  
  
## 範例  
 下列範例示範如何將 BSTR 從 Unmanaged 函式傳遞至 Managed 函式。  接收的 Managed 函式可以使用字串做為 BSTR，或使用 <xref:System.Runtime.InteropServices.Marshal.PtrToStringBSTR%2A> 將它轉換為 <xref:System.String>，以搭配其他 Managed 函式使用。  由於表示 BSTR 的記憶體是配置在 Unmanaged 堆積 \(Heap\) 上，因此不需要執行 Pin，因為 Unmanaged 堆疊上不會有記憶體回收。  
  
```  
// MarshalBSTR2.cpp  
// compile with: /clr  
#define WINVER 0x0502  
#define _AFXDLL  
#include <afxwin.h>  
  
#include <iostream>  
using namespace std;  
  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
#pragma managed  
  
void ManagedTakesAString(BSTR bstr) {  
   String^ s = Marshal::PtrToStringBSTR(static_cast<IntPtr>(bstr));  
   Console::WriteLine("(managed) convered BSTR to String: '{0}'", s);  
}  
  
#pragma unmanaged  
  
void UnManagedFunc() {  
   BSTR bs = SysAllocString(L"test string");  
   printf_s("(unmanaged) passing BSTR to managed func...\n");  
   ManagedTakesAString(bs);  
}  
  
#pragma managed  
  
int main() {  
   UnManagedFunc();  
}  
```  
  
## 請參閱  
 [使用 C\+\+ Interop \(隱含 PInvoke\)](../dotnet/using-cpp-interop-implicit-pinvoke.md)