---
title: binder2nd 類別
ms.date: 02/21/2019
f1_keywords:
- functional/std::binder2nd
helpviewer_keywords:
- binder2nd class
ms.assetid: b2a9c1d1-dfc4-4ca9-a10e-ae84e195a62d
ms.openlocfilehash: 8c1ed74da939c5f5cc83a2a109d32b43b5ac7f41
ms.sourcegitcommit: 4299caac2dc9e806c74ac833d856a3838b0f52a1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "57006483"
---
# <a name="binder2nd-class"></a>binder2nd 類別

提供一個建構函式的樣板類別，這個建構函式透過將二元函式的第二個引數繫結至指定值，將二元函式物件轉換成一元函式物件。 在 C + + 11 中，在 c++17 中移除已被取代。

## <a name="syntax"></a>語法

```cpp
template <class Operation>
class binder2nd
    : public unaryFunction <typename Operation::first_argument_type,
    typename Operation::result_type>
{
public:
    typedef typename Operation::argument_type argument_type;
    typedef typename Operation::result_type result_type;
    binder2nd(
        const Operation& Func,
        const typename Operation::second_argument_type& right);

    result_type operator()(const argument_type& left) const;
    result_type operator()(argument_type& left) const;

protected:
    Operation op;
    typename Operation::second_argument_type value;
};
```

### <a name="parameters"></a>參數

*Func*<br/>
要轉換為一元函式物件的二元函式物件。

*right*<br/>
二元函式物件的第二個引數所要繫結的值。

*left*<br/>
調整後的二元物件用來與第二個引數的固定值進行比較的引數值。

## <a name="return-value"></a>傳回值

一元函式物件所產生的繫結至值的二元函式物件的第二個引數*右*。

## <a name="remarks"></a>備註

此範本類別會儲存一份二元函式物件 _ *Func*中`op`，和一份*右*在`value`。 它會在傳回下列項目時定義其成員函式 `operator()`：**op**( `left`, **value**)。

如果`Func`是型別的物件`Operation`和 c 是常數，則[bind2nd](../standard-library/functional-functions.md#bind2nd) ( `Func`， `c` ) 相當於`binder2nd`類別建構函式`binder2nd` \< **作業**> ( `Func`， `c` )、 更方便。

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
/* Output:
The vector v1 = ( 0 5 10 15 20 25 )
The number of elements in v1 greater than 10 is: 3.
The number of elements in v1 less than 10 is: 2.
*/
```

## <a name="requirements"></a>需求

**標頭：**\<functional>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)<br/>
