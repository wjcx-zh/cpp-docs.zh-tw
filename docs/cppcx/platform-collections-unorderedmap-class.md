---
title: Platform::Collections::UnorderedMap 類別 |Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- collection/Platform::Collections::UnorderedMap
ms.assetid: dc84f261-b13c-4c0a-9b57-30dcb9e3065e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2050be008f89ff2d125842d5919407dc292eed40
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44105831"
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

*V*<br/>
機碼值組中，值的型別。

*C*<br/>
一個型別，提供函式物件，可以根據排序鍵比較兩個項目值，判斷它們在 Map 中的相對順序。 根據預設， [std:: equal_to\<K >](../standard-library/equal-to-struct.md)。

### <a name="remarks"></a>備註

可使用的型別如下：

- 整數

- 介面類別 ^

- 公用 ref 類別^

- value struct

- 公用列舉類別

**UnorderedMap**基本上是包裝函式[std:: unordered_map](../standard-library/unordered-map-class.md)可支援 Windows 執行階段類型的儲存體。 它是具象實作[Windows::Foundation::Collections::IMap](/uwp/api/Windows.Foundation.Collections.IMap_K_V_)並[IObservableMap](/uwp/api/Windows.Foundation.Collections.IObservableMap_K_V_)類型跨公用傳遞 Windows 執行階段介面。 如果您嘗試在公用傳回值或參數中使用 `Platform::Collections::UnorderedMap` 類型，則會引發編譯器錯誤 C3986。 您可以修正這個錯誤，藉由變更參數或傳回值的型別[Windows::Foundation::Collections::IMap](/uwp/api/Windows.Foundation.Collections.IMap_K_V_)。

如需詳細資訊，請參閱 <<c0> [ 集合](../cppcx/collections-c-cx.md)。

### <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[UnorderedMap::UnorderedMap](#ctor)|初始化 Map 類別的新執行個體。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[UnorderedMap::Clear](#clear)|從目前 Map 物件移除所有機碼值組。|
|[UnorderedMap::First](#first)|傳回迭代器，指定 Map 中的第一個項目。|
|[UnorderedMap::GetView](#getview)|傳回目前 Map 的唯讀檢視，也就是 Platform::Collections::UnorderedMapView 類別。|
|[UnorderedMap::HasKey](#haskey)|判斷目前 Map 是否包含指定的機碼。|
|[UnorderedMap::Insert](#insert)|將指定的機碼值組加入目前 Map 物件中。|
|[UnorderedMap::Lookup](#lookup)|擷取目前 Map 物件中，所指定機碼處的項目。|
|[UnorderedMap::Remove](#remove)|從目前 Map 物件中刪除指定的機碼值組。|
|[UnorderedMap::Size](#size)|傳回目前 Map 物件中的項目數。|

### <a name="events"></a>事件

|||
|-|-|
|名稱|描述|
|[Map:: mapchanged](#mapchanged)事件|發生於 Map 變更時。|

## <a name="inheritance-hierarchy"></a>繼承階層

`UnorderedMap`

### <a name="requirements"></a>需求

**標頭：** collection.h

**命名空間：** Platform::Collections

## <a name="clear"></a>  Unorderedmap:: Clear 方法

從目前 UnorderedMap 物件移除所有機碼值組。

### <a name="syntax"></a>語法

```cpp
virtual void Clear();
```

## <a name="first"></a>  Unorderedmap:: First 方法

傳回迭代器，指定第一個[Windows::Foundation::Collections::IKeyValuePair\<K，V >](https://msdn.microsoft.com/library/windows/apps/br226031.aspx) unorderedmap 中的項目。

### <a name="syntax"></a>語法

```cpp
virtual Windows::Foundation::Collections::IIterator<
   Windows::Foundation::Collections::IKeyValuePair<K, V>^>^
   First();
```

### <a name="return-value"></a>傳回值

迭代器，指定對應中的第一個元素。

### <a name="remarks"></a>備註

若要保留 first （） 所傳回的迭代器的方便作法是將傳回的值指派給宣告的變數**自動**類型推斷關鍵字。 例如，`auto x = myUnorderedMap->First();`。

## <a name="getview"></a>  Unorderedmap:: Getview 方法

傳回目前 UnorderedMap 的唯讀檢視亦即[Platform::Collections::UnorderedMapView 類別](../cppcx/platform-collections-unorderedmapview-class.md)會實作 [Windows::Foundation::Collections::IMapView::IMapView]/uwp/api/Windows.Foundation.Collections.IMapView_K_V_) 介面。

### <a name="syntax"></a>語法

```cpp
Windows::Foundation::Collections::IMapView<K, V>^ GetView();
```

### <a name="return-value"></a>傳回值

`UnorderedMapView` 物件。

## <a name="haskey"></a>  Unorderedmap:: Haskey 方法

判斷目前 UnorderedMap 是否包含指定的機碼。

### <a name="syntax"></a>語法

```cpp
bool HasKey(
   K key
);
```

### <a name="parameters"></a>參數

*key*<br/>
用來尋找 UnorderedMap 元素的機碼。 型別*金鑰*為 typename *K*。

### <a name="return-value"></a>傳回值

如果找到機碼則為 `true`，否則為 `false`。

## <a name="insert"></a>  UnorderedMap::Insert Method

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
機碼值組的機碼部分。 型別*金鑰*為 typename *K*。

*值*<br/>
機碼值組的值部分。 型別*值*為 typename *V*。

### <a name="return-value"></a>傳回值

`true` 如果目前 Map 中現有項目的索引鍵符合*金鑰*，而且該元素的值部分設定為*值*。 `false` 如果目前 Map 中的任何現有項目不符合*金鑰*並*金鑰*並*值*參數會使其成為的索引鍵 / 值組，而且接著加入目前 UnorderedMap。

## <a name="lookup"></a>  Unorderedmap:: Lookup 方法

取得與類型為 K 之指定機碼相關聯且類型為 V 的值。

### <a name="syntax"></a>語法

```cpp
V Lookup(
   K key
);
```

### <a name="parameters"></a>參數

*key*<br/>
用來在 UnorderedMap 中尋找元素的機碼。 型別*金鑰*為 typename *K*。

### <a name="return-value"></a>傳回值

值，會搭配*金鑰*。 傳回值的類型為 typename *V*。

## <a name="mapchanged"></a>  UnorderedMap::MapChanged

在對應中插入或移除項目時引發。

### <a name="syntax"></a>語法

```cpp
event Windows::Foundation::Collections::MapChangedEventHandler<K,V>^ MapChanged;
```

### <a name="property-valuereturn-value"></a>屬性值/傳回值

A [Mapchangedeventhandler<k\<K，V >](/uwp/api/windows.foundation.collections.mapchangedeventhandler) ，包含引發事件，以及發生的變更類型的物件相關資訊。 另請參閱[Imapchangedeventargs<k\<K >](https://msdn.microsoft.com/library/windows/apps/br226034.aspx)並[CollectionChange 列舉](https://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.collectionchange.aspx)。

## <a name="net-framework-equivalent"></a>.NET Framework 同等

Windows 執行階段應用程式使用 C# 或 Visual Basic 專案 Imap<k\<K，V > 做為 idictionary<k，V>\<K，V >。

## <a name="remove"></a>  Unorderedmap:: Remove 方法

從目前 UnorderedMap 物件中刪除指定的機碼值組。

### <a name="syntax"></a>語法

```cpp
virtual void Remove(
   K key);
```

### <a name="parameters"></a>參數

*key*<br/>
機碼值組的機碼部分。 型別*金鑰*為 typename *K*。

## <a name="size"></a>  Unorderedmap:: Size 方法

傳回的數目[Windows::Foundation::Collections::IKeyValuePair\<K，V >](https://msdn.microsoft.com/library/windows/apps/br226031.aspx) UnorderedMap 中的項目。

### <a name="syntax"></a>語法

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>傳回值

UnorderedMap 中的元素數目。

## <a name="ctor"></a>  UnorderedMap::UnorderedMap 建構函式

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

*InIt*<br/>
目前 UnorderedMap 的 typename。

*P*<br/>
可比較兩個機碼以判斷它們是否相等的函式物件。 此參數的預設值[std:: equal_to\<K >](../standard-library/equal-to-struct.md)。

*H*<br/>
可為機碼產生雜湊值的函式物件。 此參數的預設值[雜湊類別 1](../standard-library/hash-class.md)類別的索引鍵類型，支援。

*m*<br/>
參考或[Lvalues 和 Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md)要[std:: unordered_map](../standard-library/unordered-map-class.md)用來初始化目前 UnorderedMap。

*il*<br/>
A [std:: initializer_list](../standard-library/initializer-list-class.md)的[std:: pair](../standard-library/pair-structure.md)用來初始化對應的物件。

*first*<br/>
用來初始化目前 UnorderedMap 的元素範圍中第一個元素的輸入迭代器。

*最後一個*<br/>
用來初始化目前 UnorderedMap 的元素範圍以外第一個元素的輸入迭代器。

## <a name="see-also"></a>另請參閱

[Platform 命名空間](platform-namespace-c-cx.md)<br/>
[Platform::Collections 命名空間](../cppcx/platform-collections-namespace.md)<br/>
[Platform::Collections::Map 類別](../cppcx/platform-collections-map-class.md)<br/>
[Platform::Collections::UnorderedMapView 類別](../cppcx/platform-collections-unorderedmapview-class.md)<br/>
[集合](../cppcx/collections-c-cx.md)<br/>
[在 c + + 中建立 Windows 執行階段元件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
