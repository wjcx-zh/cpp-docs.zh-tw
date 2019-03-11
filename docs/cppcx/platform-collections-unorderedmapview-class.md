---
title: Platform::Collections::UnorderedMapView 類別
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- collection/Platform::Collections::UnorderedMapView
ms.assetid: 545a3725-2efd-4cc1-b590-4a7cd2351f61
ms.openlocfilehash: ebda6f179c365aaa009eb45425a36058105def10
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2019
ms.locfileid: "57743441"
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

*V*<br/>
機碼值組中，值的型別。

*C*<br/>
可提供函式物件用來比較兩個機碼值是否相等的類型。 根據預設， [std:: equal_to\<K >](../standard-library/equal-to-struct.md)

### <a name="remarks"></a>備註

UnorderedMapView 是具象 c + + 實作[Windows::Foundation::Collections::IMapView\<K，V >](/uwp/api/Windows.Foundation.Collections.IMapView_K_V_)傳遞應用程式二進位介面 (ABI) 之間的介面。 如需詳細資訊，請參閱 [集合 (C++/CX)](../cppcx/collections-c-cx.md)。

### <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[UnorderedMapView::UnorderedMapView](#ctor)|初始化 UnorderedMapView 類別的新執行個體。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[UnorderedMapView::First](#first)|傳回迭代器，初始化為對應檢視中的第一個元素。|
|[UnorderedMapView::HasKey](#haskey)|判斷目前 UnorderedMapView 是否包含指定的機碼。|
|[UnorderedMapView::Lookup](#lookup)|取得目前 UnorderedMapView 物件中，所指定機碼處的項目。|
|[UnorderedMapView::Size](#size)|傳回目前 UnorderedMapView 物件中的元素數目。|
|[UnorderedMapView::Split](#split)|將原始 UnorderedMapView 物件分割為兩個 UnorderedMapView 物件。|

## <a name="inheritance-hierarchy"></a>繼承階層

`UnorderedMapView`

### <a name="requirements"></a>需求

**標頭：** collection.h

**命名空間：** Platform::Collections

## <a name="first"></a>  UnorderedMapView::First 方法

傳回迭代器，指定第一個[Windows::Foundation::Collections::IKeyValuePair\<K，V >](/uwp/api/Windows.Foundation.Collections.IKeyValuePair_K_V_) unorderedmap 中的項目。

### <a name="syntax"></a>語法

```cpp
virtual Windows::Foundation::Collections::IIterator<
    Windows::Foundation::Collections::IKeyValuePair<K, V>^>^
    First();
```

### <a name="return-value"></a>傳回值

迭代器，指定對應檢視中的第一個元素。

### <a name="remarks"></a>備註

若要保留 first （） 所傳回的迭代器的方便作法是將傳回的值指派給宣告的變數**自動**類型推斷關鍵字。 例如， `auto x = myMapView->First();` 。

## <a name="haskey"></a>  UnorderedMapView::HasKey 方法

判斷目前 UnorderedMap 是否包含指定的機碼。

### <a name="syntax"></a>語法

```cpp
bool HasKey(K key);
```

### <a name="parameters"></a>參數

*key*<br/>
用來尋找元素的機碼。 型別`key`為 typename *K*。

### <a name="return-value"></a>傳回值

**真**找到則為索引鍵是否**false**。

## <a name="lookup"></a>  UnorderedMapView::Lookup 方法

取得與類型為 K 之指定機碼相關聯且類型為 V 的值。

### <a name="syntax"></a>語法

```cpp
V Lookup(K key);
```

### <a name="parameters"></a>參數

*key*<br/>
用來在 UnorderedMapView 中尋找元素的機碼。 型別`key`為 typename *K*。

### <a name="return-value"></a>傳回值

與 `key` 配對的值。 傳回值的類型為 typename *V*。

## <a name="size"></a>  UnorderedMapView::Size 方法

傳回的數目[Windows::Foundation::Collections::IKeyValuePair\<K，V >](/uwp/api/Windows.Foundation.Collections.IKeyValuePair_K_V_) UnorderedMapView 中的項目。

### <a name="syntax"></a>語法

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>傳回值

UnorderedMapView 中的元素數目。

## <a name="split"></a>  UnorderedMapView::Split 方法

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

## <a name="ctor"></a>  UnorderedMapView::UnorderedMapView 建構函式

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

*InIt*<br/>
UnorderedMapView 的 typename。

*H*<br/>
可為機碼產生雜湊值的函式物件。 預設值為[std::hash\<K >](../standard-library/hash-class.md)類型的`std::hash`支援。

*P*<br/>
可提供函式物件用來比較兩個機碼是否相等的類型。 預設值為[std:: equal_to\<K >](../standard-library/equal-to-struct.md)。

*m*<br/>
參考或[Lvalues 和 Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md)要[std:: unordered_map](../standard-library/unordered-map-class.md)用來初始化 UnorderedMapView。

*first*<br/>
用來初始化 UnorderedMapView 的項目範圍中，第一個元素的輸入迭代器。

*last*<br/>
用來初始化 UnorderedMapView 的項目範圍以外第一個元素的輸入迭代器。

## <a name="see-also"></a>另請參閱

[Platform::Collections 命名空間](../cppcx/platform-collections-namespace.md)<br/>
[Windows::Foundation::IMapView](/uwp/api/Windows.Foundation.Collections.IMapView_K_V_)
