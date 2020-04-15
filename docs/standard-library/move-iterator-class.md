---
title: move_iterator 類別
ms.date: 03/27/2019
f1_keywords:
- iterator/std::move_iterator
- iterator/std::move_iterator::iterator_type
- iterator/std::move_iterator::iterator_category
- iterator/std::move_iterator::value_type
- iterator/std::move_iterator::difference_type
- iterator/std::move_iterator::pointer
- iterator/std::move_iterator::reference
- iterator/std::move_iterator::base
helpviewer_keywords:
- std::move_iterator [C++]
- std::move_iterator [C++], iterator_type
- std::move_iterator [C++], iterator_category
- std::move_iterator [C++], value_type
- std::move_iterator [C++], difference_type
- std::move_iterator [C++], pointer
- std::move_iterator [C++], reference
- std::move_iterator [C++], base
ms.assetid: a5e5cdd8-a264-4c6b-9f9c-68b0e8edaab7
ms.openlocfilehash: 17af246a85c4e3f1e0c7eb9d387161ad7b5123a1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377413"
---
# <a name="move_iterator-class"></a>move_iterator 類別

類別樣板 `move_iterator` 是迭代器的包裝函式。 move_iterator 和它所包裝 (儲存) 的迭代器提供相同的行為，不過，它會將預存迭代器的取值運算子變更為右值參考，而將複製變成移動。 如需有關 rvalue 的詳細資訊，請參閱 [Rvalue 參考宣告子：&&](../cpp/rvalue-reference-declarator-amp-amp.md)。

## <a name="syntax"></a>語法

```cpp
class move_iterator;
```

## <a name="remarks"></a>備註

類範本描述一個物件,該物件的活動類似於反覆運算器,除非取消引用。 它會儲存 `Iterator` 類型的隨機存取迭代器，此迭代器可透過成員函式 `base()` 來存取。 `move_iterator` 的所有作業是直接在預存迭代器上執行，不過，`operator*` 的結果會隱含轉型為 `value_type&&` 以建立右值參考。

`move_iterator` 可能會執行包裝的迭代器所未定義的作業。 不應該使用這些作業。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[move_iterator](#move_iterator)|`move_iterator` 類型物件的建構函式。|

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|[iterator_type](#iterator_type)|`RandomIterator` 樣板參數的同義字。|
|[iterator_category](#iterator_category)|同名的較長**類型名稱**表達式的同`iterator_category`義詞 標識反覆運算器的一般能力。|
|[value_type](#value_type)|同名的較長**類型名稱**表達式的同`value_type`義詞 描述反覆運算器元素的類型。|
|[difference_type](#difference_type)|同名的較長**類型名稱**表達式的同`difference_type`義詞 描述表示元素之間的差異值所需的積分類型。|
|[指標](#pointer)|`RandomIterator` 樣板參數的同義字。|
|[參考](#reference)|`rvalue` 參考 `value_type&&` 的同義字。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[base](#base)|成員函式傳回這個 `move_iterator` 所包裝的預存迭代器。|

### <a name="operators"></a>操作員

|運算子|描述|
|-|-|
|[move_iterator::操作員*](#op_star)|傳回 `(reference)*base().`。|
|[move_iterator::操作員*](#op_add_add)|遞增預存迭代器。 確切行為取決於它是否前置遞增或後置遞增作業。|
|[move_iterator::operator--](#operator--)|遞減預存迭代器。 確切行為取決於它是否前置遞減或後置遞減作業。|
|[move_iterator:操作員-&gt;](#op_arrow)|傳回 `&**this`。|
|[move_iterator:操作員-](#operator-)|藉由先從目前位置減去右值來傳回 `move_iterator(*this) -=`。|
|[move_iterator:運算子*](#op_at)|傳回 `(reference)*(*this + off)`。 可讓您指定距離目前基底的位移，取得該位置上的值。|
|[move_iterator::操作員*](#op_add)|傳回 `move_iterator(*this) +=` 值。 可讓您將位移加入至基底，取得該位置上的值。|
|[move_iterator::操作員*](#op_add_eq)|將右值加入到預存迭代器，並傳回 `*this`。|
|[move_iterator::操作員*](#operator-_eq)|從預存迭代器減去右值，並傳回 `*this`。|

## <a name="requirements"></a>需求

**標頭：** \<iterator>

**命名空間：** std

## <a name="move_iteratorbase"></a><a name="base"></a>move_iterator::基地

傳回此 `move_iterator` 的預存迭代器。

```cpp
RandomIterator base() const;
```

### <a name="remarks"></a>備註

成員函式會傳回儲存的迭代器。

## <a name="move_iteratordifference_type"></a><a name="difference_type"></a>move_iterator::d)類型

`difference_type` 類型是以迭代器特性 `difference_type` 為基礎的 `move_iterator` `typedef`，可與其交替使用。

```cpp
typedef typename iterator_traits<RandomIterator>::difference_type difference_type;
```

### <a name="remarks"></a>備註

這個類型與迭代器特性 `typename iterator_traits<RandomIterator>::pointer` 同義。

## <a name="move_iteratoriterator_category"></a><a name="iterator_category"></a>move_iterator:iterator_category

`iterator_category` 類型是以迭代器特性 `iterator_category` 為基礎的 `move_iterator` `typedef`，可與其交替使用。

```cpp
typedef typename iterator_traits<RandomIterator>::iterator_category  iterator_category;
```

### <a name="remarks"></a>備註

這個類型與迭代器特性 `typename iterator_traits<RandomIterator>::iterator_category` 同義。

## <a name="move_iteratoriterator_type"></a><a name="iterator_type"></a>move_iterator:iterator_type

`iterator_type` 類型以類別範本 `move_iterator` 的範本參數 `RandomIterator` 為基礎，可與其交替使用。

```cpp
typedef RandomIterator iterator_type;
```

### <a name="remarks"></a>備註

此類型是樣板參數 `RandomIterator` 的同義字。

## <a name="move_iteratormove_iterator"></a><a name="move_iterator"></a>move_iterator:move_iterator

建構移動迭代器。 這個參數可當做預存迭代器使用。

```cpp
move_iterator();
explicit move_iterator(RandomIterator right);
template <class Type>
move_iterator(const move_iterator<Type>& right);
```

### <a name="parameters"></a>參數

*對*\
要當做預存迭代器使用的迭代器。

### <a name="remarks"></a>備註

第一個建構函式會使用預存迭代器的預設建構函式來初始化迭代器。 其餘建構函式則會使用 `base.base()` 來初始化預存迭代器。

## <a name="move_iteratoroperator"></a><a name="op_add_eq"></a>move_iterator::操作員*

將位移加入預存迭代器，以便此預存迭代器指向目前新位置的項目。 然後運算子再移動新的目前項目。

```cpp
move_iterator& operator+=(difference_type _Off);
```

### <a name="parameters"></a>參數

*_Off*\
要加入至目前位置的位移，藉以判斷目前新位置。

### <a name="return-value"></a>傳回值

傳回新的目前項目。

### <a name="remarks"></a>備註

運算元將 *_Off*添加到存儲的反覆運算器。 接著傳回 `*this`。

## <a name="move_iteratoroperator-"></a><a name="operator-_eq"></a>move_iterator::操作員*

在指定數目的先前項目之間移動。 這個運算子會從預存迭代器減去位移。

```cpp
move_iterator& operator-=(difference_type _Off);
```

### <a name="parameters"></a>參數

### <a name="remarks"></a>備註

運算子會評估 `*this += -_Off`。 接著傳回 `*this`。

## <a name="move_iteratoroperator"></a><a name="op_add_add"></a>move_iterator::操作員*

遞增預存迭代器，其屬於此 `move_iterator.`。目前項目會由後置遞增運算子存取。 下個項目由前置遞增運算子存取。

```cpp
move_iterator& operator++();
move_iterator operator++(int);
```

### <a name="parameters"></a>參數

### <a name="remarks"></a>備註

第一個 (前置遞增) 運算子會遞增預存迭代器。 接著傳回 `*this`。

第二個 (後置遞增) 運算子會複製 `*this`，並評估 `++*this`。 接著傳回複本。

## <a name="move_iteratoroperator"></a><a name="op_add"></a>move_iterator::操作員*

傳回前進任意項目數的迭代器位置。

```cpp
move_iterator operator+(difference_type _Off) const;
```

### <a name="parameters"></a>參數

### <a name="remarks"></a>備註

運算子傳回`move_iterator(*this) +=``_Off`。

## <a name="move_iteratoroperator"></a><a name="op_at"></a>move_iterator:運算子*

允許陣列索引存取 `move iterator` 範圍內的元素。

```cpp
reference operator[](difference_type _Off) const;
```

### <a name="parameters"></a>參數

### <a name="remarks"></a>備註

第一個運算子會傳回 `(reference)*(*this + _Off)`。

## <a name="move_iteratoroperator--"></a><a name="operator--"></a>move_iterator:運算子 --

前置遞減和後置遞減成員運算子會在預存迭代器上執行遞減。

```cpp
move_iterator& operator--();
move_iterator operator--();
```

### <a name="parameters"></a>參數

### <a name="remarks"></a>備註

第一個成員運算子 (前置遞減) 會遞減預存迭代器。 接著傳回 `*this`。

第二個 (後置遞減) 運算子會複製 `*this`，並評估 `--*this`。 接著傳回複本。

## <a name="move_iteratoroperator-"></a><a name="operator-"></a>move_iterator:操作員-

將預存迭代器遞減並傳回指定的值。

```cpp
move_iterator operator-(difference_type _Off) const;
```

### <a name="parameters"></a>參數

### <a name="remarks"></a>備註

第一個運算子會傳回 `move_iterator(*this) -= _Off`。

## <a name="move_iteratoroperator"></a><a name="op_star"></a>move_iterator::操作員*

取值預存迭代器並傳回值。 這個行為類似 `rvalue reference` 並會執行移動指派。 這個運算子會將目前項目傳送到基底迭代器之外。 後面的項目會成為新的目前項目。

```cpp
reference operator*() const;
```

### <a name="remarks"></a>備註

第一個運算子會傳回 `(reference)*base()`。

## <a name="move_iteratoroperator-gt"></a><a name="op_arrow"></a>move_iterator:操作員-&gt;

與一般 `RandomIterator` `operator->` 一樣，它也可用來存取屬於目前元素的欄位。

```cpp
pointer operator->() const;
```

### <a name="remarks"></a>備註

第一個運算子會傳回 `&**this`。

## <a name="move_iteratorpointer"></a><a name="pointer"></a>move_iterator::p奧米特

類型`pointer`是基於的隨機反覆運算`RandomIterator``move_iterator`器**的類型def,** 可以互換使用。

```cpp
typedef RandomIterator  pointer;
```

### <a name="remarks"></a>備註

這個類型與 `RandomIterator`同義。

## <a name="move_iteratorreference"></a><a name="reference"></a>move_iterator:參考

類型`reference`是基於**的類型def,**`value_type&&``move_iterator``value_type&&`可以與互換使用。

```cpp
typedef value_type&& reference;
```

### <a name="remarks"></a>備註

此類型與 `value_type&&` 同義，後者是一個 rvalue 參考。

## <a name="move_iteratorvalue_type"></a><a name="value_type"></a>move_iterator::value_type

`value_type` 類型是以迭代器特性 `value_type` 為基礎的 `move_iterator` `typedef`，可與其交替使用。

```cpp
typedef typename iterator_traits<RandomIterator>::value_type   value_type;
```

### <a name="remarks"></a>備註

這個類型與迭代器特性 `typename iterator_traits<RandomIterator>::value_type` 同義。

## <a name="see-also"></a>另請參閱

[\<反覆運算器>](../standard-library/iterator.md)\
[L 值與 R 值](../cpp/lvalues-and-rvalues-visual-cpp.md)\
[移動建構函數和移動配置運算符 (C++)](../cpp/move-constructors-and-move-assignment-operators-cpp.md)\
[C++標準函式庫參考](../standard-library/cpp-standard-library-reference.md)
