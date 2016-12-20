---
title: "ABI 界限上的可攜性 (現代 C++) | Microsoft Docs"
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
ms.assetid: abbd405e-3038-427c-8c24-e00598f0936a
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ABI 界限上的可攜性 (現代 C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用完全可移植的型別和 在二進位介面 \(ABI\) 界限的慣例。  「可攜式型別」是 C\+\+. 內建的型別或只包含 C 內建型別的結構。  類別型別當呼叫端和被呼叫端對配置、呼叫慣例等達成協議時才能使用。當兩個使用相同編譯器編譯和編譯器設定時，才有可能。  
  
## 如何簡化 C 可攜性的類別  
 當呼叫端可能會被其他編譯器\/語言編譯時，那麼以特定呼叫慣例「簡化」至「外部 C」API:  
  
```cpp  
// class widget {  
//   widget();  
//   ~widget();  
//   double method( int, gadget& );  
// };  
extern “C” {    // functions using explicit “this”  
  struct widget;   // + opaque type (fwd decl only)  
  widget* STDCALL widget_create();    // ctor → create new  “this”  
  void STDCALL widget_destroy( widget* );    // dtor → consume “this”  
  double STDCALL widget_method( widget*, int, gadget* );    // method → use “this”  
}  
  
```  
  
## 請參閱  
 [歡迎回到 C\+\+](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [C\+\+ 語言參考](../cpp/cpp-language-reference.md)   
 [C\+\+ Standard Library](../standard-library/cpp-standard-library-reference.md)