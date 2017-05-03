---
title: "UnorderedMap::UnorderedMap 建構函式 | Microsoft Docs"
ms.custom: ""
ms.date: "01/25/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::UnorderedMap::UnorderedMap"
ms.assetid: bd62e663-7f3a-43ef-ad6d-8266128c778b
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# UnorderedMap::UnorderedMap 建構函式
初始化 UnorderedMap 類別的新執行個體。  
  
## 語法  
  
```scr  
UnorderedMap();  
  
  explicit UnorderedMap(  
      size_t n  
      );  
  
  UnorderedMap(  
      size_t n,  
      const H& h  
      );  
  
  UnorderedMap(  
      size_t n,  
      const H& h,  
      const P& p  
      );  
  
  explicit UnorderedMap(  
      const std::unordered_map<K, V, H, P>& m  
      );  
  
  explicit UnorderedMap(  
      std::unordered_map<K, V, H, P>&& m  
      );  
  
  template <typename InIt> UnorderedMap(  
      InIt first,  
      InIt last  
      );  
  
  template <typename InIt> UnorderedMap(  
      InIt first,  
      InIt last,  
      size_t n  
      );  
  
  template <typename InIt> UnorderedMap(  
      InIt first,  
      InIt last,  
      size_t n,  
      const H& h  
      );  
  
  template <typename InIt> UnorderedMap(  
      InIt first,  
      InIt last,  
      size_t n,  
      const H& h,  
      const P& p  
      );  
  
  UnorderedMap(std::initializer_list<  
      std::pair<const K, V>> il  
      );  
  
  UnorderedMap(::std::initializer_list<  
      std::pair<const K, V>> il,  
      size_t n  
      );  
  
  UnorderedMap(  
      ::std::initializer_list< ::std::pair<const K, V>> il,  
      size_t n,  
      const H& h  
      );  
  
  UnorderedMap(::std::initializer_list<  
      ::std::pair<const K, V>> il,  
      size_t n,  
      const H& h,  
      const P& p  
      );  
```  
  
#### 參數  
 `InIt`  
 目前 UnorderedMap 的 typename。  
  
 `P`  
 可比較兩個機碼以判斷它們是否相等的函式物件。 這個參數預設為 [std::equal\_to\<K\>](../standard-library/equal-to-struct.md)。  
  
 `H`  
 可為機碼產生雜湊值的函式物件。 如果是 [hash 類別](../Topic/hash%20Class%201.md)支援的機碼類型，那麼這個參數預設為該類別。  
  
 `m`  
 用來初始化目前 UnorderedMap 之 [std::unordered\_map](../standard-library/unordered-map-class.md) 的參考或 [Lvalues 和 Rvalues](../Topic/Lvalues%20and%20Rvalues%20\(Visual%20C++\).md)。  
  
 il  
 將用來初始化對應之 [std::pair](../standard-library/initializer-list-class.md) 物件的 [std::initializer\_list](../standard-library/pair-structure.md)。  
  
 `first`  
 用來初始化目前 UnorderedMap 的元素範圍中第一個元素的輸入迭代器。  
  
 `last`  
 用來初始化目前 UnorderedMap 的元素範圍以外第一個元素的輸入迭代器。  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [Platform::Collections 命名空間](../cppcx/platform-collections-namespace.md)   
 [集合](../cppcx/collections-c-cx.md)