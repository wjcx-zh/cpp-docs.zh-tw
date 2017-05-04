---
title: "UnorderedMap::Lookup 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::UnorderedMap::Lookup"
ms.assetid: 6f9bb393-3791-423d-bfee-925e0531e1a5
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# UnorderedMap::Lookup 方法
取得與類型為 K 之指定機碼相關聯且類型為 V 的值。  
  
## 語法  
  
```scr  
V Lookup(  
   K key  
);  
```  
  
#### 參數  
 `key`  
 用來在 UnorderedMap 中尋找元素的機碼。`key` 的類型為 typename *K*。  
  
## 傳回值  
 與 `key` 配對的值。 傳回值的類型為 typename *V*。  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [集合](../cppcx/collections-c-cx.md)   
 [Platform::Collections::UnorderedMap 類別](../cppcx/platform-collections-unorderedmap-class.md)