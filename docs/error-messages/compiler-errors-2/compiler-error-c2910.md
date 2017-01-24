---
title: "編譯器錯誤 C2910 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2910"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2910"
ms.assetid: 09c50e6a-e099-42f6-8ed6-d80e292a7a36
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2910
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function' : 無法明確地特製化  
  
 編譯器偵測到兩次嘗試要明確地特製化函式。  
  
 下列範例會產生 C2910：  
  
```  
// C2910.cpp  
// compile with: /c  
template <class T>  
struct S;  
  
template <> struct S<int> { void f() {} };  
template <> void S<int>::f() {}   // C2910 delete this specialization  
```  
  
 如果您嘗試明確地特製化非樣板成員，也可能會產生 C2910。  也就是說，您只能明確地特製化函式樣板。  
  
 下列範例會產生 C2910：  
  
```  
// C2910b.cpp  
// compile with: /c  
template <class T> struct A {  
   A(T* p);  
};  
  
template <> struct A<void> {  
   A(void* p);  
};  
  
template <class T>  
inline A<T>::A(T* p) {}  
  
template <> A<void>::A(void* p){}   // C2910  
// try the following line instead  
// A<void>::A(void* p){}  
```  
  
 對 Visual Studio .NET 2003 的編譯器完成符合標準處理後也會出現這個錯誤。  
  
 若要使程式碼在 Visual C\+\+ 的 Visual Studio .NET 2003 和 Visual Studio .NET 版本中都有效，請移除 `template <>`。  
  
 下列範例會產生 C2910：  
  
```  
// C2910c.cpp  
// compile with: /c  
template <class T> class A {  
   void f();  
};  
  
template <> class A<int> {  
   void f();  
};  
  
template <> void A<int>::f() {}   // C2910  
// try the following line instead  
// void A<int>::f(){}   // OK  
```