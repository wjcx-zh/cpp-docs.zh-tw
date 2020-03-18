---
title: '&lt;set&gt; 函式'
ms.date: 11/04/2016
f1_keywords:
- set/std::swap (map)
- set/std::swap (multiset)
ms.assetid: d1277d14-8502-46c0-b820-bcda820f9406
ms.openlocfilehash: a3a63fb86caa3485b1ee14538c3eb1f1ff72923e
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79419550"
---
# <a name="ltsetgt-functions"></a>&lt;set&gt; 函式

## <a name="swap"></a>swap （map）

交換兩個集合的項目。

```cpp
template <class Key, class Traits, class Allocator>
void swap(set<Key, Traits, Allocator>& left, set<Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>參數

*right*\
提供要交換之元素的集合，或其專案要與*左方*的集合交換的集合。

*左方*\
要與集合*許可權*的元素交換的集合。

### <a name="remarks"></a>備註

範本函式是在容器類別集上特製化的演算法，用來執行成員函式 `left.`[swap](../standard-library/set-class.md#swap)（`right`）。 這是編譯器所執行的函式範本部分排序執行個體。 當因範本函式多載而導致範本與函式呼叫的比對不是唯一的時，編譯器就會選取最特製化的範本函式版本。 在演算法類別中，一般的樣板函式版本

`template` \< **classT**> **void swap**（ **t &** ， **t &** ）

會依指派運作而作業緩慢。 每個容器中的特製化版本運作速度會更快，因為它可以與容器類別的內部表示法一起運作。

### <a name="example"></a>範例

如需使用 [ 樣板版本的範例，請參閱成員函式 ](../standard-library/set-class.md#swap)set::swap`swap` 的程式碼範例。

## <a name="swap_multiset"></a>交換（多重集）

交換兩個 multiset 的項目。

```cpp
template <class Key, class Traits, class Allocator>
void swap(multiset<Key, Traits, Allocator>& left, multiset<Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>參數

*right*\
提供要交換之專案的多重集，或其專案要與所*遺留*的多因素交換的多重集。

*左方*\
其專案要與多重集*許可權*的元件交換的多重集。

### <a name="remarks"></a>備註

範本函式是在容器類別多重集上特製化的演算法，用來執行成員函式 `left.`[swap](../standard-library/multiset-class.md#swap)（`right`）。 這是編譯器所執行的函式範本部分排序執行個體。 當因範本函式多載而導致範本與函式呼叫的比對不是唯一的時，編譯器就會選取最特製化的範本函式版本。 在演算法類別中，一般的樣板函式版本

`template` \< **classT**> **void swap**（ **t &** ， **t &** ）

會依指派運作而作業緩慢。 每個容器中的特製化版本運作速度會更快，因為它可以與容器類別的內部表示法一起運作。

### <a name="example"></a>範例

如需使用 [ 樣板版本的範例，請參閱成員函式 ](../standard-library/multiset-class.md#swap)multiset::swap`swap` 的程式碼範例。
