---
title: "WriteOnlyArray::set 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vccorlib/Platform::WriteOnlyArray::set"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "WriteOnlyArray::set 函式"
ms.assetid: 0359f922-f25e-47d1-b7df-87e7fd0f76e5
caps.latest.revision: 8
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# WriteOnlyArray::set 函式
在陣列中指定的索引處設定指定的值。  
  
## 語法  
  
```cpp  
T& set(  
   unsigned int indexArg,  
   T valueArg);  
```  
  
#### 參數  
 `indexArg`  
 要設定之元素的索引。  
  
 `valueArg`  
 要在 `indexArg` 設定的值。  
  
## 傳回值  
 剛才設定之元素的參考。  
  
## 需求  
 **標頭：**vccorlib.h  
  
 **命名空間：**Platform  
  
## 請參閱  
 [Platform::WriteOnlyArray 類別](../cppcx/platform-writeonlyarray-class.md)   
 [Array 和 WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)