---
title: shared_ptr 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- memory/std::shared_ptr
- memory/std::shared_ptr::element_type
- memory/std::shared_ptr::get
- memory/std::shared_ptr::owner_before
- memory/std::shared_ptr::reset
- memory/std::shared_ptr::swap
- memory/std::shared_ptr::unique
- memory/std::shared_ptr::use_count
- memory/std::shared_ptr::operator boolean-type
- memory/std::shared_ptr::operator*
- memory/std::shared_ptr::operator=
- memory/std::shared_ptr::operator->
dev_langs:
- C++
helpviewer_keywords:
- std::shared_ptr [C++]
- std::shared_ptr [C++], element_type
- std::shared_ptr [C++], get
- std::shared_ptr [C++], owner_before
- std::shared_ptr [C++], reset
- std::shared_ptr [C++], swap
- std::shared_ptr [C++], unique
- std::shared_ptr [C++], use_count
- std::shared_ptr [C++], element_type
- std::shared_ptr [C++], get
- std::shared_ptr [C++], owner_before
- std::shared_ptr [C++], reset
- std::shared_ptr [C++], swap
- std::shared_ptr [C++], unique
- std::shared_ptr [C++], use_count
ms.assetid: 1469fc51-c658-43f1-886c-f4530dd84860
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eff0c41993a450e74b468b747776368bae6ad848
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33862870"
---
# <a name="sharedptr-class"></a>shared_ptr 類別

將參考計數的智慧型指標環繞動態配置物件。

## <a name="syntax"></a>語法

```cpp
template <class T>
class shared_ptr;
```

## <a name="remarks"></a>備註

shared_ptr 類別描述使用參考計數來管理資源的物件。 `shared_ptr`物件實際上存放了它擁有之資源的指標，或是存放 null 指標。 資源可以由多個 `shared_ptr` 物件擁有；當擁有特定資源的最後一個 `shared_ptr` 物件終結時，會釋放資源。

`shared_ptr` 會在重新指派或重設時停止擁有資源。

樣板引數 `T` 可能是不完整的類型，針對特定成員函式註明者除外。

當 `shared_ptr<T>` 物件是從 `G*` 類型的資源指標或是從`shared_ptr<G>`建構時，指標類型 `G*` 必須可轉換為 `T*`。 否則將不會編譯程式碼。 例如: 

```cpp
#include <memory>
using namespace std;

class F {};
class G : public F {};

shared_ptr<G> sp0(new G);   // okay, template parameter G and argument G*
shared_ptr<G> sp1(sp0);     // okay, template parameter G and argument shared_ptr<G>
shared_ptr<F> sp2(new G);   // okay, G* convertible to F*
shared_ptr<F> sp3(sp0);     // okay, template parameter F and argument shared_ptr<G>
shared_ptr<F> sp4(sp2);     // okay, template parameter F and argument shared_ptr<F>
shared_ptr<int> sp5(new G); // error, G* not convertible to int*
shared_ptr<int> sp6(sp2);   // error, template parameter int and argument shared_ptr<F>
```

`shared_ptr` 物件在下列情況下會擁有資源：

- 如果它是使用該資源的指標建構，

- 如果它是從擁有該資源的 `shared_ptr` 物件建構，

- 如果它是從指向該資源的 [weak_ptr 類別](../standard-library/weak-ptr-class.md)物件所建構，或者

- 如果已將該資源的擁有權指派給它，不論是利用 [shared_ptr::operator=](#op_eq) 或藉由呼叫成員函式 [shared_ptr::reset](#reset)。

擁有資源的 `shared_ptr` 物件也會共用控制區塊。 控制區塊會存放：

- 擁有資源的 `shared_ptr` 物件數目、

- 指向資源的 `weak_ptr` 物件數目、

- 如果有的話，該資源的刪除者、

- 如果有的話，控制區塊的自訂配置器。

使用 null 指標初始化的 `shared_ptr` 物件具有控制區塊，且不是空的。 在 `shared_ptr` 物件釋放資源之後，它不再擁有該資源。 在 `weak_ptr` 物件釋放資源之後，它不再指向該資源。

當擁有資源的 `shared_ptr` 物件數目變成零時，會藉由刪除資源或將資源的位址傳遞至刪除者來釋放資源，視原先建立資源擁有權的方式而定。 當擁有資源的 `shared_ptr` 物件數目為零，且指向該資源的 `weak_ptr`物件為零時，會使用控制區塊的自訂配置器來釋放控制區塊，如果有的話。

空的 `shared_ptr` 物件未擁有任何資源，也沒有控制區塊。

刪除者是具有成員函式 `operator()` 的函式物件。 它的類型必須是可複製建構，且其複製建構函式和解構函式不能擲回例外狀況。 它接受一個參數，也就是要刪除的物件。

有些函式接受引數清單，其中定義所產生之 `shared_ptr<T>` 或 `weak_ptr<T>` 物件的內容。 您可以透過數種方法指定這類引數清單：

無引數 -- 產生的物件是空白的 `shared_ptr` 物件或是空白的 `weak_ptr` 物件。

`ptr` -- `Other*` 類型的待管理資源指標。 `T` 必須是完整的類型。 如果函式失敗 (因為無法配置控制區塊)，它會評估運算式 `delete ptr`。

`ptr, dtor` -- `Other*` 類型的待管理資源指源，以及該資源的刪除者。 如果函式失敗 (因為無法配置控制區塊)，它會呼叫 `dtor(ptr)`，這必須妥善定義。

`ptr, dtor, alloc` -- `Other*` 類型的待管理資源指標、該資源的刪除者，以及管理任何必須配置和釋放之儲存體的配置器。 如果函式失敗 (因為無法配置控制區塊)，它會呼叫 `dtor(ptr)`，這必須妥善定義。

`sp` -- 擁有待管理資源的 `shared_ptr<Other>` 物件。

`wp` -- 指向待管理資源的 `weak_ptr<Other>` 物件。

`ap` -- 存放待管理資源指標的 `auto_ptr<Other>` 物件。 如果函式成功，它會呼叫 `ap.release()`；否則它會維持 `ap` 不變。

在所有情況下，指標類型 `Other*` 必須可轉換為 `T*`。

## <a name="thread-safety"></a>執行緒安全

多個執行緒可以同時讀取和寫入不同的 `shared_ptr` 物件，即使物件是共用擁有權的複本時也是一樣。

## <a name="members"></a>成員

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[shared_ptr](#shared_ptr)|建構 `shared_ptr`。|
|[shared_ptr::~shared_ptr](#dtorshared_ptr)|終結 `shared_ptr`。|

### <a name="types"></a>類型

|類型名稱|描述|
|-|-|
|[element_type](#element_type)|元素的類型。|

### <a name="functions"></a>函式

|功能|描述|
|-|-|
|[get](#get)|取得擁有的資源位址。|
|[owner_before](#owner_before)|如果這個 `shared_ptr` 排序在所提供的指標之前 (或小於)，則傳回 true。|
|[reset](#reset)|取代所擁有的資源。|
|[swap](#swap)|交換兩個 `shared_ptr` 物件。|
|[unique](#unique)|測試擁有的資源是否唯一。|
|[use_count](#use_count)|計算資源擁有者的數目。|

### <a name="operators"></a>運算子

|運算子|描述|
|-|-|
|[shared_ptr:: operator bool](#op_bool)|測試擁有的資源是否存在。|
|[shared_ptr::operator*](#op_star)|取得指定的值。|
|[shared_ptr::operator=](#op_eq)|取代所擁有的資源。|
|[shared_ptr::operator-&gt;](#op_arrow)|取得指定值的指標。|

## <a name="requirements"></a>需求

**標頭：**\<memory>

**命名空間：** std

## <a name="element_type"></a>  shared_ptr::element_type

元素的類型。

```cpp
typedef T element_type;
```

### <a name="remarks"></a>備註

此類型是範本參數 `T`的同義字。

### <a name="example"></a>範例

```cpp
// std__memory__shared_ptr_element_type.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp0(new int(5));
    std::shared_ptr<int>::element_type val = *sp0;

    std::cout << "*sp0 == " << val << std::endl;

    return (0);
}

```

```Output
*sp0 == 5
```

## <a name="get"></a>  shared_ptr::get

取得擁有的資源位址。

```cpp
T *get() const;
```

### <a name="remarks"></a>備註

此成員函式會傳回所擁有資源的位址。 如果物件未擁有資源，則會傳回 0。

### <a name="example"></a>範例

```cpp
// std__memory__shared_ptr_get.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp0;
    std::shared_ptr<int> sp1(new int(5));

    std::cout << "sp0.get() == 0 == " << std::boolalpha
        << (sp0.get() == 0) << std::endl;
    std::cout << "*sp1.get() == " << *sp1.get() << std::endl;

    return (0);
}

```

```Output
sp0.get() == 0 == true
*sp1.get() == 5
```

## <a name="op_bool"></a>  shared_ptr:: operator bool

測試擁有的資源是否存在。

```cpp
explicit operator bool() const noexcept;
```

### <a name="remarks"></a>備註

此運算子會傳回值為`true`時`get() != nullptr`，否則為`false`。

### <a name="example"></a>範例

```cpp
// std__memory__shared_ptr_operator_bool.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp0;
    std::shared_ptr<int> sp1(new int(5));

    std::cout << "(bool)sp0 == " << std::boolalpha
        << (bool)sp0 << std::endl;
    std::cout << "(bool)sp1 == " << std::boolalpha
        << (bool)sp1 << std::endl;

    return (0);
}

```

```Output
(bool)sp0 == false
(bool)sp1 == true
```

## <a name="op_star"></a>  shared_ptr::operator*

取得指定的值。

```cpp
T& operator*() const;
```

### <a name="remarks"></a>備註

間接取值運算子會傳回 `*get()`。 因此，儲存的指標不能是 null。

### <a name="example"></a>範例

```cpp
// std__memory__shared_ptr_operator_st.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp0(new int(5));

    std::cout << "*sp0 == " << *sp0 << std::endl;

    return (0);
}

```

```Output
*sp0 == 5
```

## <a name="op_eq"></a>  shared_ptr::operator=

取代所擁有的資源。

```cpp
shared_ptr& operator=(const shared_ptr& sp);

template <class Other>
shared_ptr& operator=(const shared_ptr<Other>& sp);

template <class Other>
shared_ptr& operator=(auto_ptr<Other>& ap);

template <class Other>
shared_ptr& operator=(auto_ptr<Other>& ap);

template <class Other>
shared_ptr& operator=(auto_ptr<Other>&& ap);

template <class Other, class Deletor>
shared_ptr& operator=(unique_ptr<Other, Deletor>&& ap);
```

### <a name="parameters"></a>參數

`sp` 要複製的共用的指標。

`ap` 要複製的自動指標。

### <a name="remarks"></a>備註

這些運算子都會遞減 `*this` 目前所擁有之資源的參考計數，並將運算元序列所命名的資源擁有權指派給 `*this`。 如果參考計數降為零，即會釋放資源。 如果運算子失敗，則會讓 `*this` 保留不變。

### <a name="example"></a>範例

```cpp
// std__memory__shared_ptr_operator_as.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp0;
    std::shared_ptr<int> sp1(new int(5));
    std::auto_ptr<int> ap(new int(10));

    sp0 = sp1;
    std::cout << "*sp0 == " << *sp0 << std::endl;

    sp0 = ap;
    std::cout << "*sp0 == " << *sp0 << std::endl;

    return (0);
}

```

```Output
*sp0 == 5
*sp0 == 10
```

## <a name="op_arrow"></a>  shared_ptr::operator-&gt;

取得指定值的指標。

```cpp
T * operator->() const;
```

### <a name="remarks"></a>備註

選取運算子會傳回 `get()`，如此一來，運算式 `sp->member` 的運作方式會與 `(sp.get())->member` 相同，其中 `sp` 是類別 `shared_ptr<T>` 的物件。 因此，儲存的指標不得為 null，而且 `T` 必須是含有 `member` 成員的類別、結構或等位類型。

### <a name="example"></a>範例

```cpp
// std__memory__shared_ptr_operator_ar.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

typedef std::pair<int, int> Mypair;
int main()
{
    std::shared_ptr<Mypair> sp0(new Mypair(1, 2));

    std::cout << "sp0->first == " << sp0->first << std::endl;
    std::cout << "sp0->second == " << sp0->second << std::endl;

    return (0);
}

```

```Output
sp0->first == 1
sp0->second == 2
```

## <a name="owner_before"></a>  shared_ptr::owner_before

如果這個 `shared_ptr` 排序在所提供的指標之前 (或小於)，則傳回 true。

```cpp
template <class Other>
bool owner_before(const shared_ptr<Other>& ptr);

template <class Other>
bool owner_before(const weak_ptr<Other>& ptr);
```

### <a name="parameters"></a>參數

`ptr` `lvalue`參考`shared_ptr`或`weak_ptr`。

### <a name="remarks"></a>備註

如果樣板成員函式會傳回 true`*this`是`ordered before` `ptr`。

## <a name="reset"></a>  shared_ptr::reset

取代所擁有的資源。

```cpp
void reset();

template <class Other>
void reset(Other *ptr;);

template <class Other, class D>
void reset(Other *ptr, D dtor);

template <class Other, class D, class A>
void reset(Other *ptr, D dtor, A alloc);
```

### <a name="parameters"></a>參數

`Other` 引數指標所控制的類型。

`D` 刪除者的類型。

`ptr` 要複製的指標。

`dtor` 若要複製的刪除者。

`A` 配置器的類型。

`alloc` 若要複製配置器。

### <a name="remarks"></a>備註

這些運算子都會遞減 `*this` 目前所擁有之資源的參考計數，並將運算元序列所命名的資源擁有權指派給 `*this`。 如果參考計數降為零，即會釋放資源。 如果運算子失敗，則會讓 `*this` 保留不變。

### <a name="example"></a>範例

```cpp
// std__memory__shared_ptr_reset.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct deleter
{
    void operator()(int *p)
    {
        delete p;
    }
};

int main()
{
    std::shared_ptr<int> sp(new int(5));

    std::cout << "*sp == " << std::boolalpha
        << *sp << std::endl;

    sp.reset();
    std::cout << "(bool)sp == " << std::boolalpha
        << (bool)sp << std::endl;

    sp.reset(new int(10));
    std::cout << "*sp == " << std::boolalpha
        << *sp << std::endl;

    sp.reset(new int(15), deleter());
    std::cout << "*sp == " << std::boolalpha
        << *sp << std::endl;

    return (0);
}

```

```Output
*sp == 5
(bool)sp == false
*sp == 10
*sp == 15
```

## <a name="shared_ptr"></a>  shared_ptr::shared_ptr

建構 `shared_ptr`。

```cpp
shared_ptr();

shared_ptr(nullptr_t);

shared_ptr(const shared_ptr& sp);

shared_ptr(shared_ptr&& sp);

template <class Other>
explicit shared_ptr(Other* ptr);

template <class Other, class D>
shared_ptr(Other* ptr, D dtor);

template <class D>
shared_ptr(nullptr_t ptr, D dtor);

template <class Other, class D, class A>
shared_ptr(Other* ptr, D dtor, A  alloc);

template <class D, class A>
shared_ptr(nullptr_t ptr, D dtor, A alloc);

template <class Other>
shared_ptr(const shared_ptr<Other>& sp);

template <class Other>
shared_ptr(const weak_ptr<Other>& wp);

template <class &>
shared_ptr(std::auto_ptr<Other>& ap);

template <class &>
shared_ptr(std::auto_ptr<Other>&& ap);

template <class Other, class D>
shared_ptr(unique_ptr<Other, D>&& up);

template <class Other>
shared_ptr(const shared_ptr<Other>& sp, T* ptr);

template <class Other, class D>
shared_ptr(const unique_ptr<Other, D>& up) = delete;
```

### <a name="parameters"></a>參數

`Other` 引數指標所控制的類型。

`ptr` 要複製的指標。

`D` 刪除者的類型。

`A` 配置器的類型。

`dtor` 刪除者。

`ator` 配置器。

`sp` 要複製的智慧型指標。

`wp` 弱式的指標。

`ap` 要複製的自動指標。

### <a name="remarks"></a>備註

每個建構函式都會建構擁有由運算元序列所命名之資源的物件。 如果 `wp.expired()`，建構函式 `shared_ptr(const weak_ptr<Other>& wp)` 即會擲回類型為 [bad_weak_ptr 類別](../standard-library/bad-weak-ptr-class.md)的例外狀況物件。

### <a name="example"></a>範例

```cpp
// std__memory__shared_ptr_construct.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct deleter
{
    void operator()(int *p)
    {
        delete p;
    }
};

int main()
{
    std::shared_ptr<int> sp0;
    std::cout << "(bool)sp0 == " << std::boolalpha
        << (bool)sp0 << std::endl;

    std::shared_ptr<int> sp1(new int(5));
    std::cout << "*sp1 == " << *sp1 << std::endl;

    std::shared_ptr<int> sp2(new int(10), deleter());
    std::cout << "*sp2 == " << *sp2 << std::endl;

    std::shared_ptr<int> sp3(sp2);
    std::cout << "*sp3 == " << *sp3 << std::endl;

    std::weak_ptr<int> wp(sp3);
    std::shared_ptr<int> sp4(wp);
    std::cout << "*sp4 == " << *sp4 << std::endl;

    std::auto_ptr<int> ap(new int(15));
    std::shared_ptr<int> sp5(ap);
    std::cout << "*sp5 == " << *sp5 << std::endl;

    return (0);
}

```

```Output
(bool)sp0 == false
*sp1 == 5
*sp2 == 10
*sp3 == 10
*sp4 == 10
*sp5 == 15
```

## <a name="dtorshared_ptr"></a>  shared_ptr::~shared_ptr

終結 `shared_ptr`。

```cpp
~shared_ptr();
```

### <a name="remarks"></a>備註

解構函式會遞減 `*this` 目前所擁有之資源的參考計數。 如果參考計數降為零，即會釋放資源。

### <a name="example"></a>範例

```cpp
// std__memory__shared_ptr_destroy.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct deleter
{
    void operator()(int *p)
    {
        delete p;
    }
};

int main()
{
    std::shared_ptr<int> sp1(new int(5));
    std::cout << "*sp1 == " << *sp1 << std::endl;
    std::cout << "use count == " << sp1.use_count() << std::endl;

    {
        std::shared_ptr<int> sp2(sp1);
        std::cout << "*sp2 == " << *sp2 << std::endl;
        std::cout << "use count == " << sp1.use_count() << std::endl;
    }

    // check use count after sp2 is destroyed
    std::cout << "use count == " << sp1.use_count() << std::endl;

    return (0);
}

```

```Output
*sp1 == 5
use count == 1
*sp2 == 5
use count == 2
use count == 1
```

## <a name="swap"></a>  shared_ptr::swap

交換兩個 `shared_ptr` 物件。

```cpp
void swap(shared_ptr& sp);
```

### <a name="parameters"></a>參數

`sp` 要交換共用的指標。

### <a name="remarks"></a>備註

成員函式會保留原先由 `*this` 擁有且後續由 `sp` 擁有的資源，以及原先由 `sp` 擁有且後續由 `*this` 擁有的資源。 此函式不會變更這兩個資源的參考計數，且不會擲回任何例外狀況。

### <a name="example"></a>範例

```cpp
// std__memory__shared_ptr_swap.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct deleter
{
    void operator()(int *p)
    {
        delete p;
    }
};

int main()
{
    std::shared_ptr<int> sp1(new int(5));
    std::shared_ptr<int> sp2(new int(10));
    std::cout << "*sp1 == " << *sp1 << std::endl;

    sp1.swap(sp2);
    std::cout << "*sp1 == " << *sp1 << std::endl;

    swap(sp1, sp2);
    std::cout << "*sp1 == " << *sp1 << std::endl;
    std::cout << std::endl;

    std::weak_ptr<int> wp1(sp1);
    std::weak_ptr<int> wp2(sp2);
    std::cout << "*wp1 == " << *wp1.lock() << std::endl;

    wp1.swap(wp2);
    std::cout << "*wp1 == " << *wp1.lock() << std::endl;

    swap(wp1, wp2);
    std::cout << "*wp1 == " << *wp1.lock() << std::endl;

    return (0);
}

```

```Output
*sp1 == 5
*sp1 == 10
*sp1 == 5

*wp1 == 5
*wp1 == 10
*wp1 == 5
```

## <a name="unique"></a>  shared_ptr::unique

測試擁有的資源是否唯一。

```cpp
bool unique() const;
```

### <a name="remarks"></a>備註

如果沒有其他 `shared_ptr` 物件擁有 `*this` 所擁有的資源，成員函式就會傳回 `true`，否則會傳回 `false`。

### <a name="example"></a>範例

```cpp
// std__memory__shared_ptr_unique.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct deleter
{
    void operator()(int *p)
    {
        delete p;
    }
};

int main()
{
    std::shared_ptr<int> sp1(new int(5));
    std::cout << "sp1.unique() == " << std::boolalpha
        << sp1.unique() << std::endl;

    std::shared_ptr<int> sp2(sp1);
    std::cout << "sp1.unique() == " << std::boolalpha
        << sp1.unique() << std::endl;

    return (0);
}

```

```Output
sp1.unique() == true
sp1.unique() == false
```

## <a name="use_count"></a>  shared_ptr::use_count

計算資源擁有者的數目。

```cpp
long use_count() const;
```

### <a name="remarks"></a>備註

成員函式會傳回擁有 `*this` 所擁有之資源的 `shared_ptr` 物件數目。

### <a name="example"></a>範例

```cpp
// std__memory__shared_ptr_use_count.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp1(new int(5));
    std::cout << "sp1.use_count() == "
        << sp1.use_count() << std::endl;

    std::shared_ptr<int> sp2(sp1);
    std::cout << "sp1.use_count() == "
        << sp1.use_count() << std::endl;

    return (0);
}

```

```Output
sp1.use_count() == 1
sp1.use_count() == 2
```

## <a name="see-also"></a>另請參閱

[weak_ptr 類別](../standard-library/weak-ptr-class.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
