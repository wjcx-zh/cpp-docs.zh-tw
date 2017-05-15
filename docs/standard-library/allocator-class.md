---
title: "allocator 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- allocator
- memory/std::allocator
- memory/std::allocator::const_pointer
- memory/std::allocator::const_reference
- memory/std::allocator::difference_type
- memory/std::allocator::pointer
- memory/std::allocator::reference
- memory/std::allocator::size_type
- memory/std::allocator::value_type
- memory/std::allocator::address
- memory/std::allocator::allocate
- memory/std::allocator::construct
- memory/std::allocator::deallocate
- memory/std::allocator::destroy
- memory/std::allocator::max_size
- memory/std::allocator::rebind
dev_langs:
- C++
helpviewer_keywords:
- allocator class
ms.assetid: 3fd58076-56cc-43bb-ad58-b4b7c9c6b410
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: a2447e0e42cc0a7fdc22db9de415f6dde46c40a5
ms.contentlocale: zh-tw
ms.lasthandoff: 04/29/2017

---
# <a name="allocator-class"></a>allocator 類別
此範本類別所描述的物件管理 **Type** 類型物件陣列的儲存空間配置和釋放。 **allocator** 類別的物件是建構函式中指定的預設配置器物件，為針對 C++ 標準程式庫中的數個容器範本類別所指定。  
  
## <a name="syntax"></a>語法  
  
```  
template <class Type>  
class allocator  
```  
  
#### <a name="parameters"></a>參數  
 *Type*  
 正在配置或取消配置儲存體的物件類型。  
  
## <a name="remarks"></a>備註  
 所有 C++ 標準程式庫容器都具有範本參數，預設值為 **allocator**。 建構包含自訂配置器的容器可控制該容器之項目的配置與釋放。  
  
 例如，配置器物件可在私密堆積或共用記憶體中配置儲存體，或是可針對小型或大型物件最佳化。 它也能指定透過其提供的類型定義，透過管理共用記憶體的特殊存取子物件來存取項目，或是執行自動化記憶體回收。 因此，使用配置器物件來配置儲存區的類別，應該使用這些類型來宣告指標和參考物件，如 C++ 標準程式庫中的容器所做的一般。  
  
 **(僅限 C_++98/03)**從 allocator 類別衍生時，您必須提供 [rebind](#rebind) 結構，其 `_Other` typedef 會參考您最近衍生的類別。  
  
 因此，配置器會定義下列類型：  
  
- [pointer](#pointer) 行為類似於 **Type** 的指標。  
  
- [const_pointer](#const_pointer) 行為類似於 **Type** 的 const 指標。  
  
- [reference](#reference) 行為類似於 **Type** 的參考。  
  
- [const_reference](#const_reference) 行為類似於 **Type** 的 const 參考。  
  
 這些 **Type** 指定指標和參考必須為所配置元素接受的格式 ([allocator::pointer](#pointer) 不一定與所有配置器的 **Type**\* 相同，即使它針對 **allocator** 類別明顯定義此類型也是如此)。  
  
 **C++ 11 和更新版本：**若要在您的配置器中啟用移動運算，請使用最小的配置器介面與實作複製建構函式、== 和 != 運算子、配置及解除配置。 如需詳細資訊和範例，請參閱[配置器](../standard-library/allocators.md)。  
  
## <a name="members"></a>Members  
  
### <a name="constructors"></a>建構函式  
  
|||  
|-|-|  
|[allocator](#allocator)|建構函式可用來建立 `allocator` 物件。|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[const_pointer](#const_pointer)|一種類型，可提供配置器管理之物件類型的常數指標。|  
|[const_reference](#const_reference)|一種類型，可提供配置器管理之物件類型的常數參考。|  
|[difference_type](#difference_type)|帶正負號整數類型，可以表示配置器所管理的物件類型的指標值之間的差異。|  
|[pointer](#pointer)|一種類型，可提供配置器管理之物件類型的指標。|  
|[reference](#reference)|一種類型，可提供配置器管理之物件類型的參考。|  
|[size_type](#size_type)|不帶正負號的整數類型，可以代表樣板類別 `allocator` 的物件可配置的任何序列的長度。|  
|[value_type](#value_type)|配置器所管理的類型。|  
  
### <a name="member-functions"></a>成員函式  
  
|||  
|-|-|  
|[address](#address)|尋找指定值所屬物件的位址。|  
|[allocate](#allocate)|配置夠大的記憶體區塊，至少儲存某些指定的項目數。|  
|[construct](#construct)|在指定值初始化的指定位址上，建構特定類型的物件。|  
|[deallocate](#deallocate)|從指定位置起算的儲存體中，釋放指定數目的物件。|  
|[destroy](#destroy)|呼叫物件解構函式，而不取消配置儲存物件的記憶體。|  
|[max_size](#max_size)|傳回在可用記憶體用完之前，無法由類別 `allocator`的物件配置之類型 `Type` 的項目數量。|  
|[rebind](#rebind)|一種結構，可讓某個類型的物件配置器，為另一種類型的物件配置儲存體。|  
  
### <a name="operators"></a>運算子  
  
|||  
|-|-|  
|[operator=](#op_eq)|將一個 `allocator` 物件指派給另一個 `allocator` 物件。|  
  
## <a name="requirements"></a>需求  
 **標頭：**\<memory>  
  
 **命名空間：** std  
  
##  <a name="address"></a> allocator::address  
 尋找指定值所屬物件的位址。  
  
```  
pointer address(reference val) const;
const_pointer address(const_reference val) const;
```  
  
### <a name="parameters"></a>參數  
 `val`  
 搜尋其位址之物件的 const 或 nonconst 值。  
  
### <a name="return-value"></a>傳回值  
 分別針對 const 或 nonconst 值找到之物件的 const 或 nonconst 指標。  
  
### <a name="remarks"></a>備註  
 這些成員函式會傳回 `val` 的位址，而且格式是指標必須為所配置元素接受的格式。  
  
### <a name="example"></a>範例  
  
```cpp  
// allocator_address.cpp  
// compile with: /EHsc  
#include <memory>  
#include <algorithm>  
#include <iostream>  
#include <vector>  
  
using namespace std;  
  
int main( )   
{  
   vector <int> v1;  
   vector <int>::iterator v1Iter;  
   vector <int>:: allocator_type v1Alloc;  
  
   int i;  
   for ( i = 1 ; i <= 7 ; i++ )  
   {  
      v1.push_back( 2 * i );  
   }  
  
   cout << "The original vector v1 is:\n ( " ;  
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ; v1Iter++ )  
      cout << *v1Iter << " ";  
   cout << ")." << endl;  
  
   allocator<int>::const_pointer v1Ptr;  
   const int k = 8;  
   v1Ptr = v1Alloc.address( *find(v1.begin( ), v1.end( ), k) );  
   // v1Ptr = v1Alloc.address( k );  
   cout << "The integer addressed by v1Ptr has a value of: "  
        << "*v1Ptr = " << *v1Ptr << "." << endl;  
}  
```  
  
```Output  
The original vector v1 is:  
 ( 2 4 6 8 10 12 14 ).  
The integer addressed by v1Ptr has a value of: *v1Ptr = 8.  
```  
  
##  <a name="allocate"></a> allocator::allocate  
 配置夠大的記憶體區塊，至少儲存某些指定的項目數。  
  
```  
pointer allocate(size_type count, const void* _Hint);
```  
  
### <a name="parameters"></a>參數  
 `count`  
 要配置足夠儲存空間的元素數。  
  
 *_Hint*  
 const 指標，可找出要求之前所配置物件的位址，來協助配置器物件符合儲存要求。  
  
### <a name="return-value"></a>傳回值  
 所配置物件的指標，如果未配置記憶體，則為 Null。  
  
### <a name="remarks"></a>備註  
 成員函式會配置 **Type** 類型之計算元素陣列的儲存空間，方法是呼叫運算子 new( `count`)。 它會傳回所配置物件的指標。 提示引數可協助部分配置器改善參考區域性；有效的選擇是相同配置器物件稍早所配置但尚未解除配置之物件的位址。 若不要提供提示，請改用 Null 指標引數。  
  
### <a name="example"></a>範例  
  
```cpp  
// allocator_allocate.cpp  
// compile with: /EHsc  
#include <memory>  
#include <iostream>  
#include <vector>  
  
using namespace std;  
  
int main( )   
{  
   allocator<int> v1Alloc;    
   allocator<int>::pointer v1aPtr;    
   v1aPtr = v1Alloc.allocate ( 10 );  
  
   int i;  
   for ( i = 0 ; i < 10 ; i++ )  
   {  
      v1aPtr[ i ] = i;  
   }  
  
   for ( i = 0 ; i < 10 ; i++ )  
   {  
      cout << v1aPtr[ i ] << " ";  
   }  
   cout << endl;    
   v1Alloc.deallocate( v1aPtr, 10 );  
}  
```  
  
```Output  
0 1 2 3 4 5 6 7 8 9   
```  
  
##  <a name="allocator"></a> allocator::allocator  
 建構函式用來建立配置器物件。  
  
```  
allocator();
allocator(const allocator<Type>& right);
template <class Other>  
allocator(const allocator<Other>& right);
```  
  
### <a name="parameters"></a>參數  
 `right`  
 要複製的配置器物件。  
  
### <a name="remarks"></a>備註  
 建構函式不會執行任何動作。 不過，一般情況下，從另一個配置器物件建構的配置器物件應該與其相等，並允許在這兩個配置器物件之間混合進行物件配置和釋放。  
  
### <a name="example"></a>範例  
  
```cpp  
// allocator_allocator.cpp  
// compile with: /EHsc  
#include <memory>  
#include <iostream>  
#include <vector>  
  
using namespace std;  
  
class Int {  
public:  
   Int( int i )   
   {  
      cout << "Constructing " << ( void* )this  << endl;   
      x = i;  
      bIsConstructed = true;  
   };  
   ~Int( )   
   {  
      cout << "Destructing " << ( void* )this << endl;   
      bIsConstructed = false;  
   };  
   Int &operator++( )   
   {  
      x++;  
      return *this;  
   };  
   int x;  
private:  
   bool bIsConstructed;  
};  
  
int main( )   
{  
   allocator<double> Alloc;  
   vector <Int>:: allocator_type v1Alloc;  
  
   allocator<double> cAlloc(Alloc);   
   allocator<Int> cv1Alloc(v1Alloc);  
  
   if ( cv1Alloc == v1Alloc )  
      cout << "The allocator objects cv1Alloc & v1Alloc are equal."  
           << endl;  
   else  
      cout << "The allocator objects cv1Alloc & v1Alloc are not equal."  
           << endl;  
  
   if ( cAlloc == Alloc )  
      cout << "The allocator objects cAlloc & Alloc are equal."  
           << endl;  
   else  
      cout << "The allocator objects cAlloc & Alloc are not equal."  
           << endl;  
}  
```  
  
```Output  
The allocator objects cv1Alloc & v1Alloc are equal.  
The allocator objects cAlloc & Alloc are equal.  
```  
  
##  <a name="const_pointer"></a> allocator::const_pointer  
 一種類型，可提供配置器管理之物件類型的常數指標。  
  
```  
typedef const value_type *const_pointer;  
```  
  
### <a name="remarks"></a>備註  
 此指標類型所描述的物件 **ptr** 可以透過運算式 **\*ptr** 來指定範本類別配置器物件可配置的任何 const 物件。  
  
### <a name="example"></a>範例  
  
```cpp  
// allocator_const_ptr.cpp  
// compile with: /EHsc  
#include <memory>  
#include <iostream>  
#include <vector>  
  
using namespace std;  
  
int main( )   
{  
   vector <int> v1;  
   vector <int>::iterator v1Iter;  
   vector <int>:: allocator_type v1Alloc;  
  
   int i;  
   for ( i = 1 ; i <= 7 ; i++ )  
   {  
      v1.push_back( i * 2 );  
   }  
  
   cout << "The original vector v1 is:\n ( " ;  
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ; v1Iter++ )  
      cout << *v1Iter << " ";  
   cout << ")." << endl;  
  
   allocator<int>::const_pointer v1Ptr;  
   const int k = 10;  
   v1Ptr = v1Alloc.address( k );  
  
   cout << "The integer's address found has a value of: "  
        << *v1Ptr << "." << endl;  
}  
```  
  
```Output  
The original vector v1 is:  
 ( 2 4 6 8 10 12 14 ).  
The integer's address found has a value of: 10.  
```  
  
##  <a name="const_reference"></a> allocator::const_reference  
 一種類型，可提供配置器管理之物件類型的常數參考。  
  
```  
typedef const value_type& const_reference;  
```  
  
### <a name="remarks"></a>備註  
 此參考類型所描述的物件可以指定範本類別配置器物件可配置的任何 const 物件。  
  
### <a name="example"></a>範例  
  
```cpp  
// allocator_const_ref.cpp  
// compile with: /EHsc  
#include <memory>  
#include <iostream>  
#include <vector>  
  
using namespace std;  
  
int main( )   
{  
   vector <double> v;  
   vector <double> ::iterator vIter, vfIter;  
   vector <double> :: allocator_type vAlloc;  
  
   int j;  
   for ( j = 1 ; j <= 7 ; j++ )  
   {  
      v.push_back( 100.0 * j );  
   }  
  
   cout << "The original vector v is:\n ( " ;  
   for ( vIter = v.begin( ) ; vIter != v.end( ) ; vIter++ )  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   vfIter = v.begin( );  
   allocator<double>::const_reference vcref =*vfIter;  
   cout << "The value of the element referred to by vref is: "  
        << vcref << ",\n the first element in the vector." << endl;  
  
   // const references can have their elements modified,  
   // so the following would generate an error:  
   // vcref = 150;  
   // but the value of the first element could be modified through  
   // its nonconst iterator and the const reference would remain valid  
 *vfIter = 175;  
   cout << "The value of the element referred to by vcref,"  
        <<"\n after nofication through its nonconst iterator, is: "  
        << vcref << "." << endl;  
}  
```  
  
```Output  
The original vector v is:  
 ( 100 200 300 400 500 600 700 ).  
The value of the element referred to by vref is: 100,  
 the first element in the vector.  
The value of the element referred to by vcref,  
 after nofication through its nonconst iterator, is: 175.  
```  
  
##  <a name="construct"></a> allocator::construct  
 在指定值初始化的指定位址上，建構特定類型的物件。  
  
```  
void construct(pointer ptr, const Type& val);
void construct(pointer ptr, Type&& val);
template <class _Other>  
void construct(pointer ptr, _Other&&...   val);
```  
  
### <a name="parameters"></a>參數  
 `ptr`  
 要建構物件之位置的指標。  
  
 `val`  
 用來初始化所建構物件的值。  
  
### <a name="remarks"></a>備註  
 第一個成員函式相當於 **new** ((`void` \*) `ptr`) **Type** (`val`)。  
  
### <a name="example"></a>範例  
  
```cpp  
// allocator_construct.cpp  
// compile with: /EHsc  
#include <memory>  
#include <iostream>  
#include <algorithm>  
#include <vector>  
  
using namespace std;  
  
int main( )   
{  
   vector <int> v1;  
   vector <int>::iterator v1Iter;  
   vector <int>:: allocator_type v1Alloc;  
  
   int i;  
   for ( i = 1 ; i <= 7 ; i++ )  
   {  
      v1.push_back( 3 * i );  
   }  
  
   cout << "The original vector v1 is:\n ( " ;  
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ; v1Iter++ )  
      cout << *v1Iter << " ";  
   cout << ")." << endl;  
  
   allocator<int>::pointer v1PtrA;  
   int kA = 6, kB = 7;  
   v1PtrA = v1Alloc.address( *find( v1.begin( ), v1.end( ), kA ) );  
   v1Alloc.destroy ( v1PtrA );  
   v1Alloc.construct ( v1PtrA , kB );  
  
   cout << "The modified vector v1 is:\n ( " ;  
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ; v1Iter++ )  
      cout << *v1Iter << " ";  
   cout << ")." << endl;  
}  
```  
  
```Output  
The original vector v1 is:  
 ( 3 6 9 12 15 18 21 ).  
The modified vector v1 is:  
 ( 3 7 9 12 15 18 21 ).  
```  
  
##  <a name="deallocate"></a> allocator::deallocate  
 從指定位置起算的儲存體中，釋放指定數目的物件。  
  
```  
void deallocate(pointer ptr, size_type count);
```  
  
### <a name="parameters"></a>參數  
 `ptr`  
 要從儲存空間解除配置之第一個物件的指標。  
  
 `count`  
 要從儲存空間解除配置的物件數目。  
  
### <a name="remarks"></a>備註  
 成員函式釋放的計數類型的物件陣列的儲存體**類型**開始`ptr`，藉由呼叫`operator delete(ptr)`。 之前必須已傳回指標 `ptr`，方法是呼叫等於 **\*this** 之配置器物件的 [allocate](#allocate)，並配置相同大小和類型的陣列物件。 `deallocate` 絕不會擲回例外狀況。  
  
### <a name="example"></a>範例  
  如需使用成員函式的範例，請參閱 [allocator::allocate](#allocate)。  
  
##  <a name="destroy"></a> allocator::destroy  
 呼叫物件解構函式，而不取消配置儲存物件的記憶體。  
  
```  
void destroy(pointer ptr);
```  
  
### <a name="parameters"></a>參數  
 `ptr`  
 指定要終結之物件位址的指標。  
  
### <a name="remarks"></a>備註  
 成員函式所指定的物件已遭終結`ptr`，藉由呼叫解構函式`ptr->`**類型**::**~ 類型**。  
  
### <a name="example"></a>範例  
  
```cpp  
// allocator_destroy.cpp  
// compile with: /EHsc  
#include <memory>  
#include <iostream>  
#include <algorithm>  
#include <vector>  
  
using namespace std;  
  
int main( )   
{  
   vector <int> v1;  
   vector <int>::iterator v1Iter;  
   vector <int>:: allocator_type v1Alloc;  
  
   int i;  
   for ( i = 1 ; i <= 7 ; i++ )  
   {  
      v1.push_back( 2 * i );  
   }  
  
   cout << "The original vector v1 is:\n ( " ;  
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ; v1Iter++ )  
      cout << *v1Iter << " ";  
   cout << ")." << endl;  
  
   allocator<int>::pointer v1PtrA;  
   int kA = 12, kB = -99;  
   v1PtrA = v1Alloc.address( *find(v1.begin( ), v1.end( ), kA) );  
   v1Alloc.destroy ( v1PtrA );  
   v1Alloc.construct ( v1PtrA , kB );  
  
   cout << "The modified vector v1 is:\n ( " ;  
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ; v1Iter++ )  
      cout << *v1Iter << " ";  
   cout << ")." << endl;  
}  
```  
  
```Output  
The original vector v1 is:  
 ( 2 4 6 8 10 12 14 ).  
The modified vector v1 is:  
 ( 2 4 6 8 10 -99 14 ).  
```  
  
##  <a name="difference_type"></a> allocator::difference_type  
 帶正負號整數類型，可以表示配置器所管理的物件類型的指標值之間的差異。  
  
```  
typedef ptrdiff_t difference_type;  
```  
  
### <a name="remarks"></a>備註  
 此帶正負號整數類型所描述的物件可以代表序列中任兩個元素位址之間的差距，而範本類別配置器物件可以配置該序列。  
  
### <a name="example"></a>範例  
  
```cpp  
// allocator_diff_type.cpp  
// compile with: /EHsc  
#include <memory>  
#include <iostream>  
#include <vector>  
  
using namespace std;  
  
int main( )   
{  
   vector <int> v1;  
   vector <int>::iterator v1Iter;  
   vector <int>:: allocator_type v1Alloc;  
  
   int i;  
   for ( i = 0 ; i <= 7 ; i++ )  
   {  
      v1.push_back( i * 2 );  
   }  
  
   cout << "The original vector v1 is:\n ( " ;  
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ; v1Iter++ )  
      cout << *v1Iter << " ";  
   cout << ")." << endl;  
  
   allocator<int>::const_pointer v1PtrA, v1PtrB;  
   const int kA = 4, kB =12;  
   v1PtrA = v1Alloc.address( kA );  
   v1PtrB = v1Alloc.address( kB );  
   allocator<int>::difference_type v1diff = *v1PtrB - *v1PtrA;  
  
   cout << "Pointer v1PtrA addresses " << *v1PtrA << "." << endl;  
   cout << "Pointer v1PtrB addresses " << *v1PtrB <<  "." << endl;  
   cout << "The difference between the integer's addresses is: "  
        << v1diff << "." << endl;  
}  
```  
  
```Output  
The original vector v1 is:  
 ( 0 2 4 6 8 10 12 14 ).  
Pointer v1PtrA addresses 4.  
Pointer v1PtrB addresses 12.  
The difference between the integer's addresses is: 8.  
```  
  
##  <a name="max_size"></a> allocator::max_size  
 傳回在可用記憶體用完之前，無法由 allocator 類別的物件所配置之類型 **Type** 的元素數。  
  
```  
size_type max_size() const;
```  
  
### <a name="return-value"></a>傳回值  
 無法配置的元素數。  
  
### <a name="example"></a>範例  
  
```cpp  
// allocator_max_size.cpp  
// compile with: /EHsc  
#include <memory>  
#include <iostream>  
#include <vector>  
  
using namespace std;  
  
int main( )   
{  
   vector <int> v1;  
   vector <int>::iterator v1Iter;  
   vector <int>:: allocator_type v1Alloc;  
  
   int i;  
   for ( i = 1 ; i <= 7 ; i++ )  
   {  
      v1.push_back( i );  
   }  
  
   cout << "The original vector v1 is:\n ( " ;  
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ; v1Iter++ )  
      cout << *v1Iter << " ";  
   cout << ")." << endl;  
  
   vector <double> v2;  
   vector <double> ::iterator v2Iter;  
   vector <double> :: allocator_type v2Alloc;  
   allocator<int>::size_type v1size;  
   v1size = v1Alloc.max_size( );  
  
   cout << "The number of integers that can be allocated before\n"  
        << " the free memory in the vector v1 is used up is: "  
        << v1size << "." << endl;  
  
   int ii;  
   for ( ii = 1 ; ii <= 7 ; ii++ )  
   {  
      v2.push_back( ii * 10.0 );  
   }  
  
   cout << "The original vector v2 is:\n ( " ;  
   for ( v2Iter = v2.begin( ) ; v2Iter != v2.end( ) ; v2Iter++ )  
      cout << *v2Iter << " ";  
   cout << ")." << endl;  
   allocator<double>::size_type v2size;  
   v2size = v2Alloc.max_size( );  
  
   cout << "The number of doubles that can be allocated before\n"  
        << " the free memory in the vector v2 is used up is: "  
        << v2size << "." << endl;  
}  
```  
  
##  <a name="op_eq"></a> allocator::operator=  
 將一個配置器物件指派給另一個配置器物件。  
  
```  
template <class Other>  
allocator<Type>& operator=(const allocator<Other>& right);
```  
  
### <a name="parameters"></a>參數  
 `right`  
 要指派給另一個這類物件的配置器物件。  
  
### <a name="return-value"></a>傳回值  
 配置器物件的參考  
  
### <a name="remarks"></a>備註  
 範本指派運算子沒有作用。 不過，一般情況下，指派給另一個配置器物件的配置器物件應該與其相等，並允許在這兩個配置器物件之間混合進行物件配置和釋放。  
  
### <a name="example"></a>範例  
  
```cpp  
// allocator_op_assign.cpp  
// compile with: /EHsc  
#include <memory>  
#include <iostream>  
#include <vector>  
  
using namespace std;  
  
class Int {  
public:  
   Int(int i)   
   {  
      cout << "Constructing " << ( void* )this  << endl;   
      x = i;  
      bIsConstructed = true;  
   };  
   ~Int( ) {  
      cout << "Destructing " << ( void* )this << endl;   
      bIsConstructed = false;  
   };  
   Int &operator++( )   
   {  
      x++;  
      return *this;  
   };  
   int x;  
private:  
   bool bIsConstructed;  
};  
  
int main( )   
{  
   allocator<Int> Alloc;  
   allocator<Int> cAlloc ;  
   cAlloc = Alloc;      
}  
```  
  
##  <a name="pointer"></a> allocator::pointer  
 一種類型，可提供配置器管理之物件類型的指標。  
  
```  
typedef value_type *pointer;  
```  
  
### <a name="remarks"></a>備註  
 此指標類型所描述的物件 **ptr** 可以透過運算式 **\*ptr** 來指定範本類別配置器物件可配置的任何物件。  
  
### <a name="example"></a>範例  
  
```cpp  
// allocator_ptr.cpp  
// compile with: /EHsc  
#include <memory>  
#include <iostream>  
#include <vector>  
  
using namespace std;  
  
int main( )   
{  
   vector <int> v1;  
   vector <int>::iterator v1Iter;  
   vector <int>:: allocator_type v1Alloc;  
  
   int i;  
   for ( i = 1 ; i <= 7 ; i++ )  
   {  
      v1.push_back( 3 * i );  
   }  
  
   cout << "The original vector v1 is:\n ( " ;  
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ; v1Iter++ )  
      cout << *v1Iter << " ";  
   cout << ")." << endl;  
  
   allocator<int>::const_pointer v1Ptr;  
   const int k = 12;  
   v1Ptr = v1Alloc.address( k );  
  
   cout << "The integer addressed by v1Ptr has a value of: "  
        << "*v1Ptr = " << *v1Ptr << "." << endl;     
}  
```  
  
```Output  
The original vector v1 is:  
 ( 3 6 9 12 15 18 21 ).  
The integer addressed by v1Ptr has a value of: *v1Ptr = 12.  
```  
  
##  <a name="rebind"></a> allocator::rebind  
 一種結構，可讓某個類型的物件配置器，為另一種類型的物件配置儲存體。  
```  
struct rebind {    typedef allocator<_Other> other ;    };  
```  
### <a name="parameters"></a>參數  
 *other*  
 正在配置儲存空間的元素類型。  
  
### <a name="remarks"></a>備註  
 如果類型與所實作容器的元素類型不同，則此結構適用於配置這類類型的記憶體。  
  
 此成員範本類別會定義 other 類型。 其唯一目的是提供類型名稱 **allocator**\<_ **Other**>，但前提是類型名稱 **allocator**\< **Type**>。  
  
 例如，如果指定 **A**類型的 allocator 物件 **al**，您可以使用下列運算式來配置類型 **_Other** 的物件︰  
  
```  
A::rebind<Other>::other(al).allocate(1, (Other *)0)  
```  
  
 或者，您可以撰寫類型來命名其指標類型︰  
  
```  
A::rebind<Other>::other::pointer  
```  
  
### <a name="example"></a>範例  
  
```cpp  
// allocator_rebind.cpp  
// compile with: /EHsc  
#include <memory>  
#include <iostream>  
#include <algorithm>  
#include <vector>  
  
using namespace std;  
  
typedef vector<int>::allocator_type IntAlloc;  
int main( )   
{  
   IntAlloc v1Iter;  
   vector<int> v1;  
  
   IntAlloc::rebind<char>::other::pointer pszC =  
      IntAlloc::rebind<char>::other(v1.get_allocator()).allocate(1, (void *)0);  
  
   int * pInt = v1Iter.allocate(10);  
}  
```  
  
##  <a name="reference"></a> allocator::reference  
 一種類型，可提供配置器管理之物件類型的參考。  
  
```  
typedef value_type& reference;  
```  
  
### <a name="remarks"></a>備註  
 此參考類型所描述的物件可以指定範本類別配置器物件可配置的任何物件。  
  
### <a name="example"></a>範例  
  
```cpp  
// allocator_reference.cpp  
// compile with: /EHsc  
#include <memory>  
#include <iostream>  
#include <vector>  
  
using namespace std;  
  
int main( )   
{  
   vector <double> v;  
   vector <double> ::iterator vIter, vfIter;  
   vector <double> :: allocator_type vAlloc;  
  
   int j;  
   for ( j = 1 ; j <= 7 ; j++ )  
   {  
      v.push_back( 100.0 * j );  
   }  
  
   cout << "The original vector v is:\n ( " ;  
   for ( vIter = v.begin( ) ; vIter != v.end( ) ; vIter++ )  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   vfIter = v.begin( );  
   allocator<double>::reference vref =*vfIter;  
   cout << "The value of the element referred to by vref is: "  
        << vref << ",\n the first element in the vector." << endl;  
  
   // nonconst references can have their elements modified  
   vref = 150;  
   cout << "The element referred to by vref after being modified is: "  
        << vref << "." << endl;  
}  
```  
  
```Output  
The original vector v is:  
 ( 100 200 300 400 500 600 700 ).  
The value of the element referred to by vref is: 100,  
 the first element in the vector.  
The element referred to by vref after being modified is: 150.  
```  
  
##  <a name="size_type"></a> allocator::size_type  
 不帶正負號的整數類型，可以代表範本類別配置器物件可配置之任何序列的長度。  
  
```  
typedef size_t size_type;  
```  
  
### <a name="example"></a>範例  
  
```cpp  
// allocator_size_type.cpp  
// compile with: /EHsc  
#include <memory>  
#include <iostream>  
#include <vector>  
  
using namespace std;  
  
int main( )  
{  
   vector <double> v;  
   vector <double> ::iterator vIter;  
   vector <double> :: allocator_type vAlloc;  
  
   int j;  
   for ( j = 1 ; j <= 7 ; j++ )  
   {  
      v.push_back( 100.0 * j );  
   }  
  
   cout << "The original vector v is:\n ( " ;  
   for ( vIter = v.begin( ) ; vIter != v.end( ) ; vIter++ )  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   allocator<double>::size_type vsize;  
   vsize = vAlloc.max_size( );  
  
   cout << "The number of doubles that can be allocated before\n"  
        << " the free memory in the vector v is used up is: "  
        << vsize << "." << endl;  
}  
```  
  
##  <a name="value_type"></a> allocator::value_type  
 配置器所管理的類型。  
  
```  
typedef Type value_type;  
```  
  
### <a name="remarks"></a>備註  
 此類型是範本參數 **Type** 的同義字。  
  
### <a name="example"></a>範例  
  
```cpp  
// allocator_value_type.cpp  
// compile with: /EHsc  
#include <memory>  
#include <iostream>  
#include <vector>  
using namespace std;  
  
int main( )   
{  
   vector <double> v;  
   vector <double> ::iterator vIter, vfIter;  
   vector <double> :: allocator_type vAlloc;  
  
   int j;  
   for ( j = 1 ; j <= 7 ; j++ )  
   {  
      v.push_back( 100.0 * j );  
   }  
  
   cout << "The original vector v is:\n ( " ;  
   for ( vIter = v.begin( ) ; vIter != v.end( ) ; vIter++ )  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   vfIter = v.begin( );  
   allocator<double>::value_type vecVal = 150.0;  
 *vfIter = vecVal;  
   cout << "The value of the element addressed by vfIter is: "  
        << *vfIter << ",\n the first element in the vector." << endl;  
  
   cout << "The modified vector v is:\n ( " ;  
   for ( vIter = v.begin( ) ; vIter != v.end( ) ; vIter++ )  
      cout << *vIter << " ";  
   cout << ")." << endl;  
}  
```  
  
```Output  
The original vector v is:  
 ( 100 200 300 400 500 600 700 ).  
The value of the element addressed by vfIter is: 150,  
 the first element in the vector.  
The modified vector v is:  
 ( 150 200 300 400 500 600 700 ).  
```  
  
## <a name="see-also"></a>另請參閱  
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)


