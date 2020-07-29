---
title: C++ 標準程式庫的函式物件
ms.date: 03/15/2019
helpviewer_keywords:
- functors
- C++ Standard Library, functors
- C++ Standard Library, function objects
- function objects
ms.assetid: 85f8a735-2c7b-4f10-9c4d-95c666ec4192
ms.openlocfilehash: ed413b2bcdcda8f65794b10c792b10358564420a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215734"
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

int main()
{
    Functor f;
    int a = 5;
    int b = 7;
    int ans = f(a, b);
}
```

`main` 函式的最後一行示範如何呼叫函式物件。 此呼叫看起來像是對函式的呼叫，但實際上是呼叫仿函數類型的 operator （）。 呼叫函式物件與函式之間的這點相似性，導致產生了函式物件一詞。

## <a name="function-objects-and-containers"></a>函式物件和容器

C + + 標準程式庫在標頭檔中包含數個函式物件 [\<functional>](../standard-library/functional.md) 。 這些函式物件的一個用途是做為容器的排序準則。 例如， `set` 容器的宣告方式如下：

```cpp
template <class Key,
    class Traits=less<Key>,
    class Allocator=allocator<Key>>
class set
```

第二個樣板引數是函式物件 `less`。 **`true`** 如果第一個參數小於第二個參數，則此函式物件會傳回。 由於某些容器會排序其元素，因此容器需要比較兩個元素的方式。 比較是使用函數物件來完成。 您可以建立一個函式物件，並在容器的樣板清單中指定這個物件，來為容器定義自己的排序準則。

## <a name="function-objects-and-algorithms"></a>函式物件和演算法

函式物件也可用於演算法。 例如， `remove_if` 演算法的宣告方式如下：

```cpp
template <class ForwardIterator, class Predicate>
ForwardIterator remove_if(
    ForwardIterator first,
    ForwardIterator last,
    Predicate pred);
```

傳遞給 `remove_if` 的最後一個引數是傳回布林值 ( *「述詞」*(Predicate)) 的函式物件。 如果函式物件的結果為 **`true`** ，則會從反覆運算器和所存取的容器中移除元素 `first` `last` 。 您可以使用引數的標頭中所宣告的任何函式物件， [\<functional>](../standard-library/functional.md) `pred` 也可以建立您自己的函式。

## <a name="see-also"></a>另請參閱

[C + + 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)
