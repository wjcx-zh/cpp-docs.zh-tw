---
title: "WriteOnlyArray::end 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vccorlib/Platform::WriteOnlyArray::end"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "WriteOnlyArray::end 方法"
ms.assetid: 045045fe-f210-400b-b688-7abb95fc702a
caps.latest.revision: 7
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# WriteOnlyArray::end 方法
傳回陣列中最後一個元素後加一的指標。  
  
## 語法  
  
```cpp  
T* end() const;  
```  
  
## 傳回值  
 陣列中最後一個元素後加一的指標迭代器。  
  
## 備註  
 這個迭代器可與 STL 演算法搭配使用，針對陣列元素執行像是 `std::sort` 這類作業。  
  
## 需求  
 **標頭：**vccorlib.h  
  
 **命名空間：**Platform  
  
## 請參閱  
 [Platform::WriteOnlyArray 類別](../cppcx/platform-writeonlyarray-class.md)   
 [Array 和 WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)