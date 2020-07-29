---
title: default_searcher 類別
ms.date: 08/03/2019
f1_keywords:
- functional/std::default_searcher
helpviewer_keywords:
- std::default_searcher [C++]
ms.openlocfilehash: 3b5b05dfa2613f9eeaaa18fa8066bcd44f57d1be
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87203724"
---
# <a name="default_searcher-class"></a>default_searcher 類別

`default_searcher`是作業的函式物件類型，會搜尋物件的函式中所指定的序列。 搜尋是在提供給物件的函式呼叫運算子的另一個序列中完成。 會叫用 `default_searcher` [std：： search](algorithm-functions.md#search)來執行搜尋。

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
| **函數** | |
| [default_searcher](#default-searcher-constructor) | |
| **運算子** | |
| [operator （）](#operator-call) | |

## <a name="default_searcher-constructor"></a><a name="default-searcher-constructor"></a>default_searcher 的構造函式

`default_searcher`使用要搜尋的序列和等號比較述詞，來構造函式物件。

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
Sequence 元素的選擇性相等比較述詞。 如果未指定相等比較類型，則預設值為 `std::equal_to` 。

### <a name="remarks"></a>備註

擲回*BinaryPredicate*或*ForwardIterator*類型的複製程式，所擲回的任何例外狀況。

這個類別是 c + + 17 的新功能。 C + + 20 製作了此函式 **`constexpr`** 。

## <a name="operator"></a><a name="operator-call"></a>operator （）

函數運算子的呼叫運算子。 在引數序列內搜尋 `[first, last)` 指定給此函數的順序。

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

傳回一對迭代器。 初始反覆運算器*i*是的有效結果：

`std::search( first, last, pat_first, pat_last, pred )`.

如果*i** 是*last*，則*最後一*組的第二個反覆運算器。 否則，它是有效的結果：

`std::next( i, std::distance( pat_first, pat_last ))`.

這個類別是 c + + 17 的新功能。 C + + 20 已進行呼叫運算子 **`constexpr`** 。

## <a name="see-also"></a>另請參閱

[\<functional>](functional.md)\
[演算法函式](algorithm-functions.md)\
[std：： search](algorithm-functions.md#search)
