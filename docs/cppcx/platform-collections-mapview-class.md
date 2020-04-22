---
title: Platform::Collections::MapView 類別
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::MapView::MapView
- COLLECTION/Platform::Collections::MapView::First
- COLLECTION/Platform::Collections::MapView::HasKey
- COLLECTION/Platform::Collections::MapView::Lookup
- COLLECTION/Platform::Collections::MapView::Size
- COLLECTION/Platform::Collections::MapView::Split
helpviewer_keywords:
- MapView Class
ms.assetid: 9577dde7-f599-43c6-b1e4-7d653706fd62
ms.openlocfilehash: a770b318d893b9e81bdf11a75c2b0b05c0a9979f
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750608"
---
# <a name="platformcollectionsmapview-class"></a>Platform::Collections::MapView 類別

表示 *對應 (Map)*(機碼值組的集合) 的唯讀檢視。

## <a name="syntax"></a>語法

```
template <
   typename K,
   typename V,
   typename C = ::std::less<K>>
ref class MapView sealed;
```

#### <a name="parameters"></a>參數

*K*<br/>
機碼值組中，機碼的類型。

*五*<br/>
機碼值組中，值的型別。

*C*<br/>
一個類型，提供函式物件，可以根據排序鍵比較兩個項目值，以判斷它們在 MapView 中的相對順序。 預設情況下[,std::減\<去 K>](../standard-library/less-struct.md)。

### <a name="remarks"></a>備註

MapView 是[Windows::基礎:集合::IMapView \<K,V>](/uwp/api/Windows.Foundation.Collections.IMapView_K_V_)介面的具體 C++實現,該介面通過應用程式二進位介面 (ABI) 傳遞。 如需詳細資訊，請參閱 [集合 (C++/CX)](../cppcx/collections-c-cx.md)。

### <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[地圖檢視:mapView](#ctor)|初始化 MapView 類別的新執行個體。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[地圖檢視:第一](#first)|傳回迭代器，初始化為對應檢視中的第一個元素。|
|[地圖檢視::有鍵](#haskey)|判斷目前 MapView 是否包含指定的機碼。|
|[地圖檢視::尋找](#lookup)|在目前 MapView 物件中擷取位於指定機碼的元素。|
|[MapView::Size](#size)|傳回目前 MapView 物件中的項目數。|
|[地圖檢視:分割](#split)|將原始 MapView 物件分割為兩個 MapView 物件。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

`MapView`

### <a name="requirements"></a>需求

**標頭：** collection.h

**命名空間：** Platform::Collections

## <a name="mapviewfirst-method"></a><a name="first"></a>地圖檢視:第一種方法

傳回指定對應檢視中之第一個項目的迭代器。

### <a name="syntax"></a>語法

```
virtual Windows::Foundation::Collections::IIterator<
   Windows::Foundation::Collections::IKeyValuePair<K, V>^>^ First();
```

### <a name="return-value"></a>傳回值

迭代器，指定對應檢視中的第一個元素。

### <a name="remarks"></a>備註

保存 First() 傳回的反覆運算器的一個方便方法是將返回值分配給使用**自動**類型扣減關鍵字聲明的變數。 例如： `auto x = myMapView->First();` 。

## <a name="mapviewhaskey-method"></a><a name="haskey"></a>地圖檢視::有鍵方法

判斷目前 MapView 是否包含指定的機碼。

### <a name="syntax"></a>語法

```

bool HasKey(K key);
```

### <a name="parameters"></a>參數

*key*<br/>
用來尋找 MapView 項目的機碼。 *鍵*的類型是類型名稱*K*。

### <a name="return-value"></a>傳回值

如果找到金鑰,**則為 true;** 否則,**假**。

## <a name="mapviewlookup-method"></a><a name="lookup"></a>地圖檢視::查找方法

取得與類型為 K 之指定機碼相關聯且類型為 V 的值。

### <a name="syntax"></a>語法

```
V Lookup(K key);
```

### <a name="parameters"></a>參數

*key*<br/>
用來在 MapView 中尋找元素的機碼。 的類型`key`是類型名稱*K*。

### <a name="return-value"></a>傳回值

與 `key` 配對的值。 傳回值的型態為類型名稱*V*。

## <a name="mapviewmapview-constructor"></a><a name="ctor"></a>地圖檢視:mapView 建構函數

初始化 MapView 類別的新執行個體。

### <a name="syntax"></a>語法

```cpp
explicit MapView(const C& comp = C());

explicit MapView(const ::std::map<K, V, C>& m);

explicit MapView(std::map<K, V, C>&& m);

template <typename InIt> MapView(
    InIt first,
    InIt last,
    const C& comp = C());

MapView(
    ::std::initializer_list<std::pair<const K, V>> il,
    const C& comp = C());
```

### <a name="parameters"></a>參數

*Init*<br/>
目前 MapView 的 typename。

*Comp*<br/>
函式物件。這個函式物件可以根據排序機碼比較兩個元素值，判斷它們在 MapView 中的相對順序。

*米*<br/>
對用於初始化當前 MapView`map Class`的引用或[Lvalue 和 Rvalue。](../cpp/lvalues-and-rvalues-visual-cpp.md)

*第一*<br/>
用來初始化目前 MapView 的項目範圍中，第一個項目的輸入迭代器。

*最後*<br/>
用來初始化目前 MapView 的項目範圍以外第一個項目的輸入迭代器。

*I l*<br/>
[std::initializer_list<下::p空氣\<K,V>>](../standard-library/initializer-list-class.md)其元素將插入MapView。

## <a name="mapviewsize-method"></a><a name="size"></a>地圖檢視:大小方法

傳回目前 MapView 物件中的項目數。

### <a name="syntax"></a>語法

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>傳回值

目前 MapView 中的項目數。

## <a name="mapviewsplit-method"></a><a name="split"></a>映射檢視::拆分方法

將目前 MapView 物件分割為兩個 MapView 物件。 這個方法無法操作。

### <a name="syntax"></a>語法

```cpp
void Split(
   Windows::Foundation::Collections::IMapView<
                         K, V>^ * firstPartition,
   Windows::Foundation::Collections::IMapView<
                         K, V>^ * secondPartition);
```

### <a name="parameters"></a>參數

*第一個分割區*<br/>
原始 MapView 物件的第一個部分。

*第二個分割區*<br/>
原始 MapView 物件的第二個部分。

### <a name="remarks"></a>備註

這個方法無法操作，不會執行任何動作。

## <a name="see-also"></a>另請參閱

[平台命名空間](platform-namespace-c-cx.md)
