---
title: "Vector::Vector 建構函式 | Microsoft Docs"
ms.custom: ""
ms.date: "01/24/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::Vector::Vector"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Vector::Vector 建構函式"
ms.assetid: 5454433d-e206-45ea-bc8b-bb5a7bf38c17
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Vector::Vector 建構函式
初始化 Vector 類別的新執行個體。  
  
## 語法  
  
```  
Vector();  
  
explicit Vector(  
    unsigned int size  
    );  
  
Vector(  
    unsigned int size,  
    T value  
    );  
  
template <typename U> explicit Vector(  
    const ::std::vector<U>& v  
    );  
  
template <typename U> explicit Vector(  
    std::vector<U>&& v  
    );  
  
Vector(  
    const T * ptr,  
    unsigned int size  
    );  
  
template <size_t N> explicit Vector(  
    const T(&arr)[N]  
    );  
  
template <size_t N> explicit Vector(  
    const std::array<T, N>& a  
    );  
  
explicit Vector(  
    const Array<T>^ arr  
    );  
  
template <typename InIt> Vector(  
    InIt first,  
    InIt last  
    );  
  
Vector(  
    std::initializer_list<T> il  
    );  
```  
  
#### 參數  
 a  
 將用來初始化 Vector 的 [std::array](../standard-library/array-class-stl.md) 物件。  
  
 a  
 將用來初始化 Vector 的 [Platform::Array](../cppcx/platform-array-class.md) 物件。  
  
 `InIt`  
 用來初始化目前 Vector 的物件集合類型。  
  
 il  
 類型為 `T` 之物件的 [std::initializer\_list](../standard-library/initializer-list-class.md)，將用來初始化 Vector。  
  
 `N`  
 用來初始化目前 Vector 之物件集合中的項目數。  
  
 `size`  
 Vector 中的項目數。  
  
 `value`  
 用來初始化目前 Vector 中各個項目的值。  
  
 `v`  
 用來初始化目前 Vector 之 [std::vector](../Topic/vector%20Class%201.md) 的 [Lvalues 和 Rvalues](~/cpp/lvalues-and-rvalues-visual-cpp.md)。  
  
 `ptr`  
 用來初始化目前 Vector 之 `std::vector` 的指標。  
  
 `arr`  
 用來初始化目前 Vector 的 [Platform::Array](../cppcx/platform-array-class.md) 物件。  
  
 `a`  
 用來初始化目前 Vector 的 [std::array](../Topic/vector%20Class%201.md) 物件。  
  
 `first`  
 用來初始化目前 Vector 之物件序列中的第一個項目。 透過「*完美轉送*」\(Perfect Forwarding\) 的方式傳遞的 `first` 型别。 如需詳細資訊，請參閱[右值參考宣告子：&&](~/cpp/rvalue-reference-declarator-amp-amp.md)。  
  
 `last`  
 用來初始化目前 Vector 之物件序列中的最後一個項目。 透過「*完美轉送*」\(Perfect Forwarding\) 的方式傳遞的 `last` 型别。 如需詳細資訊，請參閱[右值參考宣告子：&&](~/cpp/rvalue-reference-declarator-amp-amp.md)。  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [Platform::Collections::Vector 類別](../cppcx/platform-collections-vector-class.md)   
 [集合 \(C\+\+\/CX\)](../cppcx/collections-c-cx.md)