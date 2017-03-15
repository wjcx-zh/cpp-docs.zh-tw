---
title: "&lt;map&gt; 函式 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7cb3d1a5-7add-4726-a73f-61927eafd466
caps.latest.revision: 6
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 85c900f2263ae1c1089478badc85388e3b5e8548
ms.openlocfilehash: d322b318ac4206c5bc27b81299190d129548ef9f
ms.lasthandoff: 02/24/2017

---
# <a name="ltmapgt-functions"></a>&lt;map&gt; 函式
|||  
|-|-|  
|[swap (map)](#swap)|[swap (multimap)](#swap_multimap)|  
  
##  <a name="a-nameswapmultimapa--swap--map"></a><a name="swap_multimap"></a>  swap  (map)
 交換兩個對應的項目。  
  
```  
template <class key, class T, class _Pr, class _Alloc>  
void swap(
    map<Key, Traits, Compare, Alloctor>& left,  
    map<Key, Traits, Compare, Alloctor>& right);
```  
  
### <a name="parameters"></a>參數  
 ` right`  
 提供要交換之元素的 map，或要與 map ` left` 交換元素的 map。  
  
 ` left`  
 要與 map ` right` 交換元素的 map。  
  
### <a name="remarks"></a>備註  
 範本函式是在容器類別 map 特製化的演算法，用來執行成員函式 ` left.`[swap](../standard-library/map-class.md#map__swap)*( right*)。 這是編譯器所執行的函式範本部分排序執行個體。 當因範本函式多載而導致範本與函式呼叫的比對不是唯一的時，編譯器就會選取最特製化的範本函式版本。 演算法類別中樣板函式的一般版本 **template** \< **class T**> **void swap**( **T&**, **T&**) 會依指派運作，且作業緩慢。 每個容器中的特製化版本運作速度會更快，因為它可以與容器類別的內部表示法一起運作。  
  
### <a name="example"></a>範例  
  如需使用 `swap` 的範本版本的範例，請參閱成員函式 [map::swap](../standard-library/map-class.md#map__swap) 的程式碼範例。  
  
##  <a name="a-nameswapa--swap--multimap"></a><a name="swap"></a>  swap  (multimap)
 交換兩個 multimap 的元素。  
  
```  
template <class key, class T, class _Pr, class _Alloc>  
void swap(
    multimap<Key, Traits, Compare, Alloctor>& left,  
    multimap<Key, Traits, Compare, Alloctor>& right);
```  
  
### <a name="parameters"></a>參數  
 ` right`  
 提供要交換之元素的 multimap，或要與 multimap ` left` 交換元素的 multimap。  
  
 ` left`  
 要與 multimap ` right` 交換元素的 multimap。  
  
### <a name="remarks"></a>備註  
 範本函式是在容器類別 map 特製化的演算法，用來執行成員函式 ` left.`[swap](../standard-library/multimap-class.md#multimap__swap) ( ` right`)。 這是編譯器所執行的函式範本部分排序執行個體。 當因範本函式多載而導致範本與函式呼叫的比對不是唯一的時，編譯器就會選取最特製化的範本函式版本。 演算法類別中樣板函式的一般版本 **template** \< **class T**> **void swap**( **T&**, **T&**) 會依指派運作，且作業緩慢。 每個容器中的特製化版本運作速度會更快，因為它可以與容器類別的內部表示法一起運作。  
  
### <a name="example"></a>範例  
  如需使用 `swap` 的範本版本的範例，請參閱成員函式 [multimap::swap](../standard-library/multimap-class.md#multimap__swap) 的程式碼範例。  
  
## <a name="see-also"></a>另請參閱  
 [\<map>](../standard-library/map.md)

