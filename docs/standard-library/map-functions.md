---
title: '&lt;map&gt; 函式 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- map/std::swap (map)
- map/std::swap (multimap)
ms.assetid: 7cb3d1a5-7add-4726-a73f-61927eafd466
ms.openlocfilehash: d6f62868d17cec9215b18451527c3a2e4e22b7f2
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33854918"
---
# <a name="ltmapgt-functions"></a>&lt;map&gt; 函式

|||
|-|-|
|[swap (map)](#swap)|[swap (multimap)](#swap_multimap)|

## <a name="swap_multimap"></a>  swap  (map)

交換兩個對應的項目。

```cpp
template <class key, class T, class _Pr, class _Alloc>
void swap(
    map<Key, Traits, Compare, Alloctor>& left,
    map<Key, Traits, Compare, Alloctor>& right);
```

### <a name="parameters"></a>參數

`right` 提供待交換，項目在地圖或地圖，其元素要與對應的交換`left`。

`left` 其元素要與對應的交換的對應`right`。

### <a name="remarks"></a>備註

樣板函式是演算法特製化的容器類別對應，以執行此成員函式`left`。[交換](../standard-library/map-class.md#swap)( `right`)。 這是編譯器所執行之函式樣板的部分排序執行個體。 當樣板與函式呼叫不是唯一配對，而使得樣板函式多載時，編譯器會選取最特製化的樣板函式版本。 演算法類別中樣板函式的一般版本 **template** \< **class T**> **void swap**( **T&**, **T&**) 會依指派運作，且作業緩慢。 每個容器中的特製化版本運作速度會更快，因為它可以與容器類別的內部表示法一起運作。

### <a name="example"></a>範例

如需使用 `swap` 的範本版本的範例，請參閱成員函式 [map::swap](../standard-library/map-class.md#swap) 的程式碼範例。

## <a name="swap"></a>  swap  (multimap)

交換兩個 multimap 的元素。

```cpp
template <class key, class T, class _Pr, class _Alloc>
void swap(
    multimap<Key, Traits, Compare, Alloctor>& left,
    multimap<Key, Traits, Compare, Alloctor>& right);
```

### <a name="parameters"></a>參數

`right` Multimap 提供待交換，項目或其項目要與 multimap 的交換的 multimap `left`。

`left` 其元素要與 multimap 的交換的 multimap `right`。

### <a name="remarks"></a>備註

樣板函式是演算法特製化的容器類別 multimap 執行成員函式上執行的容器類別對應`left`。[交換](../standard-library/multimap-class.md#swap)( `right`)。 這是編譯器所執行之函式樣板的部分排序執行個體。 當樣板與函式呼叫不是唯一配對，而使得樣板函式多載時，編譯器會選取最特製化的樣板函式版本。 演算法類別中樣板函式的一般版本 **template** \< **class T**> **void swap**( **T&**, **T&**) 會依指派運作，且作業緩慢。 每個容器中的特製化版本運作速度會更快，因為它可以與容器類別的內部表示法一起運作。

### <a name="example"></a>範例

如需使用 `swap` 的範本版本的範例，請參閱成員函式 [multimap::swap](../standard-library/multimap-class.md#swap) 的程式碼範例。

## <a name="see-also"></a>另請參閱

[\<map>](../standard-library/map.md)<br/>
