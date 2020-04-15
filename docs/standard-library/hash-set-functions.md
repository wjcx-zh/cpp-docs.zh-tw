---
title: '&lt;hash_set&gt; 函式'
ms.date: 11/04/2016
f1_keywords:
- hash_set/std::swap
- hash_set/std::swap (hash_multiset)
ms.assetid: 557a0162-3728-4537-97dc-f9f6cc7ece94
ms.openlocfilehash: d7df6b3c5dc0d0d493d17b3e9995bc4758ffd6d4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370591"
---
# <a name="lthash_setgt-functions"></a>&lt;hash_set&gt; 函式

|||
|-|-|
|[交換](#swap)|[swap (hash_multiset)](#swap_hash_multiset)|

## <a name="swap"></a><a name="swap"></a>交換

> [!NOTE]
> 這個 API 已過時。 替代方案是 [unordered_set 類別](../standard-library/unordered-set-class.md)。

交換兩個 hash_set 的元素。

```cpp
void swap(
    hash_set <Key, Traits, Allocator>& left,
    hash_set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>參數

*對*\
提供要交換的元素的hash_set,或hash_set其元素要與*hash_set的*要素交換。

*離開*\
hash_set,其要素將與hash_set*權利*者交換。

### <a name="remarks"></a>備註

範本`swap`函數是hash_set執行成員函`left.`數[交換](../standard-library/hash-set-class.md#swap)()`right`的容器類中專用的演演演算法。 這是編譯器所執行的函式範本部分排序執行個體。 當樣板與函式呼叫不是唯一配對，而使得樣板函式多載時，編譯器會選取最特製化的樣板函式版本。 在演算法類別中，一般的樣板函式版本

**template \<class T> void swap(T&, T&)**

會依指派運作而作業緩慢。 每個容器中的特製化版本運作速度會更快，因為它可以與容器類別的內部表示法一起運作。

### <a name="example"></a>範例

如需使用 `swap` 之範本版本的範例，請參閱成員函式 [hash_set::swap](../standard-library/hash-set-class.md#swap) 的程式碼範例。

## <a name="swap-hash_multiset"></a><a name="swap_hash_multiset"></a>交換 (hash_multiset)

> [!NOTE]
> 這個 API 已過時。 替代方案是 [unordered_set 類別](../standard-library/unordered-set-class.md)。

交換兩個 hash_multiset 的元素。

```cpp
void swap(hash_multiset <Key, Traits, Allocator>& left, hash_multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>參數

*對*\
提供要交換的元素hash_multiset,或hash_multiset其元素要與*hash_multiset的*要素交換。

*離開*\
hash_multiset,其要素將與hash_multiset*權*的要素交換。

### <a name="remarks"></a>備註

範本`swap`函數是容器類上專門hash_multiset執行成員函`left.`數[交換](../standard-library/hash-multiset-class.md#swap)()`right`的演演演算法。 這是編譯器所執行的函式範本部分排序執行個體。 當樣板與函式呼叫不是唯一配對，而使得樣板函式多載時，編譯器會選取最特製化的樣板函式版本。 在演算法類別中，一般的樣板函式版本

**template \<class T> void swap(T&, T&)**

會依指派運作而作業緩慢。 每個容器中的特製化版本運作速度會更快，因為它可以與容器類別的內部表示法一起運作。

### <a name="example"></a>範例

如需使用 `swap` 之範本版本的範例，請參閱成員函式 [hash_multiset::swap](../standard-library/hash-multiset-class.md#swap) 的程式碼範例。

## <a name="see-also"></a>另請參閱

[<hash_set>](../standard-library/hash-set.md)
