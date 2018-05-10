---
title: '&lt;hash_map&gt; 運算子 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- hash_map/std::operator!=
- hash_map/std::operator==
dev_langs:
- C++
ms.assetid: 24b9bb9e-e983-4060-bce5-2c7c8161ee61
ms.openlocfilehash: aa5c2a662fb5e827978a7c00aa3035dcc6cc97f2
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="lthashmapgt-operators"></a>&lt;hash_map&gt; 運算子

|||
|-|-|
|[operator!=](#op_neq)|[operator!= (multimap)](#op_neq_mm)|
|[operator==](#op_eq_eq)|[operator== (multimap)](#op_eq_eq_mm)|

## <a name="op_neq"></a> operator!=

> [!NOTE]
> 這個 API 已過時。 替代方案是 [unordered_map 類別](unordered-map-class.md)。

測試運算子左邊的 hash_map 物件是否不等於右邊的 hash_map 物件。

```cpp
bool operator!=(const hash_map <Key, Type, Traits, Allocator>& left, const hash_map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>參數

`left` 型別的物件`hash_map`。

`right` 型別的物件`hash_map`。

### <a name="return-value"></a>傳回值

如果 hash_map 不相等，便會傳回 **true**；如果 hash_map 相等，則會傳回 **false**。

### <a name="remarks"></a>備註

hash_map 物件之間的比較是以其元素的成對比較為基礎。 兩個 hash_map 如果元素數目相同，且其個別元素的值也相同，兩者便相等。 反之則為不相等。

成員[< hash_map >](hash-map.md)和[< hash_set >](hash-set.md)標頭檔中[stdext 命名空間](stdext-namespace.md)。

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

## <a name="op_eq_eq"></a> operator==

> [!NOTE]
> 這個 API 已過時。 替代方案是 [unordered_map 類別](unordered-map-class.md)。

測試運算子左邊的 hash_map 物件是否等於右邊的 hash_map 物件。

```cpp
bool operator==(const hash_map <Key, Type, Traits, Allocator>& left, const hash_map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>參數

`left` 型別的物件`hash_map`。

`right` 型別的物件`hash_map`。

### <a name="return-value"></a>傳回值

如果運算子左邊的 hash_map 等於運算子右邊的 hash_map，便會傳回 **true**；否則會傳回 **false**。

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

## <a name="op_neq_mm"></a>  運算子 ！ = (hash_multimap)

> [!NOTE]
> 這個 API 已過時。 替代方案是 [unordered_multimap 類別](unordered-multimap-class.md)。

測試運算子左邊的 hash_multimap 物件是否不等於右邊的 hash_multimap 物件。

```cpp
bool operator!=(const hash_multimap <Key, Type, Traits, Allocator>& left, const hash_multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>參數

`left` 型別的物件`hash_multimap`。

`right` 型別的物件`hash_multimap`。

### <a name="return-value"></a>傳回值

如果 hash_multimap 不相等，便會傳回 **true**；如果 hash_multimap 相等，則會傳回 **false**。

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

## <a name="op_eq_eq_mm"></a>  運算子 = = (hash_multimap)

> [!NOTE]
> 這個 API 已過時。 替代方案是 [unordered_multimap 類別](unordered-multimap-class.md)。

測試運算子左邊的 hash_multimap 物件是否等於右邊的 hash_multimap 物件。

```cpp
bool operator==(const hash_multimap <Key, Type, Traits, Allocator>& left, const hash_multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>參數

`left` 型別的物件`hash_multimap`。

`right` 型別的物件`hash_multimap`。

### <a name="return-value"></a>傳回值

如果運算子左邊的 hash_multimap 等於運算子右邊的 hash_multimap，便會傳回 **true**；否則會傳回 **false**。

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

[<hash_map>](hash-map.md)<br/>
