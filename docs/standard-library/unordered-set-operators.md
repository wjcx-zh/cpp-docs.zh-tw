---
title: '&lt;unordered_set&gt; 運算子'
ms.date: 11/04/2016
f1_keywords:
- unordered_set/std::operator!=
- unordered_set/std::operator==
ms.assetid: 8653eea6-12f2-4dd7-aa2f-db38a71599a0
ms.openlocfilehash: 59a7154ed46ac788516bc9f42c3385ec8f07dcf1
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68243424"
---
# <a name="ltunorderedsetgt-operators"></a>&lt;unordered_set&gt; 運算子

## <a name="op_neq"></a> 運算子 ！ =

測試運算子左邊的 [unordered_set](../standard-library/unordered-set-class.md) 物件是否不等於右邊的 unordered_set 物件。

```cpp
bool operator!=(const unordered_set <Key, Hash, Pred, Allocator>& left, const unordered_set <Key, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>參數

*左邊*\
`unordered_set` 類型的物件。

*權限*\
`unordered_set` 類型的物件。

### <a name="return-value"></a>傳回值

**true**如果 unordered_set 不相等。**false**兩者是否相等。

### <a name="remarks"></a>備註

unordered_set 物件之間的比較不會受到其儲存元素的任何順序影響。 如果兩個 unordered_set 的元素數量相同，且一個容器中的元素是另一個容器中元素的排列，則兩個 unordered_set 相等。 反之則為不相等。

### <a name="example"></a>範例

```cpp
// unordered_set_ne.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_set>
#include <iostream>
#include <ios>

int main()
{
    using namespace std;

    unordered_set<char> c1, c2, c3;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    c2.insert('c');
    c2.insert('a');
    c2.insert('d');

    c3.insert('c');
    c3.insert('a');
    c3.insert('b');

   cout << boolalpha;
   cout << "c1 != c2: " << (c1 != c2) << endl;
   cout << "c1 != c3: " << (c1 != c3) << endl;
   cout << "c2 != c3: " << (c2 != c3) << endl;

    return (0);
}
```

**輸出：**

`c1 != c2: true`

`c1 != c3: false`

`c2 != c3: true`

## <a name="op_eq_eq"></a> 運算子 = =

測試運算子左邊的 [unordered_set](../standard-library/unordered-set-class.md) 物件是否等於右邊的 unordered_set 物件。

```cpp
bool operator==(const unordered_set <Key, Hash, Pred, Allocator>& left, const unordered_set <Key, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>參數

*左邊*\
`unordered_set` 類型的物件。

*權限*\
`unordered_set` 類型的物件。

### <a name="return-value"></a>傳回值

**true**如果 unordered_set 相等;**false**如果不相等。

### <a name="remarks"></a>備註

unordered_set 物件之間的比較不會受到其儲存元素的任何順序影響。 如果兩個 unordered_set 的元素數量相同，且一個容器中的元素是另一個容器中元素的排列，則兩個 unordered_set 相等。 反之則為不相等。

### <a name="example"></a>範例

```cpp
// unordered_set_eq.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_set>
#include <iostream>
#include <ios>

int main()
{
    using namespace std;

    unordered_set<char> c1, c2, c3;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    c2.insert('c');
    c2.insert('a');
    c2.insert('d');

    c3.insert('c');
    c3.insert('a');
    c3.insert('b');

   cout << boolalpha;
   cout << "c1 == c2: " << (c1 == c2) << endl;
   cout << "c1 == c3: " << (c1 == c3) << endl;
   cout << "c2 == c3: " << (c2 == c3) << endl;

    return (0);
}
```

```Output
c1 == c2: false
c1 == c3: true
c2 == c3: false
```

## <a name="op_neq_unordered_multiset"></a> 運算子 ！ =

測試運算子左邊的 [unordered_multiset](../standard-library/unordered-multiset-class.md) 物件是否不等於右邊的 unordered_multiset 物件。

```cpp
bool operator!=(const unordered_multiset <Key, Hash, Pred, Allocator>& left, const unordered_multiset <Key, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>參數

*左邊*\
`unordered_multiset` 類型的物件。

*權限*\
`unordered_multiset` 類型的物件。

### <a name="return-value"></a>傳回值

**true**如果 unordered_multiset 不相等。**false**兩者是否相等。

### <a name="remarks"></a>備註

unordered_multiset 物件之間的比較不會受到其儲存元素的任何順序影響。 如果兩個 unordered_multiset 的元素數量相同，且一個容器中的元素是另一個容器中元素的排列，則兩個 unordered_multiset 相等。 反之則為不相等。

### <a name="example"></a>範例

```cpp
// unordered_multiset_ne.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_set>
#include <iostream>
#include <ios>

int main()
{
    using namespace std;

    unordered_multiset<char> c1, c2, c3;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');
    c1.insert('c');

    c2.insert('c');
    c2.insert('c');
    c2.insert('a');
    c2.insert('d');

    c3.insert('c');
    c3.insert('c');
    c3.insert('a');
    c3.insert('b');

   cout << boolalpha;
   cout << "c1 != c2: " << (c1 != c2) << endl;
   cout << "c1 != c3: " << (c1 != c3) << endl;
   cout << "c2 != c3: " << (c2 != c3) << endl;

    return (0);
}
```

```Output
c1 != c2: true
c1 != c3: false
c2 != c3: true
```

## <a name="op_eq_eq_unordered_multiset"></a> 運算子 = =

測試運算子左邊的 [unordered_multiset](../standard-library/unordered-multiset-class.md) 物件是否等於右邊的 unordered_multiset 物件。

```cpp
bool operator==(const unordered_multiset <Key, Hash, Pred, Allocator>& left, const unordered_multiset <Key, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>參數

*左邊*\
`unordered_multiset` 類型的物件。

*權限*\
`unordered_multiset` 類型的物件。

### <a name="return-value"></a>傳回值

**true**如果 unordered_multiset 相等;**false**如果不相等。

### <a name="remarks"></a>備註

unordered_multiset 物件之間的比較不會受到其儲存元素的任何順序影響。 如果兩個 unordered_multiset 的元素數量相同，且一個容器中的元素是另一個容器中元素的排列，則兩個 unordered_multiset 相等。 反之則為不相等。

### <a name="example"></a>範例

```cpp
// unordered_multiset_eq.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_set>
#include <iostream>
#include <ios>

int main()
{
    using namespace std;

    unordered_multiset<char> c1, c2, c3;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');
    c1.insert('c');

    c2.insert('c');
    c2.insert('c');
    c2.insert('a');
    c2.insert('d');

    c3.insert('c');
    c3.insert('c');
    c3.insert('a');
    c3.insert('b');

   cout << boolalpha;
   cout << "c1 == c2: " << (c1 == c2) << endl;
   cout << "c1 == c3: " << (c1 == c3) << endl;
   cout << "c2 == c3: " << (c2 == c3) << endl;

    return (0);
}
```

```Output
c1 == c2: false
c1 == c3: true
c2 == c3: false
```
