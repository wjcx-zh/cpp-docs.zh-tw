---
title: "如何：指定 out 參數 | Microsoft Docs"
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
  - "函式參數"
  - "out 參數"
ms.assetid: 02862448-603c-4e9d-a5c5-b45fe38446e3
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# 如何：指定 out 參數
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這個範例顯示如何將函式參數指定為 out 參數，以及如何從 C\# 程式呼叫該函式。  
  
 在 Visual C\+\+ 中，out 參數是以 <xref:System.Runtime.InteropServices.OutAttribute> 指定。  
  
## 範例  
 這個範例的第一個部分是 Visual C\+\+ DLL，它的型別中包含具有 out 參數的函式。  
  
```  
// cpp_out_param.cpp  
// compile with: /LD /clr:safe  
using namespace System;  
public value struct TestStruct {  
   static void Test([Runtime::InteropServices::Out] String^ %s) {  
      s = "a string";  
   }  
};  
```  
  
## 範例  
 這是 C\# 用戶端，此用戶端使用上一個範例所建立的 Visual C\+\+ 元件。  
  
```  
// cpp_out_param_2.cs  
// compile with: /reference:cpp_out_param.dll  
using System;  
class TestClass {  
   public static void Main() {  
      String t;  
      TestStruct.Test(out t);  
      System.Console.WriteLine(t);  
   }  
}  
```  
  
  **字串。**   
## 請參閱  
 [使用 C\+\+ Interop \(隱含 PInvoke\)](../dotnet/using-cpp-interop-implicit-pinvoke.md)