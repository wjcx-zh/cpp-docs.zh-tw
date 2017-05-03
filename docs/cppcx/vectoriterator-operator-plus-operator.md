---
title: "VectorIterator::operator+ 運算子 | Microsoft Docs"
ms.custom: ""
ms.date: "12/13/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorIterator::operator+"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorIterator::operator+ 運算子"
ms.assetid: 5e907537-7d10-4766-a412-e7ea08b3456a
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorIterator::operator+ 運算子
傳回 VectorIterator ，參考從指定的 VectorIterator 開始指定位移的項目。  
  
## 語法  
  
```  
  
VectorIterator operator+(  
   difference_type n) ;  
  
template <  
   typename T  
>  
inline VectorIterator<T> operator+(  
   ptrdiff_t n,  
   const VectorIterator<T>& i  
);  
  
```  
  
#### 參數  
 `T`  
 在第二個語法中，是 VectorIterator 的 typename。  
  
 `n`  
 整數位移。  
  
 `i`  
 在第二個語法中是 VectorIterator。  
  
## 傳回值  
 在第一個語法中是 VectorIterator，參考從目前 VectorIterator 開始指定位移的項目。  
  
 在第二個語法中是 VectorIterator，參考從參數 `i` 的開頭開始指定位移的項目。  
  
## 備註  
 第一個語法範例  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [\(NOTINBUILD\) Platform 命名空間](http://msdn.microsoft.com/zh-tw/f3ce3eab-028c-4204-ba9f-9ab8af17c8c4)