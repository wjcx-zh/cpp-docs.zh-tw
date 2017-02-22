---
title: "編譯器錯誤 C2252 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2252"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2252"
ms.assetid: fee74ab9-1997-4615-82fe-e6d1fe3aacd9
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 編譯器錯誤 C2252
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

無法在目前的範圍中明確具現樣板  
  
 編譯器偵測到樣板有明確具現化 \(Instantiation\) 的問題。例如，您不能明確地具現化函式中的樣板。  
  
 下列範例會產生 C2252：  
  
```  
// C2252.cpp  
class A {  
public:  
   template <class T>  
   int getit(int i , T * it ) {  
      return i;  
   }  
   template int A::getit<double>(int i, double * it);   // C2252  
   // try the following line instead  
   // template <> int A::getit<double>(int i, double * it);  
  
};  
  
int main() {  
   // cannot explicitly instantiate in function  
   template int A::getit<long>(int i, long * it);   // C2252  
}  
```