---
title: "MapView::HasKey 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::MapView::HasKey"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MapView::HasKey 方法"
ms.assetid: c1a24f63-e6fd-4cfd-90ce-b89352b98324
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# MapView::HasKey 方法
判斷目前 MapView 是否包含指定的機碼。  
  
## 語法  
  
```  
  
bool HasKey(  
   K key  
);  
```  
  
#### 參數  
 `key`  
 用來尋找 MapView 項目的機碼。`key` 的類型為 typename *K*。  
  
## 傳回值  
 如果找到機碼則為 `true`，否則為 `false`。  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [Platform::Collections::MapView 類別](../cppcx/platform-collections-mapview-class.md)