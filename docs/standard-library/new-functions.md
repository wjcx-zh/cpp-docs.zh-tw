---
title: '&lt;new&gt; 函式'
ms.date: 11/04/2016
f1_keywords:
- new/std::get_new_handler
- new/std::nothrow
- new/std::set_new_handler
ms.assetid: e250f06a-b025-4509-ae7a-5356d56aad7d
ms.openlocfilehash: c912e5be07ea0ebdd3148d30c80c39a5f8cfa1a5
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68243672"
---
# <a name="ltnewgt-functions"></a>&lt;new&gt; 函式

## <a name="get_new_handler"></a> get_new_handler

```cpp
new_handler get_new_handler() noexcept;
```

### <a name="remarks"></a>備註

傳回目前`new_handler`。

## <a name="launder"></a> launder

```cpp
template <class T>
    constexpr T* launder(T* ptr) noexcept;
```

### <a name="parameters"></a>參數

*ptr*\
其中包含物件類型的記憶體中的位元組的位址是類似*T*。

### <a name="return-value"></a>傳回值

型別的值*T\** 指向 X。

### <a name="remarks"></a>備註

也稱為指標最佳化屏障。

當其引數的值可用於常數運算式，請使用當做常數運算式。 連線到透過指向的物件，如果是在另一個物件，具有類似指標的物件所佔用的儲存體的指標值的位元組的儲存體。

### <a name="example"></a>範例

```cpp
struct X { const int n; };

X *p = new X{3};
const int a = p->n;
new (p) X{5}; // p does not point to new object because X::n is const
const int b = p->n; // undefined behavior
const int c = std::launder(p)->n; // OK
```

## <a name="nothrow"></a> nothrow

提供要用來做為引數物件**nothrow**新版**新**並**刪除**。

```cpp
extern const std::nothrow_t nothrow;
```

### <a name="remarks"></a>備註

此物件是用來作為函式引數，以符合參數類型 [std::nothrow_t](../standard-library/nothrow-t-structure.md)。

### <a name="example"></a>範例

如需如何使用 `std::nothrow_t` 作為函式參數的範例，請參閱 [operator new](../standard-library/new-operators.md#op_new) 和 [operator new&#91;&#93;](../standard-library/new-operators.md#op_new_arr)。

## <a name="set_new_handler"></a> set_new_handler

安裝時要呼叫的使用者函式**new 運算子**中嘗試配置記憶體失敗。

```cpp
new_handler set_new_handler(new_handler Pnew) throw();
```

### <a name="parameters"></a>參數

*Pnew*\
`new_handler`安裝。

### <a name="return-value"></a>傳回值

第一次呼叫時，會傳回 0，後續呼叫時，則傳回前一個 `new_handler`。

### <a name="remarks"></a>備註

此函式會*Pnew*的靜態[新的處理常式](../standard-library/new-typedefs.md#new_handler)指標，它會維護，然後傳回先前儲存的指標的值。 新的處理常式會由[new 運算子](../standard-library/new-operators.md#op_new)(**size_t**)。

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
