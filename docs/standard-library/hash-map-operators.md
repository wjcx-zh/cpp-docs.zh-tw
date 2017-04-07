---
title: "&lt;hash_map&gt; 運算子 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24b9bb9e-e983-4060-bce5-2c7c8161ee61
caps.latest.revision: 13
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 6960d7dfc3a6f36f803ae765ad4cbeb77038401c
ms.lasthandoff: 02/24/2017

---
# <a name="lthashmapgt-operators"></a>&lt;hash_map&gt; 運算子
||||  
|-|-|-|  
|[operator!=](#operator_neq)|[operator!= (hash_map)](#operator_neq__hash_map_)|[operator==](#operator_eq_eq)|  
|[operator== (hash_map)](#operator_eq_eq__hash_map_)|  
  
##  <a name="operator_neq__hash_map_"></a>  operator!= (hash_map)  
  
> [!NOTE]
>  這個 API 已過時。 替代方案是 [unordered_map 類別](../standard-library/unordered-map-class.md)。  
  
 測試運算子左邊的 hash_map 物件是否不等於右邊的 hash_map 物件。  
  
```  
bool operator!=(const hash_map <Key, Type, Traits, Allocator>& left, const hash_map <Key, Type, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>參數  
 `left`  
 `hash_map` 類型的物件。  
  
 `right`  
 `hash_map` 類型的物件。  
  
### <a name="return-value"></a>傳回值  
 如果 hash_map 不相等，便會傳回 **true**；如果 hash_map 相等，則會傳回 **false**。  
  
### <a name="remarks"></a>備註  
 hash_map 物件之間的比較是以其元素的成對比較為基礎。 兩個 hash_map 如果元素數目相同，且其個別元素的值也相同，兩者便相等。 反之則為不相等。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 標頭檔的成員不再位於 std 命名空間中，而是已移到 stdext 命名空間中。 如需詳細資訊，請參閱 [stdext 命名空間](../standard-library/stdext-namespace.md)。  
  
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
  
##  <a name="operator_eq_eq__hash_map_"></a>  operator== (hash_map)  
  
> [!NOTE]
>  這個 API 已過時。 替代方案是 [unordered_map 類別](../standard-library/unordered-map-class.md)。  
  
 測試運算子左邊的 hash_map 物件是否等於右邊的 hash_map 物件。  
  
```  
bool operator==(const hash_map <Key, Type, Traits, Allocator>& left, const hash_map <Key, Type, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>參數  
 `left`  
 `hash_map` 類型的物件。  
  
 `right`  
 `hash_map` 類型的物件。  
  
### <a name="return-value"></a>傳回值  
 如果運算子左邊的 hash_map 等於運算子右邊的 hash_map，便會傳回 **true**；否則會傳回 **false**。  
  
### <a name="remarks"></a>備註  
 hash_map 物件之間的比較是以其元素的成對比較為基礎。 兩個 hash_map 如果元素數目相同，且其個別元素的值也相同，兩者便相等。 反之則為不相等。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 標頭檔的成員不再位於 std 命名空間中，而是已移到 stdext 命名空間中。 如需詳細資訊，請參閱 [stdext 命名空間](../standard-library/stdext-namespace.md)。  
  
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
  
##  <a name="operator_neq"></a>  operator!=  
  
> [!NOTE]
>  這個 API 已過時。 替代方案是 [unordered_multimap 類別](../standard-library/unordered-multimap-class.md)。  
  
 測試運算子左邊的 hash_multimap 物件是否不等於右邊的 hash_multimap 物件。  
  
```  
bool operator!=(const hash_multimap <Key, Type, Traits, Allocator>& left, const hash_multimap <Key, Type, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>參數  
 `left`  
 `hash_multimap` 類型的物件。  
  
 `right`  
 `hash_multimap` 類型的物件。  
  
### <a name="return-value"></a>傳回值  
 如果 hash_multimap 不相等，便會傳回 **true**；如果 hash_multimap 相等，則會傳回 **false**。  
  
### <a name="remarks"></a>備註  
 hash_multimap 物件之間的比較是以其元素的成對比較為基礎。 兩個 hash_multimap 如果元素數目相同，且其個別元素的值也相同，兩者便相等。 反之則為不相等。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 標頭檔的成員不再位於 std 命名空間中，而是已移到 stdext 命名空間中。 如需詳細資訊，請參閱 [stdext 命名空間](../standard-library/stdext-namespace.md)。  
  
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
  
##  <a name="operator_eq_eq"></a>  operator==  
  
> [!NOTE]
>  這個 API 已過時。 替代方案是 [unordered_multimap 類別](../standard-library/unordered-multimap-class.md)。  
  
 測試運算子左邊的 hash_multimap 物件是否等於右邊的 hash_multimap 物件。  
  
```  
bool operator==(const hash_multimap <Key, Type, Traits, Allocator>& left, const hash_multimap <Key, Type, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>參數  
 `left`  
 `hash_multimap` 類型的物件。  
  
 `right`  
 `hash_multimap` 類型的物件。  
  
### <a name="return-value"></a>傳回值  
 如果運算子左邊的 hash_multimap 等於運算子右邊的 hash_multimap，便會傳回 **true**；否則會傳回 **false**。  
  
### <a name="remarks"></a>備註  
 hash_multimap 物件之間的比較是以其元素的成對比較為基礎。 兩個 hash_multimap 如果元素數目相同，且其個別元素的值也相同，兩者便相等。 反之則為不相等。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 標頭檔的成員不再位於 std 命名空間中，而是已移到 stdext 命名空間中。 如需詳細資訊，請參閱 [stdext 命名空間](../standard-library/stdext-namespace.md)。  
  
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
 [<hash_map>](../standard-library/hash-map.md)


