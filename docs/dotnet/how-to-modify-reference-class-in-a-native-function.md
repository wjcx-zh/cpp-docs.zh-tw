---
title: "如何：修改原生函式中的參考類別 | Microsoft Docs"
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
  - "平台叫用, 參考類別"
  - "參考類型, 在 C++ 原生函式中修改"
ms.assetid: c701145b-62a0-4c4b-b32a-db8d69a59720
caps.latest.revision: 12
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：修改原生函式中的參考類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以使用 PInvoke 服務，將具有 CLR 陣列的參考類別傳遞至原生 \(Native\) 函式，並修改此類別。  
  
## 範例  
 編譯下列原生程式庫。  
  
```  
// modify_ref_class_in_native_function.cpp  
// compile with: /LD  
#include <stdio.h>  
#include <windows.h>  
  
struct S {  
   wchar_t* str;  
   int intarr[2];  
};  
  
extern "C"  {  
   __declspec(dllexport) int bar(S* param) {  
      printf_s("str: %S\n", param->str);  
      fflush(stdin);  
      fflush(stdout);  
      printf_s("In native: intarr: %d, %d\n",  
                param->intarr[0], param->intarr[1]);  
      fflush(stdin);  
      fflush(stdout);  
      param->intarr[0]=300;param->intarr[1]=400;  
      return 0;  
    }  
};  
```  
  
## 範例  
 編譯下列組件。  
  
```  
// modify_ref_class_in_native_function_2.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
[StructLayout(LayoutKind::Sequential, CharSet = CharSet::Unicode)]  
ref class S  {  
public:  
   [MarshalAsAttribute(UnmanagedType::LPWStr)]  
   String ^ str;  
   [MarshalAsAttribute(UnmanagedType::ByValArray,  
        ArraySubType=UnmanagedType::I4, SizeConst=2)]  
   array<Int32> ^ intarr;  
};  
  
[DllImport("modify_ref_class_in_native_function.dll",  
           CharSet=CharSet::Unicode)]  
int bar([In][Out] S ^ param);  
  
int main() {  
   S ^ param = gcnew S;  
   param->str = "Hello";  
   param->intarr = gcnew array<Int32>(2);  
   param->intarr[0] = 100;  
   param->intarr[1] = 200;  
   bar(param);   // Call to native function  
   Console::WriteLine("In managed: intarr: {0}, {1}",  
                       param->intarr[0], param->intarr[1]);  
}  
```  
  
  **str: Hello**  
**In native: intarr: 100, 200**  
**In managed: intarr: 300, 400**   
## 請參閱  
 [使用 C\+\+ Interop \(隱含 PInvoke\)](../dotnet/using-cpp-interop-implicit-pinvoke.md)