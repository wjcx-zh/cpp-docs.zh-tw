---
title: boyer_moore_horspool_searcher 類別
ms.date: 08/03/2019
f1_keywords:
- functional/std::boyer_moore_horspool_searcher
helpviewer_keywords:
- std::boyer_moore_horspool_searcher [C++]
ms.openlocfilehash: 1eb1f099ca2976dd4b0ea80ebdfb93a8b5c61f70
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2020
ms.locfileid: "90039829"
---
# <a name="boyer_moore_horspool_searcher-class"></a>boyer_moore_horspool_searcher 類別

`boyer_moore_horspool_searcher`類別是一種函式物件類型，會使用 Boyer-堯-Horspool 演算法來搜尋物件的函式中指定的序列。 搜尋是在另一個提供給物件函式呼叫運算子的序列中完成。 此類別會以參數形式傳遞至 [std：： search](algorithm-functions.md#search)的其中一個多載。

## <a name="syntax"></a>語法

```cpp
template <
    class RandomAccessIterator,
    class Hash = hash<typename iterator_traits<RandomAccessIterator>::value_type>,
    class BinaryPredicate = equal_to<>>
class boyer_moore_horspool_searcher
{
    boyer_moore_horspool_searcher(
        RandomAccessIterator pat_first,
        RandomAccessIterator pat_last,
        Hash hf = Hash(),
        BinaryPredicate pred = BinaryPredicate());

    template <class RandomAccessIterator2>
    pair<RandomAccessIterator2, RandomAccessIterator2> operator()(
        RandomAccessIterator2 first,
        RandomAccessIterator2 last) const;
};
```

## <a name="members"></a>成員

| member | 描述 |
| - | - |
| **構造 函數** | |
| [boyer_moore_horspool_searcher](#boyer-moore-horspool-searcher-constructor) | 建立搜尋的實例。 |
| **運算子** | |
| [運算子 ( # B1 ](#operator-call) | 叫用序列上的作業。 |

## <a name="boyer_moore_horspool_searcher-constructor"></a><a name="boyer-moore-horspool-searcher-constructor"></a> boyer_moore_horspool_searcher 的函式

`boyer_moore_horspool_searcher`使用序列來搜尋、雜湊函式物件和等號比較述詞，以建立函式物件。

```cpp
boyer_moore_horspool_searcher(
    RandomAccessIterator pat_first,
    RandomAccessIterator pat_last,
    Hash hf = Hash(),
    BinaryPredicate pred = BinaryPredicate());
```

### <a name="parameters"></a>參數

*pat_first*\
要搜尋之序列的初始元素。

*pat_last*\
要搜尋的序列結尾。

*高頻*\
可呼叫的物件，用來雜湊順序元素。

*Pred*\
Sequence 元素的選擇性相等比較述詞。 如果未指定相等比較型別，則預設值為 `std::equal_to` 。

### <a name="remarks"></a>備註

擲回 *BinaryPredicate*、 *Hash*或 *RandomAccessIterator* 類型的複製方法所擲回的任何例外狀況，或 *BinaryPredicate* 或 *Hash*的呼叫運算子所擲回的任何例外狀況。

這個類別是 c + + 17 的新類別。

## <a name="operator"></a><a name="operator-call"></a> 運算子 ( # A1

函數物件的呼叫運算子。 在引數序列內搜尋指定給函式的 `[first, last)` 順序。

```cpp
template <class ForwardIterator2>   // C++17
pair<RandomAccessIterator2, RandomAccessIterator2> operator()(
    RandomAccessIterator2 first,
    RandomAccessIterator2 last) const;
```

### <a name="parameters"></a>參數

*第一*\
要在其中搜尋之序列的初始元素。

*最後*\
要在其中搜尋的序列結尾。

### <a name="remarks"></a>備註

如果搜尋模式 `[pat_first, pat_last)` 是空的，則會傳回 `make_pair(first, first)` 。 如果找不到搜尋模式，則會傳回 `make_pair(last, last)` 。 否則，會傳回一組反覆運算器到序列中的開頭和結尾，而 `[first, last)` 該值等於根據述詞 `[pat_first, pat_last)` *pred*。

這個類別是 c + + 17 的新類別。

## <a name="see-also"></a>另請參閱

[\<functional>](functional.md)\
[演算法函數](algorithm-functions.md)\
[boyer_moore_searcher 類別](boyer-moore-searcher-class.md)\
[std：： search](algorithm-functions.md#search)
