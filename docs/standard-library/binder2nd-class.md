---
title: binder2nd 類別
ms.date: 02/21/2019
f1_keywords:
- functional/std::binder2nd
helpviewer_keywords:
- binder2nd class
ms.assetid: b2a9c1d1-dfc4-4ca9-a10e-ae84e195a62d
ms.openlocfilehash: 46c8bb2ae450b3ef56f2729717fb9b5563a7c139
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689941"
---
# <a name="binder2nd-class"></a>binder2nd 類別

類別樣板，提供將二元函式的第二個引數系結至指定的值，藉此將二元函式物件轉換成一元函式物件的函式。 在 c + + 11 中已被取代，在 c + + 17 中移除

## <a name="syntax"></a>語法

```cpp
template <class Operation>
class binder2nd
    : public unaryFunction <typename Operation::first_argument_type,
    typename Operation::result_type>
{
    typedef typename Operation::argument_type argument_type;
    typedef typename Operation::result_type result_type;
    binder2nd(
        const Operation& Func,
        const typename Operation::second_argument_type& right);

    result_type operator()(const argument_type& left) const;
    result_type operator()(argument_type& left) const;
};
```

### <a name="parameters"></a>參數

*Func* \
要轉換為一元函式物件的二元函式物件。

*right* \
二元函式物件的第二個引數所要繫結的值。

*左方*\
調整後的二元物件用來與第二個引數的固定值進行比較的引數值。

## <a name="return-value"></a>傳回值

一元函式物件，其結果是將二元函式物件的第二個引數系結至值*right*。

## <a name="remarks"></a>備註

類別樣板會在 `op` 中儲存二元函式物件 _ *Func*的複本，並在 `value` 中儲存一份*許可權*複本。 它會將其成員函式 `operator()` 定義為傳回**op**（`left`， **value**）。

如果 `Func` 是 `Operation` 類型的物件，而 c 是常數，則[bind2nd](../standard-library/functional-functions.md#bind2nd) （`Func`，`c`）相當於 `binder2nd` 類別的函式 **`binder2nd` \< 作業 > （** `Func`，0），而且更方便。

## <a name="example"></a>範例

```cpp
// functional_binder2nd.cpp
// compile with: /EHsc
#include <vector>
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std;

int main()
{
    vector<int> v1;
    vector<int>::iterator Iter;

    int i;
    for (i = 0; i <= 5; i++)
    {
        v1.push_back(5 * i);
    }

    cout << "The vector v1 = ( ";
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)
        cout << *Iter << " ";
    cout << ")" << endl;

    // Count the number of integers > 10 in the vector
    vector<int>::iterator::difference_type result1;
    result1 = count_if(v1.begin(), v1.end(),
        binder2nd<greater<int> >(greater<int>(), 10));
    cout << "The number of elements in v1 greater than 10 is: "
         << result1 << "." << endl;

    // Compare using binder1st fixing 1st argument:
    // count the number of integers < 10 in the vector
    vector<int>::iterator::difference_type result2;
    result2 = count_if(v1.begin(), v1.end(),
        binder1st<greater<int> >(greater<int>(), 10));
    cout << "The number of elements in v1 less than 10 is: "
         << result2 << "." << endl;
}
```

```Output
The vector v1 = ( 0 5 10 15 20 25 )
The number of elements in v1 greater than 10 is: 3.
The number of elements in v1 less than 10 is: 2.
```
