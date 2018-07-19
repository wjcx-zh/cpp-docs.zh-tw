---
title: '&lt;hash_set&gt; 函式 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- hash_set/std::swap
- hash_set/std::swap (hash_multiset)
ms.assetid: 557a0162-3728-4537-97dc-f9f6cc7ece94
ms.openlocfilehash: ad8041ff6a4abab84272d2bbbdee290bfce4eff6
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38961873"
---
# <a name="lthashsetgt-functions"></a>&lt;hash_set&gt; 函式

|||
|-|-|
|[swap](#swap)|[swap (hash_multiset)](#swap_hash_multiset)|

## <a name="swap"></a>  swap

> [!NOTE]
> 這個 API 已過時。 替代方案是 [unordered_set 類別](../standard-library/unordered-set-class.md)。

交換兩個 hash_set 的元素。

```cpp
void swap(
    hash_set <Key, Traits, Allocator>& left,
    hash_set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>參數

*右*提供要交換之元素的 hash_set 或其項目要與 hash_set 交換的 hash_set*左*。

*左*其項目要與 hash_set 交換的 hash_set*右*。

### <a name="remarks"></a>備註

`swap`範本函式是執行成員函式的容器類別 hash_set 特製化的演算法`left.`[交換](../standard-library/hash-set-class.md#swap)(`right`)。 這是編譯器所執行之函式樣板的部分排序執行個體。 若因樣板函式多載而導致樣板與函式呼叫的比對不是唯一，則編譯器就會選取特製化程度最高的樣板函式版本。 演算法類別中範本函式的一般版本

**template \<class T> void swap(T&, T&)**

會依指派運作而作業緩慢。 每個容器中的特製化版本運作速度會更快，因為它可以與容器類別的內部表示法一起運作。

### <a name="example"></a>範例

如需使用 `swap` 之範本版本的範例，請參閱成員函式 [hash_set::swap](../standard-library/hash-set-class.md#swap) 的程式碼範例。

## <a name="swap_hash_multiset"></a>  swap (hash_multiset)

> [!NOTE]
> 這個 API 已過時。 替代方案是 [unordered_set 類別](../standard-library/unordered-set-class.md)。

交換兩個 hash_multiset 的元素。

```cpp
void swap(hash_multiset <Key, Traits, Allocator>& left, hash_multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>參數

*右*提供要交換之元素的 hash_multiset 或其項目要與 hash_multiset 交換的 hash_multiset*左*。

*左*其項目要與 hash_multiset 交換的 hash_multiset*右*。

### <a name="remarks"></a>備註

`swap`範本函式是執行成員函式的容器類別 hash_multiset 特製化的演算法`left.`[交換](../standard-library/hash-multiset-class.md#swap)(`right`)。 這是編譯器所執行之函式樣板的部分排序執行個體。 若因樣板函式多載而導致樣板與函式呼叫的比對不是唯一，則編譯器就會選取特製化程度最高的樣板函式版本。 演算法類別中範本函式的一般版本

**template \<class T> void swap(T&, T&)**

會依指派運作而作業緩慢。 每個容器中的特製化版本運作速度會更快，因為它可以與容器類別的內部表示法一起運作。

### <a name="example"></a>範例

如需使用 `swap` 之範本版本的範例，請參閱成員函式 [hash_multiset::swap](../standard-library/hash-multiset-class.md#swap) 的程式碼範例。

## <a name="see-also"></a>另請參閱

[<hash_set>](../standard-library/hash-set.md)<br/>
