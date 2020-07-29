---
title: '&lt;unordered_map&gt; 運算子'
ms.date: 11/04/2016
f1_keywords:
- unordered_map/std::operator!=
- unordered_map/std::operator==
ms.assetid: 9d5add0b-84bd-4a79-bd82-3f58b55145ed
ms.openlocfilehash: 6a22ccfaf77c3be524bf7127eac3d76c7be827ca
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87201852"
---
# <a name="ltunordered_mapgt-operators"></a>&lt;unordered_map&gt; 運算子

|||||
|-|-|-|-|
|[operator！ =](#op_neq)|[operator = =](#op_eq_eq)|[operator！ =](#op_neq_multimap)|[operator = =](#op_eq_eq_multimap)|

## <a name="operator"></a><a name="op_neq"></a>operator！ =

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

**`true`** 如果 unordered_maps 不相等，則為，**`false`** 如果相等則為。

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

## <a name="operator"></a><a name="op_eq_eq"></a>operator = =

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

**`true`** 如果 unordered_maps 相等，則為，**`false`** 如果不相等，則為。

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

## <a name="operator"></a><a name="op_neq_multimap"></a>operator！ =

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

**`true`** 如果 unordered_multimaps 不相等，則為，**`false`** 如果相等則為。

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

## <a name="operator"></a><a name="op_eq_eq_multimap"></a>operator = =

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

**`true`** 如果 unordered_multimaps 相等，則為，**`false`** 如果不相等，則為。

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
