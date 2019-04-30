---
title: '&lt;memory&gt; 函式'
ms.date: 02/06/2019
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
- xmemory/std::get_temporary_buffer
- memory/std::make_shared
- memory/std::make_unique
- memory/std::owner_less
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
ms.openlocfilehash: 71cae7bfbb8bfc0bef79a087d4450505c2880e5c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412848"
---
# <a name="ltmemorygt-functions"></a>&lt;memory&gt; 函式

||||
|-|-|-|
|[addressof](#addressof)|[align](#align)|[allocate_shared](#allocate_shared)|
|[const_pointer_cast](#const_pointer_cast)|[declare_no_pointers](#declare_no_pointers)|[declare_reachable](#declare_reachable)|
|[default_delete](#default_delete)|[dynamic_pointer_cast](#dynamic_pointer_cast)|[get_deleter](#get_deleter)|
|[get_pointer_safety](#get_pointer_safety)|[get_temporary_buffer](#get_temporary_buffer)|[make_shared](#make_shared)|
|[make_unique](#make_unique)|[owner_less](#owner_less)|[return_temporary_buffer](#return_temporary_buffer)|
|[static_pointer_cast](#static_pointer_cast)|[swap (C++ 標準程式庫)](#swap)|[undeclare_no_pointers](#undeclare_no_pointers)|
|[undeclare_reachable](#undeclare_reachable)|[uninitialized_copy](#uninitialized_copy)|[uninitialized_copy_n](#uninitialized_copy_n)|
|[uninitialized_fill](#uninitialized_fill)|[uninitialized_fill_n](#uninitialized_fill_n)|

## <a name="addressof"></a>  addressof

取得物件真正的位址。

```cpp
template <class T>
T* addressof(T& Val);
```

### <a name="parameters"></a>參數

*Val*<br/>
要取得真正位址的物件或函式。

### <a name="return-value"></a>傳回值

物件或函式所參考的實際位址*Val*，即使多載`operator&()`存在。

### <a name="remarks"></a>備註

## <a name="align"></a>  align

將指定大小的儲存體 (由特定對齊規格所對齊) 放入指定儲存體的第一個可能位址。

```cpp
void* align(
    size_t Alignment, // input
    size_t Size,      // input
    void*& Ptr,        // input/output
    size_t& Space     // input/output
);
```

### <a name="parameters"></a>參數

*對齊*<br/>
嘗試的對齊界限。

*Size*<br/>
對齊儲存體的大小 (位元組)。

*Ptr*<br/>
要使用的可用連續儲存集區的開始位址。 這個參數也是一個 output 參數，並設定為包含新的起始位址，如果對齊成功。 如果 `align()` 不成功，則不會修改這個參數。

*空格鍵*<br/>
`align()` 可用來建立對齊儲存體的總空間。 這個參數也是輸出參數，在對齊儲存體和任何關聯的額外負荷減去之後，會包含儲存緩衝區中剩下的調整空間。

如果 `align()` 不成功，則不會修改這個參數。

### <a name="return-value"></a>傳回值

如果可用空間，不符合要求的對齊的緩衝區為 null 指標否則，新的值*Ptr*。

### <a name="remarks"></a>備註

已修改*Ptr*並*空間*參數可讓您呼叫`align()`重複在同一個緩衝區，可能包含不同的值*對齊*和*大小*。 下列程式碼片段示範`align()` 的一個用法。

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

## <a name="allocate_shared"></a>  allocate_shared

建立 `shared_ptr`，指向透過使用指定的配置器為特定類型配置及建構的物件。 傳回 `shared_ptr`。

```cpp
template <class Type, class Allocator, class... Types>
shared_ptr<Type>
allocate_shared(Allocator Alloc, Types&&... Args);
```

### <a name="parameters"></a>參數

*Alloc*<br/>
用來建立物件的配置器。

*Args*<br/>
成為物件的零個或多個引數。

### <a name="remarks"></a>備註

函式會建立物件`shared_ptr<Type>`，指向`Type(Args...)`所配置和建構之*配置*。

## <a name="const_pointer_cast"></a>  const_pointer_cast

常數轉型成 shared_ptr。

```cpp
template <class Ty, class Other>
shared_ptr<Ty>
const_pointer_cast(const shared_ptr<Other>& sp);
```

### <a name="parameters"></a>參數

*Ty*<br/>
傳回之共用指標所控制的類型。

*其他*<br/>
引數共用指標所控制的類型。

*其他*<br/>
引數共用指標。

### <a name="remarks"></a>備註

範本函式會傳回空的 shared_ptr 物件，如果`const_cast<Ty*>(sp.get())`會傳回 null 指標; 否則會傳回[shared_ptr 類別](../standard-library/shared-ptr-class.md)\<Ty > 擁有之資源的擁有者的物件`sp`。 運算式 `const_cast<Ty*>(sp.get())` 必須有效。

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

## <a name="declare_no_pointers"></a>  declare_no_pointers

通知記憶體回收行程，指出基底位址指標和區塊大小所定義之記憶體區塊中的字元未包含任何可追蹤的指標。

```cpp
void declare_no_pointers(
    char* ptr,
    size_t _Size);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*ptr*|已不再包含可追蹤指標的第一個位元位址。|
|*_Size*|開始區塊的大小*ptr* ，其中包含任何可追蹤指標。|

### <a name="remarks"></a>備註

函式會通知任何記憶體回收行程的位址範圍`[ ptr, ptr + _Size)`不再包含可追蹤的指標。 （任何指向已配置的儲存體必須不取值除非進行連線。）

## <a name="declare_reachable"></a>  declare_reachable

告知記憶體回收，指示的位址是前往配置儲存體且可連接。

```cpp
void declare_reachable(void* ptr);
```

### <a name="parameters"></a>參數

*ptr*<br/>
指向可存取、已配置之有效儲存區域的指標。

### <a name="remarks"></a>備註

如果*ptr*不是 null，函式會通知任何記憶體回收行程所*ptr*以下是供存取 （指向有效的已配置儲存體）。

## <a name="default_delete"></a>  default_delete

刪除配置的物件**new 運算子**。 適合搭配 `unique_ptr` 使用。

```cpp
struct default_delete {
   constexpr default_delete() noexcept = default;
   template <class Other, class = typename enable_if<is_convertible<Other*, T*>::value, void>::type>>
   default_delete(const default_delete<Other>&) noexcept;
   void operator()(T* Ptr) const noexcept;
};
```

### <a name="parameters"></a>參數

*Ptr*<br/>
要刪除的物件指標。

*其他*<br/>
要刪除的陣列項目類型。

### <a name="remarks"></a>備註

此範本類別描述`deleter`刪除配置的純量物件**new 運算子**適用於範本的類別、 `unique_ptr`。 它也具有明確的特製化 `default_delete<Type[]>`。

## <a name="dynamic_pointer_cast"></a>  dynamic_pointer_cast

動態轉換成 shared_ptr。

```cpp
template <class Ty, class Other>
shared_ptr<Ty>
dynamic_pointer_cast(const shared_ptr<Other>& sp);
```

### <a name="parameters"></a>參數

*Ty*<br/>
傳回之共用指標所控制的類型。

*其他*<br/>
引數共用指標所控制的類型。

*sp*<br/>
引數共用指標。

### <a name="remarks"></a>備註

範本函式會傳回空的 shared_ptr 物件，如果`dynamic_cast<Ty*>(sp.get())`會傳回 null 指標; 否則會傳回[shared_ptr 類別](../standard-library/shared-ptr-class.md)\<Ty > 擁有之資源的擁有者的物件*預存程序*. 運算式 `dynamic_cast<Ty*>(sp.get())` 必須有效。

### <a name="example"></a>範例

```cpp
// std__memory__dynamic_pointer_cast.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct base
{
    virtual ~base() {}
    int val;
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

    sp0->val = 3;
    std::cout << "sp1->val == " << sp1->val << std::endl;

    return (0);
}
```

```Output
sp1->val == 3
```

## <a name="get_deleter"></a>  get_deleter

從 shared_ptr 取得刪除者。

```cpp
template <class D, class Ty>
D* get_deleter(const shared_ptr<Ty>& sp);
```

### <a name="parameters"></a>參數

*D*<br/>
刪除者的類型。

*Ty*<br/>
共用指標所控制的類型。

*sp*<br/>
共用指標。

### <a name="remarks"></a>備註

範本函式傳回的指標類型的刪除者*D*屬於[shared_ptr 類別](../standard-library/shared-ptr-class.md)物件*sp*。 如果*sp*沒有任何刪除者或其刪除者不是型別的*D*函式會傳回 0。

### <a name="example"></a>範例

```cpp
// std__memory__get_deleter.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct base
{
    int val;
};

struct deleter
{
    void operator()(base *p)
    {
        delete p;
    }
};

int main()
{
    std::shared_ptr<base> sp0(new base);

    sp0->val = 3;
    std::cout << "get_deleter(sp0) != 0 == " << std::boolalpha
        << (std::get_deleter<deleter>(sp0) != 0) << std::endl;

    std::shared_ptr<base> sp1(new base, deleter());

    sp0->val = 3;
    std::cout << "get_deleter(sp1) != 0 == " << std::boolalpha
        << (std::get_deleter<deleter>(sp1) != 0) << std::endl;

    return (0);
}
```

```Output
get_deleter(sp0) != 0 == false
get_deleter(sp1) != 0 == true
```

## <a name="get_pointer_safety"></a>  get_pointer_safety

傳回任何記憶體回收行程所假設之指標安全的類型。

```cpp
pointer_safety get_pointer_safety();
```

### <a name="remarks"></a>備註

此函式傳回任何自動的記憶體回收行程所假設的指標安全的類型。

## <a name="get_temporary_buffer"></a>  get_temporary_buffer

為項目序列 (不超過指定的項目數目) 配置暫時儲存區。

```cpp
template <class Type>
pair<Type *, ptrdiff_t> get_temporary_buffer(ptrdiff_t count);
```

### <a name="parameters"></a>參數

*count*<br/>
所要求的元素數目上限，將針對這些元素配置記憶體。

### <a name="return-value"></a>傳回值

一個 `pair`，其第一個元件是指向所配置記憶體的指標，第二個元件提供緩衝區的大小，指出它所能儲存的元素數目上限。

### <a name="remarks"></a>備註

此函式會提出記憶體要求，但可能不會成功。 如果未配置任何緩衝區，此函式就會傳回一個配對，其中第二個元件等於零，而第一個元件等於 Null 指標。

此函式應僅用於暫時的記憶體。

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
   int intArray [ ] = { 10, 20, 30, 40, 100, 200, 300, 1000, 2000 };
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

## <a name="make_shared"></a>  make_shared

建立並傳回 `shared_ptr`，它會指向使用預設配置器從零個或多個引數建構的配置物件。 配置並建構指定類別的物件和 `shared_ptr` 來管理共用的物件擁有權，並傳回 `shared_ptr`。

```cpp
template <class Type, class... Types>
shared_ptr<Type>
make_shared(Types&&... _Args);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*_Args*|零或多個建構函式引數。 函式會根據所提供的引數推斷要叫用的建構函式多載。|

### <a name="remarks"></a>備註

使用 `make_shared` 做為建立物件和 `shared_ptr` 的一個簡單且更有效率的方式，並藉以同時管理物件的共用存取權。 語意上來說，這兩個陳述式是相等的：

```cpp
auto sp = std::shared_ptr<Example>(new Example(argument));
auto msp = std::make_shared<Example>(argument);
```

但是，第一個陳述式會產生兩個配置，而若 `shared_ptr` 物件配置成功之後，`Example` 配置失敗，則未命名的 `Example` 物件會遭到洩露。 使用 `make_shared` 的陳述式比較簡單，因為這樣只會使用一個函式呼叫。 這樣會更有效率，因為程式庫可以讓物件和智慧型指標進行單一配置。 這樣會更迅速，並會減少記憶體分散的情形，且絕不會發生其中一個配置出現例外但其他配置未出現例外的情形。 改善參考物件的程式碼位置，並更新智慧型指標中的參考計數，便能夠提升效能。

如果您不需要物件的共用存取權，請考慮使用 [make_unique](../standard-library/memory-functions.md#make_unique)。 如果您需要為物件指定自訂的配置器，請使用 [allocate_shared](../standard-library/memory-functions.md#allocate_shared)。 如果您的物件需要自訂刪除者，則您無法使用 `make_shared`，因為您無法將刪除者做為引數傳遞。

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

void CreateSharedPointers() {
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
   for (auto&& sp : playlist) {
      std::wcout << L"Playing " << sp->title_ <<
         L" by " << sp->artist_ << L", use count: " <<
         sp.use_count() << std::endl;
   }
}

int main() {
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

## <a name="make_unique"></a>  make_unique

建立並傳回指向指定類型之物件的 [unique_ptr](../standard-library/unique-ptr-class.md)，該類型是使用指定的引數所建構。

```cpp
// make_unique<T>
template <class T, class... Types>
unique_ptr<T>
make_unique(Types&&... Args)
{
    return (unique_ptr<T>(new T(forward<Types>(Args)...)));
}

// make_unique<T[]>
template <class T>
make_unique(size_t Size)
{
    return (unique_ptr<T>(new Elem[Size]()));
}

// make_unique<T[N]> disallowed
template <class T, class... Types>
typename enable_if<extent<T>::value != 0, void>::type
make_unique(Types&&...) = delete;
```

### <a name="parameters"></a>參數

*T*<br/>
`unique_ptr` 指向的物件類型。

*型別*<br/>
建構函式引數所指定的型別*Args*。

*Args*<br/>
要傳遞至類型的物件的建構函式的引數*T*。

*Elem*<br/>
型別的項目陣列*T*。

*Size*<br/>
在新陣列中要為其配置空間的元素數目。

### <a name="remarks"></a>備註

第一個多載用於單一物件、 陣列、 叫用第二個多載和第三個多載可防止您的型別引數中指定陣列大小 (make_unique\<T [N] >); 目前不支援這個建構標準。 當您使用 `make_unique` 來建立陣列的 `unique_ptr`，必須將陣列元素個別初始化。 如果您要將這個多載納入考量，較佳的選擇會是使用 [std::vector](../standard-library/vector-class.md)。

為了例外狀況安全，`make_unique` 實作很謹慎，因此建議您使用 `make_unique`，而不是直接呼叫 `unique_ptr` 建構函式。

### <a name="example"></a>範例

下列範例示範如何使用 `make_unique`。 如需更多範例，請參閱[如何：建立和使用 unique_ptr 執行個體](../cpp/how-to-create-and-use-unique-ptr-instances.md)。

[!code-cpp[stl_smart_pointers#214](../cpp/codesnippet/CPP/memory-functions_1.cpp)]

當您看到與 `unique_ptr` 有關的錯誤 C2280 時，通常都是因為您嘗試叫用它的複製建構函式，這是一個被刪除的函式。

## <a name="owner_less"></a>  owner_less

允許按擁有權混合比較共用指標和弱式指標。 傳回**真**如果 left 的參數排序在 right 參數之前，由成員函式`owner_before`。

```cpp
template <class Type>
struct owner_less; // not defined

template <class Type>
struct owner_less<shared_ptr<Type>> {
    bool operator()(
    const shared_ptr<Type>& left,
    const shared_ptr<Type>& right);

    bool operator()(
    const shared_ptr<Type>& left,
    const weak_ptr<Type>& right);

    bool operator()(
    const weak_ptr<Type>& left,
    const shared_ptr<Type>& right);
};

template <class Type>
struct owner_less<weak_ptr<Type>>
    bool operator()(
    const weak_ptr<Type>& left,
    const weak_ptr<Type>& right);

    bool operator()(
    const weak_ptr<Type>& left,
    const shared_ptr<Ty>& right);

    bool operator()(
    const shared_ptr<Type>& left,
    const weak_ptr<Type>& right);
};
```

### <a name="parameters"></a>參數

*_left*<br/>
共用指標或弱式指標。

*right*<br/>
共用指標或弱式指標。

### <a name="remarks"></a>備註

這些範本類型會將其所有成員運算子都定義成傳回 `left.owner_before(right)`。

## <a name="return_temporary_buffer"></a>  return_temporary_buffer

將使用 `get_temporary_buffer` 樣板函式配置的暫存記憶體取消配置。

```cpp
template <class Type>
void return_temporary_buffer(Type* _Pbuf);
```

### <a name="parameters"></a>參數

*_Pbuf*<br/>
指向要配置之記憶體的指標。

### <a name="remarks"></a>備註

此函式應僅用於暫時的記憶體。

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
   int intArray [ ] = { 10, 20, 30, 40, 100, 200, 300 };
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
   return_temporary_buffer ( tempBuffer );
}
```

```Output
The number of integers in the array is: 7.
The number of elements that the allocated memory
could store is given by: resultPair.second = 7.
```

## <a name="static_pointer_cast"></a>  static_pointer_cast

靜態轉型至 shared_ptr。

```cpp
template <class Ty, class Other>
shared_ptr<Ty>
static_pointer_cast(const shared_ptr<Other>& sp);
```

### <a name="parameters"></a>參數

*Ty*<br/>
傳回之共用指標所控制的類型。

*其他*<br/>
引數共用指標所控制的類型。

*其他*<br/>
引數共用指標。

### <a name="remarks"></a>備註

範本函式會傳回空的 shared_ptr 物件，如果`sp`為空`shared_ptr`物件; 否則會傳回[shared_ptr 類別](../standard-library/shared-ptr-class.md)\<Ty > 擁有之資源的擁有者的物件`sp`. 運算式 `static_cast<Ty*>(sp.get())` 必須有效。

### <a name="example"></a>範例

```cpp
// std__memory__static_pointer_cast.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct base
{
    int val;
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

    sp0->val = 3;
    std::cout << "sp1->val == " << sp1->val << std::endl;

    return (0);
}
```

```Output
sp1->val == 3
```

## <a name="swap"></a>  swap (C++ 標準程式庫)

交換兩個 shared_ptr 或 weak_ptr 物件。

```cpp
template <class Ty, class Other>
void swap(shared_ptr<Ty>& left, shared_ptr<Other>& right);

template <class Ty, class Other>
void swap(weak_ptr<Ty>& left, weak_ptr<Other>& right);
```

### <a name="parameters"></a>參數

*Ty*<br/>
由左側共用/弱式指標控制的類型。

*其他*<br/>
由右側共用/弱式指標所控制的類型。

*left*<br/>
左側共用/弱式指標。

*right*<br/>
右側共用/弱式指標。

### <a name="remarks"></a>備註

範本函式呼叫 `left.swap(right)`。

### <a name="example"></a>範例

```cpp
// std__memory__swap.cpp
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

## <a name="undeclare_no_pointers"></a>  undeclare_no_pointers

通知記憶體回收行程，基底位址指標和區塊大小定義的記憶體區塊中的字元現在可能會包含可追蹤的指標。

```cpp
void undeclare_no_pointers(
    char* ptr,
    size_t _Size);
```

### <a name="remarks"></a>備註

函式會通知任何記憶體回收行程的位址範圍`[ptr, ptr + _Size)`現在可能會包含可追蹤的指標。

## <a name="undeclare_reachable"></a>  undeclare_reachable

撤銷指定的記憶體位置的連線能力的宣告。

```cpp
template <class Type>
Type *undeclare_reachable(Type* ptr);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*ptr*|指向要宣告為不可存取之記憶體位置的指標。|

### <a name="remarks"></a>備註

如果*ptr*不是**nullptr**，函式會通知任何記憶體回收行程所*ptr*不再可供存取。 它會傳回以安全方式衍生的指標比較相等*ptr*。

## <a name="uninitialized_copy"></a>  uninitialized_copy

從指定的來源範圍將物件複製到未初始化的目的範圍內。

```cpp
template <class InputIterator, class ForwardIterator>
ForwardIterator uninitialized_copy(InputIterator first, InputIterator last, ForwardIterator dest);
```

### <a name="parameters"></a>參數

*first*<br/>
輸入迭代器，為來源範圍中的第一個項目定址。

*last*<br/>
輸入迭代器，為來源範圍中的最後一個項目定址。

*dest*<br/>
正向迭代器，為目的範圍中的第一個項目定址。

### <a name="return-value"></a>傳回值

正向迭代器，定址目的範圍之外的第一個位置，除非來源範圍是空白。

### <a name="remarks"></a>備註

這個演算法允許記憶體配置與物件建構分開處理。

樣板函式有效地執行：

```cpp
while (first != last) {
    new (static_cast<void*>(&* dest++))
        typename iterator_traits<InputIterator>::value_type(*first++);
}
return dest;
```

除非程式碼擲回例外狀況。 在這種情況下，會終結所有建構的物件，並重新擲回例外狀況。

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
    Integer(int x) : val(x) {}
    int get() { return val; }
private:
    int val;
};

int main()
{
    int Array[] = { 10, 20, 30, 40 };
    const int N = sizeof(Array) / sizeof(int);

    int i;
    cout << "The initialized Array contains " << N << " elements: ";
    for (i = 0; i < N; i++)
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

## <a name="uninitialized_copy_n"></a>  uninitialized_copy_n

從輸入迭代器建立所指定項目數的複本。 複本會放在正向迭代器中。

```cpp
template <class InputIterator, class Size, class ForwardIterator>
ForwardIterator uninitialized_copy_n(
    InputIterator first,
    Size count,
    ForwardIterator dest);
```

### <a name="parameters"></a>參數

*first*<br/>
輸入迭代器，參考要複製的物件。

*count*<br/>
帶正負號或不帶正負號的整數類型，指定複製物件的次數。

*dest*<br/>
正向迭代器，參考放置新複本的位置。

### <a name="return-value"></a>傳回值

正向迭代器，定址目的之外的第一個位置。 如果來源範圍是空的迭代器定址*第一個*。

### <a name="remarks"></a>備註

樣板函式有效地執行下列：

```cpp
    for (; 0 < count; --count)
        new (static_cast<void*>(&* dest++))
            typename iterator_traits<InputIterator>::value_type(*first++);
    return dest;
```

除非程式碼擲回例外狀況。 在這種情況下，會終結所有建構的物件，並重新擲回例外狀況。

## <a name="uninitialized_fill"></a>  uninitialized_fill

將所指定值的物件複製到未初始化的目的範圍內。

```cpp
template <class ForwardIterator, class Type>
void uninitialized_fill(ForwardIterator first, ForwardIterator last, const Type& val);
```

### <a name="parameters"></a>參數

*first*<br/>
正向迭代器，定址對象是要起始之目的範圍中的第一個元素。

*last*<br/>
正向迭代器，定址對象是要起始之目的範圍中的最後一個元素。

*val*<br/>
用來初始化目的範圍的值。

### <a name="remarks"></a>備註

這個演算法允許記憶體配置與物件建構分開處理。

樣板函式有效地執行：

```cpp
while (first != last)
    new (static_cast<void*>(&* first ++))
        typename iterator_traits<ForwardIterator>::value_type (val);
```

除非程式碼擲回例外狀況。 在這種情況下，會終結所有建構的物件，並重新擲回例外狀況。

### <a name="example"></a>範例

```cpp
// memory_uninit_fill.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

using namespace std;

class Integer {         // No default constructor
   public:
      Integer( int x ) : val( x ) {}
      int get( ) { return val; }
   private:
      int val;
};

int main( )
{
   const int N = 10;
   Integer val ( 25 );
   Integer* Array = ( Integer* ) malloc( N * sizeof( int ) );
   uninitialized_fill( Array, Array + N, val );
   int i;
   cout << "The initialized Array contains: ";
      for ( i = 0 ; i < N; i++ )
      {
         cout << Array [ i ].get( ) << " ";
      }
   cout << endl;
}
```

```Output
The initialized Array contains: 25 25 25 25 25 25 25 25 25 25
```

## <a name="uninitialized_fill_n"></a>  uninitialized_fill_n

將所指定值的物件複製到未初始化目的範圍的指定項目數內。

```cpp
template <class FwdIt, class Size, class Type>
void uninitialized_fill_n(ForwardIterator first, Size count, const Type& val);
```

### <a name="parameters"></a>參數

*first*<br/>
正向迭代器，為目的範圍中要起始的第一個項目定址。

*count*<br/>
要初始化的項目數目。

*val*<br/>
用來初始化目的範圍的值。

### <a name="remarks"></a>備註

這個演算法允許記憶體配置與物件建構分開處理。

樣板函式有效地執行：

```cpp
while (0 < count--)
    new (static_cast<void*>(&* first++))
        typename iterator_traits<ForwardIterator>::value_type(val);
```

除非程式碼擲回例外狀況。 在這種情況下，會終結所有建構的物件，並重新擲回例外狀況。

### <a name="example"></a>範例

```cpp
// memory_uninit_fill_n.cpp
// compile with: /EHsc /W3
#include <memory>
#include <iostream>

using namespace std;

class Integer {   // No default constructor
public:
   Integer( int x ) : val( x ) {}
   int get( ) { return val; }
private:
   int val;
};

int main() {
   const int N = 10;
   Integer val ( 60 );
   Integer* Array = ( Integer* ) malloc( N * sizeof( int ) );
   uninitialized_fill_n( Array, N, val );  // C4996
   int i;
   cout << "The uninitialized Array contains: ";
   for ( i = 0 ; i < N; i++ )
      cout << Array [ i ].get( ) <<  " ";
}
```

## <a name="see-also"></a>另請參閱

[\<memory>](../standard-library/memory.md)<br/>
