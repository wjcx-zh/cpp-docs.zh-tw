---
title: "如何：攔截 MSIL 擲回之機器碼的例外狀況 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "攔截例外狀況, 從 MSIL 擲回"
  - "例外狀況, 攔截"
  - "MSIL, 攔截機器碼中的例外狀況"
ms.assetid: c15afd2b-8505-43bf-8a4a-f1d41532a124
caps.latest.revision: 9
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：攔截 MSIL 擲回之機器碼的例外狀況
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在機器碼中，您可以攔截 MSIL 的原生 C\+\+ 例外狀況。您可以攔截與 `__try` 和 `__except`的 CLR 例外狀況。  
  
 如需詳細資訊，請參閱[結構化例外狀況處理](../cpp/structured-exception-handling-c-cpp.md)與[C\+\+ 例外狀況處理](../cpp/cpp-exception-handling.md)。  
  
## 範例  
 下列範例定義具有兩個函式的，擲回原生例外狀況擲回之例外狀況的和類別的模組。  
  
```  
// catch_MSIL_in_native.cpp  
// compile with: /clr /c  
void Test() {  
   throw ("error");  
}  
  
void Test2() {  
   throw (gcnew System::Exception("error2"));  
}  
```  
  
## 範例  
 下列範例定義了一個攔截原生和 MSIL 例外狀況中的模組。  
  
```  
// catch_MSIL_in_native_2.cpp  
// compile with: /clr catch_MSIL_in_native.obj  
#include <iostream>  
using namespace std;  
void Test();  
void Test2();  
  
void Func() {  
   // catch any exception from MSIL  
   // should not catch Visual C++ exceptions like this  
   // runtime may not destroy the object thrown  
   __try {  
      Test2();  
   }  
   __except(1) {  
      cout << "caught an exception" << endl;  
   }  
  
}  
  
int main() {  
   // catch native C++ exception from MSIL  
   try {  
      Test();  
   }  
   catch(char * S) {  
      cout << S << endl;  
   }  
   Func();  
}  
```  
  
  **錯誤**  
**攔截到例外狀況。**   
## 請參閱  
 [Exception Handling](../windows/exception-handling-cpp-component-extensions.md)