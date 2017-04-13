---
title: "編譯器錯誤 C3206 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3206
dev_langs:
- C++
helpviewer_keywords:
- C3206
ms.assetid: d62995b5-e349-4418-bbe8-8a5e776ca7b0
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 62b23c33d1c2aada0e490cdf1dfe14e3abc6c713
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c3206"></a>編譯器錯誤 C3206
'function' : 'param' 的類型引數無效，類別類型 'typename' 遺漏類型引數清單  
  
 樣板函式定義為使用範本類型引數。 不過，傳遞了樣板類樣板引數。  
  
 下列範例會產生 C3206：  
  
```  
// C3206.cpp  
template <class T>  
void f() {}  
  
template <class T>  
struct S {};  
  
void f1() {  
   f<S>();   // C3206  
   // try the following line instead  
   // f<S<int> >();  
}  
```  
  
 可能的解決方式：  
  
```  
// C3206b.cpp  
// compile with: /c  
template <class T>  
void f() {}  
  
template <class T>  
struct S {};  
  
void f1() {  
   f<S<int> >();  
}  
```  
  
 使用泛型時，也會發生 C3206：  
  
```  
// C3206c.cpp  
// compile with: /clr  
generic <class GT1>  
void gf() {}  
  
generic <class T>  
value struct GS {};  
  
int main() {  
   gf<GS>();   // C3206  
}  
```  
  
 可能的解決方式：  
  
```  
// C3206d.cpp  
// compile with: /clr  
generic <class GT1>  
void gf() {}  
  
generic <class T>  
value struct GS {};  
  
int main() {  
   gf<GS<int> >();  
}  
```  
  
 此錯誤也可能因為 Visual C++ .NET 2003 中的編譯器一致性處理而產生，其中類別樣板不允許作為範本類型引數。  
  
 類別樣板不允許作為範本類型引數。 這過去在 Visual C++ .NET 2003 中可行，但它現在是無效的 C++。  
  
 下列範例可在 Visual C++ .NET 2002 中編譯，但在 Visual C++ .NET 2003 中將會失敗：  
  
```  
// C3206e.cpp  
template <class T>  
struct S {};  
  
template <class T>  
void func() {   // takes a type  
   T<int> t;  
}  
  
int main() {  
   func<S>();   // C3206 S is not a type.  
}  
```  
  
 可能的解決方式：  
  
```  
// C3206f.cpp  
template <class T>  
struct S {};  
  
template <class T>  
void func() {   // takes a type  
   T t;  
}  
  
int main() {  
   func<S<int> >();  
}  
```  
  
 如果樣板類樣板參數是必要的，則 Visual C++ .NET 2003 和 Visual C++ .NET 2002 版本中都有效的錯誤解決方法需要您將函式包裝在使用樣板類樣板參數的樣板類別中：  
  
```  
// C3206g.cpp  
template <class T>  
struct S {};  
  
template<template<class> class TT>  
struct X {  
   static void func() {  
      TT<int> t1;  
      TT<char> t2;  
   }  
};  
  
int main() {  
   X<S>::func();  
}  
```
