---
title: "陣列建構函式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vccorlib/Platform::Array::Array"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Array::Array"
ms.assetid: befb8088-3915-4b5c-b7fd-90f79961412d
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# 陣列建構函式
初始化由類別範本參數 *T* 所指定之可修改的一維類型陣列。  
  
## 語法  
  
```  
  
Array(unsigned int size);  
Array(T* data, unsigned int size);  
  
```  
  
#### 參數  
 `T`  
 類別樣板參數。  
  
 `size`  
 陣列中的項目數。  
  
 `data`  
 用來初始化此 Array 物件的 `T` 類型資料陣列的指標。  
  
## 備註  
 如需如何建立 Platform::Array 執行個體的詳細資訊，請參閱[Array 和 WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)。  
  
## 需求  
 **標頭：**vccorlib.h  
  
 **命名空間：**Platform  
  
## 請參閱  
 [Platform::Array 類別](../cppcx/platform-array-class.md)