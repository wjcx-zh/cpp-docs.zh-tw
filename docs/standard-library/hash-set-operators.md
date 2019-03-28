---
title: '&lt;hash_set&gt; 運算子'
ms.date: 03/27/2019
f1_keywords:
- hash_set/std::operator!=
- hash_set/std::operator==
ms.assetid: 403d8e4e-0b3f-43fb-bc5a-8100c4f331c5
ms.openlocfilehash: 901070731d372904ae297a5360ec0da78d179468
ms.sourcegitcommit: 309dc532f13242854b47759cef846de59bb807f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2019
ms.locfileid: "58565580"
---
# <a name="lthashsetgt-operators"></a>&lt;hash_set&gt; 運算子

||||
|-|-|-|
|[operator!=](#op_neq)|[operator!= (hash_multiset)](#op_neq_hash_multiset)|[operator==](#op_eq_eq)|
|[operator== (hash_multiset)](#op_eq_eq_hash_multiset)|

## <a name="op_neq"></a> operator!=

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_set 類別](../standard-library/unordered-set-class.md)。

測試運算子左邊的 hash_set 物件是否不等於右邊的 hash_set 物件。

```cpp
bool operator!=(const hash_set <Key, Traits, Allocator>& left, const hash_set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>參數

*left*<br/>
`hash_set` 類型的物件。

*right*<br/>
`hash_set` 類型的物件。

### <a name="return-value"></a>傳回值

如果 hash_set 不相等，便會傳回 **true**；如果 hash_set 相等，則會傳回 **false**。

### <a name="remarks"></a>備註

hash_set 物件之間的比較是以其元素之間的成對比較為基礎。 兩個 hash_set 如果元素數目相同，且其個別元素的值也相同，兩者便相等。 反之則為不相等。

成員[< p >](../standard-library/hash-map.md)並[< hash_set >](../standard-library/hash-set.md)標頭檔位於[stdext 命名空間](../standard-library/stdext-namespace.md)。

### <a name="example"></a>範例

```cpp
// hash_set_op_ne.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1, hs2, hs3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      hs1.insert ( i );
      hs2.insert ( i * i );
      hs3.insert ( i );
   }

   if ( hs1 != hs2 )
      cout << "The hash_sets hs1 and hs2 are not equal." << endl;
   else
      cout << "The hash_sets hs1 and hs2 are equal." << endl;

   if ( hs1 != hs3 )
      cout << "The hash_sets hs1 and hs3 are not equal." << endl;
   else
      cout << "The hash_sets hs1 and hs3 are equal." << endl;
}
```

```Output
The hash_sets hs1 and hs2 are not equal.
The hash_sets hs1 and hs3 are equal.
```

## <a name="op_eq_eq"></a> operator==

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_set 類別](../standard-library/unordered-set-class.md)。

測試運算子左邊的 hash_set 物件是否等於右邊的 hash_set 物件。

```cpp
bool operator!==(const hash_set <Key, Traits, Allocator>& left, const hash_set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>參數

*left*<br/>
`hash_set` 類型的物件。

*right*<br/>
`hash_set` 類型的物件。

### <a name="return-value"></a>傳回值

如果運算子左邊的 hash_set 等於運算子右邊的 hash_set，便會傳回 **true**；否則會傳回 **false**。

### <a name="remarks"></a>備註

hash_set 物件之間的比較是以其元素的成對比較為基礎。 兩個 hash_set 如果元素數目相同，且其個別元素的值也相同，兩者便相等。 反之則為不相等。

### <a name="example"></a>範例

```cpp
// hash_set_op_eq.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i );
   }

   if ( s1 == s2 )
      cout << "The hash_sets s1 and s2 are equal." << endl;
   else
      cout << "The hash_sets s1 and s2 are not equal." << endl;

   if ( s1 == s3 )
      cout << "The hash_sets s1 and s3 are equal." << endl;
   else
      cout << "The hash_sets s1 and s3 are not equal." << endl;
}
```

```Output
The hash_sets s1 and s2 are not equal.
The hash_sets s1 and s3 are equal.
```

## <a name="op_neq_hash_multiset"></a>  operator!= (hash_multiset)

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_set 類別](../standard-library/unordered-set-class.md)。

測試運算子左邊的 hash_multiset 物件是否不等於右邊的 hash_multiset 物件。

```cpp
bool operator!=(const hash_multiset <Key, Traits, Allocator>& left, const hash_multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>參數

*left*<br/>
`hash_multiset` 類型的物件。

*right*<br/>
`hash_multiset` 類型的物件。

### <a name="return-value"></a>傳回值

如果 hash_multiset 不相等，便會傳回 **true**；如果 hash_multiset 相等，則會傳回 **false**。

### <a name="remarks"></a>備註

hash_multiset 物件之間的比較是以其元素之間的成對比較為基礎。 兩個 hash_multiset 如果元素數目相同，且其個別元素的值也相同，兩者便相等。 反之則為不相等。

### <a name="example"></a>範例

```cpp
// hashset_op_ne.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hs1, hs2, hs3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      hs1.insert ( i );
      hs2.insert ( i * i );
      hs3.insert ( i );
   }

   if ( hs1 != hs2 )
      cout << "The hash_multisets hs1 and hs2 are not equal." << endl;
   else
      cout << "The hash_multisets hs1 and hs2 are equal." << endl;

   if ( hs1 != hs3 )
      cout << "The hash_multisets hs1 and hs3 are not equal." << endl;
   else
      cout << "The hash_multisets hs1 and hs3 are equal." << endl;
}
```

```Output
The hash_multisets hs1 and hs2 are not equal.
The hash_multisets hs1 and hs3 are equal.
```

## <a name="op_eq_eq_hash_multiset"></a>  operator== (hash_multiset)

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_set 類別](../standard-library/unordered-set-class.md)。

測試運算子左邊的 hash_multiset 物件是否等於右邊的 hash_multiset 物件。

```cpp
bool operator!==(const hash_multiset <Key, Traits, Allocator>& left, const hash_multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>參數

*left*<br/>
`hash_multiset` 類型的物件。

*right*<br/>
`hash_multiset` 類型的物件。

### <a name="return-value"></a>傳回值

如果運算子左邊的 hash_multiset 等於運算子右邊的 hash_multiset，便會傳回 **true**；否則會傳回 **false**。

### <a name="remarks"></a>備註

hash_multiset 物件之間的比較是以其元素的成對比較為基礎。 兩個 hash_multiset 如果元素數目相同，且其個別元素的值也相同，兩者便相等。 反之則為不相等。

### <a name="example"></a>範例

```cpp
// hash_multiset_op_eq.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i );
   }

   if ( s1 == s2 )
      cout << "The hash_multisets s1 and s2 are equal." << endl;
   else
      cout << "The hash_multisets s1 and s2 are not equal." << endl;

   if ( s1 == s3 )
      cout << "The hash_multisets s1 and s2 are equal." << endl;
   else
      cout << "The hash_multisets s1 and s2 are not equal." << endl;
}
```

```Output
The hash_multisets s1 and s2 are not equal.
The hash_multisets s1 and s2 are equal.
```

## <a name="see-also"></a>另請參閱

[<hash_set>](../standard-library/hash-set.md)<br/>
