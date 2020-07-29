---
title: Platform::Collections::UnorderedMap 類別
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- collection/Platform::Collections::UnorderedMap
ms.assetid: dc84f261-b13c-4c0a-9b57-30dcb9e3065e
ms.openlocfilehash: 3c95f4a982e23d757b330ecadcae5cfbfd6fd531
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213069"
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

*&*<br/>
機碼值組中，值的型別。

*C*<br/>
一個型別，提供函式物件，可以根據排序鍵比較兩個項目值，判斷它們在 Map 中的相對順序。 預設[為 std：： equal_to \<K> ](../standard-library/equal-to-struct.md)。

### <a name="remarks"></a>備註

允許的類型為：

- integers

- 介面類別別 ^

- 公用 ref 類別^

- value struct

- 公用列舉類別

**UnorderedMap**基本上是[std：： unordered_map](../standard-library/unordered-map-class.md)的包裝函式，可支援 Windows 執行階段類型的儲存。 它是跨公用 Windows 執行階段介面傳遞之[Windows：： Foundation：： collection：： IMap](/uwp/api/windows.foundation.collections.imap-2)和[IObservableMap](/uwp/api/windows.foundation.collections.iobservablemap-2)類型的具體執行。 如果您嘗試在公用傳回值或參數中使用 `Platform::Collections::UnorderedMap` 類型，則會引發編譯器錯誤 C3986。 您可以將參數或傳回值的類型變更為 [Windows::Foundation::Collections::IMap](/uwp/api/windows.foundation.collections.imap-2)來修正錯誤。

如需詳細資訊，請參閱[集合](../cppcx/collections-c-cx.md)。

### <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[UnorderedMap：： UnorderedMap](#ctor)|初始化 Map 類別的新執行個體。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[UnorderedMap：： Clear](#clear)|從目前 Map 物件移除所有機碼值組。|
|[UnorderedMap：： First](#first)|傳回迭代器，指定 Map 中的第一個項目。|
|[UnorderedMap：： GetView](#getview)|傳回目前 Map 的唯讀檢視，也就是 Platform::Collections::UnorderedMapView 類別。|
|[UnorderedMap：： HasKey](#haskey)|判斷目前 Map 是否包含指定的機碼。|
|[UnorderedMap：： Insert](#insert)|將指定的機碼值組加入目前 Map 物件中。|
|[UnorderedMap：： Lookup](#lookup)|擷取目前 Map 物件中，所指定機碼處的項目。|
|[UnorderedMap：： Remove](#remove)|從目前 Map 物件中刪除指定的機碼值組。|
|[UnorderedMap：： Size](#size)|傳回目前 Map 物件中的項目數。|

### <a name="events"></a>事件

|||
|-|-|
|名稱|說明|
|[Map：： MapChanged](#mapchanged)事件|發生於 Map 變更時。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

`UnorderedMap`

### <a name="requirements"></a>需求

**標頭：** collection.h

**命名空間：** Platform::Collections

## <a name="unorderedmapclear-method"></a><a name="clear"></a>UnorderedMap：： Clear 方法

從目前 UnorderedMap 物件移除所有機碼值組。

### <a name="syntax"></a>語法

```cpp
virtual void Clear();
```

## <a name="unorderedmapfirst-method"></a><a name="first"></a>UnorderedMap：： First 方法

傳回反覆運算器，指定未排序對應中的第一個[Windows：： Foundation： \<K,V> ： collection：： inputiterator<ikeyvaluepair<k](/uwp/api/windows.foundation.collections.ikeyvaluepair-2)元素。

### <a name="syntax"></a>語法

```cpp
virtual Windows::Foundation::Collections::IIterator<
   Windows::Foundation::Collections::IKeyValuePair<K, V>^>^
   First();
```

### <a name="return-value"></a>傳回值

迭代器，指定對應中的第一個元素。

### <a name="remarks"></a>備註

若要保留 First （）所傳回的反覆運算器，有一個方便的方式，就是將傳回值指派給使用類型推算關鍵字所宣告的變數 **`auto`** 。 例如： `auto x = myUnorderedMap->First();` 。

## <a name="unorderedmapgetview-method"></a><a name="getview"></a>UnorderedMap：： GetView 方法

傳回目前 UnorderedMap 的唯讀視圖;也就是，會執行[Windows：： Foundation：： collection：： IMapView：： IMapView](/uwp/api/windows.foundation.collections.imapview-2)介面的[Platform：： Collection：： UnorderedMapView 類別](../cppcx/platform-collections-unorderedmapview-class.md)。

### <a name="syntax"></a>語法

```cpp
Windows::Foundation::Collections::IMapView<K, V>^ GetView();
```

### <a name="return-value"></a>傳回值

`UnorderedMapView` 物件。

## <a name="unorderedmaphaskey-method"></a><a name="haskey"></a>UnorderedMap：： HasKey 方法

判斷目前 UnorderedMap 是否包含指定的機碼。

### <a name="syntax"></a>語法

```cpp
bool HasKey(
   K key
);
```

### <a name="parameters"></a>參數

*key*<br/>
用來尋找 UnorderedMap 元素的機碼。 *金鑰*的類型為 typename *K*。

### <a name="return-value"></a>傳回值

**`true`** 如果找到索引鍵，則為，否則為 **`false`** 。

## <a name="unorderedmapinsert-method"></a><a name="insert"></a>UnorderedMap：： Insert 方法

將指定的機碼值組加入目前 UnorderedMap 物件中。

### <a name="syntax"></a>語法

```cpp
virtual bool Insert(
   K key,
   V value
);
```

### <a name="parameters"></a>參數

*key*<br/>
機碼值組的機碼部分。 *金鑰*的類型為 typename *K*。

*value*<br/>
機碼值組的值部分。 *值*的類型為 typename *V*。

### <a name="return-value"></a>傳回值

**`true`** 如果目前對應中現有專案的索引鍵符合索引*鍵*，且該元素的值部分設定為*value*。 **`false`** 如果目前對應中沒有任何現有的專案*key*符合索引鍵 *，而且索引鍵和**值*參數已變成索引鍵/值組，然後加入至目前的 UnorderedMap。

## <a name="unorderedmaplookup-method"></a><a name="lookup"></a>UnorderedMap：： Lookup 方法

取得與類型為 K 之指定機碼相關聯且類型為 V 的值。

### <a name="syntax"></a>語法

```cpp
V Lookup(
   K key
);
```

### <a name="parameters"></a>參數

*key*<br/>
用來在 UnorderedMap 中尋找元素的機碼。 *金鑰*的類型為 typename *K*。

### <a name="return-value"></a>傳回值

與索引*鍵*配對的值。 傳回值的類型為 typename *V*。

## <a name="unorderedmapmapchanged"></a><a name="mapchanged"></a>UnorderedMap：： MapChanged

在對應中插入或移除項目時引發。

### <a name="syntax"></a>語法

```cpp
event Windows::Foundation::Collections::MapChangedEventHandler<K,V>^ MapChanged;
```

### <a name="property-valuereturn-value"></a>屬性值/傳回值

[MapChangedEventHandler \<K,V> ](/uwp/api/windows.foundation.collections.mapchangedeventhandler-2) ，其中包含引發事件之物件的相關資訊，以及發生的變更類型。 另請[參閱 \<K> IMapChangedEventArgs](/uwp/api/windows.foundation.collections.imapchangedeventargs-1)和[CollectionChange 列舉](/uwp/api/windows.foundation.collections.collectionchange)。

## <a name="net-framework-equivalent"></a>.NET Framework 同等

Windows 執行階段以 c # 或 Visual Basic project IMap 作為 IDictionary 的應用程式 \<K,V> \<K,V> 。

## <a name="unorderedmapremove-method"></a><a name="remove"></a>UnorderedMap：： Remove 方法

從目前 UnorderedMap 物件中刪除指定的機碼值組。

### <a name="syntax"></a>語法

```cpp
virtual void Remove(
   K key);
```

### <a name="parameters"></a>參數

*key*<br/>
機碼值組的機碼部分。 *金鑰*的類型為 typename *K*。

## <a name="unorderedmapsize-method"></a><a name="size"></a>UnorderedMap：： Size 方法

傳回 UnorderedMap 中的[Windows：： Foundation：： collection：： inputiterator<ikeyvaluepair<k \<K,V> ](/uwp/api/windows.foundation.collections.ikeyvaluepair-2)元素數目。

### <a name="syntax"></a>語法

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>傳回值

UnorderedMap 中的元素數目。

## <a name="unorderedmapunorderedmap-constructor"></a><a name="ctor"></a>UnorderedMap：： UnorderedMap 函式

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

*初始*<br/>
目前 UnorderedMap 的 typename。

*P*<br/>
可比較兩個機碼以判斷它們是否相等的函式物件。 此參數預設為[std：： equal_to \<K> ](../standard-library/equal-to-struct.md)。

*H*<br/>
可為機碼產生雜湊值的函式物件。 此參數預設為類別支援的索引鍵類型的[雜湊類別 1](../standard-library/hash-class.md) 。

*分鐘*<br/>
用來初始化目前 UnorderedMap 之[std：： unordered_map](../standard-library/unordered-map-class.md)的參考或[左值和右值](../cpp/lvalues-and-rvalues-visual-cpp.md)。

*il*<br/>
Std： [： initializer_list](../standard-library/initializer-list-class.md) ，屬於用來初始化對應的[std：:p 空中](../standard-library/pair-structure.md)物件。

*first*<br/>
用來初始化目前 UnorderedMap 的元素範圍中第一個元素的輸入迭代器。

*last*<br/>
用來初始化目前 UnorderedMap 的元素範圍以外第一個元素的輸入迭代器。

## <a name="see-also"></a>另請參閱

[Platform 命名空間](platform-namespace-c-cx.md)<br/>
[Platform：： collection 命名空間](../cppcx/platform-collections-namespace.md)<br/>
[Platform：： collection：： Map 類別](../cppcx/platform-collections-map-class.md)<br/>
[Platform：： collection：： UnorderedMapView 類別](../cppcx/platform-collections-unorderedmapview-class.md)<br/>
[集合](../cppcx/collections-c-cx.md)<br/>
[在 C++ 中建立 Windows 執行階段元件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
