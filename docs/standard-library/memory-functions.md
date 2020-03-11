---
title: '&lt;memory&gt; 函式'
ms.date: 08/05/2019
f1_keywords:
- memory/std::addressof
- memory/std::align
- memory/std::allocate_shared
- memory/std::const_pointer_cast
- memory/std::declare_no_pointers
- memory/std::declare_reachable
- memory/std::default_delete
- memory/std::dynamic_pointer_cast
- memory/std::get_deleter
- memory/std::get_pointer_safety
- memory/std::get_temporary_buffer
- xmemory/std::get_temporary_buffer
- memory/std::make_shared
- memory/std::make_unique
- memory/std::owner_less
- memory/std::reinterpret_pointer_cast
- memory/std::return_temporary_buffer
- xmemory/std::return_temporary_buffer
- memory/std::static_pointer_cast
- memory/std::swap
- memory/std::undeclare_no_pointers
- memory/std::undeclare_reachable
- memory/std::uninitialized_copy
- memory/std::uninitialized_copy_n
- memory/std::uninitialized_fill
- memory/std::uninitialized_fill_n
- memory/std::get_temporary_buffer
- memory/std::return_temporary_buffer
ms.assetid: 3e1898c2-44b7-4626-87ce-84962e4c6f1a
helpviewer_keywords:
- std::addressof [C++]
- std::align [C++]
- std::allocate_shared [C++]
- std::const_pointer_cast [C++]
- std::declare_no_pointers [C++]
- std::declare_reachable [C++]
- std::default_delete [C++]
- std::dynamic_pointer_cast [C++]
- std::get_deleter [C++]
- std::get_pointer_safety [C++]
- std::get_temporary_buffer [C++]
- std::make_shared [C++]
- std::make_unique [C++]
- std::owner_less [C++]
- std::return_temporary_buffer [C++]
- std::static_pointer_cast [C++]
- std::swap [C++]
- std::undeclare_no_pointers [C++]
- std::undeclare_reachable [C++]
- std::uninitialized_copy [C++]
- std::uninitialized_copy_n [C++]
- std::uninitialized_fill [C++]
- std::uninitialized_fill_n [C++]
- std::addressof [C++]
- std::align [C++]
- std::allocate_shared [C++]
- std::const_pointer_cast [C++]
- std::declare_no_pointers [C++]
- std::declare_reachable [C++]
- std::default_delete [C++]
- std::dynamic_pointer_cast [C++]
- std::get_deleter [C++]
- std::get_pointer_safety [C++]
- std::get_temporary_buffer [C++]
- std::make_shared [C++]
- std::make_unique [C++]
- std::owner_less [C++]
- std::return_temporary_buffer [C++]
- std::static_pointer_cast [C++]
- std::undeclare_no_pointers [C++]
- std::undeclare_reachable [C++]
- std::uninitialized_copy [C++]
- std::uninitialized_copy_n [C++]
- std::uninitialized_fill [C++]
- std::uninitialized_fill_n [C++]
ms.openlocfilehash: 2aceb96fcda49df8a1fd40a1bd8011170dccd8ef
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78856679"
---
# <a name="ltmemorygt-functions"></a>&lt;memory&gt; 函式

## <a name="addressof"></a>addressof

取得物件真正的位址。

```cpp
template <class T>
T* addressof(
    T& value) noexcept;    // before C++17

template <class T>
constexpr T* addressof(
    T& value) noexcept;    // C++17

template <class T>
const T* addressof(
    const T&& value) = delete;   // C++17
```

### <a name="parameters"></a>參數

*value*\
要取得真正位址的物件或函式。

### <a name="return-value"></a>傳回值

*值*所參考之物件或函式的實際位址，即使有多載的 `operator&()` 存在也一樣。

### <a name="remarks"></a>備註

## <a name="align"></a>對齊

根據指定的對齊規格，將指定大小的儲存空間納入給定儲存體的第一個可能位址。

```cpp
void* align(
    size_t alignment, // input
    size_t size,      // input
    void*& ptr,       // input/output
    size_t& space     // input/output
);
```

### <a name="parameters"></a>參數

*對齊*\
嘗試的對齊界限。

*size*\
對齊儲存體的大小 (位元組)。

*ptr*\
要使用的可用連續儲存集區的開始位址。 這個參數也是輸出參數，如果對齊成功，則設定為包含新的起始位址。 如果 `align()` 不成功，則不會修改此參數。

*空間*\
`align()` 可用來建立對齊儲存體的總空間。 這個參數也是輸出參數，在對齊儲存體和任何關聯的額外負荷減去之後，會包含儲存緩衝區中剩下的調整空間。

如果 `align()` 不成功，則不會修改此參數。

### <a name="return-value"></a>傳回值

如果要求的對齊緩衝區無法放入可用空間中，則為 null 指標;否則為*ptr*的新值。

### <a name="remarks"></a>備註

修改過的*ptr*和*空間*參數可讓您在相同的緩衝區上重複呼叫 `align()`，可能會有不同的*對齊*和*大小*值。 下列程式碼片段示範`align()` 的一個用法。

```cpp
#include <type_traits> // std::alignment_of()
#include <memory>
//...
char buffer[256]; // for simplicity
size_t alignment = std::alignment_of<int>::value;
void * ptr = buffer;
std::size_t space = sizeof(buffer); // Be sure this results in the true size of your buffer

while (std::align(alignment, sizeof(MyObj), ptr, space)) {
    // You now have storage the size of MyObj, starting at ptr, aligned on
    // int boundary. Use it here if you like, or save off the starting address
    // contained in ptr for later use.
    // ...
    // Last, move starting pointer and decrease available space before
    // the while loop restarts.
    ptr = reinterpret_cast<char*>(ptr) + sizeof(MyObj);
    space -= sizeof(MyObj);
}
// At this point, align() has returned a null pointer, signaling it is not
// possible to allow more aligned storage in this buffer.
```

## <a name="allocate_shared"></a>allocate_shared

使用指定的配置器，為指定的類型建立和所設定物件的[shared_ptr](shared-ptr-class.md) 。 傳回 `shared_ptr`。

```cpp
template <class T, class Allocator, class... Args>
shared_ptr<T> allocate_shared(
    Allocator alloc,
    Args&&... args);
```

### <a name="parameters"></a>參數

配置\
用來建立物件的配置器。

*args*\
成為物件的零個或多個引數。

### <a name="remarks"></a>備註

函式會建立物件 `shared_ptr<T>`，`T(args...)` 由*配置所配置*和建立的指標。

## <a name="atomic_compare_exchange_strong"></a>atomic_compare_exchange_strong

```cpp
template<class T>
bool atomic_compare_exchange_strong(
    shared_ptr<T>* u,
    shared_ptr<T>* v,
    shared_ptr<T> w);
```

## <a name="atomic_compare_exchange_weak"></a>atomic_compare_exchange_weak

```cpp
template<class T>
bool atomic_compare_exchange_weak(
    shared_ptr<T>* u,
    shared_ptr<T>* v,
    shared_ptr<T> w);
```

## <a name="atomic_compare_exchange_strong_explicit"></a>atomic_compare_exchange_strong_explicit

```cpp
template<class T>
bool atomic_compare_exchange_strong_explicit(
    shared_ptr<T>* u,
    shared_ptr<T>* v,
    shared_ptr<T> w,
    memory_order success,
    memory_order failure);
```

## <a name="atomic_compare_exchange_weak_explicit"></a>atomic_compare_exchange_weak_explicit

```cpp
template<class T>
bool atomic_compare_exchange_weak_explicit(
    shared_ptr<T>* u,
    shared_ptr<T>* v,
    shared_ptr<T> w,
    memory_order success,
    memory_order failure);
```

## <a name="atomic_exchange"></a>atomic_exchange

```cpp
template<class T>
shared_ptr<T> atomic_exchange(
    shared_ptr<T>* u,
    shared_ptr<T> r);
```

## <a name="atomic_exchange_explicit"></a>atomic_exchange_explicit

```cpp
template<class T>
shared_ptr<T> atomic_exchange_explicit(
    shared_ptr<T>* u,
    shared_ptr<T> r,
    memory_order mo);
```

## <a name="atomic_is_lock_free"></a>atomic_is_lock_free

```cpp
template<class T>
bool atomic_is_lock_free(
    const shared_ptr<T>* u);
```

## <a name="atomic_load"></a>atomic_load

```cpp
template<class T>
shared_ptr<T> atomic_load(
    const shared_ptr<T>* u);
```

## <a name="atomic_load_explicit"></a>atomic_load_explicit

```cpp
template<class T>
shared_ptr<T> atomic_load_explicit(
    const shared_ptr<T>* u,
    memory_order mo);
```

## <a name="atomic_store"></a>atomic_store

```cpp
template<class T>
void atomic_store(
    shared_ptr<T>* u,
    shared_ptr<T> r);
```

## <a name="atomic_store_explicit"></a>atomic_store_explicit

```cpp
template<class T>
void atomic_store_explicit(
    shared_ptr<T>* u,
    shared_ptr<T> r,
    memory_order mo);
```

## <a name="const_pointer_cast"></a>const_pointer_cast

Const 轉換成[shared_ptr](shared-ptr-class.md)。

```cpp
template <class T, class Other>
shared_ptr<T> const_pointer_cast(
    const shared_ptr<Other>& sp) noexcept;

template <class T, class Other>
shared_ptr<T> const_pointer_cast(
    shared_ptr<Other>&& sp) noexcept;
```

### <a name="parameters"></a>參數

*T*\
傳回之共用指標所控制的類型。

*其他*\
引數共用指標所控制的類型。

*sp*\
引數共用指標。

### <a name="remarks"></a>備註

如果 `const_cast<T*>(sp.get())` 傳回 null 指標，則範本函式會傳回空的 `shared_ptr` 物件。否則，它會傳回擁有*sp*所擁有之資源的 `shared_ptr<T>` 物件。 運算式 `const_cast<T*>(sp.get())` 必須有效。

### <a name="example"></a>範例

```cpp
// std__memory__const_pointer_cast.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp0(new int);
    std::shared_ptr<const int> sp1 =
        std::const_pointer_cast<const int>(sp0);

    *sp0 = 3;
    std::cout << "sp1 == " << *sp1 << std::endl;

    return (0);
}
```

```Output
sp1 == 3
```

## <a name="declare_no_pointers"></a>declare_no_pointers

通知記憶體回收行程，指出基底位址指標和區塊大小所定義之記憶體區塊中的字元未包含任何可追蹤的指標。

```cpp
void declare_no_pointers(
    char* ptr,
    size_t size);
```

### <a name="parameters"></a>參數

*ptr*\
已不再包含可追蹤指標的第一個位元位址。

*size*\
從不包含可追蹤指標的*ptr*開始的區塊大小。

### <a name="remarks"></a>備註

函式會通知任何垃圾收集行程，範圍中的位址 `[ ptr, ptr + size)` 不再包含可追蹤的指標。 （除非能夠連線，否則任何指向已配置之儲存體的指標都不得取值）。

## <a name="declare_reachable"></a>declare_reachable

告知記憶體回收，指示的位址是前往配置儲存體且可連接。

```cpp
void declare_reachable(
    void* ptr);
```

### <a name="parameters"></a>參數

*ptr*\
指向可存取、已配置之有效儲存區域的指標。

### <a name="remarks"></a>備註

如果*ptr*不是 null，此函式會通知任何垃圾收集行程現在可以觸達*ptr* ，也就是說，它會指向有效的已配置儲存體。

## <a name="default_delete"></a>default_delete

刪除以**operator new**所配置的物件。 適合與[unique_ptr](unique-ptr-class.md)搭配使用。

```cpp
struct default_delete
{
    constexpr default_delete() noexcept = default;

    template <class Other, class = typename enable_if<is_convertible<Other*, T*>::value, void>::type>>
    default_delete(const default_delete<Other>&) noexcept;

    void operator()(T* ptr) const noexcept;
};
```

### <a name="parameters"></a>參數

*ptr*\
要刪除的物件指標。

*其他*\
要刪除的陣列項目類型。

### <a name="remarks"></a>備註

類別樣板描述的刪除者會刪除以**operator new**配置的純量物件，適合搭配類別樣板 `unique_ptr`使用。 它也具有明確的特製化 `default_delete<T[]>`。

## <a name="destroy_at"></a>destroy_at

```cpp
template <class T>
void destroy_at(
    T* location);
```

與 `location->~T()` 相同。

## <a name="destroy"></a>予以

```cpp
template <class ForwardIterator>
void destroy(
    ForwardIterator first,
    ForwardIterator last);
```

與相同：

```cpp
for (; first != last; ++first)
    destroy_at(addressof(*first));
```

## <a name="destroy_n"></a>destroy_n

```cpp
template <class ForwardIterator, class Size>
ForwardIterator destroy_n(
    ForwardIterator first,
    Size count);
```

與相同：

```cpp
for (; count > 0; (void)++first, --count)
    destroy_at(addressof(*first));
return first;
```

## <a name="dynamic_pointer_cast"></a>dynamic_pointer_cast

動態轉換成[shared_ptr](shared-ptr-class.md)。

```cpp
template <class T, class Other>
shared_ptr<T> dynamic_pointer_cast(
    const shared_ptr<Other>& sp) noexcept;

template <class T, class Other>
shared_ptr<T> dynamic_pointer_cast(
    shared_ptr<Other>&& sp) noexcept;
```

### <a name="parameters"></a>參數

*T*\
傳回之共用指標所控制的類型。

*其他*\
引數共用指標所控制的類型。

*sp*\
引數共用指標。

### <a name="remarks"></a>備註

如果 `dynamic_cast<T*>(sp.get())` 傳回 null 指標，則範本函式會傳回空的 `shared_ptr` 物件。否則，它會傳回擁有*sp*所擁有之資源的 `shared_ptr<T>` 物件。 運算式 `dynamic_cast<T*>(sp.get())` 必須有效。

### <a name="example"></a>範例

```cpp
// std__memory__dynamic_pointer_cast.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct base
{
    virtual ~base() {}
    int value;
};

struct derived
    : public base
{
};

int main()
{
    std::shared_ptr<base> sp0(new derived);
    std::shared_ptr<derived> sp1 =
        std::dynamic_pointer_cast<derived>(sp0);

    sp0->value = 3;
    std::cout << "sp1->value == " << sp1->value << std::endl;

    return (0);
}
```

```Output
sp1->value == 3
```

## <a name="get_deleter"></a>get_deleter

從[shared_ptr](shared-ptr-class.md)取得刪除者。

```cpp
template <class Deleter, class T>
Deleter* get_deleter(
    const shared_ptr<T>& sp) noexcept;
```

### <a name="parameters"></a>參數

*刪除者*\
刪除者的類型。

*T*\
共用指標所控制的類型。

*sp*\
共用指標。

### <a name="remarks"></a>備註

此範本函式會傳回屬於 `shared_ptr` 物件*sp*之*刪除者*類型的刪除者指標。 如果*sp*沒有刪除者，或其刪除者不是*刪除者*型別，則此函式會傳回0。

### <a name="example"></a>範例

```cpp
// std__memory__get_deleter.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct base
{
    int value;
};

struct deleter
{
    void operator()(base *pb)
    {
        delete pb;
    }
};

int main()
{
    std::shared_ptr<base> sp0(new base);

    sp0->value = 3;
    std::cout << "get_deleter(sp0) != 0 == " << std::boolalpha
        << (std::get_deleter<deleter>(sp0) != 0) << std::endl;

    std::shared_ptr<base> sp1(new base, deleter());

    sp0->value = 3;
    std::cout << "get_deleter(sp1) != 0 == " << std::boolalpha
        << (std::get_deleter<deleter>(sp1) != 0) << std::endl;

    return (0);
}
```

```Output
get_deleter(sp0) != 0 == false
get_deleter(sp1) != 0 == true
```

## <a name="get_pointer_safety"></a>get_pointer_safety

傳回任何記憶體回收行程所假設之指標安全的類型。

```cpp
pointer_safety get_pointer_safety() noexcept;
```

### <a name="remarks"></a>備註

函式會傳回任何自動垃圾收集行程所採用的指標安全類型。

## <a name="get_temporary_buffer"></a>get_temporary_buffer

為專案序列（不超過指定數目的專案）配置暫存儲存體。

```cpp
template <class T>
pair<T *, ptrdiff_t> get_temporary_buffer(
    ptrdiff_t count);
```

### <a name="parameters"></a>參數

*計數*\
所要求的元素數目上限，將針對這些元素配置記憶體。

### <a name="return-value"></a>傳回值

一個 `pair`，其第一個元件是指向所配置記憶體的指標，第二個元件提供緩衝區的大小，指出它所能儲存的元素數目上限。

### <a name="remarks"></a>備註

此函式會提出記憶體要求，但可能不會成功。 如果未配置任何緩衝區，此函式就會傳回一個配對，其中第二個元件等於零，而第一個元件等於 Null 指標。

僅針對暫時性的記憶體使用此函式。

### <a name="example"></a>範例

```cpp
// memory_get_temp_buf.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

using namespace std;

int main( )
{
    // Create an array of ints
    int intArray [] = { 10, 20, 30, 40, 100, 200, 300, 1000, 2000 };
    int count = sizeof ( intArray ) / sizeof ( int );
    cout << "The number of integers in the array is: "
        << count << "." << endl;

    pair<int *, ptrdiff_t> resultPair;
    resultPair = get_temporary_buffer<int>( count );

    cout << "The number of elements that the allocated memory\n"
        << "could store is given by: resultPair.second = "
        << resultPair.second << "." << endl;
}
```

```Output
The number of integers in the array is: 9.
The number of elements that the allocated memory
could store is given by: resultPair.second = 9.
```

## <a name="make_shared"></a>make_shared

建立並傳回[shared_ptr](shared-ptr-class.md) ，該物件指向使用預設配置器從零個或多個引數所構成的已設定物件。 配置並建構指定類別的物件和 `shared_ptr` 來管理共用的物件擁有權，並傳回 `shared_ptr`。

```cpp
template <class T, class... Args>
shared_ptr<T> make_shared(
    Args&&... args);
```

### <a name="parameters"></a>參數

*args*\
零或多個建構函式引數。 函式會根據所提供的引數推斷要叫用的建構函式多載。

### <a name="remarks"></a>備註

使用 `make_shared` 做為建立物件和 `shared_ptr` 的一個簡單且更有效率的方式，並藉以同時管理物件的共用存取權。 語意上來說，這兩個陳述式是相等的：

```cpp
auto sp = std::shared_ptr<Example>(new Example(argument));
auto msp = std::make_shared<Example>(argument);
```

但是，第一個陳述式會產生兩個配置，而若 `shared_ptr` 物件配置成功之後，`Example` 配置失敗，則未命名的 `Example` 物件會遭到洩露。 使用 `make_shared` 的陳述式比較簡單，因為這樣只會使用一個函式呼叫。 這樣會更有效率，因為程式庫可以讓物件和智慧型指標進行單一配置。 此函式的速度會更快，而且會導致記憶體分散較少，且在一個配置中沒有可能發生例外狀況，而不是另一個配置。 改善參考物件的程式碼位置，並更新智慧型指標中的參考計數，便能夠提升效能。

如果您不需要物件的共用存取權，請考慮使用[make_unique](memory-functions.md#make_unique) 。 如果您需要為物件指定自訂的配置器，請使用 [allocate_shared](memory-functions.md#allocate_shared)。 如果您的物件需要自訂刪除者，您就無法使用 `make_shared`，因為沒有任何方法可將刪除者當做引數傳遞。

下列範例示範如何透過叫用特定的建構函式多載來建立共用的類型指標。

### <a name="example"></a>範例

```cpp
// stl_make_shared.cpp
// Compile by using: cl /W4 /EHsc stl_make_shared.cpp
#include <iostream>
#include <string>
#include <memory>
#include <vector>

class Song {
public:
    std::wstring title_;
    std::wstring artist_;

    Song(std::wstring title, std::wstring artist) : title_(title), artist_(artist) {}
    Song(std::wstring title) : title_(title), artist_(L"Unknown") {}
};

void CreateSharedPointers()
{
    // Okay, but less efficient to have separate allocations for
    // Song object and shared_ptr control block.
    auto song = new Song(L"Ode to Joy", L"Beethoven");
    std::shared_ptr<Song> sp0(song);

    // Use make_shared function when possible. Memory for control block
    // and Song object are allocated in the same call:
    auto sp1 = std::make_shared<Song>(L"Yesterday", L"The Beatles");
    auto sp2 = std::make_shared<Song>(L"Blackbird", L"The Beatles");

    // make_shared infers which constructor to use based on the arguments.
    auto sp3 = std::make_shared<Song>(L"Greensleeves");

    // The playlist vector makes copies of the shared_ptr pointers.
    std::vector<std::shared_ptr<Song>> playlist;
    playlist.push_back(sp0);
    playlist.push_back(sp1);
    playlist.push_back(sp2);
    playlist.push_back(sp3);
    playlist.push_back(sp1);
    playlist.push_back(sp2);
    for (auto&& sp : playlist)
    {
        std::wcout << L"Playing " << sp->title_ <<
            L" by " << sp->artist_ << L", use count: " <<
            sp.use_count() << std::endl;
    }
}

int main()
{
    CreateSharedPointers();
}
```

該範例會產生以下輸出：

```Output
Playing Ode to Joy by Beethoven, use count: 2
Playing Yesterday by The Beatles, use count: 3
Playing Blackbird by The Beatles, use count: 3
Playing Greensleeves by Unknown, use count: 2
Playing Yesterday by The Beatles, use count: 3
Playing Blackbird by The Beatles, use count: 3
```

## <a name="make_unique"></a>make_unique

建立並傳回指向指定類型之物件的 [unique_ptr](unique-ptr-class.md)，該類型是使用指定的引數所建構。

```cpp
// make_unique<T>
template <class T, class... Args>
unique_ptr<T> make_unique(Args&&... args);

// make_unique<T[]>
template <class T>
unique_ptr<T> make_unique(size_t size);

// make_unique<T[N]> disallowed
template <class T, class... Args>
/* unspecified */ make_unique(Args&&...) = delete;
```

### <a name="parameters"></a>參數

*T*\
`unique_ptr` 指向的物件類型。

*Args*\
*Args*所指定之參數的類型。

*args*\
要傳遞給*T 型別*物件之函式的引數。

*元素*\
類型*T*的元素陣列。

*size*\
在新陣列中要為其配置空間的元素數目。

### <a name="remarks"></a>備註

第一個多載用於單一物件。 針對陣列叫用第二個多載。 第三個多載可防止您在類型引數中指定陣列大小（make_unique\<T [N] >）;目前的標準不支援此結構。 當您使用 `make_unique` 來建立陣列的 `unique_ptr`，必須將陣列元素個別初始化。 最好的選擇是使用[std：： vector](vector-class.md)，而不是使用這個多載。

為了例外狀況安全，`make_unique` 實作很謹慎，因此建議您使用 `make_unique`，而不是直接呼叫 `unique_ptr` 建構函式。

### <a name="example"></a>範例

下列範例示範如何使用 `make_unique`。 如需更多範例，請參閱[如何：建立和使用 unique_ptr 執行個體](../cpp/how-to-create-and-use-unique-ptr-instances.md)。

[!code-cpp[stl_smart_pointers#214](../cpp/codesnippet/CPP/memory-functions_1.cpp)]

當您看到與 `unique_ptr` 有關的錯誤 C2280 時，通常都是因為您嘗試叫用它的複製建構函式，這是一個被刪除的函式。

## <a name="owner_less"></a>owner_less

允許按擁有權混合比較共用指標和弱式指標。 如果左側參數是在成員函式 `owner_before`的 right 參數之前排序，則傳回**true** 。

```cpp
template <class T>
    struct owner_less; // not defined

template <class T>
struct owner_less<shared_ptr<T>>
{
    bool operator()(
        const shared_ptr<T>& left,
        const shared_ptr<T>& right) const noexcept;

    bool operator()(
        const shared_ptr<T>& left,
        const weak_ptr<T>& right) const noexcept;

    bool operator()(
        const weak_ptr<T>& left,
        const shared_ptr<T>& right) const noexcept;
};

template <class T>
struct owner_less<weak_ptr<T>>
    bool operator()(
        const weak_ptr<T>& left,
        const weak_ptr<T>& right) const noexcept;

    bool operator()(
        const weak_ptr<T>& left,
        const shared_ptr<T>& right) const noexcept;

    bool operator()(
        const shared_ptr<T>& left,
        const weak_ptr<T>& right) const noexcept;
};

template<> struct owner_less<void>
{
    template<class T, class U>
    bool operator()(
        const shared_ptr<T>& left,
        const shared_ptr<U>& right) const noexcept;

    template<class T, class U>
    bool operator()(
        const shared_ptr<T>& left,
        const weak_ptr<U>& right) const noexcept;

    template<class T, class U>
    bool operator()(
        const weak_ptr<T>& left,
        const shared_ptr<U>& right) const noexcept;

    template<class T, class U>
    bool operator()(
        const weak_ptr<T>& left,
        const weak_ptr<U>& right) const noexcept;
};
```

### <a name="parameters"></a>參數

*左方*\
共用指標或弱式指標。

*right*\
共用指標或弱式指標。

### <a name="remarks"></a>備註

類別樣板會將其所有成員運算子定義為傳回 `left.owner_before(right)`。

## <a name="reinterpret_pointer_cast"></a>reinterpret_pointer_cast

使用轉換，從現有的共用指標建立新的 `shared_ptr`。

```cpp
template<class T, class U>
shared_ptr<T> reinterpret_pointer_cast(
    const shared_ptr<U>& ptr) noexcept;

template<class T, class U>
shared_ptr<T> reinterpret_pointer_cast(
    shared_ptr<U>&& ptr) noexcept;
```

### <a name="parameters"></a>參數

*ptr*\
`shared_ptr<U>`的參考。

### <a name="remarks"></a>備註

如果*ptr*是空的，新的 `shared_ptr` 也是空的，否則會與*ptr*共用擁有權。 新的共用指標是評估 `reinterpret_cast<Y*>(ptr.get())`的結果，其中 `Y` 為 `typename std::shared_ptr<T>::element_type`。 如果 `reinterpret_cast<T*>((U*)nullptr)` 的格式不正確，則此行為未定義。

接受左值參考的樣板函式是 c + + 17 的新功能。 採用右值參考的範本函式是 c + + 20 的新功能。

## <a name="return_temporary_buffer"></a>return_temporary_buffer

將使用 `get_temporary_buffer` 樣板函式配置的暫存記憶體取消配置。

```cpp
template <class T>
void return_temporary_buffer(
    T* buffer);
```

### <a name="parameters"></a>參數

*緩衝區*\
指向要配置之記憶體的指標。

### <a name="remarks"></a>備註

僅針對暫時性的記憶體使用此函式。

### <a name="example"></a>範例

```cpp
// memory_ret_temp_buf.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

using namespace std;

int main( )
{
    // Create an array of ints
    int intArray [] = { 10, 20, 30, 40, 100, 200, 300 };
    int count = sizeof ( intArray ) / sizeof ( int );
    cout << "The number of integers in the array is: "
         << count << "." << endl;

    pair<int *, ptrdiff_t> resultPair;
    resultPair = get_temporary_buffer<int>( count );

    cout << "The number of elements that the allocated memory\n"
         << " could store is given by: resultPair.second = "
         << resultPair.second << "." << endl;

    int* tempBuffer = resultPair.first;

    // Deallocates memory allocated with get_temporary_buffer
    return_temporary_buffer( tempBuffer );
}
```

```Output
The number of integers in the array is: 7.
The number of elements that the allocated memory
could store is given by: resultPair.second = 7.
```

## <a name="static_pointer_cast"></a>static_pointer_cast

靜態轉換成[shared_ptr](shared-ptr-class.md)。

```cpp
template <class T, class Other>
shared_ptr<T> static_pointer_cast(
    const shared_ptr<Other>& sp) noexcept;

template <class T, class Other>
shared_ptr<T> static_pointer_cast(
    shared_ptr<Other>&& sp) noexcept;
```

### <a name="parameters"></a>參數

*T*\
傳回之共用指標所控制的類型。

*其他*\
引數共用指標所控制的類型。

*sp*\
引數共用指標。

### <a name="remarks"></a>備註

如果*sp*是空的 `shared_ptr` 物件，則範本函式會傳回空的 `shared_ptr` 物件。否則，它會傳回擁有*sp*所擁有之資源的 `shared_ptr<T>` 物件。 運算式 `static_cast<T*>(sp.get())` 必須有效。

### <a name="example"></a>範例

```cpp
// std__memory__static_pointer_cast.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct base
{
    int value;
};

struct derived
    : public base
{
};

int main()
{
    std::shared_ptr<base> sp0(new derived);
    std::shared_ptr<derived> sp1 =
        std::static_pointer_cast<derived>(sp0);

    sp0->value = 3;
    std::cout << "sp1->value == " << sp1->value << std::endl;

    return (0);
}
```

```Output
sp1->value == 3
```

## <a name="swap"></a>調換

交換兩個[shared_ptr](shared-ptr-class.md)、 [unique_ptr](unique-ptr-class.md)或[weak_ptr](weak-ptr-class.md)物件。

```cpp
template <class T>
void swap(
    shared_ptr<T>& left,
    shared_ptr<T>& right) noexcept;

template <class T, class Deleter>
void swap(
    unique_ptr<T, Deleter>& left,
    unique_ptr<T, Deleter>& right) noexcept;

template <class T>
void swap(
    weak_ptr<T>& left,
    weak_ptr<T>& right) noexcept;

```

### <a name="parameters"></a>參數

*T*\
引數指標所控制的類型。

*刪除者*\
唯一指標類型的刪除者。

*左方*\
左邊的指標。

*right*\
右指標。

### <a name="remarks"></a>備註

範本函式呼叫 `left.swap(right)`。

### <a name="example"></a>範例

```cpp
// std__memory__swap.cpp
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

## <a name="undeclare_no_pointers"></a>undeclare_no_pointers

通知記憶體回收行程，基底位址指標和區塊大小定義的記憶體區塊中的字元現在可能會包含可追蹤的指標。

```cpp
void undeclare_no_pointers(
    char* ptr,
    size_t size);
```

### <a name="parameters"></a>參數

*ptr*\
先前使用[declare_no_pointers](#declare_no_pointers)標示之記憶體位址的指標。

*size*\
記憶體範圍中的位元組數目。 這個值必須等於 `declare_no_pointers` 呼叫中所使用的數位。

### <a name="remarks"></a>備註

函式會通知任何垃圾收集行程，`[ptr, ptr + size)` 的位址範圍現在可能包含可追蹤的指標。

## <a name="undeclare_reachable"></a>undeclare_reachable

撤銷指定記憶體位置的可連線性聲明。

```cpp
template <class T>
T *undeclare_reachable(
    T* ptr);
```

### <a name="parameters"></a>參數

*ptr*\
先前使用[declare_reachable](#declare_reachable)標示之記憶體位址的指標。

### <a name="remarks"></a>備註

如果*ptr*不是**nullptr**，此函式會通知任何垃圾收集行程，指出*ptr*已無法再連線。 它會傳回與*ptr*比較的安全衍生指標。

## <a name="uninitialized_copy"></a>uninitialized_copy

從指定的來源範圍將物件複製到未初始化的目的範圍內。

```cpp
template <class InputIterator, class ForwardIterator>
ForwardIterator uninitialized_copy(
    InputIterator first,
    InputIterator last,
    ForwardIterator dest);

template <class ExecutionPolicy, class InputIterator, class ForwardIterator>
ForwardIterator uninitialized_copy(
    ExecutionPolicy&& policy,
    InputIterator first,
    InputIterator last,
    ForwardIterator dest);
```

### <a name="parameters"></a>參數

*原則*\
要使用的執行原則。

*第一個*\
輸入迭代器，為來源範圍中的第一個項目定址。

*上次*\
輸入迭代器，為來源範圍中的最後一個項目定址。

*目的地*\
正向迭代器，為目的範圍中的第一個項目定址。

### <a name="return-value"></a>傳回值

正向反覆運算器，定址目的範圍以外的第一個位置，除非來源範圍是空的。

### <a name="remarks"></a>備註

這個演算法允許記憶體配置與物件建構分開處理。

樣板函式有效地執行：

```cpp
while (first != last)
{
    new (static_cast<void*>(&* dest++))
        typename iterator_traits<InputIterator>::value_type(*first++);
}
return dest;
```

除非程式碼擲回例外狀況。 在這種情況下，會終結所有建構的物件，並重新擲回例外狀況。

具有執行原則的多載是 c + + 17 的新功能。

### <a name="example"></a>範例

```cpp
// memory_uninit_copy.cpp
// compile with: /EHsc /W3
#include <memory>
#include <iostream>

using namespace std;

class Integer
{
public:
    Integer(int x) : value(x) {}
    int get() { return value; }
private:
    int value;
};

int main()
{
    int Array[] = { 10, 20, 30, 40 };
    const int N = sizeof(Array) / sizeof(int);

    cout << "The initialized Array contains " << N << " elements: ";
    for (int i = 0; i < N; i++)
    {
        cout << " " << Array[i];
    }
    cout << endl;

    Integer* ArrayPtr = (Integer*)malloc(N * sizeof(int));
    Integer* LArrayPtr = uninitialized_copy(
        Array, Array + N, ArrayPtr);  // C4996

    cout << "Address of position after the last element in the array is: "
        << &Array[0] + N << endl;
    cout << "The iterator returned by uninitialized_copy addresses: "
        << (void*)LArrayPtr << endl;
    cout << "The address just beyond the last copied element is: "
        << (void*)(ArrayPtr + N) << endl;

    if ((&Array[0] + N) == (void*)LArrayPtr)
        cout << "The return value is an iterator "
        << "pointing just beyond the original array." << endl;
    else
        cout << "The return value is an iterator "
        << "not pointing just beyond the original array." << endl;

    if ((void*)LArrayPtr == (void*)(ArrayPtr + N))
        cout << "The return value is an iterator "
        << "pointing just beyond the copied array." << endl;
    else
        cout << "The return value is an iterator "
        << "not pointing just beyond the copied array." << endl;

    free(ArrayPtr);

    cout << "Note that the exact addresses returned will vary\n"
        << "with the memory allocation in individual computers."
        << endl;
}
```

## <a name="uninitialized_copy_n"></a>uninitialized_copy_n

從輸入迭代器建立所指定項目數的複本。 複本會放在正向迭代器中。

```cpp
template <class InputIterator, class Size, class ForwardIterator>
ForwardIterator uninitialized_copy_n(
    InputIterator first,
    Size count,
    ForwardIterator dest);

template <class ExecutionPolicy, class InputIterator, class Size, class ForwardIterator>
ForwardIterator uninitialized_copy_n(
    ExecutionPolicy&& policy,
    InputIterator first,
    Size count,
    ForwardIterator dest);
```

### <a name="parameters"></a>參數

*原則*\
要使用的執行原則。

*第一個*\
輸入迭代器，參考要複製的物件。

*計數*\
帶正負號或不帶正負號的整數類型，指定複製物件的次數。

*目的地*\
正向迭代器，參考放置新複本的位置。

### <a name="return-value"></a>傳回值

正向迭代器，定址目的之外的第一個位置。 如果來源範圍是空的，則反覆運算器會*先*定址。

### <a name="remarks"></a>備註

此範本函式會有效地執行下列程式碼：

```cpp
    for (; 0 < count; --count)
        new (static_cast<void*>(&* dest++))
            typename iterator_traits<InputIterator>::value_type(*first++);
    return dest;
```

除非程式碼擲回例外狀況。 在這種情況下，會終結所有建構的物件，並重新擲回例外狀況。

具有執行原則的多載是 c + + 17 的新功能。

## <a name="uninitialized_default_construct"></a>uninitialized_default_construct

預設會在指定的範圍內，將反覆運算器的物件 `value_type` 結構。

```cpp
template <class ForwardIterator>
void uninitialized_default_construct(
    ForwardIterator first,
    ForwardIterator last);

template <class ExecutionPolicy, class ForwardIterator>
void uninitialized_default_construct(
    ExecutionPolicy&& policy,
    ForwardIterator first,
    ForwardIterator last);
```

### <a name="parameters"></a>參數

*原則*\
要使用的執行原則。

*第一個*\
反覆運算器，定址要建立之範圍中的第一個元素。

*上次*\
反覆運算器，定址範圍中最後一個元素之後的一個專案。

### <a name="remarks"></a>備註

沒有執行原則的版本實際上與相同：

```cpp
for (; first != last; ++first)
    ::new (static_cast<void*>(addressof(*first)))
        typename iterator_traits<ForwardIterator>::value_type;
```

如果擲回例外狀況，則會以未指定的順序終結先前的結構化物件。

具有執行原則的版本具有相同的結果，但會根據指定的*原則*執行。

這些函式是 c + + 17 的新功能。

## <a name="uninitialized_default_construct_n"></a>uninitialized_default_construct_n

預設會從指定的位置開始，建立反覆運算器 `value_type`的指定數目物件。

```cpp
template <class ForwardIterator, class Size>
ForwardIterator uninitialized_default_construct_n(
    ForwardIterator first,
    Size count);

template <class ExecutionPolicy, class ForwardIterator, class Size>
ForwardIterator uninitialized_default_construct_n(
    ExecutionPolicy&& policy,
    ForwardIterator first,
    Size count);
```

### <a name="parameters"></a>參數

*原則*\
要使用的執行原則。

*第一個*\
反覆運算器，定址目的範圍中要建立的第一個元素。

*計數*\
要建立之目的範圍中的元素計數。

### <a name="return-value"></a>傳回值

正向反覆運算器，定址目的範圍以外的第一個位置，除非來源範圍是空的。

### <a name="remarks"></a>備註

沒有執行原則的版本實際上與相同：

```cpp
for (; count>0; (void)++first, --count)
    ::new (static_cast<void*>(addressof(*first)))
        typename iterator_traits<ForwardIterator>::value_type;
return first;
```

如果擲回例外狀況，則會以未指定的順序終結先前的結構化物件。

具有執行原則的版本具有相同的結果，但會根據指定的*原則*執行。

這些函式是 c + + 17 的新功能。

## <a name="uninitialized_fill"></a>uninitialized_fill

將所指定值的物件複製到未初始化的目的範圍內。

```cpp
template <class ForwardIterator, class T>
void uninitialized_fill(
    ForwardIterator first,
    ForwardIterator last,
    const T& value);

template <class ExecutionPolicy, class ForwardIterator, class T>
void uninitialized_fill(
    ExecutionPolicy&& policy,
    ForwardIterator first,
    ForwardIterator last,
    const T& value);
```

### <a name="parameters"></a>參數

*原則*\
要使用的執行原則。

*第一個*\
正向反覆運算器，定址目的範圍中要初始化的第一個元素。

*上次*\
正向反覆運算器，定址目的範圍中要初始化的最後一個元素。

*value*\
用來初始化目的範圍的值。

### <a name="remarks"></a>備註

這個演算法允許記憶體配置與物件建構分開處理。

樣板函式有效地執行：

```cpp
while (first != last)
    new (static_cast<void*>(&* first ++))
        typename iterator_traits<ForwardIterator>::value_type (value);
```

除非程式碼擲回例外狀況。 在這種情況下，會終結所有建構的物件，並重新擲回例外狀況。

具有執行原則的多載是 c + + 17 的新功能。

### <a name="example"></a>範例

```cpp
// memory_uninit_fill.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

using namespace std;

class Integer
{
public:
    // No default constructor
    Integer( int x ) : value( x ) {}
    int get() { return value; }
private:
    int value;
};

int main()
{
    const int N = 10;
    Integer value ( 25 );
    Integer* Array = ( Integer* ) malloc( N * sizeof( int ) );
    uninitialized_fill( Array, Array + N, value );
    cout << "The initialized Array contains: ";
    for ( int i = 0; i < N; i++ )
        {
            cout << Array[ i ].get() << " ";
        }
    cout << endl;
}
```

```Output
The initialized Array contains: 25 25 25 25 25 25 25 25 25 25
```

## <a name="uninitialized_fill_n"></a>uninitialized_fill_n

將指定值的物件複製到未初始化目的範圍的指定元素數目。

```cpp
template <class ForwardIterator, class Size, class T>
ForwardIterator uninitialized_fill_n(
    ForwardIterator first,
    Size count,
    const T& value);

template <class ExecutionPolicy, class ForwardIterator, class Size, class T>
ForwardIterator uninitialized_fill_n(
    ExecutionPolicy&& policy,
    ForwardIterator first,
    Size count,
    const T& value);
```

### <a name="parameters"></a>參數

*原則*\
要使用的執行原則。

*第一個*\
正向反覆運算器，定址目的範圍中要初始化的第一個元素。

*計數*\
要初始化的元素數目。

*value*\
要用來初始化目的範圍的值。

### <a name="remarks"></a>備註

這個演算法允許記憶體配置與物件建構分開處理。

樣板函式有效地執行：

```cpp
while (0 < count--)
    new (static_cast<void*>(&* first++))
        typename iterator_traits<ForwardIterator>::value_type(value);
return first;
```

除非程式碼擲回例外狀況。 在這種情況下，會終結所有建構的物件，並重新擲回例外狀況。

具有執行原則的多載是 c + + 17 的新功能。

### <a name="example"></a>範例

```cpp
// memory_uninit_fill_n.cpp
// compile with: /EHsc /W3
#include <memory>
#include <iostream>

using namespace std;

class Integer
{
public:
    // No default constructor
    Integer( int x ) : value( x ) {}
    int get() { return value; }
private:
    int value;
};

int main()
{
    const int N = 10;
    Integer value( 60 );
    Integer* Array = ( Integer* ) malloc( N * sizeof( int ) );
    uninitialized_fill_n( Array, N, value );  // C4996
    cout << "The uninitialized Array contains: ";
    for ( int i = 0; i < N; i++ )
        cout << Array[ i ].get() <<  " ";
}
```

## <a name="uninitialized_move"></a>uninitialized_move

將元素從來源範圍移到未初始化的目的記憶體區域。

```cpp
template <class InputIterator, class ForwardIterator>
ForwardIterator uninitialized_move(
    InputIterator first,
    InputIterator last,
    ForwardIterator dest);

template <class ExecutionPolicy, class InputIterator, class ForwardIterator>
ForwardIterator uninitialized_move(
    ExecutionPolicy&& policy,
    InputIterator first,
    InputIterator last,
    ForwardIterator dest);
```

### <a name="parameters"></a>參數

*原則*\
要使用的執行原則。

*第一個*\
輸入反覆運算器，定址要移動之來源範圍中的第一個元素。

*上次*\
輸入反覆運算器，定址要移動之來源範圍中最後一個元素之後的一個。

*目的地*\
目的範圍的開頭。

### <a name="remarks"></a>備註

沒有執行原則的版本實際上與相同：

```cpp
for (; first != last; (void)++dest, ++first)
    ::new (static_cast<void*>(addressof(*dest)))
        typename iterator_traits<ForwardIterator>::value_type(std::move(*first));
return dest;
```

如果擲回例外狀況，則來源範圍中的某些物件可能會保留為有效但未指定的狀態。 先前的結構化物件會以未指定的順序終結。

具有執行原則的版本具有相同的結果，但會根據指定的*原則*執行。

這些函式是 c + + 17 的新功能。

## <a name="uninitialized_move_n"></a>uninitialized_move_n

將指定數目的專案從來源範圍移動到未初始化的目的記憶體區域。

```cpp
template <class InputIterator, class Size, class ForwardIterator>
pair<InputIterator, ForwardIterator> uninitialized_move_n(
    InputIterator first,
    Size count,
    ForwardIterator dest);

template <class ExecutionPolicy, class InputIterator, class Size, class ForwardIterator>
pair<InputIterator, ForwardIterator> uninitialized_move_n(
    ExecutionPolicy&& policy,
    InputIterator first,
    Size count,
    ForwardIterator dest);
```

### <a name="parameters"></a>參數

*原則*\
要使用的執行原則。

*第一個*\
輸入反覆運算器，定址要移動之來源範圍中的第一個元素。

*計數*\
要移動之來源範圍中的元素計數。

*目的地*\
目的範圍的開頭。

### <a name="remarks"></a>備註

沒有執行原則的版本實際上與相同：

```cpp
for (; count > 0; ++dest, (void) ++first, --count)
    ::new (static_cast<void*>(addressof(*dest)))
        typename iterator_traits<ForwardIterator>::value_type(std::move(*first));
return {first, dest};
```

如果擲回例外狀況，則來源範圍中的某些物件可能會保留為有效但未指定的狀態。 先前的結構化物件會以未指定的順序終結。

具有執行原則的版本具有相同的結果，但會根據指定的*原則*執行。

這些函式是 c + + 17 的新功能。

## <a name="uninitialized_value_construct"></a>uninitialized_value_construct

在指定的範圍內，以值初始化來建立反覆運算器 `value_type` 的物件。

```cpp
template <class ForwardIterator>
void uninitialized_value_construct(
    ForwardIterator first,
    ForwardIterator last);

template <class ExecutionPolicy, class ForwardIterator>
void uninitialized_value_construct(
    ExecutionPolicy&& policy,
    ForwardIterator first,
    ForwardIterator last);
```

### <a name="parameters"></a>參數

*原則*\
要使用的執行原則。

*第一個*\
反覆運算器，定址範圍中的第一個專案至值結構。

*上次*\
反覆運算器，定址範圍到值結構中最後一個元素之後的一個。

### <a name="remarks"></a>備註

沒有執行原則的版本實際上與相同：

```cpp
for (; first != last; ++first)
    ::new (static_cast<void*>(addressof(*first)))
        typename iterator_traits<ForwardIterator>::value_type();
```

如果擲回例外狀況，則會以未指定的順序終結先前的結構化物件。

具有執行原則的版本具有相同的結果，但會根據指定的*原則*執行。

如果發生記憶體配置失敗，則會擲回 `std::bad_alloc` 例外狀況。

這些函式是 c + + 17 的新功能。

## <a name="uninitialized_value_construct_n"></a>uninitialized_value_construct_n

從指定的位置開始，依據值初始化，來構造反覆運算器 `value_type` 的指定數目物件。

```cpp
template <class ForwardIterator, class Size>
ForwardIterator uninitialized_value_construct_n(
    ForwardIterator first,
    Size count);

template <class ExecutionPolicy, class ForwardIterator, class Size>
ForwardIterator uninitialized_value_construct_n(
    ExecutionPolicy&& policy,
    ForwardIterator first,
    Size count);
```

### <a name="parameters"></a>參數

*原則*\
要使用的執行原則。

*第一個*\
反覆運算器，定址目的範圍中要建立的第一個元素。

*計數*\
要建立之目的範圍中的元素計數。

### <a name="remarks"></a>備註

沒有執行原則的版本實際上與相同：

```cpp
for (; count > 0; (void)++first, --count)
    ::new (static_cast<void*>(addressof(*first)))
        typename iterator_traits<ForwardIterator>::value_type();
return first;
```

如果擲回例外狀況，則會以未指定的順序終結先前的結構化物件。

具有執行原則的版本具有相同的結果，但會根據指定的*原則*執行。

如果發生記憶體配置失敗，則會擲回 `std::bad_alloc` 例外狀況。

這些函式是 c + + 17 的新功能。

## <a name="uses_allocator_v"></a>uses_allocator_v

用來存取 `uses_allocator` 範本值的 helper 變數範本。

```cpp
template <class T, class Alloc>
inline constexpr bool uses_allocator_v = uses_allocator<T, Alloc>::value;
```

## <a name="see-also"></a>另請參閱

[\<memory>](memory.md)
