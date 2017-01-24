---
title: "如何：將 char * 字串轉換為 System::Byte 陣列 | Microsoft Docs"
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
  - "陣列 [C++], 字元"
  - "字元陣列, 轉換為 System::Byte 陣列"
  - "範例 [C++], 陣列"
  - "範例 [C++], 字串"
ms.assetid: de9bc4eb-773c-4796-a496-9b90ca986503
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：將 char * 字串轉換為 System::Byte 陣列
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

將 `char *` 字串轉換為 <xref:System.Byte> 陣列最有效率的方式是使用 <xref:System.Runtime.InteropServices.Marshal> 類別。  
  
## 範例  
  
```  
// convert_native_string_to_Byte_array.cpp  
// compile with: /clr  
#include <string.h>  
  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
int main() {  
   char buf[] = "Native String";  
   int len = strlen(buf);  
  
   array< Byte >^ byteArray = gcnew array< Byte >(len + 2);  
  
   // convert native pointer to System::IntPtr with C-Style cast  
   Marshal::Copy((IntPtr)buf,byteArray, 0, len);  
  
   for ( int i = byteArray->GetLowerBound(0); i <= byteArray->GetUpperBound(0); i++ ) {  
      char dc =  *(Byte^)   byteArray->GetValue(i);  
      Console::Write((Char)dc);  
   }  
  
   Console::WriteLine();  
}  
```  
  
```  
Native String  
```  
  
## 請參閱  
 [使用 C\+\+ Interop \(隱含 PInvoke\)](../dotnet/using-cpp-interop-implicit-pinvoke.md)