---
title: "如何： 指定 out 參數 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs:
- C++
helpviewer_keywords:
- function parameters
- out parameters
ms.assetid: 02862448-603c-4e9d-a5c5-b45fe38446e3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 0905220a1e2ab3e209fe80598ec67903999245b5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-specify-an-out-parameter"></a>如何：指定 out 參數
這個範例會示範如何指定函式參數是輸出參數以及如何從 C# 程式呼叫該函式。  
  
 Visual c + + 中指定 out 參數<xref:System.Runtime.InteropServices.OutAttribute>。  
  
## <a name="example"></a>範例  
 此範例的第一個部分是 Visual c + + DLL 包含 out 參數的函式的類型。  
  
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
  
## <a name="example"></a>範例  
 這是使用前一個範例中所建立的 Visual c + + 元件的 C# 用戶端。  
  
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
  
```Output  
a string  
```  
  
## <a name="see-also"></a>請參閱  
 [使用 C++ Interop (隱含 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)