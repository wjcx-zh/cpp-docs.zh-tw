---
title: "begin 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "01/22/2017"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Windows::Foundation::Collections::begin"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "begin 函式"
ms.assetid: 5a44fb33-e247-49fd-b7a1-4a5b42e9e1e4
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 4
---
# begin 函式
傳回迭代器，指向指定的介面參數所存取之集合的開頭。  
  
## 語法  
  
```  
  
template <typename T>   
    ::Platform::Collections::VectorIterator<T>   
    begin(  
          IVector<T>^ v         );  
  
template <typename T>   
    ::Platform::Collections::VectorViewIterator<T>   
    begin(  
          IVectorView<T>^ v  
         );   
  
template <typename T>   
    ::Platform::Collections::InputIterator<T>   
    begin(  
          IIterable<T>^ i         );  
  
```  
  
#### 參數  
 `T`  
 樣板類型參數。  
  
 `v`  
 IVector\<T\> 或 IVectorView\<T\> 介面所存取的 Vector\<T\> 或 VectorView\<T\> 物件集合。  
  
 `i`  
 IIterable\<T\> 介面所存取的任意 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]物件集合。  
  
## 傳回值  
 指向集合開頭的迭代器。  
  
## 備註  
 前兩個樣板函式會傳回迭代器，第三個樣板函式會傳回輸入迭代器。  
  
 begin 傳回的 VectorIterator 物件是會儲存類型為 VectorProxy\<T\> 的 Proxy 迭代器。 不過，對使用者程式碼來說，Proxy 物件永遠都像是不存在一樣。 如需詳細資訊，請參閱[集合 \(C\+\+\/CX\)](../cppcx/collections-c-cx.md)。  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Windows::Foundation::Collections  
  
## 請參閱  
 [Windows::Foundation::Collections 命名空間](../cppcx/windows-foundation-collections-namespace-c-cx.md)