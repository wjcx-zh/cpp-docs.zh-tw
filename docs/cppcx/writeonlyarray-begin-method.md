---
title: "WriteOnlyArray::begin 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vccorlib/Platform::WriteOnlyArray::begin"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "WriteOnlyArray::begin 方法"
ms.assetid: 25025fa0-8f55-4abf-93ad-71db45ddfae3
caps.latest.revision: 7
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# WriteOnlyArray::begin 方法
傳回陣列中第一個元素的指標。  
  
## 語法  
  
```cpp  
T* begin() const;  
```  
  
## 傳回值  
 陣列中第一個元素的指標。  
  
## 備註  
 這個迭代器可與 `std::sort` 這類 STL 演算法搭配使用，針對陣列元素執行作業。  
  
## 需求  
 **標頭：**vccorlib.h  
  
 **命名空間：**Platform  
  
## 請參閱  
 [Platform::WriteOnlyArray 類別](../cppcx/platform-writeonlyarray-class.md)   
 [Array 和 WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)