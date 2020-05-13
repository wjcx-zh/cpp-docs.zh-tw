---
title: boyer_moore_horspool_searcher類
ms.date: 08/03/2019
f1_keywords:
- functional/std::boyer_moore_horspool_searcher
helpviewer_keywords:
- std::boyer_moore_horspool_searcher [C++]
ms.openlocfilehash: 4d404b414ad632e02be5f4e9fad0e22cefb86ce2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366782"
---
# <a name="boyer_moore_horspool_searcher-class"></a>boyer_moore_horspool_searcher類

類`boyer_moore_horspool_searcher`是一種函數物件類型,它使用 Boyer-Moore-Horspool 演演演算法來搜尋物件建構函數中指定的序列。 搜索在提供給物件的函數調用運算符的另一個序列中完成。 類作為參數傳遞給[std::search](algorithm-functions.md#search)的重載之一。

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
| **操作員** | |
| [運算子()](#operator-call) | |

## <a name="boyer_moore_horspool_searcher-constructor"></a><a name="boyer-moore-horspool-searcher-constructor"></a>boyer_moore_horspool_searcher建構函數

通過使用序列搜索`boyer_moore_horspool_searcher`、哈希函數物件和相等謂詞來構造函數物件。

```cpp
boyer_moore_horspool_searcher(
    RandomAccessIterator pat_first,
    RandomAccessIterator pat_last,
    Hash hf = Hash(),
    BinaryPredicate pred = BinaryPredicate());
```

### <a name="parameters"></a>參數

*pat_first*\
要搜尋的序列的初始元素。

*pat_last*\
要搜索的序列的末尾。

*高頻*\
用於哈希序列元素的可調用物件。

*Pred*\
序列元素的可選相等比較謂詞。 如果未指定相等比較類型,則預設值為`std::equal_to`。

### <a name="remarks"></a>備註

引發*BinaryPredicate、**哈希*或*隨機存取反覆運算器*類型的複製建構函數或*BinaryPredicate*或*哈希*的調用運算符引發的任何異常。

此類在 C++17 中是新的。

## <a name="operator"></a><a name="operator-call"></a>運算子()

函數物件的調用運算符。 在參數序列`[first, last)`中搜尋指定給建構函數的序列。

```cpp
template <class ForwardIterator2>   // C++17
pair<RandomAccessIterator2, RandomAccessIterator2> operator()(
    RandomAccessIterator2 first,
    RandomAccessIterator2 last) const;
```

### <a name="parameters"></a>參數

*第一*\
要在其中搜索的序列的初始元素。

*最後*\
要在其中搜索的序列的末尾。

### <a name="remarks"></a>備註

如果搜尋模式`[pat_first, pat_last)`為空,則`make_pair(first, first)`傳回 。 找不到搜尋模式,則傳回`make_pair(last, last)`。 否則,將一對反覆運算器傳回到序列的開始和`[first, last)`結束 ,該序列`[pat_first, pat_last)`等於 謂詞 *。*

此類在 C++17 中是新的。

## <a name="see-also"></a>另請參閱

[\<功能>](functional.md)\
[演演算法函數](algorithm-functions.md)\
[boyer_moore_searcher類](boyer-moore-searcher-class.md)\
[分::搜尋](algorithm-functions.md#search)
