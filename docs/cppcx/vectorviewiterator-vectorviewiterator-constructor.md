---
title: "VectorViewIterator::VectorViewIterator 建構函式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorViewIterator::VectorViewIterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorViewIterator::VectorViewIterator 建構函式"
ms.assetid: 30bf643a-4100-4547-b34c-ce16c89f78ed
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorViewIterator::VectorViewIterator 建構函式
初始化 VectorViewIterator 類別的新執行個體。  
  
## 語法  
  
```  
  
VectorViewIterator();  
  
explicit VectorViewIterator(  
   Windows::Foundation::Collections::IVectorView<T>^ v  
);  
```  
  
#### 參數  
 `v`  
 IVectorView\<T\> 物件。  
  
## 備註  
 第一個語法範例是預設建構函式。 第二個語法範例是用來從 IVectorView\<T\> 物件建構 VectorViewIterator 的明確建構函式。  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [Platform::Collections::VectorViewIterator 類別](../cppcx/platform-collections-vectorviewiterator-class.md)