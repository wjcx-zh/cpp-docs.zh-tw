---
title: "Platform::Collections::UnorderedMap 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::UnorderedMap"
ms.assetid: dc84f261-b13c-4c0a-9b57-30dcb9e3065e
caps.latest.revision: 7
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 7
---
# Platform::Collections::UnorderedMap 類別
代表未排序的 *Map*，這是機碼值組的集合。  
  
## 語法  
  
```scr  
template <  
   typename K,  
   typename V,  
   typename C = std::equal_to<K>  
>  
ref class Map sealed;  
```  
  
#### 參數  
 `K`  
 機碼值組中，機碼的類型。  
  
 `V`  
 機碼值組中，值的型別。  
  
 `C`  
 一個型別，提供函式物件，可以根據排序鍵比較兩個項目值，判斷它們在 Map 中的相對順序。 預設是 [std::equal\_to\<K\>](../standard-library/equal-to-struct.md)。  
  
## 備註  
 可使用的型別如下：  
  
-   整數  
  
-   介面類別 ^  
  
-   公用 ref 類別^  
  
-   value struct  
  
-   公用列舉類別  
  
 UnorderedMap 基本上是 [std::unordered\_map](../standard-library/unordered-map-class.md) 的包裝函式，可以儲存 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 類型。 它是類型為 [Windows::Foundation::Collections::IMap](http://go.microsoft.com/fwlink/p/?LinkId=262408) 和 [IObservableMap](http://msdn.microsoft.com/library/windows/apps/br226050.aspx) 且在公用 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 介面之間傳遞的具象實作。 如果您嘗試在公用傳回值或參數中使用 Platform::Collections::UnorderedMap 類型，則會引發編譯器錯誤 C3986。 您可以將參數或傳回值的類型變更為 [Windows::Foundation::Collections::IMap](http://go.microsoft.com/fwlink/p/?LinkId=262408) 來修正錯誤。  
  
 如需詳細資訊，請參閱[集合](../cppcx/collections-c-cx.md)。  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|UnorderedMap::UnorderedMap 建構函式|初始化 Map 類別的新執行個體。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[UnorderedMap::Clear 方法](../cppcx/unorderedmap-clear-method.md)|從目前 Map 物件移除所有機碼值組。|  
|[UnorderedMap::First 方法](../cppcx/unorderedmap-first-method.md)|傳回迭代器，指定 Map 中的第一個項目。|  
|[UnorderedMap::GetView 方法](../cppcx/unorderedmap-getview-method.md)|傳回目前 Map 的唯讀檢視，也就是 Platform::Collections::UnorderedMapView 類別。|  
|[UnorderedMap::HasKey 方法](../cppcx/unorderedmap-haskey-method.md)|判斷目前 Map 是否包含指定的機碼。|  
|[UnorderedMap::Insert 方法](../cppcx/unorderedmap-insert-method.md)|將指定的機碼值組加入目前 Map 物件中。|  
|[UnorderedMap::Lookup 方法](../cppcx/unorderedmap-lookup-method.md)|擷取目前 Map 物件中，所指定機碼處的項目。|  
|[UnorderedMap::Remove 方法](../cppcx/unorderedmap-remove-method.md)|從目前 Map 物件中刪除指定的機碼值組。|  
|[UnorderedMap::Size 方法](../cppcx/unorderedmap-size-method.md)|傳回目前 Map 物件中的項目數。|  
  
### 事件  
  
|||  
|-|-|  
|名稱|描述|  
|[Map::MapChanged 事件](../cppcx/map-mapchanged-event.md) `event`|發生於 Map 變更時。|  
  
## 繼承階層  
 `UnorderedMap`  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [\(NOTINBUILD\) Platform 命名空間](http://msdn.microsoft.com/zh-tw/f3ce3eab-028c-4204-ba9f-9ab8af17c8c4)   
 [Platform::Collections 命名空間](../cppcx/platform-collections-namespace.md)   
 [Platform::Collections::Map 類別](../cppcx/platform-collections-map-class.md)   
 [Platform::Collections::UnorderedMapView 類別](../cppcx/platform-collections-unorderedmapview-class.md)   
 [集合](../cppcx/collections-c-cx.md)   
 [在 C\+\+ 中建立 Windows 執行階段元件](../Topic/Creating%20Windows%20Runtime%20Components%20in%20C++.md)