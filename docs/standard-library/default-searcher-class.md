---
title: default_searcher 類別
ms.date: 08/03/2019
f1_keywords:
- functional/std::default_searcher
helpviewer_keywords:
- std::default_searcher [C++]
ms.openlocfilehash: 307fc6da3b383690e0b65bff2a72f386a37d6711
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2020
ms.locfileid: "90039686"
---
# <a name="default_searcher-class"></a>default_searcher 類別

`default_searcher`是作業的函式物件類型，可搜尋物件的函式中指定的序列。 搜尋是在另一個提供給物件函式呼叫運算子的序列中完成。 會叫用 `default_searcher` [std：： search](algorithm-functions.md#search) 來執行搜尋。

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

| member | 描述 |
| - | - |
| **構造 函數** | |
| [default_searcher](#default-searcher-constructor) | 建立搜尋的實例。 |
| **運算子** | |
| [運算子 ( # B1 ](#operator-call) | 叫用序列上的作業。 |

## <a name="default_searcher-constructor"></a><a name="default-searcher-constructor"></a> default_searcher 的函式

`default_searcher`使用序列來搜尋和等號比較述詞，以建立函式物件。

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

*Pred*\
Sequence 元素的選擇性相等比較述詞。 如果未指定相等比較型別，則預設值為 `std::equal_to` 。

### <a name="remarks"></a>備註

擲回 *BinaryPredicate* 或 *>forwarditerator* 類型的複製函式所擲回的任何例外狀況。

這個類別是 c + + 17 的新類別。 C + + 20 建立了函式 **`constexpr`** 。

## <a name="operator"></a><a name="operator-call"></a> 運算子 ( # A1

函數運算子的呼叫運算子。 在引數序列內搜尋指定給函式的 `[first, last)` 順序。

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

*第一*\
要在其中搜尋之序列的初始元素。

*最後*\
要在其中搜尋的序列結尾。

### <a name="remarks"></a>備註

傳回一對迭代器。 初始反覆運算器 *i* 是有效的結果：

`std::search( first, last, pat_first, pat_last, pred )`.

第二個反覆運算器的第二個*i*反覆運算*器是最後一個。* *last* 否則，它是的有效結果：

`std::next( i, std::distance( pat_first, pat_last ))`.

這個類別是 c + + 17 的新類別。 C + + 20 建立呼叫運算子 **`constexpr`** 。

## <a name="see-also"></a>另請參閱

[\<functional>](functional.md)\
[演算法函數](algorithm-functions.md)\
[std：： search](algorithm-functions.md#search)
