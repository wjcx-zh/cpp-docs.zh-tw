---
title: '&lt;unordered_map&gt; 運算子'
ms.date: 11/04/2016
f1_keywords:
- unordered_map/std::operator!=
- unordered_map/std::operator==
ms.assetid: 9d5add0b-84bd-4a79-bd82-3f58b55145ed
ms.openlocfilehash: fe4877bc5b371a2570c18950bac36a003078ccc7
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454774"
---
# <a name="ltunorderedmapgt-operators"></a>&lt;unordered_map&gt; 運算子

|||||
|-|-|-|-|
|[operator!=](#op_neq)|[operator==](#op_eq_eq)|[operator!=](#op_neq_multimap)|[operator==](#op_eq_eq_multimap)|

## <a name="op_neq"></a> operator!=

測試運算子左邊的 [unordered_map](../standard-library/unordered-map-class.md) 物件是否不等於右邊的 unordered_map 物件。

```cpp
bool operator!=(const unordered_map <Key, Type, Hash, Pred, Allocator>& left, const unordered_map <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>參數

*左面*\
`unordered_map` 類型的物件。

*再*\
`unordered_map` 類型的物件。

### <a name="return-value"></a>傳回值

如果 unordered_maps 不相等, 則為**true** ;如果相等, 則**為 false** 。

### <a name="remarks"></a>備註

unordered_map 物件之間的比較不會受到其儲存元素的任何順序影響。 如果兩個 unordered_map 的元素數量相同，且一個容器中的元素是另一個容器中元素的排列，則兩個 unordered_map 相等。 反之則為不相等。

### <a name="example"></a>範例

```cpp
// unordered_map_op_ne.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_map>
#include <iostream>
#include <ios>

int main( )
{
   using namespace std;
   unordered_map<int, int> um1, um2, um3;

   for ( int i = 0 ; i < 3 ; ++i ) {
      um1.insert( make_pair( i+1, i ) );
      um1.insert( make_pair( i, i ) );

      um2.insert( make_pair( i, i+1 ) );
      um2.insert( make_pair( i, i ) );

      um3.insert( make_pair( i, i ) );
      um3.insert( make_pair( i+1, i ) );
   }

   cout << boolalpha;
   cout << "um1 != um2: " << (um1 != um2) << endl;
   cout << "um1 != um3: " << (um1 != um3) << endl;
   cout << "um2 != um3: " << (um2 != um3) << endl;
}
```

**輸出：**

`um1 != um2: true`

`um1 != um3: false`

`um2 != um3: true`

## <a name="op_eq_eq"></a> operator==

測試運算子左邊的 [unordered_map](../standard-library/unordered-map-class.md) 物件是否等於右邊的 unordered_map 物件。

```cpp
bool operator==(const unordered_map <Key, Type, Hash, Pred, Allocator>& left, const unordered_map <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>參數

*左面*\
`unordered_map` 類型的物件。

*再*\
`unordered_map` 類型的物件。

### <a name="return-value"></a>傳回值

如果 unordered_maps 相等, 則為**true** ;如果不相等, 則**為 false** 。

### <a name="remarks"></a>備註

unordered_map 物件之間的比較不會受到其儲存元素的任何順序影響。 如果兩個 unordered_map 的元素數量相同，且一個容器中的元素是另一個容器中元素的排列，則兩個 unordered_map 相等。 反之則為不相等。

### <a name="example"></a>範例

```cpp
// unordered_map_op_eq.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_map>
#include <iostream>
#include <ios>

int main( )
{
   using namespace std;
   unordered_map<int, int> um1, um2, um3;

   for ( int i = 0 ; i < 3 ; ++i ) {
      um1.insert( make_pair( i+1, i ) );
      um1.insert( make_pair( i, i ) );

      um2.insert( make_pair( i, i+1 ) );
      um2.insert( make_pair( i, i ) );

      um3.insert( make_pair( i, i ) );
      um3.insert( make_pair( i+1, i ) );
   }

   cout << boolalpha;
   cout << "um1 == um2: " << (um1 == um2) << endl;
   cout << "um1 == um3: " << (um1 == um3) << endl;
   cout << "um2 == um3: " << (um2 == um3) << endl;
}
```

**輸出：**

`um1 == um2: false`

`um1 == um3: true`

`um2 == um3: false`

## <a name="op_neq_multimap"></a> operator!=

測試運算子左邊的 [unordered_multimap](../standard-library/unordered-multimap-class.md) 物件是否不等於右邊的 unordered_multimap 物件。

```cpp
bool operator!=(const unordered_multimap <Key, Type, Hash, Pred, Allocator>& left, const unordered_multimap <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>參數

*左面*\
`unordered_multimap` 類型的物件。

*再*\
`unordered_multimap` 類型的物件。

### <a name="return-value"></a>傳回值

如果 unordered_multimaps 不相等, 則為**true** ;如果相等, 則**為 false** 。

### <a name="remarks"></a>備註

unordered_multimap 物件之間的比較不會受到其儲存元素的任何順序影響。 如果兩個 unordered_multimap 的元素數量相同，且一個容器中的元素是另一個容器中元素的排列，則兩個 unordered_multimap 相等。 否則，它們不相等。

### <a name="example"></a>範例

```cpp
// unordered_multimap_op_ne.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_map>
#include <iostream>
#include <ios>

int main( )
{
   using namespace std;
   unordered_multimap<int, int> um1, um2, um3;

   for ( int i = 0 ; i < 3 ; ++i ) {
      um1.insert( make_pair( i, i ) );
      um1.insert( make_pair( i, i ) );

      um2.insert( make_pair( i, i ) );
      um2.insert( make_pair( i, i ) );
      um2.insert( make_pair( i, i ) );

      um3.insert( make_pair( i, i ) );
      um3.insert( make_pair( i, i ) );
   }

   cout << boolalpha;
   cout << "um1 != um2: " << (um1 != um2) << endl;
   cout << "um1 != um3: " << (um1 != um3) << endl;
   cout << "um2 != um3: " << (um2 != um3) << endl;
}
```

**輸出：**

`um1 != um2: true`

`um1 != um3: false`

`um2 != um3: true`

## <a name="op_eq_eq_multimap"></a> operator==

測試運算子左邊的 [unordered_multimap](../standard-library/unordered-multimap-class.md) 物件是否等於右邊的 unordered_multimap 物件。

```cpp
bool operator==(const unordered_multimap <Key, Type, Hash, Pred, Allocator>& left, const unordered_multimap <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>參數

*左面*\
`unordered_multimap` 類型的物件。

*再*\
`unordered_multimap` 類型的物件。

### <a name="return-value"></a>傳回值

如果 unordered_multimaps 相等, 則為**true** ;如果不相等, 則**為 false** 。

### <a name="remarks"></a>備註

unordered_multimap 物件之間的比較不會受到其儲存元素的任何順序影響。 如果兩個 unordered_multimap 的元素數量相同，且一個容器中的元素是另一個容器中元素的排列，則兩個 unordered_multimap 相等。 反之則為不相等。

### <a name="example"></a>範例

```cpp
// unordered_multimap_op_eq.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_map>
#include <iostream>
#include <ios>

int main( )
{
   using namespace std;
   unordered_multimap<int, int> um1, um2, um3;

   for ( int i = 0 ; i < 3 ; ++i ) {
      um1.insert( make_pair( i, i ) );
      um1.insert( make_pair( i, i ) );

      um2.insert( make_pair( i, i ) );
      um2.insert( make_pair( i, i ) );
      um2.insert( make_pair( i, i ) );

      um3.insert( make_pair( i, i ) );
      um3.insert( make_pair( i, i ) );
   }

   cout << boolalpha;
   cout << "um1 == um2: " << (um1 == um2) << endl;
   cout << "um1 == um3: " << (um1 == um3) << endl;
   cout << "um2 == um3: " << (um2 == um3) << endl;
}
```

**輸出：**

`um1 == um2: false`

`um1 == um3: true`

`um2 == um3: false`

## <a name="see-also"></a>另請參閱

[<unordered_map>](../standard-library/unordered-map.md)
