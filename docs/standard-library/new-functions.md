---
title: '&lt;new&gt; 函式'
ms.date: 11/04/2016
f1_keywords:
- new/std::get_new_handler
- new/std::nothrow
- new/std::set_new_handler
ms.assetid: e250f06a-b025-4509-ae7a-5356d56aad7d
ms.openlocfilehash: 6b51a5bcbb9c90370cef1391d4020862d2e2cefd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212172"
---
# <a name="ltnewgt-functions"></a>&lt;new&gt; 函式

## <a name="get_new_handler"></a><a name="get_new_handler"></a>get_new_handler

```cpp
new_handler get_new_handler() noexcept;
```

### <a name="remarks"></a>備註

傳回目前的 `new_handler`。

## <a name="launder"></a><a name="launder"></a>launder

```cpp
template <class T>
    constexpr T* launder(T* ptr) noexcept;
```

### <a name="parameters"></a>參數

*指標*\
記憶體中的位元組位址，其中包含類型類似*T*的物件。

### <a name="return-value"></a>傳回值

指向 X 的類型*T \* *的值。

### <a name="remarks"></a>備註

也稱為指標優化屏障。

當常數運算式中可能使用其引數的值時，用來做為常數運算式。 如果儲存在另一個物件所佔用的儲存體（具有類似指標的物件）中，可透過指向物件的指標值來連線到一個位元組的儲存體。

### <a name="example"></a>範例

```cpp
struct X { const int n; };

X *p = new X{3};
const int a = p->n;
new (p) X{5}; // p does not point to new object because X::n is const
const int b = p->n; // undefined behavior
const int c = std::launder(p)->n; // OK
```

## <a name="nothrow"></a><a name="nothrow"></a>nothrow

提供物件，以便當做和版本的引數使用 **`nothrow`** **`new`** **`delete`** 。

```cpp
extern const std::nothrow_t nothrow;
```

### <a name="remarks"></a>備註

此物件是用來作為函式引數，以符合參數類型 [std::nothrow_t](../standard-library/nothrow-t-structure.md)。

### <a name="example"></a>範例

如需如何使用 `std::nothrow_t` 作為函式參數的範例，請參閱 [operator new](../standard-library/new-operators.md#op_new) 和 [operator new&#91;&#93;](../standard-library/new-operators.md#op_new_arr)。

## <a name="set_new_handler"></a><a name="set_new_handler"></a>set_new_handler

安裝當**operator new**在嘗試配置記憶體時失敗時所要呼叫的使用者函式。

```cpp
new_handler set_new_handler(new_handler Pnew) throw();
```

### <a name="parameters"></a>參數

*Pnew*\
`new_handler`要安裝的。

### <a name="return-value"></a>傳回值

第一次呼叫時，會傳回 0，後續呼叫時，則傳回前一個 `new_handler`。

### <a name="remarks"></a>備註

函式會將*Pnew*儲存在它所維護的靜態[新處理常式](../standard-library/new-typedefs.md#new_handler)指標中，然後傳回先前儲存在指標中的值。 New 處理常式是由[operator new](../standard-library/new-operators.md#op_new)（**size_t**）所使用。

### <a name="example"></a>範例

```cpp
// new_set_new_handler.cpp
// compile with: /EHsc
#include<new>
#include<iostream>

using namespace std;
void __cdecl newhandler( )
{
   cout << "The new_handler is called:" << endl;
   throw bad_alloc( );
   return;
}

int main( )
{
   set_new_handler (newhandler);
   try
   {
      while ( 1 )
      {
         new int[5000000];
         cout << "Allocating 5000000 ints." << endl;
      }
   }
   catch ( exception e )
   {
      cout << e.what( ) << endl;
   }
}
```

```Output
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
The new_handler is called:
bad allocation
```
