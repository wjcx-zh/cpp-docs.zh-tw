---
title: '&lt;map&gt; 函式'
ms.date: 11/04/2016
f1_keywords:
- map/std::swap (map)
- map/std::swap (multimap)
ms.assetid: 7cb3d1a5-7add-4726-a73f-61927eafd466
ms.openlocfilehash: 8cc4a82e08963902f9ba5c21ace759c47bdd0014
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228215"
---
# <a name="ltmapgt-functions"></a>&lt;map&gt; 函式

## <a name="swap-map"></a><a name="swap_multimap"></a>swap （map）

交換兩個對應的項目。

```cpp
template <class key, class T, class _Pr, class _Alloc>
void swap(
    map<Key, Traits, Compare, Alloctor>& left,
    map<Key, Traits, Compare, Alloctor>& right);
```

### <a name="parameters"></a>參數

*再*\
提供要交換之專案的對應，或其專案要與*左邊*的對應交換的對應。

*左面*\
對應，其專案會與對應*右方*的元素交換。

### <a name="remarks"></a>備註

範本函式是在容器類別對應上特製化的演算法，用來執行成員函式 `left` 。[swap](../standard-library/map-class.md#swap)（ `right` ）。 這是編譯器所執行的函式範本部分排序執行個體。 當樣板與函式呼叫不是唯一配對，而使得樣板函式多載時，編譯器會選取最特製化的樣板函式版本。 在演算法類別中，樣板函式的一般版本 **`template`** \< **class T**> （ **void swap**（ **t&**， **t&**）會依指派運作，而且是緩慢的作業。 每個容器中的特製化版本運作速度會更快，因為它可以與容器類別的內部表示法一起運作。

### <a name="example"></a>範例

如需使用 `swap` 的範本版本的範例，請參閱成員函式 [map::swap](../standard-library/map-class.md#swap) 的程式碼範例。

## <a name="swap-multimap"></a><a name="swap"></a>swap （multimap）

交換兩個 multimap 的元素。

```cpp
template <class key, class T, class _Pr, class _Alloc>
void swap(
    multimap<Key, Traits, Compare, Alloctor>& left,
    multimap<Key, Traits, Compare, Alloctor>& right);
```

### <a name="parameters"></a>參數

*再*\
提供要交換之元素的 multimap，或要與 multimap*左邊*的專案交換其元素的 multimap。

*左面*\
要與 multimap*許可權*的元素交換其專案的 multimap。

### <a name="remarks"></a>備註

範本函式是在容器類別對應上特製化的演算法，可在容器類別 multimap 上執行，以執行成員函式 `left` 。[swap](../standard-library/multimap-class.md#swap) （ `right` ）。 這是編譯器所執行的函式範本部分排序執行個體。 當樣板與函式呼叫不是唯一配對，而使得樣板函式多載時，編譯器會選取最特製化的樣板函式版本。 在演算法類別中，樣板函式的一般版本 **`template`** \< **class T**> （ **void swap**（ **t&**， **t&**）會依指派運作，而且是緩慢的作業。 每個容器中的特製化版本運作速度會更快，因為它可以與容器類別的內部表示法一起運作。

### <a name="example"></a>範例

如需使用 `swap` 的範本版本的範例，請參閱成員函式 [multimap::swap](../standard-library/multimap-class.md#swap) 的程式碼範例。
