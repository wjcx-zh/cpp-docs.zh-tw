---
title: "VectorViewIterator::operator+ 運算子 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorViewIterator::operator+"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorViewIterator::operator+ 運算子"
ms.assetid: 8206de2f-61b3-49cd-9715-d57695d880b3
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorViewIterator::operator+ 運算子
傳回 VectorViewIterator ，參考從指定的 VectorViewIterator 開始指定位移的項目。  
  
## 語法  
  
```  
  
VectorViewIterator operator+(  
   difference_type n  
) const;  
  
template <  
   typename T  
>   
inline VectorViewIterator<T> operator+  
   (ptrdiff_t n,   
   const VectorViewIterator<T>& i  
);  
  
```  
  
#### 參數  
 `T`  
 在第二個語法中，是 VectorViewIterator 的 typename。  
  
 `n`  
 整數位移。  
  
 `i`  
 在第二個語法中是 VectorViewIterator。  
  
## 傳回值  
 在第一個語法中是 VectorViewIterator，參考從目前 VectorViewIterator 開始指定位移的項目。  
  
 在第二個語法中是 VectorViewIterator，參考從參數 `i` 的開頭開始指定位移的項目。  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [Platform::Collections::VectorViewIterator 類別](../cppcx/platform-collections-vectorviewiterator-class.md)