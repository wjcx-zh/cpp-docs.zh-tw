---
title: "UnorderedMapView::HasKey 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::UnorderedMapView::HasKey"
ms.assetid: 4704da18-8606-4df7-be51-d125b2e4aee0
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# UnorderedMapView::HasKey 方法
判斷目前 UnorderedMap 是否包含指定的機碼。  
  
## 語法  
  
```cpp  
  
bool HasKey(  
   K key  
);  
```  
  
#### 參數  
 `key`  
 用來尋找元素的機碼。`key` 的類型為 typename *K*。  
  
## 傳回值  
 如果找到機碼則為 `true`，否則為 `false`。  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [Platform::Collections::UnorderedMap 類別](../cppcx/platform-collections-unorderedmap-class.md)   
 [集合](../cppcx/collections-c-cx.md)   
 [Windows::Foundation::Collections::IKeyValuePair\<K,V\>](http://msdn.microsoft.com/library/windows/apps/br226031.aspx)