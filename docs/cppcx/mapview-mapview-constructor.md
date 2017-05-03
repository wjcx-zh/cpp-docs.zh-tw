---
title: "MapView::MapView 建構函式 | Microsoft Docs"
ms.custom: ""
ms.date: "01/25/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::MapView::MapView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MapView::MapView 建構函式"
ms.assetid: 67a3250c-b527-47ac-a103-0fd186046d71
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# MapView::MapView 建構函式
初始化 MapView 類別的新執行個體。  
  
## 語法  
  
```  
explicit MapView(  
    const C& comp = C()  
    );  
  
explicit MapView(  
    const ::std::map<K, V, C>& m  
    );  
  
explicit MapView(  
    std::map<K, V, C>&& m  
    );  
  
template <typename InIt> MapView(  
    InIt first,  
    InIt last,  
    const C& comp = C()  
    );  
  
MapView(::std::initializer_list<  
    std::pair<const K, V>> il,  
    const C& comp = C()  
    );  
```  
  
#### 參數  
 `InIt`  
 目前 MapView 的 typename。  
  
 `comp`  
 函式物件。這個函式物件可以根據排序機碼比較兩個元素值，判斷它們在 MapView 中的相對順序。  
  
 `m`  
 用來初始化目前 MapView 之 [Lvalues 和 Rvalues](../Topic/Lvalues%20and%20Rvalues%20\(Visual%20C++\).md) 的參考或 [map 類別](../standard-library/map-class.md)。  
  
 `first`  
 用來初始化目前 MapView 的項目範圍中，第一個項目的輸入迭代器。  
  
 `last`  
 用來初始化目前 MapView 的項目範圍以外第一個項目的輸入迭代器。  
  
 il  
 [std::initializer\_list\<std::pair\<K,V\>\>](../standard-library/initializer-list-class.md)，其元素將插入至 MapView。  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [Platform::Collections::MapView 類別](../cppcx/platform-collections-mapview-class.md)