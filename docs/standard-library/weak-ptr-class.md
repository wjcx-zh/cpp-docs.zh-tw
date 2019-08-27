---
title: weak_ptr 類別
ms.date: 07/29/2019
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
ms.openlocfilehash: d4ba30f737bc570a4ee700b3a317b5feebe8a50a
ms.sourcegitcommit: 725e86dabe2901175ecc63261c3bf05802dddff4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2019
ms.locfileid: "68682414"
---
# <a name="weakptr-class"></a>weak_ptr 類別

包裝弱式連結的指標。

## <a name="syntax"></a>語法

```cpp
template<class T> class weak_ptr;
```

### <a name="parameters"></a>參數

*而已*\
弱式指標所控制的類型。

## <a name="remarks"></a>備註

此範本類別描述的物件, 指向由一或多個[shared_ptr](shared-ptr-class.md)物件管理的資源。 指向`weak_ptr`資源的物件不會影響資源的參考計數。 當管理該`shared_ptr`資源的最後一個物件損毀時, 即使`weak_ptr`有物件指向該資源, 也會釋放資源。 若要避免資料結構中的迴圈, 這是不可或缺的行為。

如果 `weak_ptr` 物件由擁有該資源的 `shared_ptr` 物件所建構，或是如果它由指向該資源的 `weak_ptr` 物件所建構，或如果該資源已藉由 [operator=](#op_eq) 指派給它，則會指向該資源。 `weak_ptr`物件不會提供其所指向資源的直接存取權。 需要使用此資源的程式碼會藉由擁有該資源的 `shared_ptr` 物件如此執行，且該物件藉由呼叫成員函式 [lock](#lock) 所建立。 當物件所指向的資源已被釋放, 因為所有`shared_ptr`擁有該資源的物件都已終結, 所以該物件已過期。 `weak_ptr` 呼叫已到期 `weak_ptr` 物件上的 `lock`會建立空的 shared_ptr 物件。

空的 weak_ptr 物件不會指向任何資源, 也沒有控制區塊。 其成員函式 `lock` 會傳回空的 shared_ptr 物件。

當由 `shared_ptr` 物件控制的兩個或多個資源保留對 `shared_ptr` 物件的交互參考時，就會發生循環。 例如，一個具有三個項目的循環連結清單會有前端節點 `N0`；該節點保留擁有下一個節點 (`N1`) 的 `shared_ptr` 物件；而保留 `shared_ptr` 物件的該節點又擁有下一個節點 (`N2`)；該節點會依序保留擁有前端節點 (`N0`) 的 `shared_ptr` 物件，並關閉此循環。 在此情況下, 參考計數永遠不會變成零, 而且永遠不會釋放迴圈中的節點。 若要消除循環，則最後一個節點 `N2` 應該保留指向 `N0` 的 `weak_ptr` 物件，而不是 `shared_ptr` 物件。 由於物件不會擁有`N0`它, 因此`N0`不會影響的參考計數, 而當程式的最後一個參考指向前端節點時, 也會終結清單中的節點。 `weak_ptr`

## <a name="members"></a>成員

|||
|-|-|
| **建構函式** | |
|[weak_ptr](#weak_ptr)|建構 `weak_ptr`。|
| **解構函式** | |
|[~ weak_ptr](#tilde-weak_ptr)|建構 `weak_ptr`。|
| **Typedefs** | |
|[element_type](#element_type)|項目的類型。|
| **成員函式** | |
|[expired](#expired)|測試擁有權是否已到期。|
|[lock](#lock)|取得資源的獨佔擁有權。|
|[owner_before](#owner_before)|若  此`weak_ptr`順序在提供的指標之前 (或小於), 則傳回 true。|
|[reset](#reset)|釋放所擁有的資源。|
|[swap](#swap)|交換兩個 `weak_ptr` 物件。|
|[use_count](#use_count)|計算物件的`shared_ptr`數目。|
| **運算子** | |
|[operator=](#op_eq)|取代所擁有的資源。|

## <a name="element_type"></a>element_type

項目的類型。

```cpp
typedef T element_type; // through C++17
using element_type = remove_extent_t<T>; // C++20
```

### <a name="remarks"></a>備註

此類型是範本參數 `T`的同義字。

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

## <a name="expired"></a>過時

測試擁有權是否已過期, 也就是已刪除參考的物件。

```cpp
bool expired() const noexcept;
```

### <a name="remarks"></a>備註

如果`*this`已過期, 成員函式會傳回 true, 否則傳回**false**。

### <a name="example"></a>範例

```cpp
// std__memory__weak_ptr_expired.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

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

## <a name="lock"></a>狀

`shared_ptr`取得共用資源擁有權的。

```cpp
shared_ptr<T> lock() const noexcept;
```

### <a name="remarks"></a>備註

`*this`如果`*this`已過期, 成員函式會傳回空的[shared_ptr](shared-ptr-class.md)物件; `shared_ptr<T>`否則會傳回擁有所指向之資源的物件。 傳回相當於不可部分完成執行的`expired() ? shared_ptr<T>() : shared_ptr<T>(*this)`值。

### <a name="example"></a>範例

```cpp
// std__memory__weak_ptr_lock.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

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

## <a name="op_eq"></a>operator =

取代所擁有的資源。

```cpp
weak_ptr& operator=(const weak_ptr& ptr) noexcept;

template <class Other>
weak_ptr& operator=(const weak_ptr<Other>& ptr) noexcept;

template <class Other>
weak_ptr& operator=(const shared_ptr<Other>& ptr) noexcept;
```

### <a name="parameters"></a>參數

*另一方面*\
由引數 shared 或弱式指標所控制的類型。

*指標*\
要複製的弱式指標或共用指標。

### <a name="remarks"></a>備註

所有的運算子都會釋放目前指向`*this`的資源, 並將由*ptr*命名的資源擁有權指派`*this`給。 如果運算子失敗, 則會`*this`保持不變。 每個運算子都有相當於`weak_ptr(ptr).swap(*this)`的效果。

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

## <a name="owner_before"></a>owner_before

若  此`weak_ptr`順序在提供的指標之前 (或小於), 則傳回 true。

```cpp
template <class Other>
bool owner_before(const shared_ptr<Other>& ptr) const noexcept;

template <class Other>
bool owner_before(const weak_ptr<Other>& ptr) const noexcept;
```

### <a name="parameters"></a>參數

*指標*\
或的左值參考。 `weak_ptr` `shared_ptr`

### <a name="remarks"></a>備註

如果  `*this`在*ptr*之前排序, 則範本成員函式會傳回 true。

## <a name="reset"></a>啟動

釋放擁有的資源。

```cpp
void reset() noexcept;
```

### <a name="remarks"></a>備註

成員函式會釋放所指向`*this`的資源, 並將轉換`*this`為`weak_ptr`空的物件。

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

## <a name="swap"></a>調換

交換兩個 `weak_ptr` 物件。

```cpp
void swap(weak_ptr& wp) noexcept;
```

也包括特製化:

```cpp
template<class T>
void swap(weak_ptr<T>& a, weak_ptr<T>& b) noexcept;
```

### <a name="parameters"></a>參數

*wp*\
要交換的弱式指標。

### <a name="remarks"></a>備註

`*this` `*this`在之後  , wp 會指向原本指向的資源, 而且 wp 原先指向的資源會指向。 `swap` 函數不會變更這兩個資源的參考計數, 而且不會擲回任何例外狀況。 範本特製化的效果等同于`a.swap(b)`。

### <a name="example"></a>範例

```cpp
// std__memory__weak_ptr_swap.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

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

## <a name="use_count"></a>use_count

計算擁有共用資源`shared_ptr`的物件數目。

```cpp
long use_count() const noexcept;
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

## <a name="weak_ptr"></a>weak_ptr

建構 `weak_ptr`。

```cpp
constexpr weak_ptr() noexcept;

weak_ptr(const weak_ptr& wp) noexcept;

weak_ptr(weak_ptr&& wp) noexcept;

template <class Other>
weak_ptr(const weak_ptr<Other>& wp) noexcept;

template <class Other>
weak_ptr(weak_ptr<Other>&& sp) noexcept;

template <class Other>
weak_ptr(const shared_ptr<Other>& sp) noexcept;
```

### <a name="parameters"></a>參數

*另一方面*\
引數共用/弱式指標所控制的類型。 除非_其他\*_ 與相容`element_type*`, 否則這些函式不會參與多載解析。

*wp*\
要複製的弱式指標。

*行距*\
要複製的共用指標。

### <a name="remarks"></a>備註

預設的函式會建立`weak_ptr`空的物件。 接受引數的函式會在引數`weak_ptr`指標為空白時, 每個都會建立一個空的物件。 否則, 它們會建立`weak_ptr`指向引數所命名之資源的物件。 共用物件的參考計數不會變更。

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

## <a name="tilde-weak_ptr"></a>~ weak_ptr

終結 `weak_ptr`。

```cpp
~weak_ptr();
```

### <a name="remarks"></a>備註

此析構函式`weak_ptr`會終結這個, 但不會影響其儲存指標指向之物件的參考計數。

## <a name="see-also"></a>另請參閱

[標頭檔參考](cpp-standard-library-header-files.md)\
[\<memory>](memory.md)\
[shared_ptr 類別](shared-ptr-class.md)
