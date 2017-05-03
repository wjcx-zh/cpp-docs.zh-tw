---
title: "UnorderedMap::HasKey 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/13/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::UnorderedMap::HasKey"
ms.assetid: 7c397cdc-82f6-470a-8a3c-f5ba2cc58ed6
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# UnorderedMap::HasKey 方法
判斷目前 UnorderedMap 是否包含指定的機碼。  
  
## 語法  
  
```scr  
  
bool HasKey(  
   K key  
);  
```  
  
#### 參數  
 `key`  
 用來尋找 UnorderedMap 元素的機碼。`key` 的類型為 typename *K*。  
  
## 傳回值  
 如果找到機碼則為 `true`，否則為 `false`。  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [Platform::Collections::UnorderedMap 類別](../cppcx/platform-collections-unorderedmap-class.md)   
 [集合](../cppcx/collections-c-cx.md)   
 [Windows::Foundation::Collections::IKeyValuePair\<K,V\>](http://msdn.microsoft.com/library/windows/apps/br226031.aspx)