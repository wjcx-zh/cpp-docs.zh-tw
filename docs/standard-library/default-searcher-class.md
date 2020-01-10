---
title: default_searcher 類別
ms.date: 08/03/2019
f1_keywords:
- functional/std::default_searcher
helpviewer_keywords:
- std::default_searcher [C++]
ms.openlocfilehash: f2b1fe83b5223bbb60e9e32149c101e6379f93c3
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "68268820"
---
# <a name="default_searcher-class"></a>default_searcher 類別

`default_searcher`是作業的函式物件類型, 會搜尋物件的函式中所指定的序列。 搜尋是在提供給物件的函式呼叫運算子的另一個序列中完成。 會叫用[std:: search](algorithm-functions.md#search)來執行搜尋。 `default_searcher`

## <a name="syntax"></a>語法

```cpp
template <class ForwardIterator, class BinaryPredicate = equal_to<>>
class default_searcher
{
    default_searcher(
        ForwardIterator pat_first,
        ForwardIterator pat_last,
        BinaryPredicate pred = BinaryPredicate());

    template <class ForwardIterator2>
    pair<ForwardIterator2, ForwardIterator2> operator()(
        ForwardIterator2 first,
        ForwardIterator2 last) const;
};
```

## <a name="members"></a>成員

| | |
| - | - |
| **建構函式** | |
| [default_searcher](#default-searcher-constructor) | |
| **運算子** | |
| [operator()](#operator-call) | |

## <a name="default-searcher-constructor"></a>default_searcher 的構造函式

`default_searcher`使用要搜尋的序列和等號比較述詞, 來構造函式物件。

```cpp
default_searcher(                   // C++17
    ForwardIterator pat_first,
    ForwardIterator pat_last,
    BinaryPredicate pred = BinaryPredicate());

constexpr default_searcher(         // C++20
    ForwardIterator pat_first,
    ForwardIterator pat_last,
    BinaryPredicate pred = BinaryPredicate());
```

### <a name="parameters"></a>參數

*pat_first*\
要搜尋之序列的初始元素。

*pat_last*\
要搜尋的序列結尾。

*pred*\
Sequence 元素的選擇性相等比較述詞。 如果未指定相等比較類型, 則預設值為`std::equal_to`。

### <a name="remarks"></a>備註

擲回*BinaryPredicate*或*ForwardIterator*類型的複製程式, 所擲回的任何例外狀況。

這個類別是 c + + 17 的新功能。 C + + 20 製作`constexpr`了此函式。

## <a name="operator-call"></a> operator()

函數運算子的呼叫運算子。 在引數序列`[first, last)`內搜尋指定給此函數的順序。

```cpp
template <class ForwardIterator2>   // C++17
pair<ForwardIterator2, ForwardIterator2> operator()(
    ForwardIterator2 first,
    ForwardIterator2 last) const;

template <class ForwardIterator2>   // C++20
constexpr pair<ForwardIterator2, ForwardIterator2> operator()(
    ForwardIterator2 first,
    ForwardIterator2 last) const;
```

### <a name="parameters"></a>參數

*頭*\
要在其中搜尋之序列的初始元素。

*次*\
要在其中搜尋的序列結尾。

### <a name="remarks"></a>備註

傳回一對迭代器。 初始反覆運算器*i*是的有效結果:

`std::search( first, last, pat_first, pat_last, pred )`.

如果*i** 是*last*, 則*最後一*組的第二個反覆運算器。 否則, 它是有效的結果:

`std::next( i, std::distance( pat_first, pat_last ))`.

這個類別是 c + + 17 的新功能。 C + + 20 已進行`constexpr`呼叫運算子。

## <a name="see-also"></a>另請參閱

[\<functional>](functional.md)\
[演算法函式](algorithm-functions.md)\
[std:: search](algorithm-functions.md#search)
