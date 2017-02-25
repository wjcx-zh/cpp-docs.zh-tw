---
title: "編譯器錯誤 C2912 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2912"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2912"
ms.assetid: bd55cecd-ab1a-4636-ab8a-a00393fe7b3d
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# 編譯器錯誤 C2912
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

明確特製化 'declaration' 不是函式樣板的特製化  
  
 您不能特製化非樣板函式。  
  
 下列範例會產生 C2912：  
  
```  
// C2912.cpp  
// compile with: /c  
void f(char);  
template<> void f(char);   // C2912  
template<class T> void f(T);   // OK  
```  
  
 因為編譯器一致性處理是在 Visual Studio.NET 2003 中完成，也會產生這個錯誤：針對每個明確特製化，您必須選擇明確特製化的參數，以致於它們會符合主要範本的參數。  
  
```  
// C2912b.cpp  
class CF {  
public:  
   template <class A> CF(const A& a) {}   // primary template  
  
   // attempted explicit specialization  
   template <> CF(const char* p) {}   // C2912  
  
   // try the following line instead  
   // template <> CF(const char& p) {}  
};  
```