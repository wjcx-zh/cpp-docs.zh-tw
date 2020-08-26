---
title: '&lt;hash_map&gt; 函式'
ms.date: 11/04/2016
f1_keywords:
- hash_map/std::swap
- hash_map/std::swap (hash_map)
ms.assetid: 28748cd0-71f7-41b9-b068-579183645fba
ms.openlocfilehash: a29254d32954556ad3a2fbedb89fb3556533ff1f
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88841190"
---
# <a name="lthash_mapgt-functions"></a>&lt;hash_map&gt; 函式

[交換](#swap)\
[swap (hash_map)](#swap_hash_map)

## <a name="swap-hash_map"></a><a name="swap_hash_map"></a> 交換 (hash_map) 

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_map 類別](../standard-library/unordered-map-class.md)。

交換兩個 hash_map 的元素。

```cpp
void swap(
    hash_map <Key, Type, Traits, Alloctor>& left,
    hash_map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>參數

*對*\
Hash_map 其元素要與 *左邊*的對應交換。

*離開*\
Hash_map，其元素要與對應的專案*交換。*

### <a name="remarks"></a>備註

範本函式是在容器類別 hash_map 特製化的演算法，用來執行成員函式 `left.`[swap](../standard-library/basic-ios-class.md#swap)*(right*)。 這是編譯器所執行的函式範本部分排序執行個體。 當樣板與函式呼叫不是唯一配對，而使得樣板函式多載時，編譯器會選取最特製化的樣板函式版本。 範本函式的一般版本（樣板 ** \<class T> void Swap (T&，t&) **）在演算法標頭檔中的運作方式是透過指派，而且是緩慢的作業。 每個容器中的特製化版本運作速度會更快，因為它可以與容器類別的內部表示法一起運作。

## <a name="swap"></a><a name="swap"></a> 交換

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_multimap 類別](../standard-library/unordered-multimap-class.md)。

交換兩個 hash_multimap 的元素。

```cpp
void swap(
    hash_multimap <Key, Type, Traits, Alloctor>& left,
    hash_multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>參數

*對*\
Hash_multimap 其元素要與 *左邊*的對應交換。

*離開*\
Hash_multimap，其元素要與對應的專案*交換。*

### <a name="remarks"></a>備註

範本函式是在容器類別 hash_multimap 特製化的演算法，用來執行成員函式 `left.`[swap](../standard-library/hash-multimap-class.md#swap)*(right*`)`。 這是編譯器所執行的函式範本部分排序執行個體。 當樣板與函式呼叫不是唯一配對，而使得樣板函式多載時，編譯器會選取最特製化的樣板函式版本。 範本函式的一般版本（樣板 ** \<class T> void Swap (T&，t&) **）在演算法標頭檔中的運作方式是透過指派，而且是緩慢的作業。 每個容器中的特製化版本運作速度會更快，因為它可以與容器類別的內部表示法一起運作。

## <a name="see-also"></a>另請參閱

[<hash_map>](../standard-library/hash-map.md)
