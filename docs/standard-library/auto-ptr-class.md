---
title: auto_ptr 類別
ms.date: 11/04/2016
f1_keywords:
- memory/std::auto_ptr
- memory/std::auto_ptr::element_type
- memory/std::auto_ptr::get
- memory/std::auto_ptr::release
- memory/std::auto_ptr::reset
helpviewer_keywords:
- std::auto_ptr [C++]
- std::auto_ptr [C++], element_type
- std::auto_ptr [C++], get
- std::auto_ptr [C++], release
- std::auto_ptr [C++], reset
ms.assetid: 7f9108b6-9eb3-4634-b615-cf7aa814f23b
ms.openlocfilehash: 587168323b8af63d232b8df63e9dcac2f4601433
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50620944"
---
# <a name="autoptr-class"></a>auto_ptr 類別

以智慧型指標包裝資源，確保當控制離開區塊時，會自動終結該資源。

更適用的 `unique_ptr` 類別會取代 `auto_ptr`。 如需詳細資訊，請參閱 [unique_ptr 類別](../standard-library/unique-ptr-class.md)。

如需 `throw()` 和例外狀況處理的詳細資訊，請參閱[例外狀況規格 (throw)](../cpp/exception-specifications-throw-cpp.md)。

## <a name="syntax"></a>語法

```cpp
class auto_ptr {
public:
    typedef Type element_type;
    explicit auto_ptr(Type* ptr = 0) throw();
    auto_ptr(auto_ptr<Type>& right) throw()
        ;
    template <class Other>
    operator auto_ptr<Other>() throw();
    template <class Other>
    auto_ptr<Type>& operator=(auto_ptr<Other>& right) throw();
    template <class Other>
    auto_ptr(auto_ptr<Other>& right);
    auto_ptr<Type>& operator=(auto_ptr<Type>& right);
    ~auto_ptr();
    Type& operator*() const throw();
    Type * operator->()const throw();
    Type *get() const throw();
    Type *release()throw();
    void reset(Type* ptr = 0);
};
```

### <a name="parameters"></a>參數

*right*<br/>
要從中取得現有資源的 `auto_ptr`。

*ptr*<br/>
此指標指定了要取代的已儲存指標。

## <a name="remarks"></a>備註

此範本類別描述一個智慧型指標，呼叫`auto_ptr`，配置的物件。 滑鼠指標必須是 null，或指定所配置的物件**新**。 如果將 `auto_ptr` 的儲存值指派給另一個物件，則會轉移擁有權。 (轉移後，會以 null 指標取代儲存值。)`auto_ptr<Type>` 的解構函式會刪除配置物件。 `auto_ptr<Type>` 可確保當控制離開區塊時 (即使是透過擲回例外狀況)，會自動刪除配置物件。 您不應該建構兩個擁有相同物件的 `auto_ptr<Type>` 物件。

您可以將 `auto_ptr<Type>` 物件當做函式呼叫的引數，以傳值方式來傳遞。 `auto_ptr` 不能是任何標準程式庫容器的項目。 您無法透過 C++ 標準程式庫容器可靠地管理一系列的 `auto_ptr<Type>` 物件。

## <a name="members"></a>成員

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[auto_ptr](#auto_ptr)|`auto_ptr` 類型物件的建構函式。|

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|[element_type](#element_type)|此類型是範本參數 `Type`的同義字。|

### <a name="member-functions"></a>成員函式

|成員函式|描述|
|-|-|
|[get](#get)|這個成員函式會傳回儲存的指標 `myptr`。|
|[release](#release)|這個成員會以 null 指標取代儲存的指標 `myptr`，並傳回先前儲存的指標。|
|[reset](#reset)|這個成員函式只有在儲存的指標值 `myptr` 因函式呼叫而變更時，才會評估運算式 `delete myptr`。 它接著會將儲存的指標取代為 *ptr*。|

### <a name="operators"></a>運算子

|運算子|描述|
|-|-|
|[operator=](#op_eq)|指派運算子，將擁有權從一個 `auto_ptr` 物件轉移至另一個物件。|
|[operator*](#op_star)|`auto_ptr` 類型物件的取值運算子。|
|[operator->](#op_arrow)|允許成員存取的運算子。|
|[operator auto_ptr\<Other>](#op_auto_ptr_lt_other_gt)|從一種 `auto_ptr` 轉換成另一種 `auto_ptr`。|
|[operator auto_ptr_ref\<Other>](#op_auto_ptr_ref_lt_other_gt)|從 `auto_ptr` 轉換成 `auto_ptr_ref`。|

## <a name="requirements"></a>需求

**標頭：**\<memory>

**命名空間：** std

## <a name="auto_ptr"></a> auto_ptr::auto_ptr

`auto_ptr` 類型物件的建構函式。

```cpp
explicit auto_ptr(Type* ptr  = 0) throw();

auto_ptr(auto_ptr<Type>& right) throw();

auto_ptr(auto _ptr_ref<Type> right) throw();

template <class Other>
auto _ptr(auto _ptr<Other>& right) throw();
```

### <a name="parameters"></a>參數

*ptr*<br/>
`auto_ptr` 所封裝物件的指標。

*right*<br/>
要由建構函式所複製的 `auto_ptr` 物件。

### <a name="remarks"></a>備註

第一個建構函式儲存*ptr*在`myptr`，儲存所配置物件的指標。 第二個建構函式將儲存在指標的擁有權*右*，藉由儲存*右*。 [釋放](#release)在`myptr`。

第三個建構函式行為與第二個，相同，不同之處在於它會儲存`right`。 `ref`. `release` 在  `myptr`，其中`ref`會參考儲存在`right`。

範本建構函式的行為相同的第二個建構函式，前提是指標`Other`能夠隱含轉換成指標`Type`。

### <a name="example"></a>範例

```cpp
// auto_ptr_auto_ptr.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

class Int
{
public:
   Int(int i)
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

void function ( auto_ptr<Int> &pi )
{
   ++( *pi );
   auto_ptr<Int> pi2( pi );
   ++( *pi2 );
   pi = pi2;
}

int main( )
{
   auto_ptr<Int> pi ( new Int( 5 ) );
   cout << pi->x << endl;
   function( pi );
   cout << pi->x << endl;
}
```

```Output
Constructing 00311AF8
5
7
Destructing 00311AF8
```

## <a name="element_type"></a> auto_ptr::element_type

此類型是範本參數 `Type`的同義字。

```cpp

typedef Type element  _type;
```

## <a name="get"></a> auto_ptr::get

這個成員函式會傳回儲存的指標 `myptr`。

```cpp
Type *get() const throw();
```

### <a name="return-value"></a>傳回值

已儲存的指標`myptr`。

### <a name="example"></a>範例

```cpp
// auto_ptr_get.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>
using namespace std;

class Int
{
public:
   Int(int i)
   {
      x = i;
      cout << "Constructing " << ( void* )this  << " Value: " << x << endl;
   };
   ~Int( )
   {
      cout << "Destructing " << ( void* )this << " Value: " << x << endl;
   };

   int x;

};

int main( )
{
   auto_ptr<Int> pi ( new Int( 5 ) );
   pi.reset( new Int( 6 ) );
   Int* pi2 = pi.get ( );
   Int* pi3 = pi.release ( );
   if (pi2 == pi3)
      cout << "pi2 == pi3" << endl;
   delete pi3;
}
```

```Output
Constructing 00311AF8 Value: 5
Constructing 00311B88 Value: 6
Destructing 00311AF8 Value: 5
pi2 == pi3
Destructing 00311B88 Value: 6
```

## <a name="op_eq"></a> auto_ptr::operator=

指派運算子，將擁有權從一個 `auto_ptr` 物件轉移至另一個物件。

```cpp
template <class Other>
auto_ptr<Type>& operator=(auto_ptr<Other>& right) throw();
auto_ptr<Type>& operator=(auto_ptr<Type>& right) throw();
auto_ptr<Type>& operator=(auto_ptr_ref<Type> right) throw();
```

### <a name="parameters"></a>參數

*right*<br/>
`auto_ptr` 類型的物件。

### <a name="return-value"></a>傳回值

`auto_ptr`\< **Type**> 類型之物件的參考。

### <a name="remarks"></a>備註

指派才會評估運算式`delete myptr`，但只有當已儲存的指標`myptr`因指派而變更。 它接著會儲存 \_*Right*，以轉移 _*Right* 中所儲存指標的擁有權。 [釋放](#release)在`myptr`。 此函式會傳回 **\*this**。

### <a name="example"></a>範例

如需成員運算子的使用範例，請參閱 [auto_ptr::auto_ptr](#auto_ptr)。

## <a name="op_star"></a> auto_ptr::operator*

`auto_ptr` 類型物件的取值運算子。

```cpp
Type& operator*() const throw();
```

### <a name="return-value"></a>傳回值

型別的物件的參考`Type`指標所擁有。

### <a name="remarks"></a>備註

間接取值運算子會傳回 `*`[get](#get)。 因此，儲存的指標不得為 Null。

### <a name="example"></a>範例

如需成員函式用法的範例，請參閱 [auto_ptr::auto_ptr](#auto_ptr)。

## <a name="op_arrow"></a> auto_ptr::operator-&gt;

允許成員存取的運算子。

```cpp
Type * operator->() const throw();
```

### <a name="return-value"></a>傳回值

物件的成員，`auto_ptr`擁有。

### <a name="remarks"></a>備註

選取運算子會傳回 [get](#get)`( )`，如此一來，運算式 *ap*-> **member** 的運作方式會與下列運算式相同：(*ap*. **get**( ) )-> **member**，其中 *ap* 是類別 `auto_ptr`\< **Type**> 的物件。 因此，儲存的指標不得為 null，並`Type`必須是類別、 結構或等位型別與`member`成員。

### <a name="example"></a>範例

如需成員函式用法的範例，請參閱 [auto_ptr::auto_ptr](#auto_ptr)。

## <a name="op_auto_ptr_lt_other_gt"></a> auto_ptr::operator auto_ptr&lt;Other&gt;

從一種 `auto_ptr` 轉換成另一種 `auto_ptr`。

```cpp
template <class Other>
operator auto _ptr<Other>() throw();
```

### <a name="return-value"></a>傳回值

類型轉型運算子會傳回 `auto_ptr` \< **Other**>( **\*this**)。

### <a name="example"></a>範例

```cpp
// auto_ptr_op_auto_ptr.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;
int main()
{
   auto_ptr<int> pi ( new int( 5 ) );
   auto_ptr<const int> pc = ( auto_ptr<const int> )pi;
}
```

## <a name="op_auto_ptr_ref_lt_other_gt"></a> auto_ptr::operator auto_ptr_ref&lt;Other&gt;

從 `auto_ptr` 轉換成 `auto_ptr_ref`。

```cpp
template <class Other>
operator auto _ptr  _ref<Other>() throw();
```

### <a name="return-value"></a>傳回值

類型轉型運算子會傳回 **auto_ptr_ref**\< **Other**>( **\*this**)。

### <a name="example"></a>範例

```cpp
// auto_ptr_op_auto_ptr_ref.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

class C {
public:
    C(int _i) : m_i(_i) {
    }
    ~C() {
        cout << "~C:  " << m_i << "\n";
    }
    C &operator =(const int &x) {
        m_i = x;
        return *this;
    }
    int m_i;
};
void f(auto_ptr<C> arg) {
};
int main()
{
    const auto_ptr<C> ciap(new C(1));
    auto_ptr<C> iap(new C(2));

    // Error: this implies transfer of ownership of iap's pointer
    // f(ciap);
    f(iap); // compiles, but gives up ownership of pointer

            // here, iap owns a destroyed pointer so the following is bad:
            // *iap = 5; // BOOM

    cout << "main exiting\n";
}
```

```Output
~C:  2
main exiting
~C:  1
```

## <a name="release"></a> auto_ptr::release

這個成員會以 null 指標取代儲存的指標 `myptr`，並傳回先前儲存的指標。

```cpp
Type *release() throw();
```

### <a name="return-value"></a>傳回值

之前儲存的指標。

### <a name="remarks"></a>備註

這個成員會以 null 指標取代儲存的指標 `myptr`，並傳回先前儲存的指標。

### <a name="example"></a>範例

```cpp
// auto_ptr_release.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>
using namespace std;

class Int
{
public:
    Int(int i)
    {
        x = i;
        cout << "Constructing " << (void*)this << " Value: " << x << endl;
    };
    ~Int() {
        cout << "Destructing " << (void*)this << " Value: " << x << endl;
    };

    int x;

};

int main()
{
    auto_ptr<Int> pi(new Int(5));
    pi.reset(new Int(6));
    Int* pi2 = pi.get();
    Int* pi3 = pi.release();
    if (pi2 == pi3)
        cout << "pi2 == pi3" << endl;
    delete pi3;
}
```

```Output
Constructing 00311AF8 Value: 5
Constructing 00311B88 Value: 6
Destructing 00311AF8 Value: 5
pi2 == pi3
Destructing 00311B88 Value: 6
```

## <a name="reset"></a> auto_ptr::reset

此成員函式評估的運算式`delete myptr`，但只有當儲存的指標值`myptr`函式呼叫而變更。 然後會以 `ptr` 取代儲存的指標。

```cpp
void reset(Type* ptr = 0);
```

### <a name="parameters"></a>參數

*ptr*<br/>
此指標指定成取代儲存的指標`myptr`。

### <a name="example"></a>範例

```cpp
// auto_ptr_reset.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

class Int
{
public:
    Int(int i)
    {
        x = i;
        cout << "Constructing " << (void*)this << " Value: " << x << endl;
    };
    ~Int()
    {
        cout << "Destructing " << (void*)this << " Value: " << x << endl;
    };

    int x;
};

int main()
{
    auto_ptr<Int> pi(new Int(5));
    pi.reset(new Int(6));
    Int* pi2 = pi.get();
    Int* pi3 = pi.release();
    if (pi2 == pi3)
        cout << "pi2 == pi3" << endl;
    delete pi3;
}
```

```Output
Constructing 00311AF8 Value: 5
Constructing 00311B88 Value: 6
Destructing 00311AF8 Value: 5
pi2 == pi3
Destructing 00311B88 Value: 6
```

## <a name="see-also"></a>另請參閱

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[unique_ptr 類別](../standard-library/unique-ptr-class.md)<br/>
