---
title: '&lt;set&gt; 函式 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- set/std::swap (map)
- set/std::swap (multiset)
ms.assetid: d1277d14-8502-46c0-b820-bcda820f9406
caps.latest.revision: 7
manager: ghogen
ms.openlocfilehash: 29579adf6b9556635862985b324e27ebea416bc0
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="ltsetgt-functions"></a>&lt;set&gt; 函式

|||
|-|-|
|[swap (map)](#swap)|[swap (multiset)](#swap_multiset)|

## <a name="swap"></a>  swap  (map)

交換兩個集合的項目。

```cpp
template <class Key, class Traits, class Allocator>
void swap(set<Key, Traits, Allocator>& left, set<Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>參數

`right` 提供待交換，項目集或其項目要與集的交換集`left`。

`left` 其元素要與集的交換集`right`。

### <a name="remarks"></a>備註

樣板函式是已在容器類別 set 上特製化的演算法，可用來執行成員函式 `left.`[swap](../standard-library/set-class.md#swap)( `right`)。 這是編譯器所執行之函式樣板的部分排序執行個體。 若因樣板函式多載而導致樣板與函式呼叫的比對不是唯一，則編譯器就會選取特製化程度最高的樣板函式版本。 在演算法類別中，一般的樣板函式版本

`template` \< **classT**> **void swap**( **T&**, **T&**)

會依指派運作而作業緩慢。 每個容器中的特製化版本運作速度會更快，因為它可以與容器類別的內部表示法一起運作。

### <a name="example"></a>範例

如需使用 `swap` 樣板版本的範例，請參閱成員函式 [set::swap](../standard-library/set-class.md#swap) 的程式碼範例。

## <a name="swap_multiset"></a>  swap  (multiset)

交換兩個 multiset 的項目。

```cpp
template <class Key, class Traits, class Allocator>
void swap(multiset<Key, Traits, Allocator>& left, multiset<Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>參數

`right` 提供要交換之項目的多重集或其項目要與多重集的交換的 multiset `left`。

`left` 其元素要與多重集的交換的 multiset `right`。

### <a name="remarks"></a>備註

樣板函式是已在容器類別 multiset 上特製化的演算法，可用來執行成員函式 `left.`[swap](../standard-library/multiset-class.md#swap)( `right`)。 這是編譯器所執行之函式樣板的部分排序執行個體。 若因樣板函式多載而導致樣板與函式呼叫的比對不是唯一，則編譯器就會選取特製化程度最高的樣板函式版本。 在演算法類別中，一般的樣板函式版本

`template` \< **classT**> **void swap**( **T&**, **T&**)

會依指派運作而作業緩慢。 每個容器中的特製化版本運作速度會更快，因為它可以與容器類別的內部表示法一起運作。

### <a name="example"></a>範例

如需使用 `swap` 樣板版本的範例，請參閱成員函式 [multiset::swap](../standard-library/multiset-class.md#swap) 的程式碼範例。

## <a name="see-also"></a>另請參閱

[\<set>](../standard-library/set.md)<br/>
