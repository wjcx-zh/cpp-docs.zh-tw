---
title: default_searcher類
ms.date: 08/03/2019
f1_keywords:
- functional/std::default_searcher
helpviewer_keywords:
- std::default_searcher [C++]
ms.openlocfilehash: 2c8b93b83b271f787c993f789e1a68f84a60f016
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368931"
---
# <a name="default_searcher-class"></a>default_searcher類

是`default_searcher`搜尋物件建構函數中指定的序列的操作的函數物件類型。 搜索在提供給物件的函數調用運算符的另一個序列中完成。 調用`default_searcher` [std::搜索](algorithm-functions.md#search)以執行搜索。

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
| **操作員** | |
| [運算子()](#operator-call) | |

## <a name="default_searcher-constructor"></a><a name="default-searcher-constructor"></a>default_searcher構構函數

通過使用序列搜索`default_searcher`和相等謂詞構造函數物件。

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
要搜尋的序列的初始元素。

*pat_last*\
要搜索的序列的末尾。

*Pred*\
序列元素的可選相等比較謂詞。 如果未指定相等比較類型,則預設值為`std::equal_to`。

### <a name="remarks"></a>備註

引發*二進位謂詞*或*轉發器*類型的複製構造函數引發的任何異常。

此類在 C++17 中是新的。 C++20 使建構函`constexpr`數 。

## <a name="operator"></a><a name="operator-call"></a>運算子()

函數運算子的呼叫運算符。 在參數序列`[first, last)`中搜尋指定給建構函數的序列。

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
要在其中搜索的序列的初始元素。

*最後*\
要在其中搜索的序列的末尾。

### <a name="remarks"></a>備註

傳回一對迭代器。 初始反覆發代器*i*是以下有效結果:

`std::search( first, last, pat_first, pat_last, pred )`.

如果*i*= 是*最後*一個,則配對的第二個反覆運算器是*最後*一個。 否則,它是以下有效結果:

`std::next( i, std::distance( pat_first, pat_last ))`.

此類在 C++17 中是新的。 C++20使呼叫接線`constexpr`員。

## <a name="see-also"></a>另請參閱

[\<功能>](functional.md)\
[演演算法函數](algorithm-functions.md)\
[分::搜尋](algorithm-functions.md#search)
