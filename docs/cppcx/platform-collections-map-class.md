---
title: Platform::Collections::Map 類別
ms.date: 10/01/2019
ms.topic: reference
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
helpviewer_keywords:
- Map Class (C++/Cx)
ms.assetid: 2b8cf968-1167-4898-a149-1195b32c1785
ms.openlocfilehash: 7f41a924811be95160b06a2097db6103cde8fc11
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354440"
---
# <a name="platformcollectionsmap-class"></a>Platform::Collections::Map 類別

代表 *Map*，這是機碼值組的集合。 在[Windows:基礎:集合::I 可觀察映射](/uwp/api/windows.foundation.collections.iobservablemap_k_v_)以幫助進行 XAML[資料繫結](/windows/uwp/data-binding/data-binding-in-depth)。

## <a name="syntax"></a>語法

```cpp
template <
   typename K,
   typename V,
   typename C = std::less<K>>
ref class Map sealed;
```

### <a name="parameters"></a>參數

*K*<br/>
機碼值組中，機碼的類型。

*五*<br/>
機碼值組中，值的型別。

*C*<br/>
一個型別，提供函式物件，可以根據排序鍵比較兩個項目值，判斷它們在 Map 中的相對順序。 預設情況下[,std::減\<去 K>](../standard-library/less-struct.md)。

*__is_valid_winrt_type()* 編譯器產生的函數,用於驗證*K*和*V*的類型,並在類型無法儲存在 Map 中時提供友好的錯誤訊息。

### <a name="remarks"></a>備註

允許的類型為：

- 整數

- 介面類*

- 公用 ref 類別^

- value struct

- 公用列舉類別

Map 基本上是 [std::map](../standard-library/map-class.md)的包裝函式。 C++ 它是[Windows::基礎:集合::iMap<Windows:基礎:集合::iKeyValuePair\<K,V>>](/uwp/api/Windows.Foundation.Collections.IMap_K_V_)和 I[可觀察映射](/uwp/api/Windows.Foundation.Collections.IObservableMap_K_V_)類型,這些類型通過公共 Windows 運行時介面傳遞。 如果您嘗試在公用傳回值或參數中使用 `Platform::Collections::Map` 類型，則會引發編譯器錯誤 C3986。 您可以通過更改參數的類型或將值返回到[Windows::基礎:集合::IMap\<K,V>来](/uwp/api/Windows.Foundation.Collections.IMap_K_V_)修復錯誤。

有關詳細資訊,請參閱[集合](../cppcx/collections-c-cx.md)。

### <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[地圖:地圖](#ctor)|初始化 Map 類別的新執行個體。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[地圖:清除](#clear)|從目前 Map 物件移除所有機碼值組。|
|[地圖:第一](#first)|傳回迭代器，指定 Map 中的第一個項目。|
|[地圖::取得檢視](#getview)|傳回目前 Map 的唯讀檢視，也就是 [Platform::Collections::MapView Class](../cppcx/platform-collections-mapview-class.md)。|
|[地圖::哈斯鍵](#haskey)|判斷目前 Map 是否包含指定的機碼。|
|[地圖::插入](#insert)|將指定的機碼值組加入目前 Map 物件中。|
|[地圖::尋找](#lookup)|擷取目前 Map 物件中，所指定機碼處的項目。|
|[Map::Remove](#remove)|從目前 Map 物件中刪除指定的機碼值組。|
|[地圖::大小](#size)|傳回目前 Map 物件中的項目數。|

### <a name="events"></a>事件

|||
|-|-|
|名稱|描述|
|[對應::對應已變更](#mapchanged)事件|發生於 Map 變更時。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

`Map`

### <a name="requirements"></a>需求

**標頭：** collection.h

**命名空間：** Platform::Collections

## <a name="mapclear-method"></a><a name="clear"></a>對應:清除方法

從目前 Map 物件移除所有機碼值組。

### <a name="syntax"></a>語法

```cpp
virtual void Clear();
```

## <a name="mapfirst-method"></a><a name="first"></a>映射:第一種方法

傳回指定 Map 中第一個元素的迭代器。如果 Map 是空的，則傳回 `nullptr`。

### <a name="syntax"></a>語法

```cpp
virtual Windows::Foundation::Collections::IIterator<
Windows::Foundation::Collections::IKeyValuePair<K, V>^>^ First();
```

### <a name="return-value"></a>傳回值

迭代器，指定對應中的第一個元素。

### <a name="remarks"></a>備註

保存 First() 傳回的反覆運算器的一個方便方法是將返回值分配給使用**自動**類型扣減關鍵字聲明的變數。 例如： `auto x = myMap->First();` 。

## <a name="mapgetview-method"></a><a name="getview"></a>映射::獲取檢視方法

返回當前地圖的唯讀檢視;即[,平臺:集合::mapView 類](../cppcx/platform-collections-mapview-class.md),實現 [Windows::基礎:集合:集合::IMapView\<K,V>]/uwp/api/Windows.Foundation.集合.IMapView_K_V_)介面。

### <a name="syntax"></a>語法

```cpp
Windows::Foundation::Collections::IMapView<K, V>^ GetView();
```

### <a name="return-value"></a>傳回值

`MapView` 物件。

## <a name="maphaskey-method"></a><a name="haskey"></a>映射::有鍵方法

判斷目前 Map 是否包含指定的機碼。

### <a name="syntax"></a>語法

```cpp
bool HasKey(K key);
```

### <a name="parameters"></a>參數

*關鍵*<br/>
用來尋找 Map 項目的機碼。 *鍵*的類型是類型名稱*K*。

### <a name="return-value"></a>傳回值

如果找到金鑰,**則為 true;** 否則,**假**。

## <a name="mapinsert-method"></a><a name="insert"></a>對應:插入方法

將指定的機碼值組加入目前 Map 物件中。

### <a name="syntax"></a>語法

```cpp
virtual bool Insert(K key, V value);
```

### <a name="parameters"></a>參數

*關鍵*<br/>
機碼值組的機碼部分。 *鍵*的類型是類型名稱*K*。

*值*<br/>
機碼值組的值部分。 *值*的類型是類型名稱*V*。

### <a name="return-value"></a>傳回值

如果目前 Map 中現有元素的鍵與*鍵*匹配,並且該元素的值部分設置為*值*,**則為 true。** 如果當前 Map 中不存在現有元素與*鍵*匹配,並且*鍵*和*值*參數被製成鍵值對,然後添加到當前 Map,**則為 false。**

## <a name="maplookup-method"></a><a name="lookup"></a>映射::查找方法

取得與類型為 K 之指定機碼 (如果該機碼存在的話) 相關聯且類型為 V 的值。

### <a name="syntax"></a>語法

```cpp
V Lookup(K key);
```

### <a name="parameters"></a>參數

*關鍵*<br/>
用來在 Map 中尋找元素的機碼。 *鍵*的類型是類型名稱*K*。

### <a name="return-value"></a>傳回值

與*鍵*配對的值。 傳回值的型態為類型名稱*V*。

### <a name="remarks"></a>備註

如果金鑰不存在,則引發[一個平臺::OutOfsexception。](../cppcx/platform-outofboundsexception-class.md)

## <a name="mapmap-constructor"></a><a name="ctor"></a>映射::地圖建構函數

初始化 Map 類別的新執行個體。

### <a name="syntax"></a>語法

```cpp
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

*Init*<br/>
目前 Map 的 typename。

*Comp*<br/>
一個型別，提供函式物件，可以根據排序鍵比較兩個項目值，判斷它們在 Map 中的相對順序。

*米*<br/>
對 用於初始化當前映`map Class`射 的引用或[rvalue。](../cpp/lvalues-and-rvalues-visual-cpp.md)

*第一*<br/>
用來初始化目前 Map 的項目範圍中，第一個項目的輸入迭代器。

*最後*<br/>
用來初始化目前 Map 的項目範圍以外第一個項目的輸入迭代器。

## <a name="mapmapchanged-event"></a><a name="mapchanged"></a>對應:對應已變更事件

在對應中插入或移除項目時引發。

### <a name="syntax"></a>語法

```cpp
event Windows::Foundation::Collections::MapChangedEventHandler<K,V>^ MapChanged;
```

### <a name="property-valuereturn-value"></a>屬性值/傳回值

[MapChangeEventHandler\<K,V>,](/uwp/api/windows.foundation.collections.mapchangedeventhandler)其中包含有關引發事件的物件以及發生的更改類型的資訊。 另請參閱[IMapChangeEventArgs\<K>](/uwp/api/Windows.Foundation.Collections.IMapChangedEventArgs_K_)與[集合變更枚舉](/uwp/api/windows.foundation.collections.collectionchange)。

## <a name="net-framework-equivalent"></a>.NET Framework 同等

使用 C# 或可視化基本專案\<IMap K 的\<Windows 執行時應用 ,V>为 I 字典 K,V>。

## <a name="mapremove-method"></a><a name="remove"></a>對應::移除方法

從目前 Map 物件中刪除指定的機碼值組。

### <a name="syntax"></a>語法

```cpp
virtual void Remove(K key);
```

### <a name="parameters"></a>參數

*關鍵*<br/>
機碼值組的機碼部分。 *鍵*的類型是類型名稱*K*。

## <a name="mapsize-method"></a><a name="size"></a>對應:大小方法

返回地圖中的[Windows::基礎:集合::IKeyValuePair\<K,V>](/uwp/api/Windows.Foundation.Collections.IKeyValuePair_K_V_)元素。

### <a name="syntax"></a>語法

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>傳回值

Map 中的元素數目。

## <a name="see-also"></a>另請參閱

[集合(C++/CX)](collections-c-cx.md)<br/>
[平台命名空間](platform-namespace-c-cx.md)<br/>
[在 C++ 中建立 Windows 執行階段元件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
