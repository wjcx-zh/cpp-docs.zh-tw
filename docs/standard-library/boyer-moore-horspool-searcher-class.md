---
title: boyer_moore_horspool_searcher 類別
ms.date: 08/03/2019
f1_keywords:
- functional/std::boyer_moore_horspool_searcher
helpviewer_keywords:
- std::boyer_moore_horspool_searcher [C++]
ms.openlocfilehash: c7d24fee4a47fc588b00e527594682f1c4aadf76
ms.sourcegitcommit: 16c0392fc8d96e814c3a40b0c5346d7389aeb525
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/12/2019
ms.locfileid: "68957167"
---
# <a name="boyer_moore_horspool_searcher-class"></a>boyer_moore_horspool_searcher 類別

`boyer_moore_horspool_searcher`類別是一種函式物件類型, 它會使用 Boyer-堯-Horspool 演算法來搜尋物件的函式中所指定的序列。 搜尋是在提供給物件的函式呼叫運算子的另一個序列中完成。 這個類別會當做參數傳遞至[std:: search](algorithm-functions.md#search)的其中一個多載。

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

| | |
| - | - |
| **建構函式** | |
| [boyer_moore_horspool_searcher](#boyer-moore-horspool-searcher-constructor) | |
| **運算子** | |
| [operator()](#operator-call) | |

## <a name="boyer-moore-horspool-searcher-constructor"></a>boyer_moore_horspool_searcher 的構造函式

`boyer_moore_horspool_searcher`使用要搜尋的序列、雜湊函式物件和等號比較述詞, 來構造函式物件。

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

*hf*\
可呼叫的物件, 用來雜湊順序元素。

*pred*\
Sequence 元素的選擇性相等比較述詞。 如果未指定相等比較類型, 則預設值為`std::equal_to`。

### <a name="remarks"></a>備註

擲回由*BinaryPredicate*、 *hash*或*RandomAccessIterator*類型的複製程式碼, 或*BinaryPredicate*或*Hash*的 call 運算子所擲回的任何例外狀況。

這個類別是 c + + 17 的新功能。

## <a name="operator-call"></a> operator()

函數物件的呼叫運算子。 在引數序列`[first, last)`內搜尋指定給此函數的順序。

```cpp
template <class ForwardIterator2>   // C++17
pair<RandomAccessIterator2, RandomAccessIterator2> operator()(
    RandomAccessIterator2 first,
    RandomAccessIterator2 last) const;
```

### <a name="parameters"></a>參數

*頭*\
要在其中搜尋之序列的初始元素。

*次*\
要在其中搜尋的序列結尾。

### <a name="remarks"></a>備註

如果搜尋模式`[pat_first, pat_last)`是空的`make_pair(first, first)`, 則會傳回。 如果找不到搜尋模式, `make_pair(last, last)`會傳回。 否則, 會`[first, last)` `[pat_first, pat_last)`根據述詞*pred*, 將一對反覆運算器傳回至序列的開頭和結尾。

這個類別是 c + + 17 的新功能。

## <a name="see-also"></a>另請參閱

[\<functional>](functional.md)\
[演算法函式](algorithm-functions.md)\
[boyer_moore_searcher 類別](boyer-moore-searcher-class.md)\
[std:: search](algorithm-functions.md#search)
