---
title: C++ 標準程式庫的函式物件
ms.date: 11/04/2016
helpviewer_keywords:
- functors
- C++ Standard Library, functors
- C++ Standard Library, function objects
- function objects
ms.assetid: 85f8a735-2c7b-4f10-9c4d-95c666ec4192
ms.openlocfilehash: 7af56f52b59b03dfed9e1233473239274a0dcbd8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50437111"
---
# <a name="function-objects-in-the-c-standard-library"></a>C++ 標準程式庫的函式物件

*「函式物件」*(Function Object) 或 *「函子」*(Functor) 是實作 operator() 的任何類型。 這個運算子稱為 *「呼叫運算子」* (Call Operator)，有時也稱為 *「應用運算子」*(Application Operator)。 C++ 標準程式庫主要是將函式物件當作容器的排序準則來使用，以及用於演算法中。

與直接呼叫函式相較下，函式物件提供兩個主要優點。 第一個優點是函式物件可以包含狀態。 第二個優點是函式物件是一種類型，因此可以做為樣板參數。

## <a name="creating-a-function-object"></a>建立函式物件

若要建立函式物件，請建立一種類型並實作 operator()，例如：

```cpp
class Functor
{
public:
    int operator()(int a, int b)
    {
        return a < b;
    }
};
```

`main` 函式的最後一行示範如何呼叫函式物件。 這個呼叫看起來像是呼叫函式，但實際上是呼叫函子類型的 operator()。 呼叫函式物件與函式之間的這點相似性，導致產生了函式物件一詞。

## <a name="function-objects-and-containers"></a>函式物件和容器

C++ 標準程式庫在 [\<functional>](../standard-library/functional.md) 標頭檔中包含數個函式物件。 這些函式物件的一個用途是做為容器的排序準則。 例如， `set` 容器的宣告方式如下：

```cpp
template <class Key,
    class Traits=less<Key>,
    class Allocator=allocator<Key>>
class set
```

第二個樣板引數是函式物件 `less`。 這個函式物件會傳回 **，則為 true**的第一個參數傳遞至其是否小於第二個參數傳遞。 由於某些容器會排序其項目，因此容器需要用於比較兩個項目的方式，透過函式物件可以達成這個目的。 您可以建立一個函式物件，並在容器的樣板清單中指定這個物件，來為容器定義自己的排序準則。

## <a name="function-objects-and-algorithms"></a>函式物件和演算法

函式物件也可用於演算法。 例如， `remove_if` 演算法的宣告方式如下：

```cpp
template <class ForwardIterator, class Predicate>
ForwardIterator remove_if(
    ForwardIterator first,
    ForwardIterator last,
    Predicate pred);
```

傳遞給 `remove_if` 的最後一個引數是傳回布林值 ( *「述詞」*(Predicate)) 的函式物件。 函式物件的結果是否 **，則為 true**，則會從迭代器所存取的容器中移除之項目的`first`和`last`。 您可以使用引數 `pred` 的 [\<functional>](../standard-library/functional.md) 標頭中所宣告的任何函式物件，或自行建立。

## <a name="see-also"></a>另請參閱

[C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)<br/>
