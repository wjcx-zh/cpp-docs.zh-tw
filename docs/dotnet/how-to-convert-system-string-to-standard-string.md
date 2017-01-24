---
title: "如何：將 System::String 轉換為標準字串 | Microsoft Docs"
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
  - "Standard C++ 程式庫, 轉換 System::String 為標準字串"
  - "字串轉換, System::String"
ms.assetid: 79e2537e-d4eb-459f-9506-0e738045b59e
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：將 System::String 轉換為標準字串
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以將 <xref:System.String> 轉換為 `std::string` 或 `std::wstring`，而不需使用 Vcclr.h 中的 `PtrToStringChars`。  
  
## 範例  
  
```  
// convert_system_string.cpp  
// compile with: /clr  
#include <string>  
#include <iostream>  
using namespace std;  
using namespace System;  
  
void MarshalString ( String ^ s, string& os ) {  
   using namespace Runtime::InteropServices;  
   const char* chars =   
      (const char*)(Marshal::StringToHGlobalAnsi(s)).ToPointer();  
   os = chars;  
   Marshal::FreeHGlobal(IntPtr((void*)chars));  
}  
  
void MarshalString ( String ^ s, wstring& os ) {  
   using namespace Runtime::InteropServices;  
   const wchar_t* chars =   
      (const wchar_t*)(Marshal::StringToHGlobalUni(s)).ToPointer();  
   os = chars;  
   Marshal::FreeHGlobal(IntPtr((void*)chars));  
}  
  
int main() {  
   string a = "test";  
   wstring b = L"test2";  
   String ^ c = gcnew String("abcd");  
  
   cout << a << endl;  
   MarshalString(c, a);  
   c = "efgh";  
   MarshalString(c, b);  
   cout << a << endl;  
   wcout << b << endl;  
}  
```  
  
```  
test  
abcd  
efgh  
```  
  
## 請參閱  
 [使用 C\+\+ Interop \(隱含 PInvoke\)](../dotnet/using-cpp-interop-implicit-pinvoke.md)