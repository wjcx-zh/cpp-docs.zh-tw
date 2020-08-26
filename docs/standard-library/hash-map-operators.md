---
title: '&lt;hash_map&gt; 運算子'
ms.date: 11/04/2016
f1_keywords:
- hash_map/std::operator!=
- hash_map/std::operator==
ms.assetid: 24b9bb9e-e983-4060-bce5-2c7c8161ee61
ms.openlocfilehash: b0884cacb11299f96d539c8c83a1fc9fa2840d16
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88844388"
---
# <a name="lthash_mapgt-operators"></a>&lt;hash_map&gt; 運算子

[operator！ =](#op_neq)\
[operator！ = (multimap) ](#op_neq_mm)\
[operator = =](#op_eq_eq)\
[operator = = (multimap) ](#op_eq_eq_mm)

## <a name="operator"></a><a name="op_neq"></a> operator！ =

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_map 類別](unordered-map-class.md)。

測試運算子左邊的 hash_map 物件是否不等於右邊的 hash_map 物件。

```cpp
bool operator!=(const hash_map <Key, Type, Traits, Allocator>& left, const hash_map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>參數

*離開*\
`hash_map` 類型的物件。

*對*\
`hash_map` 類型的物件。

### <a name="return-value"></a>傳回值

**`true`** 如果 hash_maps 不相等，則為， **`false`** 如果 hash_maps 相等則為。

### <a name="remarks"></a>備註

hash_map 物件之間的比較是以其元素的成對比較為基礎。 兩個 hash_map 如果元素數目相同，且其個別元素的值也相同，兩者便相等。 反之則為不相等。

[<hash_map](hash-map.md)的成員>和[<Hash_set](hash-set.md) [stdext 命名空間](stdext-namespace.md)中>的標頭檔。

### <a name="example"></a>範例

```cpp
// hash_map_op_ne.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1, hm2, hm3;
   int i;
   typedef pair <int, int> Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      hm1.insert ( Int_Pair ( i, i ) );
      hm2.insert ( Int_Pair ( i, i * i ) );
      hm3.insert ( Int_Pair ( i, i ) );
   }

   if ( hm1 != hm2 )
      cout << "The hash_maps hm1 and hm2 are not equal." << endl;
   else
      cout << "The hash_maps hm1 and hm2 are equal." << endl;

   if ( hm1 != hm3 )
      cout << "The hash_maps hm1 and hm3 are not equal." << endl;
   else
      cout << "The hash_maps hm1 and hm3 are equal." << endl;
}
```

```Output
The hash_maps hm1 and hm2 are not equal.
The hash_maps hm1 and hm3 are equal.
```

## <a name="operator"></a><a name="op_eq_eq"></a> operator = =

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_map 類別](unordered-map-class.md)。

測試運算子左邊的 hash_map 物件是否等於右邊的 hash_map 物件。

```cpp
bool operator==(const hash_map <Key, Type, Traits, Allocator>& left, const hash_map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>參數

*離開*\
`hash_map` 類型的物件。

*對*\
`hash_map` 類型的物件。

### <a name="return-value"></a>傳回值

**`true`** 如果運算子左邊的 hash_map 等於運算子右邊的 hash_map，則為，否則為 **`false`** 。

### <a name="remarks"></a>備註

hash_map 物件之間的比較是以其元素的成對比較為基礎。 兩個 hash_map 如果元素數目相同，且其個別元素的值也相同，兩者便相等。 反之則為不相等。

### <a name="example"></a>範例

```cpp
// hash_map_op_eq.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1, hm2, hm3;
   int i;
   typedef pair <int, int> Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      hm1.insert ( Int_Pair ( i, i ) );
      hm2.insert ( Int_Pair ( i, i * i ) );
      hm3.insert ( Int_Pair ( i, i ) );
   }

   if ( hm1 == hm2 )
      cout << "The hash_maps hm1 and hm2 are equal." << endl;
   else
      cout << "The hash_maps hm1 and hm2 are not equal." << endl;

   if ( hm1 == hm3 )
      cout << "The hash_maps hm1 and hm3 are equal." << endl;
   else
      cout << "The hash_maps hm1 and hm3 are not equal." << endl;
}
```

```Output
The hash_maps hm1 and hm2 are not equal.
The hash_maps hm1 and hm3 are equal.
```

## <a name="operator-hash_multimap"></a><a name="op_neq_mm"></a> operator！ = (hash_multimap) 

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_multimap 類別](unordered-multimap-class.md)。

測試運算子左邊的 hash_multimap 物件是否不等於右邊的 hash_multimap 物件。

```cpp
bool operator!=(const hash_multimap <Key, Type, Traits, Allocator>& left, const hash_multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>參數

*離開*\
`hash_multimap` 類型的物件。

*對*\
`hash_multimap` 類型的物件。

### <a name="return-value"></a>傳回值

**`true`** 如果 hash_multimaps 不相等，則為， **`false`** 如果 hash_multimaps 相等則為。

### <a name="remarks"></a>備註

hash_multimap 物件之間的比較是以其元素的成對比較為基礎。 兩個 hash_multimap 如果元素數目相同，且其個別元素的值也相同，兩者便相等。 反之則為不相等。

### <a name="example"></a>範例

```cpp
// hash_multimap_op_ne.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1, hm2, hm3;
   int i;
   typedef pair <int, int> Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      hm1.insert ( Int_Pair ( i, i ) );
      hm2.insert ( Int_Pair ( i, i * i ) );
      hm3.insert ( Int_Pair ( i, i ) );
   }

   if ( hm1 != hm2 )
      cout << "The hash_multimaps hm1 and hm2 are not equal." << endl;
   else
      cout << "The hash_multimaps hm1 and hm2 are equal." << endl;

   if ( hm1 != hm3 )
      cout << "The hash_multimaps hm1 and hm3 are not equal." << endl;
   else
      cout << "The hash_multimaps hm1 and hm3 are equal." << endl;
}
```

```Output
The hash_multimaps hm1 and hm2 are not equal.
The hash_multimaps hm1 and hm3 are equal.
```

## <a name="operator--hash_multimap"></a><a name="op_eq_eq_mm"></a> operator = = (hash_multimap) 

> [!NOTE]
> 這個 API 已經過時。 替代方案是 [unordered_multimap 類別](unordered-multimap-class.md)。

測試運算子左邊的 hash_multimap 物件是否等於右邊的 hash_multimap 物件。

```cpp
bool operator==(const hash_multimap <Key, Type, Traits, Allocator>& left, const hash_multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>參數

*離開*\
`hash_multimap` 類型的物件。

*對*\
`hash_multimap` 類型的物件。

### <a name="return-value"></a>傳回值

**`true`** 如果運算子左邊的 hash_multimap 等於運算子右邊的 hash_multimap，則為，否則為 **`false`** 。

### <a name="remarks"></a>備註

hash_multimap 物件之間的比較是以其元素的成對比較為基礎。 兩個 hash_multimap 如果元素數目相同，且其個別元素的值也相同，兩者便相等。 反之則為不相等。

### <a name="example"></a>範例

```cpp
// hash_multimap_op_eq.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap<int, int> hm1, hm2, hm3;
   int i;
   typedef pair<int, int> Int_Pair;

   for (i = 0; i < 3; i++)
   {
      hm1.insert(Int_Pair(i, i));
      hm2.insert(Int_Pair(i, i*i));
      hm3.insert(Int_Pair(i, i));
   }

   if ( hm1 == hm2 )
      cout << "The hash_multimaps hm1 and hm2 are equal." << endl;
   else
      cout << "The hash_multimaps hm1 and hm2 are not equal." << endl;

   if ( hm1 == hm3 )
      cout << "The hash_multimaps hm1 and hm3 are equal." << endl;
   else
      cout << "The hash_multimaps hm1 and hm3 are not equal." << endl;
}
```

```Output
The hash_multimaps hm1 and hm2 are not equal.
The hash_multimaps hm1 and hm3 are equal.
```

## <a name="see-also"></a>另請參閱

[<hash_map>](hash-map.md)
