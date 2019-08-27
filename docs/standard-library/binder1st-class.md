---
title: binder1st 類別
ms.date: 02/21/2019
f1_keywords:
- functional/std::binder1st
helpviewer_keywords:
- binder1st class
ms.assetid: 6b8ee343-c82f-48f8-867d-06f9d1d324c0
ms.openlocfilehash: 384a870a10c9f806684443d8c67647e924b6b2aa
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68243376"
---
# <a name="binder1st-class"></a>binder1st 類別

提供一個建構函式的樣板類別，這個建構函式透過將二元函式的第一個引數繫結至指定值，將二元函式物件轉換成一元函式物件。 支持的 C + + 11 中已被取代[繫結](functional-functions.md#bind)，並在 c++17 中移除。

## <a name="syntax"></a>語法

```cpp
template <class Operation>
class binder1st
    : public unaryFunction <typename Operation::second_argument_type,
                             typename Operation::result_type>
{
public:
    typedef typename Operation::argument_type argument_type;
    typedef typename Operation::result_type result_type;
    binder1st(
        const Operation& binary_fn,
        const typename Operation::first_argument_type& left);

    result_type operator()(const argument_type& right) const;
    result_type operator()(const argument_type& right) const;

protected:
    Operation op;
    typename Operation::first_argument_type value;
};
```

### <a name="parameters"></a>參數

*binary_fn*\
要轉換為一元函式物件的二元函式物件。

*左邊*\
二元函式物件的第一個引數所要繫結的值。

*權限*\
調整後的二元物件用來與第二個引數的固定值進行比較的引數值。

## <a name="return-value"></a>傳回值

一元函式物件所產生的繫結至值的二元函式物件的第一個引數*左*。

## <a name="remarks"></a>備註

此範本類別會儲存二元函式物件的複本*binary_fn*中`op`，和一份*左*在`value`。 它會定義其成員函式`operator()`做為傳回`op(value, right)`。

如果*binary_fn*是類型的物件`Operation`並`c`是常數，則`bind1st(binary_fn, c)`更方便對等項目`binder1st<Operation>(binary_fn, c)`。 如需詳細資訊，請參閱 < [bind1st](../standard-library/functional-functions.md#bind1st)。

## <a name="example"></a>範例

```cpp
// functional_binder1st.cpp
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
        binder1st<less<int> >(less<int>(), 10));
    cout << "The number of elements in v1 greater than 10 is: "
         << result1 << "." << endl;

    // Compare use of binder2nd fixing 2nd argument:
    // count the number of integers < 10 in the vector
    vector<int>::iterator::difference_type result2;
    result2 = count_if(v1.begin(), v1.end(),
        binder2nd<less<int> >(less<int>(), 10));
    cout << "The number of elements in v1 less than 10 is: "
         << result2 << "." << endl;
}
```

```Output
The vector v1 = ( 0 5 10 15 20 25 )
The number of elements in v1 greater than 10 is: 3.
The number of elements in v1 less than 10 is: 2.
```
