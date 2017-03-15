---
title: "編譯器錯誤 C2993 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2993"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2993"
ms.assetid: 4ffd2b78-654b-46aa-95a6-b62101cf91c8
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 編譯器錯誤 C2993
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' : 非型別樣板參數 'parameter' 的不合法型別  
  
 您不能以結構或等位引數宣告樣板。  請使用指標當做樣板參數傳遞結構和等位。  
  
 下列範例會產生 C2993：  
  
```  
// C2993.cpp  
// compile with: /c  
// C2993 expected  
struct MyStruct {  
   int a;char b;  
};  
  
template <class T, struct MyStruct S>   // C2993  
  
// try the following line instead  
// template <class T, struct MyStruct * S>  
class CMyClass {};  
```  
  
 對 Visual Studio .NET 2003 的編譯器完成符合標準處理後也會出現這個錯誤：已不再允許使用浮點非型別樣板參數。  C\+\+ 標準不允許使用浮點非型別樣板參數。  
  
 如果是函式樣板，請使用函式引數來傳入浮點非型別樣板參數 \(這個程式碼在 Visual Studio .NET 2003 和 Visual Studio .NET 版本的 Visual C\+\+ 中是有效的\)。  如果是類別樣板，則沒有簡單的解決方法。  
  
```  
// C2993b.cpp  
// compile with: /c  
template<class T, float f> void func(T) {}   // C2993  
  
// OK  
template<class T>   void func2(T, float) {}  
```