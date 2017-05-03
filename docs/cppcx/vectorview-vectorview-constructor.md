---
title: "VectorView::VectorView 建構函式 | Microsoft Docs"
ms.custom: ""
ms.date: "01/24/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorView::VectorView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorView::VectorView 建構函式"
ms.assetid: 5ec14dbc-5f6f-44b6-8fc4-f5a31053eb5f
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorView::VectorView 建構函式
初始化 VectorView 類別的新執行個體。  
  
## 語法  
  
```  
VectorView();  
explicit VectorView(  
   UInt32 size  
);  
VectorView(  
   UInt32 size,  
   T value  
);  
explicit VectorView(  
   const ::std::vector<T>& v  
);  
explicit VectorView(  
   ::std::vector<T>&& v  
);  
VectorView(  
   const T * ptr,  
   UInt32 size  
);  
  
template <  
   size_t N  
>  
explicit VectorView(  
   const T (&arr)[N]  
);  
  
template <  
   size_t N  
>  
explicit VectorView(  
   const ::std::array<T,  
   N>& a  
);  
  
explicit VectorView(  
   const ::Platform::Array<T>^ arr  
);  
  
template <  
   typename InIt  
>  
VectorView(  
   InItfirst,  
   InItlast  
);  
  
VectorView(  
   std::initializer_list<T> il  
);  
```  
  
#### 參數  
 `InIt`  
 用來初始化目前 VectorView 的物件集合類型。  
  
 il  
 其元素將用來初始化 VectorView 的 [std::initializer\_list](../standard-library/initializer-list-class.md)。  
  
 `N`  
 用來初始化目前 VectorView 之物件集合中的項目數。  
  
 `size`  
 VectorView 中的項目數。  
  
 `value`  
 用來初始化目前 VectorView 中各個項目的值。  
  
 `v`  
 用來初始化目前 VectorView 之 [::std::vector](../Topic/vector%20Class%201.md) 的 [Lvalues 和 Rvalues](../Topic/Lvalues%20and%20Rvalues%20\(Visual%20C++\).md)。  
  
 `ptr`  
 用來初始化目前 VectorView 之 `std::vector` 的指標。  
  
 `arr`  
 用來初始化目前 VectorView 的 [Platform::Array](../cppcx/platform-array-class.md) 物件。  
  
 `a`  
 用來初始化目前 VectorView 的 [std::array](../Topic/vector%20Class%201.md) 物件。  
  
 `first`  
 用來初始化目前 VectorView 之物件序列中的第一個項目。 透過「*完美轉送*」\(Perfect Forwarding\) 的方式傳遞的 `first` 型别。 如需詳細資訊，請參閱[右值參考宣告子：&&](../Topic/Rvalue%20Reference%20Declarator:%20&&.md)。  
  
 `last`  
 用來初始化目前 VectorView 之物件序列中的最後一個項目。 透過「*完美轉送*」\(Perfect Forwarding\) 的方式傳遞的 `last` 型别。 如需詳細資訊，請參閱[右值參考宣告子：&&](../Topic/Rvalue%20Reference%20Declarator:%20&&.md)。  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [Platform::Collections::Vector 類別](../cppcx/platform-collections-vector-class.md)