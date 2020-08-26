---
title: allocator 類別
ms.date: 11/04/2016
f1_keywords:
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
helpviewer_keywords:
- std::allocator [C++]
- std::allocator [C++], const_pointer
- std::allocator [C++], const_reference
- std::allocator [C++], difference_type
- std::allocator [C++], pointer
- std::allocator [C++], reference
- std::allocator [C++], size_type
- std::allocator [C++], value_type
- std::allocator [C++], address
- std::allocator [C++], allocate
- std::allocator [C++], construct
- std::allocator [C++], deallocate
- std::allocator [C++], destroy
- std::allocator [C++], max_size
- std::allocator [C++], rebind
ms.assetid: 3fd58076-56cc-43bb-ad58-b4b7c9c6b410
ms.openlocfilehash: 4857de0b77d69a0d256da2200e5f4d0eb9d51c51
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88844817"
---
# <a name="allocator-class"></a>allocator 類別

類別樣板描述物件，該物件會管理類型之物件陣列的儲存配置和釋放 `Type` 。 類別的物件 `allocator` 是 c + + 標準程式庫中數個容器類別樣板的函式中所指定的預設配置器物件。

## <a name="syntax"></a>語法

```cpp
template <class Type>
class allocator
```

### <a name="parameters"></a>參數

*類型*\
正在配置或取消配置儲存體的物件類型。

## <a name="remarks"></a>備註

所有 c + + 標準程式庫容器都有一個預設為的範本參數 `allocator` 。 建構包含自訂配置器的容器可控制該容器之項目的配置與釋放。

例如，配置器物件可在私密堆積或共用記憶體中配置儲存體，或是可針對小型或大型物件最佳化。 它也能指定透過其提供的類型定義，透過管理共用記憶體的特殊存取子物件來存取項目，或是執行自動化記憶體回收。 因此，使用配置器物件來配置儲存區的類別，應該使用這些類型來宣告指標和參考物件，如 C++ 標準程式庫中的容器所做的一般。

<strong> 僅 (c + + 98/03) </strong> 當您從配置器類別衍生時，必須提供重新系 [結結構，](#rebind) 其 typedef 會 `_Other` 參考您新衍生的類別。

因此，配置器會定義下列類型：

- [指標](#pointer) 的行為就像是的指標 `Type` 。

- [const_pointer](#const_pointer) 的行為類似于的 const 指標 `Type` 。

- [參考](#reference) 的行為類似于的參考 `Type` 。

- [const_reference](#const_reference) 的行為就像是的 const 參考 `Type` 。

這些 `Type` 會指定指標和參考必須針對配置的元素採用的表單。  ( 配置器 [：:p ointer](#pointer) 不一定會與所有配置器 `Type*` 物件相同，即使它具有類別的這種明顯定義也一樣 `allocator` 。 ) 

**C++ 11 和更新版本：** 若要在您的配置器中啟用移動運算，請使用最小的配置器介面與實作複製建構函式、== 和 != 運算子、配置及解除配置。 如需詳細資訊和範例，請參閱[配置器](allocators.md)。

## <a name="members"></a>成員

### <a name="constructors"></a>建構函式

|名稱|描述|
|-|-|
|[allocator](#allocator)|建構函式可用來建立 `allocator` 物件。|

### <a name="typedefs"></a>Typedefs

|名稱|描述|
|-|-|
|[const_pointer](#const_pointer)|一種類型，可提供配置器管理之物件類型的常數指標。|
|[const_reference](#const_reference)|一種類型，可提供配置器管理之物件類型的常數參考。|
|[difference_type](#difference_type)|帶正負號整數類型，可以表示配置器所管理的物件類型的指標值之間的差異。|
|[指標](#pointer)|一種類型，可提供配置器管理之物件類型的指標。|
|[reference](#reference)|一種類型，可提供配置器管理之物件類型的參考。|
|[size_type](#size_type)|不帶正負號的整數類型，可以代表類型的物件可以配置之任何序列的長度 `allocator` 。|
|[value_type](#value_type)|配置器所管理的類型。|

### <a name="functions"></a>Functions

|名稱|描述|
|-|-|
|[address](#address)|尋找指定值所屬物件的位址。|
|[分配](#allocate)|配置夠大的記憶體區塊，至少儲存某些指定的項目數。|
|[建構](#construct)|在指定值初始化的指定位址上，建構特定類型的物件。|
|[解除](#deallocate)|從指定位置起算的儲存體中，釋放指定數目的物件。|
|[摧毀](#destroy)|呼叫物件解構函式，而不取消配置儲存物件的記憶體。|
|[max_size](#max_size)|傳回在可用記憶體用完之前，無法由類別 `allocator`的物件配置之類型 `Type` 的項目數量。|
|[rebind](#rebind)|一種結構，可讓某個類型的物件配置器，為另一種類型的物件配置儲存體。|

### <a name="operators"></a>運算子

|名稱|描述|
|-|-|
|[運算子 =](#op_eq)|將一個 `allocator` 物件指派給另一個 `allocator` 物件。|

### <a name="address"></a><a name="address"></a> 位址

尋找指定值所屬物件的位址。

```cpp
pointer address(reference val) const;
const_pointer address(const_reference val) const;
```

#### <a name="parameters"></a>參數

*瓦爾*\
搜尋其位址之物件的 const 或 nonconst 值。

#### <a name="return-value"></a>傳回值

分別針對 const 或 nonconst 值找到之物件的 const 或 nonconst 指標。

#### <a name="remarks"></a>備註

成員函式會傳回 *val*的位址，其格式為指標必須針對配置的元素採取的形式。

#### <a name="example"></a>範例

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

### <a name="allocate"></a><a name="allocate"></a> 分配

配置夠大的記憶體區塊，至少儲存某些指定的項目數。

```cpp
pointer allocate(size_type count, const void* _Hint);
```

#### <a name="parameters"></a>參數

*count*\
要配置足夠儲存體的項目數。

*_Hint*\
const 指標，可找出要求之前所配置物件的位址，來協助配置器物件符合儲存要求。

#### <a name="return-value"></a>傳回值

所配置物件的指標，如果未配置記憶體，則為 Null。

#### <a name="remarks"></a>備註

成員函式會藉 `Type` 由呼叫 operator new (*count*) ，為型別的 count 元素陣列配置儲存區。 它會傳回所配置物件的指標。 提示引數可協助部分配置器改善參考區域性；有效的選擇是相同配置器物件稍早所配置但尚未解除配置之物件的位址。 若不要提供提示，請改用 Null 指標引數。

#### <a name="example"></a>範例

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

### <a name="allocator"></a><a name="allocator"></a> 分配器

建構函式用來建立配置器物件。

```cpp
allocator();
allocator(const allocator<Type>& right);
template <class Other>
    allocator(const allocator<Other>& right);
```

#### <a name="parameters"></a>參數

*對*\
要複製的配置器物件。

#### <a name="remarks"></a>備註

建構函式不會執行任何動作。 不過，一般情況下，從另一個配置器物件建構的配置器物件應該與其相等，並允許在這兩個配置器物件之間混合進行物件配置和釋放。

#### <a name="example"></a>範例

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

### <a name="const_pointer"></a><a name="const_pointer"></a> const_pointer

一種類型，可提供配置器管理之物件類型的常數指標。

```cpp
typedef const value_type *const_pointer;
```

#### <a name="remarks"></a>備註

指標類型所描述的物件， `ptr` 可透過運算式指定 `*ptr` 類型物件可配置的任何 const 物件 `allocator` 。

#### <a name="example"></a>範例

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

### <a name="const_reference"></a><a name="const_reference"></a> const_reference

一種類型，可提供配置器管理之物件類型的常數參考。

```cpp
typedef const value_type& const_reference;
```

#### <a name="remarks"></a>備註

參考型別描述的物件可以指定類型物件可以配置的任何 const 物件 `allocator` 。

#### <a name="example"></a>範例

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

### <a name="construct"></a><a name="construct"></a> 構建

在指定值初始化的指定位址上，建構特定類型的物件。

```cpp
void construct(pointer ptr, const Type& val);
void construct(pointer ptr, Type&& val);
template <class _Other>
    void construct(pointer ptr, _Other&&... val);
```

#### <a name="parameters"></a>參數

*Ptr*\
要建構物件之位置的指標。

*瓦爾*\
用來初始化所建構物件的值。

#### <a name="remarks"></a>備註

第一個成員函式相當於 `new ((void *) ptr) Type(val)` 。

#### <a name="example"></a>範例

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

### <a name="deallocate"></a><a name="deallocate"></a> 解除

從指定位置起算的儲存體中，釋放指定數目的物件。

```cpp
void deallocate(pointer ptr, size_type count);
```

#### <a name="parameters"></a>參數

*Ptr*\
要從儲存空間解除配置之第一個物件的指標。

*count*\
要從儲存空間解除配置的物件數目。

#### <a name="remarks"></a>備註

成員函式會藉 `Type` 由呼叫來釋出型別之 count 物件*ptr*的儲存區 `operator delete(ptr)` 。 *指標指標必須先由*配置的呼叫所傳回，此[配置](#allocate)器物件會比較等於** \* this**，配置相同大小和類型的陣列物件。 `deallocate` 絕不會擲回例外狀況。

#### <a name="example"></a>範例

如需使用成員函式的範例，請參閱 [allocator::allocate](#allocate)。

### <a name="destroy"></a><a name="destroy"></a> 摧毀

呼叫物件解構函式，而不取消配置儲存物件的記憶體。

```cpp
void destroy(pointer ptr);
```

#### <a name="parameters"></a>參數

*Ptr*\
指定要終結之物件位址的指標。

#### <a name="remarks"></a>備註

成員函式會藉由呼叫函式來終結由 *ptr*指定的物件 `ptr->Type::~Type` 。

#### <a name="example"></a>範例

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

### <a name="difference_type"></a><a name="difference_type"></a> difference_type

帶正負號整數類型，可以表示配置器所管理的物件類型的指標值之間的差異。

```cpp
typedef ptrdiff_t difference_type;
```

#### <a name="remarks"></a>備註

帶正負號的整數類型所描述的物件，可以代表類型的物件可以配置的序列中，任何兩個元素的位址之間的差異 `allocator` 。

#### <a name="example"></a>範例

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

### <a name="max_size"></a><a name="max_size"></a> max_size

傳回在可用記憶體用完之前，無法由類別配置器的物件配置之類型 `Type` 的元素數。

```cpp
size_type max_size() const;
```

#### <a name="return-value"></a>傳回值

無法配置的元素數。

#### <a name="example"></a>範例

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

### <a name="operator"></a><a name="op_eq"></a> 運算子 =

將一個配置器物件指派給另一個配置器物件。

```cpp
template <class Other>
    allocator<Type>& operator=(const allocator<Other>& right);
```

#### <a name="parameters"></a>參數

*對*\
要指派給另一個這類物件的配置器物件。

#### <a name="return-value"></a>傳回值

配置器物件的參考

#### <a name="remarks"></a>備註

範本指派運算子沒有作用。 不過，一般情況下，指派給另一個配置器物件的配置器物件應該與其相等，並允許在這兩個配置器物件之間混合進行物件配置和釋放。

#### <a name="example"></a>範例

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

### <a name="pointer"></a><a name="pointer"></a> 指標

一種類型，可提供配置器管理之物件類型的指標。

```cpp
typedef value_type *pointer;
```

#### <a name="remarks"></a>備註

指標類型所描述的物件， `ptr` 可以透過運算式** \* ptr**來指定，也就是類型物件可以配置的任何物件 `allocator` 。

#### <a name="example"></a>範例

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

   cout << "The original vector v1 is:\n( " ;
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

### <a name="rebind"></a><a name="rebind"></a> 再次

一種結構，可讓某個類型的物件配置器，為另一種類型的物件配置儲存體。

```cpp
struct rebind { typedef allocator<_Other> other; };
```

#### <a name="parameters"></a>參數

*其他*\
正在配置儲存空間的元素類型。

#### <a name="remarks"></a>備註

如果類型與所實作容器的元素類型不同，則此結構適用於配置這類類型的記憶體。

成員類別範本會定義其他類型。 其唯一目的是提供型別名稱 `allocator<_Other>` ，並指定型別名稱 `allocator<Type>` 。

例如，假設有一個 `al` 型別的配置器物件 `A` ，您可以使用運算式來配置類型的物件 `_Other` ：

```cpp
A::rebind<Other>::other(al).allocate(1, (Other *)0)
```

或者，您可以撰寫類型來命名其指標類型︰

```cpp
A::rebind<Other>::other::pointer
```

#### <a name="example"></a>範例

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

### <a name="reference"></a><a name="reference"></a> 參考

一種類型，可提供配置器管理之物件類型的參考。

```cpp
typedef value_type& reference;
```

#### <a name="remarks"></a>備註

參考型別描述的物件可以指定類型物件可以配置的任何物件 `allocator` 。

#### <a name="example"></a>範例

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

### <a name="size_type"></a><a name="size_type"></a> size_type

不帶正負號的整數類型，可以代表類型的物件可以配置之任何序列的長度 `allocator` 。

```cpp
typedef size_t size_type;
```

#### <a name="example"></a>範例

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

### <a name="value_type"></a><a name="value_type"></a> value_type

配置器所管理的類型。

```cpp
typedef Type value_type;
```

#### <a name="remarks"></a>備註

此類型是樣板參數 `Type` 的同義字。

#### <a name="example"></a>範例

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

## <a name="helpers"></a>協助程式

### <a name="allocator_arg_t"></a><a name="allocator_arg_t"></a> allocator_arg_t

```cpp
struct allocator_arg_t { explicit allocator_arg_t() = default; };
inline constexpr allocator_arg_t allocator_arg{};
```

### <a name="uses_allocator"></a><a name="uses_allocator"></a> uses_allocator

```cpp
template <class T, class Alloc> struct uses_allocator;
```
