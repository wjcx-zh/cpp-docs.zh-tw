---
title: '&lt;new&gt; 函式 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- new/std::nothrow
- new/std::set_new_handler
ms.assetid: e250f06a-b025-4509-ae7a-5356d56aad7d
ms.openlocfilehash: 6192805f0f427f86267a646b11d9f1d3365a1d57
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716036"
---
# <a name="ltnewgt-functions"></a>&lt;new&gt; 函式

|||
|-|-|
|[nothrow](#nothrow)|[set_new_handler](#set_new_handler)|

## <a name="nothrow"></a>  nothrow

提供要用來做為引數物件**nothrow**新版**新**並**刪除**。

```cpp
extern const std::nothrow_t nothrow;
```

### <a name="remarks"></a>備註

此物件是用來作為函式引數，以符合參數類型 [std::nothrow_t](../standard-library/nothrow-t-structure.md)。

### <a name="example"></a>範例

如需如何使用 `std::nothrow_t` 作為函式參數的範例，請參閱 [operator new](../standard-library/new-operators.md#op_new) 和 [operator new&#91;&#93;](../standard-library/new-operators.md#op_new_arr)。

## <a name="set_new_handler"></a>  set_new_handler

安裝時要呼叫的使用者函式**new 運算子**中嘗試配置記憶體失敗。

```cpp
new_handler set_new_handler(new_handler Pnew) throw();
```

### <a name="parameters"></a>參數

*Pnew*<br/>
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

## <a name="see-also"></a>另請參閱

[\<new>](../standard-library/new.md)<br/>
