---
title: "novtable | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "novtable"
  - "novtable_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec 關鍵字 [C++], novtable"
  - "novtable __declspec 關鍵字"
ms.assetid: cfef09c5-8c1e-4b14-8a72-7d726ded4484
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# novtable
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Microsoft 特定的  
 這是 `__declspec` 擴充屬性。  
  
 這種形式的 `__declspec` 可以套用至任何類別宣告，但只應套用於純介面類別，也就是本身不會執行個體化的類別。  `__declspec` 會阻止編譯器產生在類別建構函式和解構函式中初始化 vfptr 的程式碼。  在大部分情況下，這樣只能移除與類別相關的 vtable 參考，因此連結器會將它移除。  使用這種形式的 `__declspec` 可能會導致大幅縮小程式碼的大小。  
  
 如果您嘗試將標記為 `novtable` 的類別執行個體化，然後存取類別成員，您會收到存取違規 \(AV\)。  
  
## 範例  
  
```  
// novtable.cpp  
#include <stdio.h>  
  
struct __declspec(novtable) X {  
   virtual void mf();  
};  
  
struct Y : public X {  
   void mf() {  
      printf_s("In Y\n");  
   }  
};  
  
int main() {  
   // X *pX = new X();  
   // pX->mf();   // Causes a runtime access violation.  
  
   Y *pY = new Y();  
   pY->mf();  
}  
```  
  
  **In Y**   
## END Microsoft 特定的  
  
## 請參閱  
 [\_\_declspec](../cpp/declspec.md)   
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)