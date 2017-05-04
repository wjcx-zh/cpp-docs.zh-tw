---
title: "Map::Insert 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::Map::Insert"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Map::Insert"
ms.assetid: 3acb2221-c12f-407a-a570-2e52df3569f6
caps.latest.revision: 2
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Map::Insert 方法
將指定的機碼值組加入目前 Map 物件中。  
  
## 語法  
  
```  
  
virtual bool Insert(  
   K key,   
   V value  
);  
```  
  
#### 參數  
 `key`  
 機碼值組的機碼部分。`key` 的類型為 typename *K*。  
  
 `value`  
 機碼值組的值部分。`value` 的類型是 typename *V*。  
  
## 傳回值  
 如果目前 Map 中現有項目的機碼符合 `true`，且該項目的值部分設定為 `key`，則為 `value`。 如果目前 Map 中沒有任何現有項目符合 `false`，且 `key` 參數和 `key` 參數已成為機碼值組接著加入目前 Map，則為 `value`。  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [Platform::Collections::Map 類別](../cppcx/platform-collections-map-class.md)