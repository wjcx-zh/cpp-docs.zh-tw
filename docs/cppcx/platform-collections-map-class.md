---
title: "Std:: map 類別 |Microsoft 文件"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- COLLECTION/Platform::Collections::Map::Map
- COLLECTION/Platform::Collections::Map::Clear
- COLLECTION/Platform::Collections::Map::First
- COLLECTION/Platform::Collections::Map::GetView
- COLLECTION/Platform::Collections::Map::HasKey
- COLLECTION/Platform::Collections::Map::Insert
- COLLECTION/Platform::Collections::Map::Lookup
- COLLECTION/Platform::Collections::Map::Remove
- COLLECTION/Platform::Collections::Map::Size
dev_langs: C++
helpviewer_keywords: Map Class (C++/Cx)
ms.assetid: 2b8cf968-1167-4898-a149-1195b32c1785
caps.latest.revision: "19"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a3893f7213bc2b154851a5d2481070d0d43724bc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="platformcollectionsmap-class"></a>Platform::Collections::Map 類別
代表 *Map*，這是機碼值組的集合。  
  
## <a name="syntax"></a>語法  
  
```  
template <  
   typename K,  
   typename V,  
   typename C = std::less<K>>  
ref class Map sealed;  
```  
#### <a name="parameters"></a>參數  
 `K`  
 機碼值組中，機碼的類型。  
  
 `V`  
 機碼值組中，值的型別。  
  
 `C`  
 一個型別，提供函式物件，可以根據排序鍵比較兩個項目值，判斷它們在 Map 中的相對順序。 根據預設， [std:: less<>\<K >](../standard-library/less-struct.md)。  
  
 __is_valid_winrt_type()  
 編譯器產生的函式，它會驗證 K 和 V 的類型。如果該類型無法儲存在 Map 中，則會提供易懂的錯誤訊息。  
  
### <a name="remarks"></a>備註  
 可使用的型別如下：  
  
-   整數  
  
-   介面類別 ^  
  
-   公用 ref 類別^  
  
-   value struct  
  
-   公用列舉類別  
  
 Map 基本上是 [std::map](../standard-library/map-class.md)的包裝函式。 它是 c + + 具象實作[Windows::Foundation::Collections::IMap < Windows::Foundation::Collections::IKeyValuePair\<K，V >>](http://go.microsoft.com/fwlink/p/?LinkId=262408)和[IObservableMap](http://msdn.microsoft.com/library/windows/apps/br226050.aspx)Windows 執行階段介面的公用之間傳遞的型別。 如果您嘗試在公用傳回值或參數中使用 `Platform::Collections::Map` 類型，則會引發編譯器錯誤 C3986。 您可以修正這個錯誤的參數或傳回值的型別變更[Windows::Foundation::Collections::IMap\<K，V >](http://go.microsoft.com/fwlink/p/?LinkId=262408)。  
  
 如需詳細資訊，請參閱[集合](../cppcx/collections-c-cx.md)。  
  
### <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[Map:: map](#ctor)|初始化 Map 類別的新執行個體。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[Map:: clear](#clear)|從目前 Map 物件移除所有機碼值組。|  
|[Map:: first](#first)|傳回迭代器，指定 Map 中的第一個項目。|  
|[Map:: getview](#getview)|傳回目前 Map 的唯讀檢視，也就是 [Platform::Collections::MapView Class](../cppcx/platform-collections-mapview-class.md)。|  
|[Map:: haskey](#haskey)|判斷目前 Map 是否包含指定的機碼。|  
|[Map:: insert](#insert)|將指定的機碼值組加入目前 Map 物件中。|  
|[Map:: lookup](#lookup)|擷取目前 Map 物件中，所指定機碼處的項目。|  
|[Map:: remove](#remove)|從目前 Map 物件中刪除指定的機碼值組。|  
|[Map:: size](#size)|傳回目前 Map 物件中的項目數。|  
  
### <a name="events"></a>事件  
  
|||  
|-|-|  
|名稱|描述|  
|[Map:: mapchanged](#mapchanged-event.md)`event`|發生於 Map 變更時。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `Map`  
  
### <a name="requirements"></a>需求  
 **標頭：** collection.h  
  
 **命名空間：** Platform::Collections  

## <a name="clear"></a>Map:: clear 方法
從目前 Map 物件移除所有機碼值組。  
  
### <a name="syntax"></a>語法  
  
```    
virtual void Clear();   
```  
  


## <a name="first"></a>Map:: first 方法
傳回指定 Map 中第一個元素的迭代器。如果 Map 是空的，則傳回 `nullptr`。  
  
### <a name="syntax"></a>語法  
  
```    
virtual Windows::Foundation::Collections::IIterator<  
Windows::Foundation::Collections::IKeyValuePair<K, V>^>^ First();  
```  
  
### <a name="return-value"></a>傳回值  
 迭代器，指定對應中的第一個元素。  
  
### <a name="remarks"></a>備註  
 若要保留 first （） 所傳回的迭代器的簡便方法是宣告的變數指派傳回值**自動**型别推斷關鍵字。 例如，`auto x = myMap->First();`。  
  


## <a name="getview"></a>Map:: getview 方法
傳回目前 Map 的唯讀檢視也就是說， [Platform::Collections::MapView 類別](../cppcx/platform-collections-mapview-class.md)，它會實作[Windows::Foundation::Collections::IMapView\<K，V >](http://msdn.microsoft.com/library/windows/apps/br226037.aspx)介面。  
  
### <a name="syntax"></a>語法  
  
```    
Windows::Foundation::Collections::IMapView<K, V>^ GetView();  
```  
  
### <a name="return-value"></a>傳回值  
 `MapView` 物件。  
  


## <a name="haskey"></a>Map:: haskey 方法
判斷目前 Map 是否包含指定的機碼。  
  
### <a name="syntax"></a>語法  
  
```    
bool HasKey(K key);  
```  
  
### <a name="parameters"></a>參數  
 `key`  
 用來尋找 Map 項目的機碼。 型別`key`為 typename *K*。  
  
### <a name="return-value"></a>傳回值  
 如果找到機碼則為 `true`，否則為 `false`。  
  


## <a name="insert"></a>Map:: insert 方法
將指定的機碼值組加入目前 Map 物件中。  
  
### <a name="syntax"></a>語法  
  
```  
  
virtual bool Insert(K key, V value);  
```  
  
### <a name="parameters"></a>參數  
 `key`  
 機碼值組的機碼部分。 型別`key`為 typename *K*。  
  
 `value`  
 機碼值組的值部分。 型別`value`為 typename *V*。  
  
### <a name="return-value"></a>傳回值  
 如果目前 Map 中現有項目的機碼符合 `true`，且該項目的值部分設定為 `key`，則為 `value`。 如果目前 Map 中沒有任何現有項目符合 `false`，且 `key` 參數和 `key` 參數已成為機碼值組接著加入目前 Map，則為 `value`。  
  


## <a name="lookup"></a>Map:: lookup 方法
取得與類型為 K 之指定機碼 (如果該機碼存在的話) 相關聯且類型為 V 的值。  
  
### <a name="syntax"></a>語法  
  
```  
V Lookup(K key);  
```  
  
### <a name="parameters"></a>參數  
 `key`  
 用來在 Map 中尋找元素的機碼。 型別`key`為 typename *K*。  
  
### <a name="return-value"></a>傳回值  
 與 `key` 配對的值。 傳回值的類型為 typename *V*。  
  
### <a name="remarks"></a>備註  
 如果索引鍵不存在，則[platform:: outofboundsexception](../cppcx/platform-outofboundsexception-class.md)就會擲回。  
  


## <a name="ctor"></a>Map:: map 建構函式
初始化 Map 類別的新執行個體。  
  
### <a name="syntax"></a>語法  
  
```  
explicit Map(const C& comp = C());  
explicit Map(const StdMap& m);  
explicit Map(StdMap&& m ;  
template <typename InIt>  
Map(  
   InItfirst,  
   InItlast,  
   const C& comp = C());  
```  
  
### <a name="parameters"></a>參數  
 `InIt`  
 目前 Map 的 typename。  
  
 `comp`  
 一個型別，提供函式物件，可以根據排序鍵比較兩個項目值，判斷它們在 Map 中的相對順序。  
  
 `m`  
 參考或[Lvalues 和 Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md)至`map Class`用來初始化目前 Map。  
  
 `first`  
 用來初始化目前 Map 的項目範圍中，第一個項目的輸入迭代器。  
  
 `last`  
 用來初始化目前 Map 的項目範圍以外第一個項目的輸入迭代器。  
  


## <a name="mapchanged"></a>Map:: mapchanged 事件
在對應中插入或移除項目時引發。  
  
### <a name="syntax"></a>語法  
  
```cpp  
event Windows::Foundation::Collections::MapChangedEventHandler<K,V>^ MapChanged;  
```  
  
### <a name="property-valuereturn-value"></a>屬性值/傳回值  
 A [Mapchangedeventhandler<k\<K，V >](http://msdn.microsoft.com/library/windows/apps/br206644.aspx)包含引發事件，以及類型的發生變更之物件的相關資訊。 另請參閱[IMapChangedEventArgs\<K >](http://msdn.microsoft.com/library/windows/apps/br226034.aspx)和[CollectionChange 列舉](http://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.collectionchange.aspx)。  
  
## <a name="net-framework-equivalent"></a>.NET Framework 同等  
 Windows 市集應用程式使用 C# 或 Visual Basic 專案 Imap<k\<K，V > 做為 Idictionary<k\<K，V >。  
  


## <a name="remove"></a>Map:: remove 方法
從目前 Map 物件中刪除指定的機碼值組。  
  
### <a name="syntax"></a>語法  
  
```    
virtual void Remove(K key);  
```  
  
### <a name="parameters"></a>參數  
 `key`  
 機碼值組的機碼部分。 型別`key`為 typename *K*。  
  


## <a name="size"></a>Map:: size 方法
傳回的數目[Windows::Foundation::Collections::IKeyValuePair\<K，V >](http://msdn.microsoft.com/library/windows/apps/br226031.aspx)對應中的項目。  
  
### <a name="syntax"></a>語法  
  
```    
virtual property unsigned int Size;  
```  
  
### <a name="return-value"></a>傳回值  
 Map 中的元素數目。  
  

  
## <a name="see-also"></a>請參閱  
 [Platform 命名空間](platform-namespace-c-cx.md)   
 [在 c + + 中建立 Windows 執行階段元件](/MicrosoftDocs/windows-uwp/blob/docs/windows-apps-src/winrt-components/creating-windows-runtime-components-in-cpp.md)