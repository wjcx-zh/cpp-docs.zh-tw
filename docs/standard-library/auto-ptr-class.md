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
ms.openlocfilehash: 7e652b18b723e2a58c1f4673baf180a14db93477
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88834774"
---
# <a name="auto_ptr-class"></a>auto_ptr 類別

以智慧型指標包裝資源，確保當控制離開區塊時，會自動終結該資源。

更適用的 `unique_ptr` 類別會取代 `auto_ptr`。 如需詳細資訊，請參閱 [unique_ptr 類別](../standard-library/unique-ptr-class.md)。

如需 `throw()` 和例外狀況處理的詳細資訊，請參閱[例外狀況規格 (throw)](../cpp/exception-specifications-throw-cpp.md)。

## <a name="syntax"></a>語法

```cpp
class auto_ptr {
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

*對*\
要從中取得現有資源的 `auto_ptr`。

*Ptr*\
此指標指定了要取代的已儲存指標。

## <a name="remarks"></a>備註

類別樣板會將智慧型指標（稱為）描述 `auto_ptr` 為已配置的物件。 指標必須是 null 或指定由配置的物件 **`new`** 。 如果將 `auto_ptr` 的儲存值指派給另一個物件，則會轉移擁有權。  (它會在以 null 指標傳送後取代儲存的值。 ) 的函式可刪除已配置 `auto_ptr<Type>` 的物件。 `auto_ptr<Type>` 可確保當控制離開區塊時 (即使是透過擲回例外狀況)，會自動刪除配置物件。 您不應該建構兩個擁有相同物件的 `auto_ptr<Type>` 物件。

您可以將 `auto_ptr<Type>` 物件當做函式呼叫的引數，以傳值方式來傳遞。 `auto_ptr` 不能是任何標準程式庫容器的項目。 您無法透過 C++ 標準程式庫容器可靠地管理一系列的 `auto_ptr<Type>` 物件。

## <a name="members"></a>成員

### <a name="constructors"></a>建構函式

|名稱|描述|
|-|-|
|[auto_ptr](#auto_ptr)|`auto_ptr` 類型物件的建構函式。|

### <a name="typedefs"></a>Typedefs

|名稱|描述|
|-|-|
|[element_type](#element_type)|此類型是樣板參數 `Type` 的同義字。|

### <a name="functions"></a>Functions

|名稱|描述|
|-|-|
|[get](#get)|這個成員函式會傳回儲存的指標 `myptr`。|
|[釋放](#release)|這個成員會以 null 指標取代儲存的指標 `myptr`，並傳回先前儲存的指標。|
|[reset](#reset)|這個成員函式只有在儲存的指標值 `myptr` 因函式呼叫而變更時，才會評估運算式 `delete myptr`。 它接著會將儲存的指標取代為 *ptr*。|

### <a name="operators"></a>運算子

|名稱|描述|
|-|-|
|[運算子 =](#op_eq)|指派運算子，將擁有權從一個 `auto_ptr` 物件轉移至另一個物件。|
|[運算子](#op_star)|`auto_ptr` 類型物件的取值運算子。|
|[運算子->](#op_arrow)|允許成員存取的運算子。|
|[operator auto_ptr\<Other>](#op_auto_ptr_lt_other_gt)|從一種 `auto_ptr` 轉換成另一種 `auto_ptr`。|
|[operator auto_ptr_ref\<Other>](#op_auto_ptr_ref_lt_other_gt)|從 `auto_ptr` 轉換成 `auto_ptr_ref`。|

### <a name="auto_ptr"></a><a name="auto_ptr"></a> auto_ptr

`auto_ptr` 類型物件的建構函式。

```cpp
explicit auto_ptr(Type* ptr  = 0) throw();

auto_ptr(auto_ptr<Type>& right) throw();

auto_ptr(auto _ptr_ref<Type> right) throw();

template <class Other>
auto _ptr(auto _ptr<Other>& right) throw();
```

#### <a name="parameters"></a>參數

*Ptr*\
`auto_ptr` 所封裝物件的指標。

*對*\
要由建構函式所複製的 `auto_ptr` 物件。

#### <a name="remarks"></a>備註

第一個函式會在中儲存 *ptr* `myptr` ，將指標儲存至配置的物件。 第二個函式會藉由儲存*right*來轉移儲存在*右方*的指標擁有權。 在中[發行](#release) `myptr` 。

第三個函式的行為與第二個相同，不同之處在于它會儲存 `right` 。 `ref`. `release` 在中 `myptr` ，其中 `ref` 是儲存在中的參考 `right` 。

範本函式的行為與第二個函式相同，前提是可以隱含地將指標 `Other` 轉換成的指標 `Type` 。

#### <a name="example"></a>範例

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

### <a name="element_type"></a><a name="element_type"></a> element_type

此類型是樣板參數 `Type` 的同義字。

```cpp
typedef Type element  _type;
```

### <a name="get"></a><a name="get"></a> 獲取

這個成員函式會傳回儲存的指標 `myptr`。

```cpp
Type *get() const throw();
```

#### <a name="return-value"></a>傳回值

儲存的指標 `myptr` 。

#### <a name="example"></a>範例

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

### <a name="operator"></a><a name="op_eq"></a> 運算子 =

指派運算子，將擁有權從一個 `auto_ptr` 物件轉移至另一個物件。

```cpp
template <class Other>
    auto_ptr<Type>& operator=(auto_ptr<Other>& right) throw();
auto_ptr<Type>& operator=(auto_ptr<Type>& right) throw();
auto_ptr<Type>& operator=(auto_ptr_ref<Type> right) throw();
```

#### <a name="parameters"></a>參數

*對*\
`auto_ptr` 類型的物件。

#### <a name="return-value"></a>傳回值

類型為 `auto_ptr<Type>` 之物件的參考。

#### <a name="remarks"></a>備註

指派會評估運算式 `delete myptr` ，但只有在儲存的指標因指派而變更時才會評估 `myptr` 。 然後，它會將儲存在 *右方*的指標擁有權儲存在 *右側*。在中[發行](#release) `myptr` 。 函數會傳回__ \* 這個__。

#### <a name="example"></a>範例

如需使用成員運算子的範例，請參閱 [auto_ptr](#auto_ptr)。

### <a name="operator"></a><a name="op_star"></a> 運算子

`auto_ptr` 類型物件的取值運算子。

```cpp
Type& operator*() const throw();
```

#### <a name="return-value"></a>傳回值

指標所擁有之類型物件的參考 `Type` 。

#### <a name="remarks"></a>備註

間接取值運算子會傳回 `*`[get](#get)。 因此，儲存的指標不能是 null。

#### <a name="example"></a>範例

如需如何使用成員函式的範例，請參閱 [auto_ptr](#auto_ptr)。

### <a name="operator-gt"></a><a name="op_arrow"></a> 運算子&gt;

允許成員存取的運算子。

```cpp
Type * operator->() const throw();
```

#### <a name="return-value"></a>傳回值

擁有之物件的成員 `auto_ptr` 。

#### <a name="remarks"></a>備註

選取運算子會傳回[get](#get) `( )` ，如此一來，運算式*ap* ->  **成員**的行為會與 ( *ap*相同。 **取得** ( ) ) >**成員**，其中的*ap*是類別的物件 `auto_ptr` \< **Type**> 。 因此，儲存的指標不得為 null，而且 `Type` 必須是具有成員的類別、結構或等位類型 `member` 。

#### <a name="example"></a>範例

如需如何使用成員函式的範例，請參閱 [auto_ptr](#auto_ptr)。

### <a name="operator-auto_ptrltothergt"></a><a name="op_auto_ptr_lt_other_gt"></a> 運算子 auto_ptr &lt; 其他&gt;

從一種 `auto_ptr` 轉換成另一種 `auto_ptr`。

```cpp
template <class Other>
operator auto _ptr<Other>() throw();
```

#### <a name="return-value"></a>傳回值

類型轉換運算子會傳回 `auto_ptr` \< **Other**> ( ** \* 這個**) 。

#### <a name="example"></a>範例

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

### <a name="operator-auto_ptr_refltothergt"></a><a name="op_auto_ptr_ref_lt_other_gt"></a> 運算子 auto_ptr_ref &lt; 其他&gt;

從 `auto_ptr` 轉換成 `auto_ptr_ref`。

```cpp
template <class Other>
operator auto _ptr  _ref<Other>() throw();
```

#### <a name="return-value"></a>傳回值

類型轉換運算子會傳回**auto_ptr_ref** \< **Other**> ** \* 此**)  ( auto_ptr_ref。

#### <a name="example"></a>範例

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

### <a name="release"></a><a name="release"></a> 釋放

這個成員會以 null 指標取代儲存的指標 `myptr`，並傳回先前儲存的指標。

```cpp
Type *release() throw();
```

#### <a name="return-value"></a>傳回值

之前儲存的指標。

#### <a name="remarks"></a>備註

這個成員會以 null 指標取代儲存的指標 `myptr`，並傳回先前儲存的指標。

#### <a name="example"></a>範例

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

### <a name="reset"></a><a name="reset"></a> 重 置

成員函式會評估運算式 `delete myptr` ，但只有在儲存的指標值 `myptr` 因為函式呼叫的結果而變更時才會評估。 然後會以 `ptr` 取代儲存的指標。

```cpp
void reset(Type* ptr = 0);
```

#### <a name="parameters"></a>參數

*Ptr*\
指定要取代儲存之指標的指標 `myptr` 。

#### <a name="example"></a>範例

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

[unique_ptr 類別](../standard-library/unique-ptr-class.md)
