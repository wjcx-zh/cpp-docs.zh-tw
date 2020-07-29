---
title: Platform::Collections::UnorderedMapView 類別
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- collection/Platform::Collections::UnorderedMapView
ms.assetid: 545a3725-2efd-4cc1-b590-4a7cd2351f61
ms.openlocfilehash: acfc168959deb83244c98c5d361cf9e73c1388f2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213056"
---
# <a name="platformcollectionsunorderedmapview-class"></a>Platform::Collections::UnorderedMapView 類別

表示 *對應 (Map)*(機碼值組的集合) 的唯讀檢視。

## <a name="syntax"></a>語法

```cpp
template <
   typename K,
   typename V,
   typename C = ::std::equal_to<K>>
ref class UnorderedMapView sealed;
```

#### <a name="parameters"></a>參數

*K*<br/>
機碼值組中，機碼的類型。

*&*<br/>
機碼值組中，值的型別。

*C*<br/>
可提供函式物件用來比較兩個機碼值是否相等的類型。 預設[為 std：： equal_to \<K> ](../standard-library/equal-to-struct.md)

### <a name="remarks"></a>備註

UnorderedMapView 是在應用程式二進位介面（ABI）之間傳遞之[Windows：： Foundation： \<K,V> ： collection：： IMapView](/uwp/api/windows.foundation.collections.imapview-2)介面的具象 c + + 執行。 如需詳細資訊，請參閱 [集合 (C++/CX)](../cppcx/collections-c-cx.md)。

### <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[UnorderedMapView：： UnorderedMapView](#ctor)|初始化 UnorderedMapView 類別的新執行個體。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[UnorderedMapView：： First](#first)|傳回迭代器，初始化為對應檢視中的第一個元素。|
|[UnorderedMapView：： HasKey](#haskey)|判斷目前 UnorderedMapView 是否包含指定的機碼。|
|[UnorderedMapView：： Lookup](#lookup)|取得目前 UnorderedMapView 物件中，所指定機碼處的項目。|
|[UnorderedMapView：： Size](#size)|傳回目前 UnorderedMapView 物件中的元素數目。|
|[UnorderedMapView：： Split](#split)|將原始 UnorderedMapView 物件分割為兩個 UnorderedMapView 物件。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

`UnorderedMapView`

### <a name="requirements"></a>需求

**標頭：** collection.h

**命名空間：** Platform::Collections

## <a name="unorderedmapviewfirst-method"></a><a name="first"></a>UnorderedMapView：： First 方法

傳回反覆運算器，指定未排序對應中的第一個[Windows：： Foundation： \<K,V> ： collection：： inputiterator<ikeyvaluepair<k](/uwp/api/windows.foundation.collections.ikeyvaluepair-2)元素。

### <a name="syntax"></a>語法

```cpp
virtual Windows::Foundation::Collections::IIterator<
    Windows::Foundation::Collections::IKeyValuePair<K, V>^>^
    First();
```

### <a name="return-value"></a>傳回值

迭代器，指定對應檢視中的第一個元素。

### <a name="remarks"></a>備註

若要保留 First （）所傳回的反覆運算器，有一個方便的方式，就是將傳回值指派給使用類型推算關鍵字所宣告的變數 **`auto`** 。 例如： `auto x = myMapView->First();` 。

## <a name="unorderedmapviewhaskey-method"></a><a name="haskey"></a>UnorderedMapView：： HasKey 方法

判斷目前 UnorderedMap 是否包含指定的機碼。

### <a name="syntax"></a>語法

```cpp
bool HasKey(K key);
```

### <a name="parameters"></a>參數

*key*<br/>
用來尋找元素的機碼。 的類型 `key` 為 Typename *K*。

### <a name="return-value"></a>傳回值

**`true`** 如果找到索引鍵，則為，否則為 **`false`** 。

## <a name="unorderedmapviewlookup-method"></a><a name="lookup"></a>UnorderedMapView：： Lookup 方法

取得與類型為 K 之指定機碼相關聯且類型為 V 的值。

### <a name="syntax"></a>語法

```cpp
V Lookup(K key);
```

### <a name="parameters"></a>參數

*key*<br/>
用來在 UnorderedMapView 中尋找元素的機碼。 的類型 `key` 為 Typename *K*。

### <a name="return-value"></a>傳回值

與 `key` 配對的值。 傳回值的類型為 typename *V*。

## <a name="unorderedmapviewsize-method"></a><a name="size"></a>UnorderedMapView：： Size 方法

傳回 UnorderedMapView 中的[Windows：： Foundation：： collection：： inputiterator<ikeyvaluepair<k \<K,V> ](/uwp/api/windows.foundation.collections.ikeyvaluepair-2)元素數目。

### <a name="syntax"></a>語法

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>傳回值

UnorderedMapView 中的元素數目。

## <a name="unorderedmapviewsplit-method"></a><a name="split"></a>UnorderedMapView：： Split 方法

將目前 UnorderedMapView 物件分割為兩個 UnorderedMapView 物件。 這個方法無法操作。

### <a name="syntax"></a>語法

```cpp
void Split(
   Windows::Foundation::Collections::IMapView<
                         K,V>^ * firstPartition,
   Windows::Foundation::Collections::IMapView<
                         K,V>^ * secondPartition);
```

### <a name="parameters"></a>參數

*firstPartition*<br/>
原始 UnorderedMapView 物件的第一個部分。

*secondPartition*<br/>
原始 UnorderedMapView 物件的第二個部分。

### <a name="remarks"></a>備註

這個方法無法操作，不會執行任何動作。

## <a name="unorderedmapviewunorderedmapview-constructor"></a><a name="ctor"></a>UnorderedMapView：： UnorderedMapView 函式

初始化 UnorderedMapView 類別的新執行個體。

### <a name="syntax"></a>語法

```cpp
UnorderedMapView();
explicit UnorderedMapView(size_t n);
UnorderedMapView(size_t n, const H& h);
UnorderedMapView(size_t n, const H& h, const P& p);

explicit UnorderedMapView(
    const std::unordered_map<K, V, H, P>& m);
explicit UnorderedMapView(
    std::unordered_map<K, V, H, P>&& m);

template <typename InIt> UnorderedMapView(InIt first, InIt last );
template <typename InIt> UnorderedMapView(InIt first, InIt last, size_t n );

template <typename InIt> UnorderedMapView(
    InIt first,
    InIt last,
    size_t n,
    const H& h );

template <typename InIt> UnorderedMapView(
    InIt first,
    InIt last,
    size_t n,
    const H& h,
    const P& p );

UnorderedMapView(std::initializer_list<std::pair<const K, V>);

UnorderedMapView(std::initializer_list< std::pair<const K, V>> il, size_t n

UnorderedMapView(
    std::initializer_list< std::pair<const K, V>> il,
    size_t n,
    const H& h);

UnorderedMapView(
    std::initializer_list< std::pair<const K, V>> il,
    size_t n,
    const H& h,
    const P& p );
```

### <a name="parameters"></a>參數

*n*<br/>
要為其預先配置空間的元素數目。

*初始*<br/>
UnorderedMapView 的 typename。

*H*<br/>
可為機碼產生雜湊值的函式物件。 針對支援的類型，預設為[std：： \<K> hash](../standard-library/hash-class.md) `std::hash` 。

*P*<br/>
可提供函式物件用來比較兩個機碼是否相等的類型。 預設為[std：： equal_to \<K> ](../standard-library/equal-to-struct.md)。

*分鐘*<br/>
用來初始化 UnorderedMapView 之[std：： unordered_map](../standard-library/unordered-map-class.md)的參考或[左值和右值](../cpp/lvalues-and-rvalues-visual-cpp.md)。

*first*<br/>
用來初始化 UnorderedMapView 的項目範圍中，第一個元素的輸入迭代器。

*last*<br/>
用來初始化 UnorderedMapView 的項目範圍以外第一個元素的輸入迭代器。

## <a name="see-also"></a>另請參閱

[Platform：： collection 命名空間](../cppcx/platform-collections-namespace.md)<br/>
[Windows::Foundation::IMapView](/uwp/api/windows.foundation.collections.imapview-2)
