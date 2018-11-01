---
title: '&lt;map&gt; 函式'
ms.date: 11/04/2016
f1_keywords:
- map/std::swap (map)
- map/std::swap (multimap)
ms.assetid: 7cb3d1a5-7add-4726-a73f-61927eafd466
ms.openlocfilehash: 6c3480e9ffbbab46a42ae790d8b70afbcd823457
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50517295"
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

*right*<br/>
提供要交換之元素的地圖或地圖其項目要與 map 交換*左*。

*left*<br/>
其項目要與 map 交換的對應*右*。

### <a name="remarks"></a>備註

範本函式是在執行成員函式的容器類別 map 特製化的演算法`left`。[交換](../standard-library/map-class.md#swap)( `right`)。 這是編譯器所執行之函式樣板的部分排序執行個體。 當樣板與函式呼叫不是唯一配對，而使得樣板函式多載時，編譯器會選取最特製化的樣板函式版本。 演算法類別中樣板函式的一般版本 **template** \< **class T**> **void swap**( **T&**, **T&**) 會依指派運作，且作業緩慢。 每個容器中的特製化版本運作速度會更快，因為它可以與容器類別的內部表示法一起運作。

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

*right*<br/>
提供要交換之元素的 multimap 或其項目要與 multimap 交換的 multimap*左*。

*left*<br/>
其項目要與 multimap 交換的 multimap*右*。

### <a name="remarks"></a>備註

範本函式是在容器類別 multimap，來執行成員函式上執行的容器類別 map 特製化的演算法`left`。[交換](../standard-library/multimap-class.md#swap)(`right`)。 這是編譯器所執行之函式樣板的部分排序執行個體。 當樣板與函式呼叫不是唯一配對，而使得樣板函式多載時，編譯器會選取最特製化的樣板函式版本。 演算法類別中樣板函式的一般版本 **template** \< **class T**> **void swap**( **T&**, **T&**) 會依指派運作，且作業緩慢。 每個容器中的特製化版本運作速度會更快，因為它可以與容器類別的內部表示法一起運作。

### <a name="example"></a>範例

如需使用 `swap` 的範本版本的範例，請參閱成員函式 [multimap::swap](../standard-library/multimap-class.md#swap) 的程式碼範例。

## <a name="see-also"></a>另請參閱

[\<map>](../standard-library/map.md)<br/>
