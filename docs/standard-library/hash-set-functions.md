---
title: '&lt;hash_set&gt; 函式'
ms.date: 11/04/2016
f1_keywords:
- hash_set/std::swap
- hash_set/std::swap (hash_multiset)
ms.assetid: 557a0162-3728-4537-97dc-f9f6cc7ece94
ms.openlocfilehash: 2fbc05c16ba6629397bbb07bab30cb9315a16e1f
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79421615"
---
# <a name="lthash_setgt-functions"></a>&lt;hash_set&gt; 函式

|||
|-|-|
|[swap](#swap)|[swap (hash_multiset)](#swap_hash_multiset)|

## <a name="swap"></a> swap

> [!NOTE]
> 這個應用程式開發介面已過時。 替代方案是 [unordered_set 類別](../standard-library/unordered-set-class.md)。

交換兩個 hash_set 的元素。

```cpp
void swap(
    hash_set <Key, Traits, Allocator>& left,
    hash_set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>參數

*right*\
Hash_set 提供要交換的專案，或要與 hash_set*左邊*的元素交換的 hash_set。

*左方*\
Hash_set，其專案要與 hash_set*許可權*的元素交換。

### <a name="remarks"></a>備註

`swap` 範本函式是在容器類別上特製化的演算法，hash_set 以執行成員函式 `left.`[swap](../standard-library/hash-set-class.md#swap)（`right`）。 這是編譯器所執行的函式範本部分排序執行個體。 當因範本函式多載而導致範本與函式呼叫的比對不是唯一的時，編譯器就會選取最特製化的範本函式版本。 在演算法類別中，一般的樣板函式版本

**template \<class T> void swap(T&, T&)**

會依指派運作而作業緩慢。 每個容器中的特製化版本運作速度會更快，因為它可以與容器類別的內部表示法一起運作。

### <a name="example"></a>範例

如需使用 [ 之範本版本的範例，請參閱成員函式 ](../standard-library/hash-set-class.md#swap)hash_set::swap`swap` 的程式碼範例。

## <a name="swap_hash_multiset"></a>  swap (hash_multiset)

> [!NOTE]
> 這個應用程式開發介面已過時。 替代方案是 [unordered_set 類別](../standard-library/unordered-set-class.md)。

交換兩個 hash_multiset 的元素。

```cpp
void swap(hash_multiset <Key, Traits, Allocator>& left, hash_multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>參數

*right*\
Hash_multiset 提供要交換的專案，或要與 hash_multiset*左邊*的元素交換的 hash_multiset。

*左方*\
Hash_multiset，其專案要與 hash_multiset*許可權*的元素交換。

### <a name="remarks"></a>備註

`swap` 範本函式是在容器類別上特製化的演算法，hash_multiset 以執行成員函式 `left.`[swap](../standard-library/hash-multiset-class.md#swap)（`right`）。 這是編譯器所執行的函式範本部分排序執行個體。 當因範本函式多載而導致範本與函式呼叫的比對不是唯一的時，編譯器就會選取最特製化的範本函式版本。 在演算法類別中，一般的樣板函式版本

**template \<class T> void swap(T&, T&)**

會依指派運作而作業緩慢。 每個容器中的特製化版本運作速度會更快，因為它可以與容器類別的內部表示法一起運作。

### <a name="example"></a>範例

如需使用 [ 之範本版本的範例，請參閱成員函式 ](../standard-library/hash-multiset-class.md#swap)hash_multiset::swap`swap` 的程式碼範例。

## <a name="see-also"></a>另請參閱

[<hash_set>](../standard-library/hash-set.md)
