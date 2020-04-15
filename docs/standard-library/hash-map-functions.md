---
title: '&lt;hash_map&gt; 函式'
ms.date: 11/04/2016
f1_keywords:
- hash_map/std::swap
- hash_map/std::swap (hash_map)
ms.assetid: 28748cd0-71f7-41b9-b068-579183645fba
ms.openlocfilehash: 7cb2e46f19bd30e3eb313cde867c6a055cb8bca5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370619"
---
# <a name="lthash_mapgt-functions"></a>&lt;hash_map&gt; 函式

|||
|-|-|
|[交換](#swap)|[swap (hash_map)](#swap_hash_map)|

## <a name="swap-hash_map"></a><a name="swap_hash_map"></a>交換 (hash_map)

> [!NOTE]
> 這個 API 已過時。 替代方案是 [unordered_map 類別](../standard-library/unordered-map-class.md)。

交換兩個 hash_map 的元素。

```cpp
void swap(
    hash_map <Key, Type, Traits, Alloctor>& left,
    hash_map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>參數

*對*\
hash_map的元素要與*左邊*的地圖的元素交換。

*離開*\
hash_map的元素要與地圖*右側*的元素交換。

### <a name="remarks"></a>備註

範本函式是在容器類別 hash_map 特製化的演算法，用來執行成員函式 `left.`[swap](../standard-library/basic-ios-class.md#swap)*(right*)。 這是編譯器所執行的函式範本部分排序執行個體。 當樣板與函式呼叫不是唯一配對，而使得樣板函式多載時，編譯器會選取最特製化的樣板函式版本。 演算法標頭檔案中函式版本的一般範本 **template \<class T> void swap(T&, T&)** 會依指派運作而作業緩慢。 每個容器中的特製化版本運作速度會更快，因為它可以與容器類別的內部表示法一起運作。

## <a name="swap"></a><a name="swap"></a>交換

> [!NOTE]
> 這個 API 已過時。 替代方案是 [unordered_multimap 類別](../standard-library/unordered-multimap-class.md)。

交換兩個 hash_multimap 的元素。

```cpp
void swap(
    hash_multimap <Key, Type, Traits, Alloctor>& left,
    hash_multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>參數

*對*\
hash_multimap的元素要與*左邊*的地圖的元素交換。

*離開*\
其元素要與地圖*右側*的元素交換的hash_multimap。

### <a name="remarks"></a>備註

範本函式是在容器類別 hash_multimap 特製化的演算法，用來執行成員函式 `left.`[swap](../standard-library/hash-multimap-class.md#swap)*(right*`)`。 這是編譯器所執行的函式範本部分排序執行個體。 當樣板與函式呼叫不是唯一配對，而使得樣板函式多載時，編譯器會選取最特製化的樣板函式版本。 演算法標頭檔案中函式版本的一般範本 **template \<class T> void swap(T&, T&)** 會依指派運作而作業緩慢。 每個容器中的特製化版本運作速度會更快，因為它可以與容器類別的內部表示法一起運作。

## <a name="see-also"></a>另請參閱

[<hash_map>](../standard-library/hash-map.md)
