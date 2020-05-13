---
title: Platform::Collections::UnorderedMapView 類別
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- collection/Platform::Collections::UnorderedMapView
ms.assetid: 545a3725-2efd-4cc1-b590-4a7cd2351f61
ms.openlocfilehash: f0096982ad5d11b9ea394c9f02ba748a52e4216b
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "82031481"
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

*五*<br/>
機碼值組中，值的型別。

*C*<br/>
可提供函式物件用來比較兩個機碼值是否相等的類型。 預設情況下[,std::equal_to\<K>](../standard-library/equal-to-struct.md)

### <a name="remarks"></a>備註

無序的 MapView 是[Windows::基礎:集合::iMapView\<K,V>](/uwp/api/windows.foundation.collections.imapview-2)介面 C++的具體實現,這些介面通過應用程式二進位介面 (ABI) 傳遞。 如需詳細資訊，請參閱 [集合 (C++/CX)](../cppcx/collections-c-cx.md)。

### <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[無序地圖檢視:無序地圖檢視](#ctor)|初始化 UnorderedMapView 類別的新執行個體。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[無序的地圖檢視:第一](#first)|傳回迭代器，初始化為對應檢視中的第一個元素。|
|[無序地圖檢視::哈斯鍵](#haskey)|判斷目前 UnorderedMapView 是否包含指定的機碼。|
|[無序的地圖檢視::尋找](#lookup)|取得目前 UnorderedMapView 物件中，所指定機碼處的項目。|
|[無序的地圖檢視:大小](#size)|傳回目前 UnorderedMapView 物件中的元素數目。|
|[無序的地圖檢視:分割](#split)|將原始 UnorderedMapView 物件分割為兩個 UnorderedMapView 物件。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

`UnorderedMapView`

### <a name="requirements"></a>需求

**標頭：** collection.h

**命名空間：** Platform::Collections

## <a name="unorderedmapviewfirst-method"></a><a name="first"></a>無序的 MapView:第一種方法

返回指定第一個[Windows::基礎:集合::iKeyValuePair\<K,V>](/uwp/api/windows.foundation.collections.ikeyvaluepair-2)無序映射中的元素的反覆運算器。

### <a name="syntax"></a>語法

```cpp
virtual Windows::Foundation::Collections::IIterator<
    Windows::Foundation::Collections::IKeyValuePair<K, V>^>^
    First();
```

### <a name="return-value"></a>傳回值

迭代器，指定對應檢視中的第一個元素。

### <a name="remarks"></a>備註

保存 First() 傳回的反覆運算器的一個方便方法是將返回值分配給使用**自動**類型扣減關鍵字聲明的變數。 例如： `auto x = myMapView->First();` 。

## <a name="unorderedmapviewhaskey-method"></a><a name="haskey"></a>無序的 MapView::有鍵方法

判斷目前 UnorderedMap 是否包含指定的機碼。

### <a name="syntax"></a>語法

```cpp
bool HasKey(K key);
```

### <a name="parameters"></a>參數

*key*<br/>
用來尋找元素的機碼。 的類型`key`是類型名稱*K*。

### <a name="return-value"></a>傳回值

如果找到金鑰,**則為 true;** 否則,**假**。

## <a name="unorderedmapviewlookup-method"></a><a name="lookup"></a>無序的 MapView:尋找方法

取得與類型為 K 之指定機碼相關聯且類型為 V 的值。

### <a name="syntax"></a>語法

```cpp
V Lookup(K key);
```

### <a name="parameters"></a>參數

*key*<br/>
用來在 UnorderedMapView 中尋找元素的機碼。 的類型`key`是類型名稱*K*。

### <a name="return-value"></a>傳回值

與 `key` 配對的值。 傳回值的型態為類型名稱*V*。

## <a name="unorderedmapviewsize-method"></a><a name="size"></a>沒有排列對應檢視:大小方法

返回"無序地圖視圖"中的視窗數[::基礎:集合::iKeyValuePair\<K,V>](/uwp/api/windows.foundation.collections.ikeyvaluepair-2)元素。

### <a name="syntax"></a>語法

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>傳回值

UnorderedMapView 中的元素數目。

## <a name="unorderedmapviewsplit-method"></a><a name="split"></a>無序映射檢視::拆分方法

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

*第一個分割區*<br/>
原始 UnorderedMapView 物件的第一個部分。

*第二個分割區*<br/>
原始 UnorderedMapView 物件的第二個部分。

### <a name="remarks"></a>備註

這個方法無法操作，不會執行任何動作。

## <a name="unorderedmapviewunorderedmapview-constructor"></a><a name="ctor"></a>無序 MapView:無序的 MapView 構造函數

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

*Init*<br/>
UnorderedMapView 的 typename。

*H*<br/>
可為機碼產生雜湊值的函式物件。 預設值為[std:::哈\<希 K>](../standard-library/hash-class.md)支援的類型`std::hash`。

*P*<br/>
可提供函式物件用來比較兩個機碼是否相等的類型。 預設值為[:equal_to\<K>](../standard-library/equal-to-struct.md)。

*米*<br/>
用於初始化無序 MapView 的[std::unordered_map](../standard-library/unordered-map-class.md)的引用或[Lvalue 和 Rvalue。](../cpp/lvalues-and-rvalues-visual-cpp.md)

*第一*<br/>
用來初始化 UnorderedMapView 的項目範圍中，第一個元素的輸入迭代器。

*最後*<br/>
用來初始化 UnorderedMapView 的項目範圍以外第一個元素的輸入迭代器。

## <a name="see-also"></a>另請參閱

[Platform::Collections 命名空間](../cppcx/platform-collections-namespace.md)<br/>
[Windows::Foundation::IMapView](/uwp/api/windows.foundation.collections.imapview-2)
