---
title: "back_inserter 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Windows::Foundation::Collections::back_inserter"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "back_inserter 函式"
ms.assetid: 91476338-5548-44b7-bc7e-2150f4fbe31a
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 4
---
# back_inserter 函式
傳回迭代器，用來在指定的集合結尾插入元素。  
  
## 語法  
  
```  
  
template <  
   typename T  
   >  
   ::Platform::BackInsertIterator<T>   
    back_inserter(  
                  IVector<T>^ v  
                 );  
  
template <  
   typename T  
   >  
   ::Platform::BackInsertIterator<T>   
   back_inserter(  
                IObservableVector<T>^ v  
                );  
```  
  
#### 參數  
 `T`  
 樣板類型參數。  
  
 `v`  
 提供存取基礎集合的介面指標。  
  
## 傳回值  
 迭代器。  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Windows::Foundation::Collections  
  
## 請參閱  
 [Windows::Foundation::Collections 命名空間](../cppcx/windows-foundation-collections-namespace-c-cx.md)