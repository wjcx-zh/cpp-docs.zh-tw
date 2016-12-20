---
title: "陣列共變數 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "陣列 [c + +]、 共異變數"
ms.assetid: 889fdde3-85fe-44d5-bf2d-d3d4aa14e746
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "mithom"
manager: "douge"
---
# 陣列共變數
指定直接或間接基底類別 B 的參考類別 D，D 型別的陣列可以被指派給陣列變數的型別 b。  
  
```  
// clr_array_covariance.cpp  
// compile with: /clr  
using namespace System;  
  
int main() {  
   // String derives from Object  
   array<Object^>^ oa = gcnew array<String^>(20);  
}  
```  
  
## 備註  
 指派至陣列元素都必須設定相容與動態陣列的型別。 指派至陣列元素與不相容的類型會導致擲回 System::ArrayTypeMismatchException。  
  
 陣列共異變數並不適用於實值類別型別的陣列。 例如，陣列的 Int32 無法轉換為物件 ^ 陣列時，即使是透過 boxing。  
  
## 範例  
  
```  
// clr_array_covariance2.cpp  
// compile with: /clr  
using namespace System;  
  
ref struct Base { int i; };  
ref struct Derived  : Base {};  
ref struct Derived2 : Base {};  
ref struct Derived3 : Derived {};  
ref struct Other { short s; };  
  
int main() {  
   // Derived* d[] = new Derived*[100];  
   array<Derived^> ^ d = gcnew array<Derived^>(100);  
  
   // ok by array covariance  
   array<Base ^> ^  b = d;  
  
   // invalid  
   // b[0] = new Other;  
  
   // error (runtime exception)  
   // b[1] = gcnew Derived2;  
  
   // error (runtime exception),  
   // must be "at least" a Derived.  
   // b[0] = gcnew Base;  
  
   b[1] = gcnew Derived;  
   b[0] = gcnew Derived3;  
}  
```  
  
## 請參閱  
 [Arrays](../windows/arrays-cpp-component-extensions.md)