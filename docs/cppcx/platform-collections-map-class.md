---
title: "Platform::Collections::Map 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::Map"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Map 類別 (C++/Cx)"
ms.assetid: 2b8cf968-1167-4898-a149-1195b32c1785
caps.latest.revision: 19
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 19
---
# Platform::Collections::Map 類別
代表 *Map*，這是機碼值組的集合。  
  
## 語法  
  
```  
template <  
   typename K,  
   typename V,  
   typename C = std::less<K>  
ref class Map sealed;  
```  
  
#### 參數  
 `K`  
 機碼值組中，機碼的類型。  
  
 `V`  
 機碼值組中，值的型別。  
  
 `C`  
 一個型別，提供函式物件，可以根據排序鍵比較兩個項目值，判斷它們在 Map 中的相對順序。 預設為 [std::less\<K\>](../standard-library/less-struct.md)。  
  
 \_\_is\_valid\_winrt\_type\(\)  
 編譯器產生的函式，它會驗證 K 和 V 的類型。如果該類型無法儲存在 Map 中，則會提供易懂的錯誤訊息。  
  
## 備註  
 可使用的型別如下：  
  
-   整數  
  
-   介面類別 ^  
  
-   公用 ref 類別^  
  
-   value struct  
  
-   公用列舉類別  
  
 Map 基本上是 [std::map](../standard-library/map-class.md) 的包裝函式。 它是類型為 [Windows::Foundation::Collections::IMap\<Windows::Foundation::Collections::IKeyValuePair\<K,V\>\>](http://go.microsoft.com/fwlink/p/?LinkId=262408) 和 [IObservableMap](http://msdn.microsoft.com/library/windows/apps/br226050.aspx) 且在公用 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]介面之間傳遞的 C\+\+ 具象實作。 如果您嘗試在公用傳回值或參數中使用 `Platform::Collections::Map` 類型，則會引發編譯器錯誤 C3986。 您可以將參數或傳回值的類型變更為 [Windows::Foundation::Collections::IMap\<K,V\>](http://go.microsoft.com/fwlink/p/?LinkId=262408) 來修正錯誤。  
  
 如需詳細資訊，請參閱[集合](../cppcx/collections-c-cx.md)。  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[Map::Map 建構函式](../cppcx/map-map-constructor.md)|初始化 Map 類別的新執行個體。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[Map::Clear 方法](../cppcx/map-clear-method.md)|從目前 Map 物件移除所有機碼值組。|  
|[Map::First 方法](../cppcx/map-first-method.md)|傳回迭代器，指定 Map 中的第一個項目。|  
|[Map::GetView 方法](../cppcx/map-getview-method.md)|傳回目前 Map 的唯讀檢視，也就是 [Platform::Collections::MapView 類別](../cppcx/platform-collections-mapview-class.md)。|  
|[Map::HasKey 方法](../cppcx/map-haskey-method.md)|判斷目前 Map 是否包含指定的機碼。|  
|[Map::Insert 方法](../cppcx/map-insert-method.md)|將指定的機碼值組加入目前 Map 物件中。|  
|[Map::Lookup 方法](../cppcx/map-lookup-method.md)|擷取目前 Map 物件中，所指定機碼處的項目。|  
|[Map::Remove 方法](../cppcx/map-remove-method.md)|從目前 Map 物件中刪除指定的機碼值組。|  
|[Map::Size 方法](../cppcx/map-size-method.md)|傳回目前 Map 物件中的項目數。|  
  
### 事件  
  
|||  
|-|-|  
|名稱|描述|  
|[Map::MapChanged 事件](../cppcx/map-mapchanged-event.md) `event`|發生於 Map 變更時。|  
  
## 繼承階層  
 `Map`  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [\(NOTINBUILD\) Platform 命名空間](http://msdn.microsoft.com/zh-tw/f3ce3eab-028c-4204-ba9f-9ab8af17c8c4)   
 [在 C\+\+ 中建立 Windows 執行階段元件](http://msdn.microsoft.com/library/5b7251e6-4271-4f13-af80-c1cf5b1489bf)