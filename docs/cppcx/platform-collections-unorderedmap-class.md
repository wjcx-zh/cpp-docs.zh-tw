---
title: Platform::Collections::UnorderedMap 類別
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- collection/Platform::Collections::UnorderedMap
ms.assetid: dc84f261-b13c-4c0a-9b57-30dcb9e3065e
ms.openlocfilehash: c6f702850f5bf84b8b1bc857c9d0a744728d0cbd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354424"
---
# <a name="platformcollectionsunorderedmap-class"></a>Platform::Collections::UnorderedMap 類別

代表未排序的 *Map*，這是機碼值組的集合。

## <a name="syntax"></a>語法

```cpp
template <
   typename K,
   typename V,
   typename C = std::equal_to<K>
>
ref class Map sealed;
```

#### <a name="parameters"></a>參數

*K*<br/>
機碼值組中，機碼的類型。

*五*<br/>
機碼值組中，值的型別。

*C*<br/>
一個型別，提供函式物件，可以根據排序鍵比較兩個項目值，判斷它們在 Map 中的相對順序。 預設情況下[,std::equal_to\<K>](../standard-library/equal-to-struct.md)。

### <a name="remarks"></a>備註

允許的類型為：

- 整數

- 介面類*

- 公用 ref 類別^

- value struct

- 公用列舉類別

**無序映射**基本上是用於支援存儲 Windows 運行時類型的[unordered_map](../standard-library/unordered-map-class.md)的包裝。 它是[Windows::基礎:集合::IMap](/uwp/api/Windows.Foundation.Collections.IMap_K_V_)和[I 可觀察映射](/uwp/api/Windows.Foundation.Collections.IObservableMap_K_V_)類型的具體實現,它們通過公共 Windows 運行時介面傳遞。 如果您嘗試在公用傳回值或參數中使用 `Platform::Collections::UnorderedMap` 類型，則會引發編譯器錯誤 C3986。 您可以將參數或傳回值的類型變更為 [Windows::Foundation::Collections::IMap](/uwp/api/Windows.Foundation.Collections.IMap_K_V_)來修正錯誤。

有關詳細資訊,請參閱[集合](../cppcx/collections-c-cx.md)。

### <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[無序對應:無序映射](#ctor)|初始化 Map 類別的新執行個體。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[沒有序映射::清除](#clear)|從目前 Map 物件移除所有機碼值組。|
|[無序映射::第一](#first)|傳回迭代器，指定 Map 中的第一個項目。|
|[沒有順序對應:取得檢視](#getview)|傳回目前 Map 的唯讀檢視，也就是 Platform::Collections::UnorderedMapView 類別。|
|[無序映射::哈斯鍵](#haskey)|判斷目前 Map 是否包含指定的機碼。|
|[沒有序映射:插入](#insert)|將指定的機碼值組加入目前 Map 物件中。|
|[無序映射::尋找](#lookup)|擷取目前 Map 物件中，所指定機碼處的項目。|
|[沒有序映射::刪除](#remove)|從目前 Map 物件中刪除指定的機碼值組。|
|[沒有順序對應:大小](#size)|傳回目前 Map 物件中的項目數。|

### <a name="events"></a>事件

|||
|-|-|
|名稱|描述|
|[對應::對應已變更](#mapchanged)事件|發生於 Map 變更時。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

`UnorderedMap`

### <a name="requirements"></a>需求

**標頭：** collection.h

**命名空間：** Platform::Collections

## <a name="unorderedmapclear-method"></a><a name="clear"></a>沒有序映射::清除方法

從目前 UnorderedMap 物件移除所有機碼值組。

### <a name="syntax"></a>語法

```cpp
virtual void Clear();
```

## <a name="unorderedmapfirst-method"></a><a name="first"></a>無序映射::第一種方法

返回指定第一個[Windows::基礎:集合::iKeyValuePair\<K,V>](/uwp/api/Windows.Foundation.Collections.IKeyValuePair_K_V_)無序映射中的元素的反覆運算器。

### <a name="syntax"></a>語法

```cpp
virtual Windows::Foundation::Collections::IIterator<
   Windows::Foundation::Collections::IKeyValuePair<K, V>^>^
   First();
```

### <a name="return-value"></a>傳回值

迭代器，指定對應中的第一個元素。

### <a name="remarks"></a>備註

保存 First() 傳回的反覆運算器的一個方便方法是將返回值分配給使用**自動**類型扣減關鍵字聲明的變數。 例如： `auto x = myUnorderedMap->First();` 。

## <a name="unorderedmapgetview-method"></a><a name="getview"></a>沒有序映射:獲取查看方法

返回當前無序地圖的唯讀檢視;即[,平臺:集合:::](../cppcx/platform-collections-unorderedmapview-class.md)實現 [Windows::基礎:集合:集合:iMapView::iMapView]/uwp/api/Windows.Foundation.集合.IMapView_K_V_)介面的無序 MapView 類。

### <a name="syntax"></a>語法

```cpp
Windows::Foundation::Collections::IMapView<K, V>^ GetView();
```

### <a name="return-value"></a>傳回值

`UnorderedMapView` 物件。

## <a name="unorderedmaphaskey-method"></a><a name="haskey"></a>無序映射::有鍵方法

判斷目前 UnorderedMap 是否包含指定的機碼。

### <a name="syntax"></a>語法

```cpp
bool HasKey(
   K key
);
```

### <a name="parameters"></a>參數

*關鍵*<br/>
用來尋找 UnorderedMap 元素的機碼。 *鍵*的類型是類型名稱*K*。

### <a name="return-value"></a>傳回值

如果找到金鑰,**則為 true;** 否則,**假**。

## <a name="unorderedmapinsert-method"></a><a name="insert"></a>沒有序映射:插入方法

將指定的機碼值組加入目前 UnorderedMap 物件中。

### <a name="syntax"></a>語法

```cpp
virtual bool Insert(
   K key,
   V value
);
```

### <a name="parameters"></a>參數

*關鍵*<br/>
機碼值組的機碼部分。 *鍵*的類型是類型名稱*K*。

*值*<br/>
機碼值組的值部分。 *值*的類型是類型名稱*V*。

### <a name="return-value"></a>傳回值

如果目前 Map 中現有元素的鍵與*鍵*匹配,並且該元素的值部分設置為*值*,**則為 true。** 如果當前 Map 中不存在現有元素與*鍵*匹配,並且*鍵*和*值*參數被製成鍵值對,然後添加到當前無序映射,**則為 false。**

## <a name="unorderedmaplookup-method"></a><a name="lookup"></a>無序映射::查找方法

取得與類型為 K 之指定機碼相關聯且類型為 V 的值。

### <a name="syntax"></a>語法

```cpp
V Lookup(
   K key
);
```

### <a name="parameters"></a>參數

*關鍵*<br/>
用來在 UnorderedMap 中尋找元素的機碼。 *鍵*的類型是類型名稱*K*。

### <a name="return-value"></a>傳回值

與*鍵*配對的值。 傳回值的型態為類型名稱*V*。

## <a name="unorderedmapmapchanged"></a><a name="mapchanged"></a>無序對應::已映射

在對應中插入或移除項目時引發。

### <a name="syntax"></a>語法

```cpp
event Windows::Foundation::Collections::MapChangedEventHandler<K,V>^ MapChanged;
```

### <a name="property-valuereturn-value"></a>屬性值/傳回值

[MapChangeEventHandler\<K,V>,](/uwp/api/windows.foundation.collections.mapchangedeventhandler)其中包含有關引發事件的物件以及發生的更改類型的資訊。 另請參閱[IMapChangeEventArgs\<K>](/uwp/api/Windows.Foundation.Collections.IMapChangedEventArgs_K_)與[集合變更枚舉](/uwp/api/windows.foundation.collections.collectionchange)。

## <a name="net-framework-equivalent"></a>.NET Framework 同等

Windows 運行時應用,我們 C# 或可視\<化基本專案 IMap K,V\<>为 I字典 K,V>。

## <a name="unorderedmapremove-method"></a><a name="remove"></a>沒有序映射::刪除方法

從目前 UnorderedMap 物件中刪除指定的機碼值組。

### <a name="syntax"></a>語法

```cpp
virtual void Remove(
   K key);
```

### <a name="parameters"></a>參數

*關鍵*<br/>
機碼值組的機碼部分。 *鍵*的類型是類型名稱*K*。

## <a name="unorderedmapsize-method"></a><a name="size"></a>無序對應::大小方法

返回"無序地圖"中[的視窗:::基礎:集合::IKeyValuePair\<K,V>](/uwp/api/Windows.Foundation.Collections.IKeyValuePair_K_V_)元素。

### <a name="syntax"></a>語法

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>傳回值

UnorderedMap 中的元素數目。

## <a name="unorderedmapunorderedmap-constructor"></a><a name="ctor"></a>無序映射::無序映射構造函數

初始化 UnorderedMap 類別的新執行個體。

### <a name="syntax"></a>語法

```cpp
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

template <typename InIt>
UnorderedMap(
    InIt first,
    InIt last
    );

template <typename InIt>
UnorderedMap(
    InIt first,
    InIt last,
    size_t n
    );

template <typename InIt>
UnorderedMap(
    InIt first,
    InIt last,
    size_t n,
    const H& h
    );

template <typename InIt>
UnorderedMap(
    InIt first,
    InIt last,
    size_t n,
    const H& h,
    const P& p
    );

UnorderedMap(
    std::initializer_list< std::pair<const K, V>> il
    );

UnorderedMap(
    std::initializer_list< std::pair<const K, V>> il,
    size_t n
    );

UnorderedMap(
    std::initializer_list< std::pair<const K, V>> il,
    size_t n,
    const H& h
    );

UnorderedMap(
    std::initializer_list< std::pair<const K, V>> il,
    size_t n,
    const H& h,
    const P& p
    );
```

### <a name="parameters"></a>參數

*Init*<br/>
目前 UnorderedMap 的 typename。

*P*<br/>
可比較兩個機碼以判斷它們是否相等的函式物件。 此參數預設為[\<std::equal_to K>](../standard-library/equal-to-struct.md)。

*H*<br/>
可為機碼產生雜湊值的函式物件。 此參數預設為類支援的關鍵類型的[哈希類1。](../standard-library/hash-class.md)

*米*<br/>
對[std::unordered_map](../standard-library/unordered-map-class.md)的引用或[Lvalue 和 Rvalue,](../cpp/lvalues-and-rvalues-visual-cpp.md)用於初始化當前無序映射。

*I l*<br/>
用於初始化地圖的[std:initializer_list::p空氣](../standard-library/pair-structure.md)物件。 [std::initializer_list](../standard-library/initializer-list-class.md)

*第一*<br/>
用來初始化目前 UnorderedMap 的元素範圍中第一個元素的輸入迭代器。

*最後*<br/>
用來初始化目前 UnorderedMap 的元素範圍以外第一個元素的輸入迭代器。

## <a name="see-also"></a>另請參閱

[平台命名空間](platform-namespace-c-cx.md)<br/>
[Platform::Collections 命名空間](../cppcx/platform-collections-namespace.md)<br/>
[Platform::Collections::Map 類別](../cppcx/platform-collections-map-class.md)<br/>
[Platform::Collections::UnorderedMapView 類別](../cppcx/platform-collections-unorderedmapview-class.md)<br/>
[集合](../cppcx/collections-c-cx.md)<br/>
[在 C++ 中建立 Windows 執行階段元件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
