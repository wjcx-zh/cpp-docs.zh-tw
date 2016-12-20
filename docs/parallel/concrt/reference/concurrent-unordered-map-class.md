---
title: "concurrent_unordered_map 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concurrent_unordered_map/concurrency::concurrent_unordered_map"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "concurrent_unordered_map 類別"
ms.assetid: b2d879dd-87ef-4af9-a266-a5443fd538b8
caps.latest.revision: 13
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# concurrent_unordered_map 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`concurrent_unordered_map` 類別是並行安全容器，控制類型 `std::pair<const _Key_type, _Element_type>` 的項目的不同長度序列。  序列的表示方式導致啟用並行安全附加、項目存取、迭代器存取及迭代器周遊作業。  
  
## 語法  
  
```  
template <  
   typename _Key_type,  
   typename _Element_type,  
   typename _Hasher = std::tr1::hash<_Key_type>,  
   typename _Key_equality = std::equal_to<_Key_type>,  
   typename _Allocator_type = std::allocator<std::pair<const _Key_type,  
   _Element_type> >  
>  
, typename _Key_equality = std::equal_to<_Key_type>, typename _Allocator_type = std::allocator<std::pair<const _Key_type, _Element_type> > > class concurrent_unordered_map : public details::_Concurrent_hash< details::_Concurrent_unordered_map_traits<_Key_type, _Element_type, details::_Hash_compare<_Key_type, _Hasher, _Key_equality>, _Allocator_type, false> >;  
```  
  
#### 參數  
 `_Key_type`  
 金鑰類型。  
  
 `_Element_type`  
 對應的類型。  
  
 `_Hasher`  
 雜湊函式物件類型。  此引數是選擇性的，而且預設值是 `std::tr1::hash<``_Key_type``>`。  
  
 `_Key_equality`  
 相等比較函式物件類型。  此引數是選擇性的，而且預設值是 `std::equal_to<``_Key_type``>`。  
  
 `_Allocator_type`  
 代表預存配置器物件 \(此物件會封裝有關配置和解除配置並行未排序對應之記憶體的詳細資訊\) 的類型。  此引數是選擇性的，而且預設值是 `std::allocator<std::pair<``_Key_type`、 `_Element_type``>>`。  
  
## Members  
  
### 公用 Typedefs  
  
|名稱|描述|  
|--------|--------|  
|`allocator_type`|管理儲存體的配置器類型。|  
|`const_iterator`|用於受控制序列的常數迭代器類型。|  
|`const_local_iterator`|用於受控制序列的常數 bucket 迭代器類型。|  
|`const_pointer`|項目的常數指標類型。|  
|`const_reference`|項目的常數參考類型。|  
|`difference_type`|兩個項目之間的帶正負號距離的類型。|  
|`hasher`|雜湊函式的類型。|  
|`iterator`|受控制序列中 iterator 的類型。|  
|`key_equal`|比較函式的類型。|  
|`key_type`|排序索引鍵的類型。|  
|`local_iterator`|用於受控制序列的 bucket 迭代器類型。|  
|`mapped_type`|與每個索引鍵關聯的對應值類型。|  
|`pointer`|項目的指標類型。|  
|`reference`|項目的參考類型。|  
|`size_type`|兩個項目之間的不帶正負號距離的類型。|  
|`value_type`|項目的類型。|  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[concurrent\_unordered\_map::concurrent\_unordered\_map 建構函式](../Topic/concurrent_unordered_map::concurrent_unordered_map%20Constructor.md)|多載。  建構並行未排序對應。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[concurrent\_unordered\_map::at 方法](../Topic/concurrent_unordered_map::at%20Method.md)|多載。  使用指定的索引鍵值，尋找 `concurrent_unordered_map` 中的項目。  這個方法是並行安全的。|  
|[concurrent\_unordered\_map::hash\_function 方法](../Topic/concurrent_unordered_map::hash_function%20Method.md)|取得儲存的雜湊函式物件。|  
|[concurrent\_unordered\_map::insert 方法](../Topic/concurrent_unordered_map::insert%20Method.md)|多載。  將項目加入至 `concurrent_unordered_map` 物件。|  
|[concurrent\_unordered\_map::key\_eq 方法](../Topic/concurrent_unordered_map::key_eq%20Method.md)|取得儲存的相等比較函式物件。|  
|[concurrent\_unordered\_map::swap 方法](../Topic/concurrent_unordered_map::swap%20Method.md)|交換兩個 `concurrent_unordered_map` 物件的內容。  這個方法不是並行安全的。|  
|[concurrent\_unordered\_map::unsafe\_erase 方法](../Topic/concurrent_unordered_map::unsafe_erase%20Method.md)|多載。  移除指定位置的 `concurrent_unordered_map` 項目。  這個方法不是並行安全的。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[concurrent\_unordered\_map::operatorOperator](../Topic/concurrent_unordered_map::operatorOperator.md)|多載。  尋找或插入具有指定索引鍵的項目。  這個方法是並行安全的。|  
|[concurrent\_unordered\_map::operator\= 運算子](../Topic/concurrent_unordered_map::operator=%20Operator.md)|多載。  將另一個 `concurrent_unordered_map` 物件的內容指派給這一個。  這個方法不是並行安全的。|  
  
## 備註  
 如需關於 `concurrent_unordered_map` 類別的詳細資訊，請參閱 [平行容器和物件](../../../parallel/concrt/parallel-containers-and-objects.md)。  
  
## 繼承階層架構  
 `_Traits`  
  
 `_Concurrent_hash`  
  
 `concurrent_unordered_map`  
  
## 需求  
 **標頭：**concurrent\_unordered\_map.h  
  
 **命名空間：**concurrency  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [平行容器和物件](../../../parallel/concrt/parallel-containers-and-objects.md)