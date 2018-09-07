---
title: checked_array_iterator 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- iterator/checked_array_iterator
- iterator/stdext::checked_array_iterator::difference_type
- iterator/stdext::checked_array_iterator::pointer
- iterator/stdext::checked_array_iterator::reference
- iterator/stdext::checked_array_iterator::base
dev_langs:
- C++
helpviewer_keywords:
- stdext::checked_array_iterator [C++], difference_type
- stdext::checked_array_iterator [C++], pointer
- stdext::checked_array_iterator [C++], reference
- stdext::checked_array_iterator [C++], base
ms.assetid: 7f07185e-d588-4ae3-9c4f-84ec4aa25a28
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d74c9930816f353be7594bb67bf5e44b5251aa6c
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44106719"
---
# <a name="checkedarrayiterator-class"></a>checked_array_iterator 類別

`checked_array_iterator` 類別可讓您將陣列或指標轉換為已檢查的迭代器。 使用這個類別作為原始指標或陣列的包裝函式 (使用 [make_checked_array_iterator](../standard-library/iterator-functions.md#make_checked_array_iterator) 函式)，作為提供檢查以及管理未檢查指標警告的目標方式，而非全域的關閉這些警告訊息。 如果需要，您可以使用這個類別的未檢查版本 [unchecked_array_iterator](../standard-library/unchecked-array-iterator-class.md)。

> [!NOTE]
> 這個類別是 C++ 標準程式庫的 Microsoft 擴充功能。 透過使用這個函式實作的程式碼不可移植到不支援此 Microsoft 擴充功能的 C++ Standard 建置環境。 關於如何撰寫不需要使用這個類別的程式碼範例，請參閱下列第二個範例。

## <a name="syntax"></a>語法

```cpp
template <class _Iterator>
class checked_array_iterator;
```

## <a name="remarks"></a>備註

這個類別是在 [stdext](../standard-library/stdext-namespace.md) 命名空間中定義的。

如需已檢查的迭代器功能的詳細資訊和範例程式碼，請參閱[已檢查的迭代器](../standard-library/checked-iterators.md)。

## <a name="example"></a>範例

下列範例示範如何定義和使用已檢查的陣列迭代器。

如果目的地不夠大，無法容納所有複製的項目，例如變更以下程式行的情況：

```cpp
copy(a, a + 5, checked_array_iterator<int*>(b, 5));
```

與

```cpp
copy(a, a + 5, checked_array_iterator<int*>(b, 4));
```

會發生執行階段錯誤。

```cpp
// compile with: /EHsc /W4 /MTd
#include <algorithm>
#include <iostream>

using namespace std;
using namespace stdext;

int main() {
   int a[]={0, 1, 2, 3, 4};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b, 5));

   cout << "(";
   for (int i = 0 ; i < 5 ; i++)
      cout << " " << b[i];
   cout << " )" << endl;

   // constructor example
   checked_array_iterator<int*> checked_out_iter(b, 5);
   copy(a, a + 5, checked_out_iter);

   cout << "(";
   for (int i = 0 ; i < 5 ; i++)
      cout << " " << b[i];
   cout << " )" << endl;
}
\* Output:
( 0 1 2 3 4 )
( 0 1 2 3 4 )
*\
```

## <a name="example"></a>範例

若要避免使用 C++ 標準程式庫演算法時對 `checked_array_iterator` 類別的需求，請考慮使用 `vector` 而非動態配置的陣列。 下列範例示範如何進行這項操作。

```cpp
// compile with: /EHsc /W4 /MTd

#include <algorithm>
#include <iostream>
#include <vector>

using namespace std;

int main()
{
    std::vector<int> v(10);
    int *arr = new int[10];
    for (int i = 0; i < 10; ++i)
    {
        v[i] = i;
        arr[i] = i;
    }

    // std::copy(v.begin(), v.end(), arr); will result in
    // warning C4996. To avoid this warning while using int *,
    // use the Microsoft extension checked_array_iterator.
    std::copy(v.begin(), v.end(),
              stdext::checked_array_iterator<int *>(arr, 10));

    // Instead of using stdext::checked_array_iterator and int *,
    // consider using std::vector to encapsulate the array. This will
    // result in no warnings, and the code will be portable.
    std::vector<int> arr2(10);    // Similar to int *arr = new int[10];
    std::copy(v.begin(), v.end(), arr2.begin());

    for (int j = 0; j < arr2.size(); ++j)
    {
        cout << " " << arr2[j];
    }
    cout << endl;

    return 0;
}
\* Output:
0 1 2 3 4 5 6 7 8 9
*\
```

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[checked_array_iterator](#checked_array_iterator)|從基底迭代器建構預設的 `checked_array_iterator` 或 `checked_array_iterator`。|

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|[difference_type](#difference_type)|類型，提供兩個參考同一容器內項目的 `checked_array_iterator` 之間的差異。|
|[pointer](#pointer)|類型，提供指向 `checked_array_iterator` 定址的項目之指標。|
|[reference](#reference)|類型，提供指向 `checked_array_iterator` 定址的項目之參考。|

### <a name="member-functions"></a>成員函式

|成員函式|描述|
|-|-|
|[base](#base)|從其 `checked_array_iterator` 復原基礎迭代器。|

### <a name="operators"></a>運算子

|運算子|描述|
|-|-|
|[operator==](#op_eq_eq)|測試兩個 `checked_array_iterator` 是否相等。|
|[operator!=](#op_neq)|測試兩個 `checked_array_iterator` 是否不等。|
|[operator<](#op_lt)|測試運算子左邊的 `checked_array_iterator` 是否小於右邊的 `checked_array_iterator`。|
|[operator>](#op_gt)|測試運算子左邊的 `checked_array_iterator` 是否大於右邊的 `checked_array_iterator`。|
|[operator<=](#op_lt_eq)|測試運算子左邊的 `checked_array_iterator` 是否小於或等於右邊的 `checked_array_iterator`。|
|[operator>=](#op_gt_eq)|測試運算子左邊的 `checked_array_iterator` 是否大於或等於右邊的 `checked_array_iterator`。|
|[operator*](#op_star)|傳回 `checked_array_iterator` 定址的項目。|
|[operator->](#op_arrow)|傳回由 `checked_array_iterator` 定址的項目之指標。|
|[operator++](#op_add_add)|遞增 `checked_array_iterator` 至下一個項目。|
|[operator--](#operator--)|遞減 `checked_array_iterator` 至上一個項目。|
|[operator+=](#op_add_eq)|加入指定位移至 `checked_array_iterator`。|
|[operator+](#op_add)|將位移新增至迭代器，並傳回新的 `checked_array_iterator`，定址在新的位移位置中插入的項目。|
|[operator-=](#operator-_eq)|從 `checked_array_iterator` 減去指定的位移。|
|[operator-](#operator-)|從迭代器中遞減位移，並傳回新的 `checked_array_iterator`，其將插入的項目定址在新的位移位置中。|
|[operator&#91;&#93;](#op_at)|以指定的位置數目，從 `checked_array_iterator` 定址的項目傳回項目位移的參考。|

## <a name="requirements"></a>需求

**標頭：**\<iterator>

**命名空間：** stdext

## <a name="base"></a>  checked_array_iterator::base

從其 `checked_array_iterator` 復原基礎迭代器。

```cpp
_Iterator base() const;
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[已檢查的迭代器](../standard-library/checked-iterators.md)。

### <a name="example"></a>範例

```cpp
// checked_array_iterators_base.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main() {
   using namespace std;

   int V1[10];

   for (int i = 0; i < 10 ; i++)
      V1[i] = i;

   int* bpos;

   stdext::checked_array_iterator<int*> rpos(V1, 10);
   rpos++;

   bpos = rpos.base ( );
   cout << "The iterator underlying rpos is bpos & it points to: "
        << *bpos << "." << endl;
}
\* Output:
The iterator underlying rpos is bpos & it points to: 1.
*\
```

## <a name="checked_array_iterator"></a>  checked_array_iterator::checked_array_iterator

從基底迭代器建構預設的 `checked_array_iterator` 或 `checked_array _iterator`。

```cpp
checked_array_iterator();

checked_array_iterator(
    ITerator ptr,
    size_t size,
    size_t index = 0);
```

### <a name="parameters"></a>參數

*ptr*<br/>
陣列的指標。

*size*<br/>
陣列的大小。

*index*<br/>
(選擇性) 陣列中用來初始化迭代器的元素。  根據預設，迭代器會初始化為陣列中的第一個元素。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[已檢查的迭代器](../standard-library/checked-iterators.md)。

### <a name="example"></a>範例

```cpp
// checked_array_iterators_ctor.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

using namespace std;
using namespace stdext;

int main() {
   int a[] = {0, 1, 2, 3, 4};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   for (int i = 0 ; i < 5 ; i++)
      cout << b[i] << " ";
   cout << endl;

   checked_array_iterator<int*> checked_output_iterator(b,5);
   copy (a, a + 5, checked_output_iterator);
   for (int i = 0 ; i < 5 ; i++)
      cout << b[i] << " ";
   cout << endl;

   checked_array_iterator<int*> checked_output_iterator2(b,5,3);
   cout << *checked_output_iterator2 << endl;
}
\* Output:
0 1 2 3 4
0 1 2 3 4
3
*\
```

## <a name="difference_type"></a>  checked_array_iterator::difference_type

類型，提供兩個參考同一容器內項目的 `checked_array_iterator` 之間的差異。

```cpp
typedef typename iterator_traits<_Iterator>::difference_type difference_type;
```

### <a name="remarks"></a>備註

`checked_array_iterator` 差異類型與迭代器差異類型相同。

如需程式碼範例，請參閱 [checked_array_iterator::operator[]](#op_at)。

如需詳細資訊，請參閱[已檢查的迭代器](../standard-library/checked-iterators.md)。

## <a name="op_eq_eq"></a>  checked_array_iterator::operator==

測試兩個 `checked_array_iterator` 是否相等。

```cpp
bool operator==(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>參數

*right*<br/>
要對其檢查是否相等的 `checked_array_iterator`。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[已檢查的迭代器](../standard-library/checked-iterators.md)。

### <a name="example"></a>範例

```cpp
// checked_array_iterators_opeq.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

using namespace std;
using namespace stdext;

int main() {
   int a[] = {0, 1, 2, 3, 4};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);
   checked_array_iterator<int*> checked_output_iterator2(b,5);

   if (checked_output_iterator2 == checked_output_iterator)
      cout << "checked_array_iterators are equal" << endl;
   else
      cout << "checked_array_iterators are not equal" << endl;

   copy (a, a + 5, checked_output_iterator);
   checked_output_iterator++;

   if (checked_output_iterator2 == checked_output_iterator)
      cout << "checked_array_iterators are equal" << endl;
   else
      cout << "checked_array_iterators are not equal" << endl;
}
\* Output:
checked_array_iterators are equal
checked_array_iterators are not equal
*\
```

## <a name="op_neq"></a>  checked_array_iterator::operator!=

測試兩個 `checked_array_iterator` 是否不等。

```cpp
bool operator!=(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>參數

*right*<br/>
要對其檢查是否不相等的 `checked_array_iterator`。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[已檢查的迭代器](../standard-library/checked-iterators.md)。

### <a name="example"></a>範例

```cpp
// checked_array_iterators_opneq.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

using namespace std;
using namespace stdext;

int main() {
   int a[] = {0, 1, 2, 3, 4};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);
   checked_array_iterator<int*> checked_output_iterator2(b,5);

   if (checked_output_iterator2 != checked_output_iterator)
      cout << "checked_array_iterators are not equal" << endl;
   else
      cout << "checked_array_iterators are equal" << endl;

   copy (a, a + 5, checked_output_iterator);
   checked_output_iterator++;

   if (checked_output_iterator2 != checked_output_iterator)
      cout << "checked_array_iterators are not equal" << endl;
   else
      cout << "checked_array_iterators are equal" << endl;
}
\* Output:
checked_array_iterators are equal
checked_array_iterators are not equal
*\
```

## <a name="op_lt"></a>  checked_array_iterator::operator&lt;

測試運算子左邊的 `checked_array_iterator` 是否小於右邊的 `checked_array_iterator`。

```cpp
bool operator<(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>參數

*right*<br/>
要對其檢查是否不相等的 `checked_array_iterator`。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[已檢查的迭代器](../standard-library/checked-iterators.md)。

### <a name="example"></a>範例

```cpp
// checked_array_iterators_oplt.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

using namespace std;
using namespace stdext;

int main() {
   int a[] = {0, 1, 2, 3, 4};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);
   checked_array_iterator<int*> checked_output_iterator2(b,5);

   if (checked_output_iterator2 < checked_output_iterator)
      cout << "checked_output_iterator2 is less than checked_output_iterator" << endl;
   else
      cout << "checked_output_iterator2 is not less than checked_output_iterator" << endl;

   copy (a, a + 5, checked_output_iterator);
   checked_output_iterator++;

   if (checked_output_iterator2 < checked_output_iterator)
      cout << "checked_output_iterator2 is less than checked_output_iterator" << endl;
   else
      cout << "checked_output_iterator2 is not less than checked_output_iterator" << endl;
}
\* Output:
checked_output_iterator2 is not less than checked_output_iterator
checked_output_iterator2 is less than checked_output_iterator
*\
```

## <a name="op_gt"></a>  checked_array_iterator::operator&gt;

測試運算子左邊的 `checked_array_iterator` 是否大於右邊的 `checked_array_iterator`。

```cpp
bool operator>(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>參數

*right*<br/>
要比較的 `checked_array_iterator`。

### <a name="remarks"></a>備註

如需程式碼範例，請參閱 [checked_array_iterator::operator&lt;](#op_lt)。

如需詳細資訊，請參閱[已檢查的迭代器](../standard-library/checked-iterators.md)。

## <a name="lt_eq"></a>  checked_array_iterator::operator&lt;=

測試運算子左邊的 `checked_array_iterator` 是否小於或等於右邊的 `checked_array_iterator`。

```cpp
bool operator<=(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>參數

*right*<br/>
要比較的 `checked_array_iterator`。

### <a name="remarks"></a>備註

如需程式碼範例，請參閱 [checked_array_iterator::operator&gt;=](#op_gt_eq)。

如需詳細資訊，請參閱[已檢查的迭代器](../standard-library/checked-iterators.md)。

## <a name="gt_eq"></a>  checked_array_iterator::operator&gt;=

測試運算子左邊的 `checked_array_iterator` 是否大於或等於右邊的 `checked_array_iterator`。

```cpp
bool operator>=(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>參數

*right*<br/>
要比較的 `checked_array_iterator`。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[已檢查的迭代器](../standard-library/checked-iterators.md)。

### <a name="example"></a>範例

```cpp
// checked_array_iterators_opgteq.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

using namespace std;
using namespace stdext;

int main() {
   int a[] = {0, 1, 2, 3, 4};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);
   checked_array_iterator<int*> checked_output_iterator2(b,5);

   if (checked_output_iterator2 >= checked_output_iterator)
      cout << "checked_output_iterator2 is greater than or equal to checked_output_iterator" << endl;
   else
      cout << "checked_output_iterator2 is less than checked_output_iterator" << endl;

   copy (a, a + 5, checked_output_iterator);
   checked_output_iterator++;

   if (checked_output_iterator2 >= checked_output_iterator)
      cout << "checked_output_iterator2 is greater than or equal to checked_output_iterator" << endl;
   else
      cout << "checked_output_iterator2 is less than checked_output_iterator" << endl;
}
\* Output:
checked_output_iterator2 is greater than or equal to checked_output_iterator
checked_output_iterator2 is less than checked_output_iterator
*\
```

## <a name="op_star"></a>  checked_array_iterator::operator*

傳回 `checked_array_iterator` 定址的項目。

```cpp
reference operator*() const;
```

### <a name="return-value"></a>傳回值

由 `checked_array_iterator` 定址之元素的值。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[已檢查的迭代器](../standard-library/checked-iterators.md)。

### <a name="example"></a>範例

```cpp
// checked_array_iterator_pointer.cpp
// compile with: /EHsc
#include <iterator>
#include <algorithm>
#include <vector>
#include <utility>
#include <iostream>

using namespace std;
using namespace stdext;

int main() {
   int a[] = {0, 1, 2, 3, 4};
   int b[5];
   pair<int, int> c[1];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   for (int i = 0 ; i < 5 ; i++)
      cout << b[i] << endl;

    c[0].first = 10;
    c[0].second = 20;

   checked_array_iterator<int*> checked_output_iterator(b,5);
   checked_array_iterator<int*>::pointer p = &(*checked_output_iterator);
   checked_array_iterator<pair<int, int>*> chk_c(c, 1);
   checked_array_iterator<pair<int, int>*>::pointer p_c = &(*chk_c);

   cout << "b[0] = " << *p << endl;
   cout << "c[0].first = " << p_c->first << endl;
}
\* Output:
0
1
2
3
4
b[0] = 0
c[0].first = 10
*\
```

## <a name="op_arrow"></a>  checked_array_iterator::operator-&gt;

傳回由 `checked_array_iterator` 定址的項目之指標。

```cpp
pointer operator->() const;
```

### <a name="return-value"></a>傳回值

由 `checked_array_iterator` 定址之項目的指標。

### <a name="remarks"></a>備註

如需程式碼範例，請參閱 [checked_array_iterator::pointer](#pointer)。

如需詳細資訊，請參閱[已檢查的迭代器](../standard-library/checked-iterators.md)。

## <a name="op_add_add"></a>  checked_array_iterator::operator++

遞增 `checked_array_iterator` 至下一個項目。

```cpp
checked_array_iterator& operator++();

checked_array_iterator<_Iterator> operator++(int);
```

### <a name="return-value"></a>傳回值

第一個運算子會傳回前置遞增的 `checked_array_iterator`，而第二個後置遞增運算子會傳回遞增的 `checked_array_iterator` 複本。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[已檢查的迭代器](../standard-library/checked-iterators.md)。

### <a name="example"></a>範例

```cpp
// checked_array_iterators_op_plus_plus.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main() {
   using namespace stdext;
   using namespace std;
   int a[] = {6, 3, 77, 199, 222};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);

   cout << *checked_output_iterator << endl;
   ++checked_output_iterator;
   cout << *checked_output_iterator << endl;
   checked_output_iterator++;
   cout << *checked_output_iterator << endl;
}
\* Output:
6
3
77
*\
```

## <a name="checked_array_iterator__operator--"></a>  checked_array_iterator::operator--

遞減 `checked_array_iterator` 至上一個項目。

```cpp
checked_array_iterator<_Iterator>& operator--();

checked_array_iterator<_Iterator> operator--(int);
```

### <a name="return-value"></a>傳回值

第一個運算子會傳回前置遞減的 `checked_array_iterator`，而第二個後置遞減運算子會傳回遞減的 `checked_array_iterator` 複本。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[已檢查的迭代器](../standard-library/checked-iterators.md)。

### <a name="example"></a>範例

```cpp
// checked_array_iterators_op_minus_minus.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main() {
   using namespace stdext;
   using namespace std;
   int a[] = {6, 3, 77, 199, 222};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);

   cout << *checked_output_iterator << endl;
   checked_output_iterator++;
   cout << *checked_output_iterator << endl;
   checked_output_iterator--;
   cout << *checked_output_iterator << endl;
}
\* Output:
6
3
6
*\
```

## <a name="op_add_eq"></a>  checked_array_iterator::operator+=

加入指定位移至 `checked_array_iterator`。

```cpp
checked_array_iterator<_Iterator>& operator+=(difference_type _Off);
```

### <a name="parameters"></a>參數

*_Off*<br/>
要遞增迭代器的位移。

### <a name="return-value"></a>傳回值

由 `checked_array_iterator` 定址之元素的參考。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[已檢查的迭代器](../standard-library/checked-iterators.md)。

### <a name="example"></a>範例

```cpp
// checked_array_iterators_op_plus_eq.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main() {
   using namespace stdext;
   using namespace std;
   int a[] = {6, 3, 77, 199, 222};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);

   cout << *checked_output_iterator << endl;
   checked_output_iterator += 3;
   cout << *checked_output_iterator << endl;
}
\* Output:
6
199
*\
```

## <a name="op_add"></a>  checked_array_iterator::operator+

將位移新增至迭代器，並傳回新的 `checked_array_iterator`，定址在新的位移位置中插入的項目。

```cpp
checked_array_iterator<_Iterator> operator+(difference_type _Off) const;
```

### <a name="parameters"></a>參數

*_Off*<br/>
要新增至 `checked_array_iterator` 的位移。

### <a name="return-value"></a>傳回值

為位移項目定址的 `checked_array_iterator`。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[已檢查的迭代器](../standard-library/checked-iterators.md)。

### <a name="example"></a>範例

```cpp
// checked_array_iterators_op_plus.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main() {
   using namespace stdext;
   using namespace std;
   int a[] = {6, 3, 77, 199, 222};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);

   cout << *checked_output_iterator << endl;
   checked_output_iterator = checked_output_iterator + 3;
   cout << *checked_output_iterator << endl;
}
\* Output:
6
199
*\
```

## <a name="checked_array_iterator__operator-_eq"></a>  checked_array_iterator::operator-=

從 `checked_array_iterator` 減去指定的位移。

```cpp
checked_array_iterator<_Iterator>& operator-=(difference_type _Off);
```

### <a name="parameters"></a>參數

*_Off*<br/>
要遞增迭代器的位移。

### <a name="return-value"></a>傳回值

由 `checked_array_iterator` 定址之元素的參考。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[已檢查的迭代器](../standard-library/checked-iterators.md)。

### <a name="example"></a>範例

```cpp
// checked_array_iterators_op_minus_eq.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main() {
   using namespace stdext;
   using namespace std;
   int a[] = {6, 3, 77, 199, 222};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);

   checked_output_iterator += 3;
   cout << *checked_output_iterator << endl;
   checked_output_iterator -= 2;
   cout << *checked_output_iterator << endl;
}
\* Output:
199
3
*\
```

## <a name="checked_array_iterator__operator-"></a>  checked_array_iterator::operator-

從迭代器中遞減位移，並傳回新的 `checked_array_iterator`，其將插入的項目定址在新的位移位置中。

```cpp
checked_array_iterator<_Iterator> operator-(difference_type _Off) const;

difference_type operator-(const checked_array_iterator& right) const;
```

### <a name="parameters"></a>參數

*_Off*<br/>
要從 `checked_array_iterator` 遞減的位移。

### <a name="return-value"></a>傳回值

為位移項目定址的 `checked_array_iterator`。

### <a name="remarks"></a>備註

如需程式碼範例，請參閱 [checked_array_iterator::operator-](#operator-)。

如需詳細資訊，請參閱[已檢查的迭代器](../standard-library/checked-iterators.md)。

## <a name="op_at"></a>  checked_array_iterator::operator[]

以指定的位置數目，從 `checked_array_iterator` 定址的項目傳回項目位移的參考。

```cpp
reference operator[](difference_type _Off) const;
```

### <a name="parameters"></a>參數

*_Off*<br/>
`checked_array_iterator` 位址的位移。

### <a name="return-value"></a>傳回值

項目位移的參考。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[已檢查的迭代器](../standard-library/checked-iterators.md)。

### <a name="example"></a>範例

```cpp
// checked_array_iterators_op_diff.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main() {
   using namespace std;
   int V1[10];

   for (int i = 0; i < 10 ; i++)
      V1[i] = i;

   // Declare a difference type for a parameter
   stdext::checked_array_iterator<int*>::difference_type diff = 2;

   stdext::checked_array_iterator<int*> VChkIter(V1, 10);

   stdext::checked_array_iterator<int*>::reference refrpos = VChkIter [diff];

   cout << refrpos + 1 << endl;
}
\* Output:
3
*\
```

## <a name="pointer"></a>  checked_array_iterator::pointer

類型，提供指向 `checked_array_iterator` 定址的項目之指標。

```cpp
typedef typename iterator_traits<_Iterator>::pointer pointer;
```

### <a name="remarks"></a>備註

如需程式碼範例，請參閱 [checked_array_iterator::operator*](#op_star)。

如需詳細資訊，請參閱[已檢查的迭代器](../standard-library/checked-iterators.md)。

## <a name="reference"></a>  checked_array_iterator::reference

類型，提供指向 `checked_array_iterator` 定址的項目之參考。

```cpp
typedef typename iterator_traits<_Iterator>::reference reference;
```

### <a name="remarks"></a>備註

如需程式碼範例，請參閱 [checked_array_iterator::operator[]](#op_at)。

如需詳細資訊，請參閱[已檢查的迭代器](../standard-library/checked-iterators.md)。

## <a name="see-also"></a>另請參閱

[\<iterator>](../standard-library/iterator.md)<br/>
[C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)<br/>
