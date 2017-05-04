---
title: "to_vector 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Windows::Foundation::Collections::to_vector"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "to_vector 函式"
ms.assetid: 9cdd5123-7243-4def-a1d3-162e0bf6219e
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 3
---
# to_vector 函式
傳回 `std::vector`，其值與指定的 IVector 或 IVectorView 參數的基礎集合相同。  
  
## 語法  
  
```  
template <  
   typename T  
>  
inline ::std::vector<T> to_vector(  
   IVector<T>^ v  
);  
template <  
   typename T  
>  
inline ::std::vector<T> to_vector(  
   IVectorView<T>^ v  
);  
```  
  
#### 參數  
 `T`  
 樣板類型參數。  
  
 `v`  
 IVector 或 IVectorView 介面，提供對基礎 Vector 或 VectorView 物件的存取。  
  
## 傳回值  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Windows::Foundation::Collections  
  
## 請參閱  
 [Windows::Foundation::Collections 命名空間](../cppcx/windows-foundation-collections-namespace-c-cx.md)