---
title: "UnorderedMapView::UnorderedMapView 建構函式 | Microsoft Docs"
ms.custom: ""
ms.date: "01/25/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::UnorderedMapView::UnorderedMapView"
ms.assetid: 408aa6ca-dd8d-4946-a817-42a31d19f429
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# UnorderedMapView::UnorderedMapView 建構函式
初始化 UnorderedMapView 類別的新執行個體。  
  
## 語法  
  
```cpp  
  
UnorderedMapView();  
  
explicit UnorderedMapView(size_t n);  
  
UnorderedMapView(size_t n, const H& h);  
  
UnorderedMapView(size_t n, const H& h, const P& p);  
  
explicit UnorderedMapView(  
    const std::unordered_map<K, V, H, P>& m  
    );  
explicit UnorderedMapView(  
    std::unordered_map<K, V, H, P>&& m  
    );  
  
template <typename InIt> UnorderedMapView(  
    InIt first,  
    InIt last  
    );  
  
template <typename InIt> UnorderedMapView(  
    InIt first,  
    InIt last,  
    size_t n  
    );  
  
template <typename InIt> UnorderedMapView(  
    InIt first,  
    InIt last,  
    size_t n,  
    const H& h  
    );  
  
template <typename InIt> UnorderedMapView(  
    InIt first,  
    InIt last,  
    size_t n,  
    const H& h,  
    const P& p  
    );  
  
UnorderedMapView(  
    std::initializer_list<std::pair<const K, V>> il  
    );  
  
UnorderedMapView(  
    std::initializer_list< std::pair<const K, V>> il,  
    size_t n  
    );  
  
UnorderedMapView(  
    std::initializer_list< std::pair<const K, V>> il,  
    size_t n,  
    const H& h  
    );  
  
UnorderedMapView(  
    std::initializer_list< std::pair<const K, V>> il,  
    size_t n,  
    const H& h,  
    const P& p  
    );  
```  
  
#### 參數  
 n  
 要為其預先配置空間的元素數目。  
  
 `InIt`  
 UnorderedMapView 的 typename。  
  
 `H`  
 可為機碼產生雜湊值的函式物件。 如果是 `std::hash` 支援的類型，則預設是 [std::hash\<K\>](http://msdn.microsoft.com/zh-tw/54f67435-af9d-4217-a29d-fa4d2491a104)。  
  
 `P`  
 可提供函式物件用來比較兩個機碼是否相等的類型。 預設是 [std::equal\_to\<K\>](../standard-library/equal-to-struct.md)。  
  
 `m`  
 用來初始化 UnorderedMapView 之 [std::unordered\_map](../standard-library/unordered-map-class.md) 的參考或 [Lvalues 和 Rvalues](~/cpp/lvalues-and-rvalues-visual-cpp.md)。  
  
 `first`  
 用來初始化 UnorderedMapView 的項目範圍中，第一個元素的輸入迭代器。  
  
 `last`  
 用來初始化 UnorderedMapView 的項目範圍以外第一個元素的輸入迭代器。  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [Platform::Collections::UnorderedMapView 類別](../cppcx/platform-collections-unorderedmapview-class.md)