---
title: unary_function 結構
ms.date: 11/04/2016
f1_keywords:
- functional/std::unary
helpviewer_keywords:
- unary_function class
ms.assetid: 04c2fbdc-c1f6-48ed-b6cc-292a6d484627
ms.openlocfilehash: 4b93664377838cd5ff97346282cb9120ae9b5e37
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2020
ms.locfileid: "87520586"
---
# <a name="unary_function-struct"></a>unary_function 結構

空的基底結構，這個結構定義可能由衍生類別繼承並提供一元函式物件的類型。

## <a name="syntax"></a>語法

```cpp
struct unary_function
{
   typedef Arg argument_type;
   typedef Result result_type;
};
```

## <a name="remarks"></a>備註

樣板結構作為定義表單成員函式之類別的基底 `result_type operator()( constargument_type& ) const` 。

所有此類衍生的一元函式可以將其唯一引數類型參考為 **argument_type**，並將其傳回類型參考為 **result_type**。

## <a name="example"></a>範例

```cpp
// functional_unary_function.cpp
// compile with: /EHsc
#include <vector>
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std;

// Creation of a user-defined function object
// that inherits from the unary_function base class
class greaterthan10: unary_function<int, bool>
{
public:
    result_type operator()(argument_type i)
    {
        return (result_type)(i > 10);
    }
};

int main()
{
    vector<int> v1;
    vector<int>::iterator Iter;

    int i;
    for (i = 0; i <= 5; i++)
    {
        v1.push_back(5 * i);
    }

    cout << "The vector v1 = ( " ;
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)
        cout << *Iter << " ";
    cout << ")" << endl;

    vector<int>::iterator::difference_type result1;
    result1 = count_if(v1.begin(), v1.end(), greaterthan10());
    cout << "The number of elements in v1 greater than 10 is: "
         << result1 << "." << endl;
}
```

```Output
The vector v1 = ( 0 5 10 15 20 25 )
The number of elements in v1 greater than 10 is: 3.
```
