---
title: "noinline | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "noinline"
  - "noinline_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec 關鍵字 [C++], noinline"
  - "noinline __declspec 關鍵字"
ms.assetid: f259d55b-dec7-4bde-8cf9-14521e4fdc42
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# noinline
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Microsoft 特定的  
 **\_\_declspec\(noinline\)** 會告知編譯器永遠不要內嵌特定成員函式 \(類別中的函式\)。  
  
 如果函式不大，而且對程式碼的效能不重要，建議不要內嵌函式。  也就是，如果函式不大且可能不常被呼叫，例如處理錯誤條件的函式。  
  
 請記住，如果函式已標記為 `noinline`，呼叫函式會較小，因而本身即為編譯器的內嵌候選項。  
  
```  
class X {  
   __declspec(noinline) int mbrfunc() {  
      return 0;   
   }   // will not inline  
};  
```  
  
## END Microsoft 特定的  
  
## 請參閱  
 [\_\_declspec](../cpp/declspec.md)   
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)   
 [inline、\_\_inline、\_\_forceinline](../misc/inline-inline-forceinline.md)