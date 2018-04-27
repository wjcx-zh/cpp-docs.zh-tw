---
title: weak_ptr 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- memory/std::weak_ptr
- memory/std::weak_ptr::element_type
- memory/std::weak_ptr::expired
- memory/std::weak_ptr::lock
- memory/std::weak_ptr::owner_before
- memory/std::weak_ptr::reset
- memory/std::weak_ptr::swap
- memory/std::weak_ptr::use_count
- memory/std::weak_ptr::operator=
dev_langs:
- C++
helpviewer_keywords:
- std::weak_ptr [C++]
- std::weak_ptr [C++], element_type
- std::weak_ptr [C++], expired
- std::weak_ptr [C++], lock
- std::weak_ptr [C++], owner_before
- std::weak_ptr [C++], reset
- std::weak_ptr [C++], swap
- std::weak_ptr [C++], use_count
- std::weak_ptr [C++], element_type
- std::weak_ptr [C++], expired
- std::weak_ptr [C++], lock
- std::weak_ptr [C++], owner_before
- std::weak_ptr [C++], reset
- std::weak_ptr [C++], swap
- std::weak_ptr [C++], use_count
ms.assetid: 2db4afb2-c7be-46fc-9c20-34ec2f8cc7c2
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c8169d8958d99de545ed03c50393bc22478b425f
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="weakptr-class"></a>weak_ptr 類別

包裝弱式連結的指標。

## <a name="syntax"></a>語法

```cpp
template<class _Ty>
   class weak_ptr {
public:
   typedef Ty element_type;
   weak_ptr();
   weak_ptr(const weak_ptr&);
   template <class Other>
      weak_ptr(const weak_ptr<Other>&);
   template <class Other>
      weak_ptr(const shared_ptr<Other>&);
   weak_ptr& operator=(const weak_ptr&);
   template <class Other>
      weak_ptr& operator=(const weak_ptr<Other>&);
   template <class Other>
      weak_ptr& operator=(shared_ptr<Other>&);
   void swap(weak_ptr&);
   void reset();
   long use_count() const;
   bool expired() const;
   shared_ptr<Ty> lock() const;
   };
```

### <a name="parameters"></a>參數

`Ty` 弱式指標所控制的類型。

## <a name="remarks"></a>備註

此範本類別描述的物件，指向由一或多個 [shared_ptr 類別](../standard-library/shared-ptr-class.md)物件管理的資源。 指向資源的 `weak_ptr` 物件不會影響資源的參考計數。 因此，當最後一個管理該資源的 `shared_ptr` 物件終結時，將會釋放該資源，即使仍有指向該資源的 `weak_ptr` 物件。 為了避免資料結構中的循環，這是不可或缺的。

如果 `weak_ptr` 物件由擁有該資源的 `shared_ptr` 物件所建構，或是如果它由指向該資源的 `weak_ptr` 物件所建構，或如果該資源已藉由 [operator=](#op_eq) 指派給它，則會指向該資源。 `weak_ptr` 物件不提供對它所指向資源的直接存取。 需要使用此資源的程式碼會藉由擁有該資源的 `shared_ptr` 物件如此執行，且該物件藉由呼叫成員函式 [lock](#lock) 所建立。 當 `weak_ptr` 物件指向的資源已釋放後，此物件就會到期，因為擁有此資源的所有 `shared_ptr` 物件已被終結。 呼叫已到期 `weak_ptr` 物件上的 `lock`會建立空的 shared_ptr 物件。

空的 weak_ptr 物件未指向任何資源，也沒有控制區塊。 其成員函式 `lock` 會傳回空的 shared_ptr 物件。

當由 `shared_ptr` 物件控制的兩個或多個資源保留對 `shared_ptr` 物件的交互參考時，就會發生循環。 例如，一個具有三個項目的循環連結清單會有前端節點 `N0`；該節點保留擁有下一個節點 (`N1`) 的 `shared_ptr` 物件；而保留 `shared_ptr` 物件的該節點又擁有下一個節點 (`N2`)；該節點會依序保留擁有前端節點 (`N0`) 的 `shared_ptr` 物件，並關閉此循環。 在此情況下，沒有任何參考計數會變成零，也不會釋放這個循環中的節點。 若要消除循環，則最後一個節點 `N2` 應該保留指向 `N0` 的 `weak_ptr` 物件，而不是 `shared_ptr` 物件。 因為 `weak_ptr` 物件並未擁有 `N0`，所以並不會影響 `N0` 的參考計數，而且當此程式最後一個對前端節點的參考被終結時，此清單中的節點也將被終結。

## <a name="members"></a>成員

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[weak_ptr](#weak_ptr)|建構 `weak_ptr`。|

### <a name="methods"></a>方法

|||
|-|-|
|[element_type](#element_type)|項目的類型。|
|[expired](#expired)|測試擁有權是否已到期。|
|[lock](#lock)|取得資源的獨佔擁有權。|
|[owner_before](#owner_before)|如果這個 `weak_ptr` 排序在所提供的指標之前 (或小於)，則傳回 `true`。|
|[reset](#reset)|釋放所擁有的資源。|
|[swap](#swap)|交換兩個 `weak_ptr` 物件。|
|[use_count](#use_count)|指定之 `shared_ptr` 物件的計數數目。|

### <a name="operators"></a>運算子

|運算子|描述|
|-|-|
|[operator=](#op_eq)|取代所擁有的資源。|

## <a name="requirements"></a>需求

**標頭：**\<memory>

**命名空間：** std

## <a name="element_type"></a>  element_type

項目的類型。

```cpp
typedef Ty element_type;
```

### <a name="remarks"></a>備註

此類型是範本參數 `Ty`的同義字。

### <a name="example"></a>範例

```cpp
// std__memory__weak_ptr_element_type.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
    {
    std::shared_ptr<int> sp0(new int(5));
    std::weak_ptr<int> wp0(sp0);
    std::weak_ptr<int>::element_type val = *wp0.lock();

    std::cout << "*wp0.lock() == " << val << std::endl;

    return (0);
    }

```

```Output
*wp0.lock() == 5
```

## <a name="expired"></a>  expired

測試擁有權是否已到期。

```cpp
bool expired() const;
```

### <a name="remarks"></a>備註

如果 `*this` 已過期則成員函式傳回 `true`，否則為 `false`。

### <a name="example"></a>範例

```cpp
// std__memory__weak_ptr_expired.cpp
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
    std::weak_ptr<int> wp;

    {
        std::shared_ptr<int> sp(new int(10));
        wp = sp;
        std::cout << "wp.expired() == " << std::boolalpha
            << wp.expired() << std::endl;
        std::cout << "*wp.lock() == " << *wp.lock() << std::endl;
    }

    // check expired after sp is destroyed
    std::cout << "wp.expired() == " << std::boolalpha
        << wp.expired() << std::endl;
    std::cout << "(bool)wp.lock() == " << std::boolalpha
        << (bool)wp.lock() << std::endl;

    return (0);
}

```

```Output
wp.expired() == false
*wp.lock() == 10
wp.expired() == true
(bool)wp.lock() == false
```

## <a name="lock"></a>  lock

取得資源的獨佔擁有權。

```cpp
shared_ptr<Ty> lock() const;
```

### <a name="remarks"></a>備註

成員函式會傳回空的 shared_ptr 物件，如果`*this`已過期; 否則它會傳回[shared_ptr 類別](../standard-library/shared-ptr-class.md)\<Ty > 物件所擁有的資源`*this`指向。

### <a name="example"></a>範例

```cpp
// std__memory__weak_ptr_lock.cpp
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
    std::weak_ptr<int> wp;

    {
        std::shared_ptr<int> sp(new int(10));
        wp = sp;
        std::cout << "wp.expired() == " << std::boolalpha
            << wp.expired() << std::endl;
        std::cout << "*wp.lock() == " << *wp.lock() << std::endl;
    }

    // check expired after sp is destroyed
    std::cout << "wp.expired() == " << std::boolalpha
        << wp.expired() << std::endl;
    std::cout << "(bool)wp.lock() == " << std::boolalpha
        << (bool)wp.lock() << std::endl;

    return (0);
}
```

```Output
wp.expired() == false
*wp.lock() == 10
wp.expired() == true
(bool)wp.lock() == false
```

## <a name="op_eq"></a>  operator=

取代所擁有的資源。

```cpp
weak_ptr& operator=(const weak_ptr& wp);

template <class Other>
weak_ptr& operator=(const weak_ptr<Other>& wp);

template <class Other>
weak_ptr& operator=(const shared_ptr<Other>& sp);
```

### <a name="parameters"></a>參數

`Other` 引數共用/弱式指標所控制的類型。

`wp` 要複製的弱式指標。

`sp` 要複製的共用的指標。

### <a name="remarks"></a>備註

這些運算子都會釋放目前 `*this` 所指向的資源，並將運算元序列所命名的資源指派給 `*this`。 如果運算子失敗，則會保留 `*this` 不變。

### <a name="example"></a>範例

```cpp
// std__memory__weak_ptr_operator_as.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp0(new int(5));
    std::weak_ptr<int> wp0(sp0);
    std::cout << "*wp0.lock() == " << *wp0.lock() << std::endl;

    std::shared_ptr<int> sp1(new int(10));
    wp0 = sp1;
    std::cout << "*wp0.lock() == " << *wp0.lock() << std::endl;

    std::weak_ptr<int> wp1;
    wp1 = wp0;
    std::cout << "*wp1.lock() == " << *wp1.lock() << std::endl;

    return (0);
}
```

```Output
*wp0.lock() == 5
*wp0.lock() == 10
*wp1.lock() == 10
```

## <a name="owner_before"></a>  owner_before

如果這個 `weak_ptr` 排序在所提供的指標之前 (或小於)，則傳回 `true`。

```cpp
template <class Other>
bool owner_before(const shared_ptr<Other>& ptr);

template <class Other>
bool owner_before(const weak_ptr<Other>& ptr);
```

### <a name="parameters"></a>參數

`ptr` `lvalue`參考`shared_ptr`或`weak_ptr`。

### <a name="remarks"></a>備註

樣板成員函式會傳回`true`如果`*this`是`ordered before` `ptr`。

## <a name="reset"></a>  reset

釋放所擁有的資源。

```cpp
void reset();
```

### <a name="remarks"></a>備註

成員函式會釋放 `*this` 所指向的資源，並將 `*this` 轉換為空的 weak_ptr 物件。

### <a name="example"></a>範例

```cpp
// std__memory__weak_ptr_reset.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp(new int(5));
    std::weak_ptr<int> wp(sp);
    std::cout << "*wp.lock() == " << *wp.lock() << std::endl;
    std::cout << "wp.expired() == " << std::boolalpha
        << wp.expired() << std::endl;

    wp.reset();
    std::cout << "wp.expired() == " << std::boolalpha
        << wp.expired() << std::endl;

    return (0);
}

```

```Output
*wp.lock() == 5
wp.expired() == false
wp.expired() == true
```

## <a name="swap"></a>  swap

交換兩個 `weak_ptr` 物件。

```cpp
void swap(weak_ptr& wp);
```

### <a name="parameters"></a>參數

`wp` 要交換的弱式指標。

### <a name="remarks"></a>備註

成員函式會使原先 `*this` 所指向的資源後續由 `wp` 指向，而原先 `wp` 所指向的資源後續則由 `*this` 指向。 函式不會變更兩個資源的參考計數，且不會擲回任何例外狀況。

### <a name="example"></a>範例

```cpp
// std__memory__weak_ptr_swap.cpp
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

## <a name="use_count"></a>  use_count

指定之 `shared_ptr` 物件的計數數目。

```cpp
long use_count() const;
```

### <a name="remarks"></a>備註

成員函式會傳回擁有 `*this` 所指向之資源的 `shared_ptr` 物件數目。

### <a name="example"></a>範例

```cpp
// std__memory__weak_ptr_use_count.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp1(new int(5));
    std::weak_ptr<int> wp(sp1);
    std::cout << "wp.use_count() == "
        << wp.use_count() << std::endl;

    std::shared_ptr<int> sp2(sp1);
    std::cout << "wp.use_count() == "
        << wp.use_count() << std::endl;

    return (0);
}

```

```Output
wp.use_count() == 1
wp.use_count() == 2
```

## <a name="weak_ptr"></a>  weak_ptr

建構 `weak_ptr`。

```cpp
weak_ptr();

weak_ptr(const weak_ptr& wp);

template <class Other>
weak_ptr(const weak_ptr<Other>& wp);

template <class Other>
weak_ptr(const shared_ptr<Other>& sp);
```

### <a name="parameters"></a>參數

`Other` 引數共用/弱式指標所控制的類型。

`wp` 要複製的弱式指標。

`sp` 要複製的共用的指標。

### <a name="remarks"></a>備註

每個建構函式會建構指向由運算元序列所命名之資源的物件。

### <a name="example"></a>範例

```cpp
// std__memory__weak_ptr_construct.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::weak_ptr<int> wp0;
    std::cout << "wp0.expired() == " << std::boolalpha
        << wp0.expired() << std::endl;

    std::shared_ptr<int> sp1(new int(5));
    std::weak_ptr<int> wp1(sp1);
    std::cout << "*wp1.lock() == "
        << *wp1.lock() << std::endl;

    std::weak_ptr<int> wp2(wp1);
    std::cout << "*wp2.lock() == "
        << *wp2.lock() << std::endl;

    return (0);
}

```

```Output
wp0.expired() == true
*wp1.lock() == 5
*wp2.lock() == 5
```

## <a name="see-also"></a>另請參閱

[shared_ptr 類別](../standard-library/shared-ptr-class.md)<br/>
