---
title: '&lt;set&gt; 函式'
ms.date: 11/04/2016
f1_keywords:
- set/std::swap (map)
- set/std::swap (multiset)
ms.assetid: d1277d14-8502-46c0-b820-bcda820f9406
ms.openlocfilehash: 3873a85218c738b3a9693926e064a10b82a553c1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50467332"
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

*right*<br/>
提供要交換之元素的集合或利用 set 來交換項目的 set*左*。

*left*<br/>
利用 set 來交換項目的 set*右*。

### <a name="remarks"></a>備註

範本函式是在容器類別 set 來執行成員函式特製化的演算法`left.`[交換](../standard-library/set-class.md#swap)(`right`)。 這是編譯器所執行之函式樣板的部分排序執行個體。 若因樣板函式多載而導致樣板與函式呼叫的比對不是唯一，則編譯器就會選取特製化程度最高的樣板函式版本。 在演算法類別中，一般的樣板函式版本

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

*right*<br/>
提供要交換的項目或其項目要與 multiset 交換的 multiset*左*。

*left*<br/>
其項目要與 multiset 交換的 multiset*右*。

### <a name="remarks"></a>備註

範本函式是在執行成員函式的容器類別 multiset 上特製化的演算法`left.`[交換](../standard-library/multiset-class.md#swap)(`right`)。 這是編譯器所執行之函式樣板的部分排序執行個體。 若因樣板函式多載而導致樣板與函式呼叫的比對不是唯一，則編譯器就會選取特製化程度最高的樣板函式版本。 在演算法類別中，一般的樣板函式版本

`template` \< **classT**> **void swap**( **T&**, **T&**)

會依指派運作而作業緩慢。 每個容器中的特製化版本運作速度會更快，因為它可以與容器類別的內部表示法一起運作。

### <a name="example"></a>範例

如需使用 `swap` 樣板版本的範例，請參閱成員函式 [multiset::swap](../standard-library/multiset-class.md#swap) 的程式碼範例。

## <a name="see-also"></a>另請參閱

[\<set>](../standard-library/set.md)<br/>
