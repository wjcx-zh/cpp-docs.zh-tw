---
title: "編譯器錯誤 C2951 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2951"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2951"
ms.assetid: c6f95aa2-c894-425b-a51c-d40d70c8daa1
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# 編譯器錯誤 C2951
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

只允許在全域、命名空間或類別範圍使用型別宣告  
  
 您不能在全域或命名空間 \(Namespace\) 範圍之外宣告泛型或樣板。  如果您在 include 檔中宣告泛型或樣板，請確定 include 檔是在全域範圍內。  
  
 下列範例會產生 C2951：  
  
```  
// C2951.cpp  
template <class T>  
class A {};  
  
int main() {  
   template <class T>   // C2951  
   class B {};  
}  
```  
  
 使用 Generics 時也可能發生 C2951：  
  
```  
// C2951b.cpp  
// compile with: /clr /c  
  
// OK  
generic <class T>   
ref class GC { };  
  
int main() {  
   generic <class T> ref class GC2 {};   // C2951  
}  
```