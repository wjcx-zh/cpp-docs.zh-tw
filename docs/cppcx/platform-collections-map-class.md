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
ms.openlocfilehash: 30dbc71a03c398c77124738b2477a3563191d50d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214980"
---
# <a name="platformcollectionsmap-class"></a>Platform::Collections::Map 類別

代表 *Map*，這是機碼值組的集合。 實行[Windows：： Foundation：： collection：： IObservableMap](/uwp/api/windows.foundation.collections.iobservablemap-2)以協助進行 XAML[資料](/windows/uwp/data-binding/data-binding-in-depth)系結。

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

*&*<br/>
機碼值組中，值的型別。

*C*<br/>
一個型別，提供函式物件，可以根據排序鍵比較兩個項目值，判斷它們在 Map 中的相對順序。 預設[為 std：： less \<K> ](../standard-library/less-struct.md)。

*__is_valid_winrt_type （）* 編譯器產生的函式，它會驗證*K*和*V*的類型，並在此類型不能儲存在對應中時，提供易記的錯誤訊息。

### <a name="remarks"></a>備註

允許的類型為：

- integers

- 介面類別別 ^

- 公用 ref 類別^

- value struct

- 公用列舉類別

Map 基本上是 [std::map](../standard-library/map-class.md)的包裝函式。 它是在公用 Windows 執行階段介面之間傳遞之[windows：： foundation：： collection：： IMap<windows：： foundation：： collection：： \<K,V> > inputiterator<ikeyvaluepair<k](/uwp/api/windows.foundation.collections.imap-2)和[IObservableMap](/uwp/api/windows.foundation.collections.iobservablemap-2)類型的 c + + 具體執行。 如果您嘗試在公用傳回值或參數中使用 `Platform::Collections::Map` 類型，則會引發編譯器錯誤 C3986。 您可以藉由將參數或傳回值的類型變更為[Windows：： Foundation：： collection：： IMap \<K,V> ](/uwp/api/windows.foundation.collections.imap-2)來修正錯誤。

如需詳細資訊，請參閱[集合](../cppcx/collections-c-cx.md)。

### <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[Map：： Map](#ctor)|初始化 Map 類別的新執行個體。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[Map：： Clear](#clear)|從目前 Map 物件移除所有機碼值組。|
|[Map：： First](#first)|傳回迭代器，指定 Map 中的第一個項目。|
|[Map：： GetView](#getview)|傳回目前 Map 的唯讀檢視，也就是 [Platform::Collections::MapView Class](../cppcx/platform-collections-mapview-class.md)。|
|[Map：： HasKey](#haskey)|判斷目前 Map 是否包含指定的機碼。|
|[Map：： Insert](#insert)|將指定的機碼值組加入目前 Map 物件中。|
|[Map：： Lookup](#lookup)|擷取目前 Map 物件中，所指定機碼處的項目。|
|[Map::Remove](#remove)|從目前 Map 物件中刪除指定的機碼值組。|
|[Map：： Size](#size)|傳回目前 Map 物件中的項目數。|

### <a name="events"></a>事件

|||
|-|-|
|名稱|說明|
|[Map：： MapChanged](#mapchanged)事件|發生於 Map 變更時。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

`Map`

### <a name="requirements"></a>需求

**標頭：** collection.h

**命名空間：** Platform::Collections

## <a name="mapclear-method"></a><a name="clear"></a>Map：： Clear 方法

從目前 Map 物件移除所有機碼值組。

### <a name="syntax"></a>語法

```cpp
virtual void Clear();
```

## <a name="mapfirst-method"></a><a name="first"></a>Map：： First 方法

傳回反覆運算器，指定對應中的第一個元素， **`nullptr`** 如果對應是空的，則為。

### <a name="syntax"></a>語法

```cpp
virtual Windows::Foundation::Collections::IIterator<
Windows::Foundation::Collections::IKeyValuePair<K, V>^>^ First();
```

### <a name="return-value"></a>傳回值

迭代器，指定對應中的第一個元素。

### <a name="remarks"></a>備註

若要保留 First （）所傳回的反覆運算器，有一個方便的方式，就是將傳回值指派給使用類型推算關鍵字所宣告的變數 **`auto`** 。 例如： `auto x = myMap->First();` 。

## <a name="mapgetview-method"></a><a name="getview"></a>Map：： GetView 方法

傳回目前地圖的唯讀視圖;也就是[Platform：： collection：： MapView 類別](../cppcx/platform-collections-mapview-class.md)，它會實作為[Windows：： Foundation：： Collection：： IMapView \<K,V> ](/uwp/api/windows.foundation.collections.imapview-2)介面。

### <a name="syntax"></a>語法

```cpp
Windows::Foundation::Collections::IMapView<K, V>^ GetView();
```

### <a name="return-value"></a>傳回值

`MapView` 物件。

## <a name="maphaskey-method"></a><a name="haskey"></a>Map：： HasKey 方法

判斷目前 Map 是否包含指定的機碼。

### <a name="syntax"></a>語法

```cpp
bool HasKey(K key);
```

### <a name="parameters"></a>參數

*key*<br/>
用來尋找 Map 項目的機碼。 *金鑰*的類型為 typename *K*。

### <a name="return-value"></a>傳回值

**`true`** 如果找到索引鍵，則為，否則為 **`false`** 。

## <a name="mapinsert-method"></a><a name="insert"></a>Map：： Insert 方法

將指定的機碼值組加入目前 Map 物件中。

### <a name="syntax"></a>語法

```cpp
virtual bool Insert(K key, V value);
```

### <a name="parameters"></a>參數

*key*<br/>
機碼值組的機碼部分。 *金鑰*的類型為 typename *K*。

*value*<br/>
機碼值組的值部分。 *值*的類型為 typename *V*。

### <a name="return-value"></a>傳回值

**`true`** 如果目前對應中現有專案的索引鍵符合索引*鍵*，且該元素的值部分設定為*value*。 **`false`** 如果目前對應中沒有任何現有的專案*key*符合索引鍵 *，而且索引鍵和**值*參數已變成索引鍵/值組，然後加入至目前的對應。

## <a name="maplookup-method"></a><a name="lookup"></a>Map：： Lookup 方法

取得與類型為 K 之指定機碼 (如果該機碼存在的話) 相關聯且類型為 V 的值。

### <a name="syntax"></a>語法

```cpp
V Lookup(K key);
```

### <a name="parameters"></a>參數

*key*<br/>
用來在 Map 中尋找元素的機碼。 *金鑰*的類型為 typename *K*。

### <a name="return-value"></a>傳回值

與索引*鍵*配對的值。 傳回值的類型為 typename *V*。

### <a name="remarks"></a>備註

如果機碼不存在，則會擲回[Platform：： OutOfBoundsException](../cppcx/platform-outofboundsexception-class.md) 。

## <a name="mapmap-constructor"></a><a name="ctor"></a>Map：： Map 函數

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

*初始*<br/>
目前 Map 的 typename。

*comp*<br/>
一個型別，提供函式物件，可以根據排序鍵比較兩個項目值，判斷它們在 Map 中的相對順序。

*分鐘*<br/>
用來初始化目前 Map 之的參考或[右](../cpp/lvalues-and-rvalues-visual-cpp.md) `map Class` 值。

*first*<br/>
用來初始化目前 Map 的項目範圍中，第一個項目的輸入迭代器。

*last*<br/>
用來初始化目前 Map 的項目範圍以外第一個項目的輸入迭代器。

## <a name="mapmapchanged-event"></a><a name="mapchanged"></a>Map：： MapChanged 事件

在對應中插入或移除項目時引發。

### <a name="syntax"></a>語法

```cpp
event Windows::Foundation::Collections::MapChangedEventHandler<K,V>^ MapChanged;
```

### <a name="property-valuereturn-value"></a>屬性值/傳回值

[MapChangedEventHandler \<K,V> ](/uwp/api/windows.foundation.collections.mapchangedeventhandler-2) ，其中包含引發事件之物件的相關資訊，以及發生的變更類型。 另請[參閱 \<K> IMapChangedEventArgs](/uwp/api/windows.foundation.collections.imapchangedeventargs-1)和[CollectionChange 列舉](/uwp/api/windows.foundation.collections.collectionchange)。

## <a name="net-framework-equivalent"></a>.NET Framework 同等

Windows 執行階段使用 c # 或 Visual Basic project IMap 作為 IDictionary 的應用程式 \<K,V> \<K,V> 。

## <a name="mapremove-method"></a><a name="remove"></a>Map：： Remove 方法

從目前 Map 物件中刪除指定的機碼值組。

### <a name="syntax"></a>語法

```cpp
virtual void Remove(K key);
```

### <a name="parameters"></a>參數

*key*<br/>
機碼值組的機碼部分。 *金鑰*的類型為 typename *K*。

## <a name="mapsize-method"></a><a name="size"></a>Map：： Size 方法

傳回對應中的[Windows：： Foundation：： collection：： inputiterator<ikeyvaluepair<k \<K,V> ](/uwp/api/windows.foundation.collections.ikeyvaluepair-2)元素數目。

### <a name="syntax"></a>語法

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>傳回值

Map 中的元素數目。

## <a name="see-also"></a>另請參閱

[集合（c + +/CX）](collections-c-cx.md)<br/>
[Platform 命名空間](platform-namespace-c-cx.md)<br/>
[在 C++ 中建立 Windows 執行階段元件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
