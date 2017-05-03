---
title: "Vector::First 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::Vector::First"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Vector::First 方法"
ms.assetid: ca6b7b55-dd49-4346-bfa4-d8010b228d44
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Vector::First 方法
傳回指向 Vector 中第一項元素的迭代器。  
  
## 語法  
  
```  
  
virtual Windows::Foundation::Collections::IIterator <T>^   
   First();  
```  
  
## 傳回值  
 指向 Vector 中第一項元素的迭代器。  
  
## 備註  
 若要保留 First\(\) 所傳回的迭代器，為使用 [auto](../Topic/auto%20\(C++\).md) 型别推斷關鍵字進行宣告的變數指派傳回值，是很方便的方式。 例如，`auto x = myVector->First();`。 此迭代器知道集合的長度。  
  
 當您需要對 STL 函式傳遞成對的迭代器時，請使用不受限的函式 [Windows::Foundation::Collections::begin](../cppcx/begin-function.md) 和 [Windows::Foundation::Collections::end](../cppcx/end-function.md)  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [Platform::Collections::Vector 類別](../cppcx/platform-collections-vector-class.md)   
 [集合](../cppcx/collections-c-cx.md)