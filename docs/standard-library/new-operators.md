---
title: '&lt;新的&gt; 運算子和列舉'
ms.date: 11/04/2016
f1_keywords:
- new/std::operator delete
- new/std::operator new
ms.assetid: d1af4b56-9a95-4c65-ab01-bf43e982c7bd
ms.openlocfilehash: a3fd5b825fe1eaf3a07d9d001f03b9d0c64ffa31
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78854928"
---
# <a name="ltnewgt-operators-and-enums"></a>&lt;新的&gt; 運算子和列舉

## <a name="op_align_val_t"></a>列舉 align_val_t

```cpp
enum class align_val_t : size_t {};
```

## <a name="op_delete"></a>運算子 delete

由 delete 運算式呼叫的函式，用來取消設定物件之個別的儲存區。

```cpp
void operator delete(void* ptr) throw();
void operator delete(void *, void*) throw();
void operator delete(void* ptr, const std::nothrow_t&) throw();
```

### <a name="parameters"></a>參數

*ptr*\
要藉由刪除來讓值變成無效的指標。

### <a name="remarks"></a>備註

Delete 運算式會呼叫第一個函式，以呈現不正確*ptr*值。 程式可以使用此函式簽章來定義函式，以取代「C++ 標準程式庫」所定義的預設版本。 所需的行為是接受*null 的值，或*先前呼叫[operator new](../standard-library/new-operators.md#op_new)（**size_t**）所傳回的值。

*Ptr* null 值的預設行為是不執行任何動作。 *Ptr*的任何其他值都必須是先前所述的呼叫先前所傳回的值。 這類非 null*值的預設行為是回收*先前呼叫所配置的儲存體。 在後續呼叫 `operator new`（**size_t**）或任何 `calloc`（ **size_t**）、`malloc`（ **size_t**）或 `realloc`（ **void** <strong>\*</strong>， **size_t**）的情況下，會將這類回收的所有儲存空間的部分或全部未指定。

呼叫第二個函式的是與 **new**( **std::size_t**) 格式之 new 運算式對應的位置 delete 運算式。 它不會執行任何動作。

呼叫第三個函式的是與 **new**( **std::size_t**, **conststd::nothrow_t&** ) 格式之 new 運算式對應的位置 delete 運算式。 程式可以使用此函式簽章來定義函式，以取代「C++ 標準程式庫」所定義的預設版本。 所需的行為是接受 `ptr` 的值，該值為 Null 或是先前對 `operator new`( **size_t**) 的呼叫所傳回的值。 預設行為是評估**delete**（`ptr`）。

### <a name="example"></a>範例

如需使用**operator delete**的範例，請參閱[operator new](../standard-library/new-operators.md#op_new) 。

## <a name="op_delete_arr"></a>operator delete []

由 delete 陳述式呼叫的函式，藉此取消配置物件陣列的儲存區。

```cpp
void operator delete[](void* ptr) throw();
void operator delete[](void *, void*) throw();
void operator delete[](void* ptr, const std::nothrow_t&) throw();
```

### <a name="parameters"></a>參數

*ptr*\
要藉由刪除來讓值變成無效的指標。

### <a name="remarks"></a>備註

第一個函式是由 `delete[]` 運算式呼叫，以呈現不正確*ptr*值。 此函式可被取代，因為程式可以使用此函式簽章來定義函式，以取代「C++ 標準程式庫」所定義的預設版本。 所需的行為是接受*null 的值，或*先前呼叫[operator new&#91;](../standard-library/new-operators.md#op_new_arr)（**size_t**）所傳回的值。 *Ptr* null 值的預設行為是不執行任何動作。 *Ptr*的任何其他值都必須是先前所述的呼叫先前所傳回的值。 這類非 null*值的預設行為是回收*先前呼叫所配置的儲存體。 在後續呼叫[operator new](../standard-library/new-operators.md#op_new)（**size_t**）或任何 `calloc`（**size_t**）、`malloc`（**size_t**）或 `realloc`（ **void** <strong>\*</strong>， **size_t**）的情況下，會將這類回收的所有儲存區所配置的條件全部未指定。

第二個函式是由對應于格式 `new[]`（**std：： size_t**）之 `new[]` 運算式的位置 `delete[]` 運算式所呼叫。 它不會執行任何動作。

呼叫第三個函式的是與 `new[]`( `new[]`std::size_t **,** const std::nothrow_t& **) 格式之**  運算式對應的位置 delete 運算式。 程式可以使用此函式簽章來定義函式，以取代「C++ 標準程式庫」所定義的預設版本。 所需的行為是接受*null 的值，或*先前呼叫 operator `new[]`（**size_t**）所傳回的值。 預設行為是評估 `delete[]`( `ptr`)。

### <a name="example"></a>範例

如需使用 [ 的範例，請參閱 ](../standard-library/new-operators.md#op_new_arr)operator new&#91;&#93;`operator delete[]`。

## <a name="op_new"></a>operator new

new 運算式所呼叫來為個別物件配置儲存體的函式。

```cpp
void* operator new(std::size_t count) throw(bad_alloc);
void* operator new(std::size_t count, const std::nothrow_t&) throw();
void* operator new(std::size_t count, void* ptr) throw();
```

### <a name="parameters"></a>參數

*計數*\
要配置的儲存體位元組數。

*ptr*\
必須傳回指標。

### <a name="return-value"></a>傳回值

新配置之儲存體的最低位元組位址指標。 或*ptr*。

### <a name="remarks"></a>備註

呼叫第一個函式的是 new 運算式，用來配置已適當校準之 `count` 個位元組的儲存體，以代表該大小的任何物件。 程式可以使用此函式簽章來定義替代函式，以取代「C++ 標準程式庫」所定義的預設版本，因此可加以取代。

所需的行為是只在可依要求配置儲存體的情況下才傳回非 Null 指標。 每個這類配置都會為與任何其他已配置儲存體皆不相鄰的儲存體產生一個指標。 在由後續的呼叫所配置之儲存體的順序和相鄰性方面，並未指定。 也未指定初始預存值。 傳回的指標會指向已配置之儲存體的開頭 (最低位元組位址)。 如果 count 為零，傳回的值便不會等於函式所傳回的任何其他值。

預設行為是執行迴圈。 在該迴圈內，函式會先嘗試配置所要求的儲存體。 至於該嘗試是否涉及對 `malloc`( **size_t**) 的呼叫，並未指定。 如果該嘗試成功，函式就會傳回已配置之儲存體的指標。 否則，函式會呼叫指定的 [new 處理常式](../standard-library/new-typedefs.md#new_handler)。 如果所呼叫的函式返回，迴圈就會重複執行。 當嘗試配置所要求的儲存體成功時，或當所呼叫的函式並未返回時，迴圈便會終止。

所需的 new 處理常式行為是執行下列其中一項操作：

- 讓更多儲存體可供配置，然後返回。

- 請呼叫**abort**或**exit**（`int`）。

- 擲回 **bad_alloc** 類型的物件。

[new 處理常式](../standard-library/new-typedefs.md#new_handler)的預設行為是擲回 `bad_alloc` 類型的物件。 Null 指標會指定預設的 new 處理常式。

`operator new`（**size_t**）連續呼叫所配置的儲存體順序和 contiguity 未指定，如同儲存在該處的初始值。

呼叫第二個函式的是位置 new 運算式，用來配置已適當校準之 `count` 個位元組的儲存體，以代表該大小的任何物件。 程式可以使用此函式簽章來定義替代函式，以取代「C++ 標準程式庫」所定義的預設版本，因此可加以取代。

預設行為是在該函式成功時傳回 `operator new`（`count`）。 否則，會傳回 Null 指標。

呼叫第三個函式的是 **new** ( **args**) T 格式的位置 *new* 運算式。此處的 *args* 是由單一物件指標所組成。 這對於在已知位址建構物件來說，相當有用。 此函式會傳回 *ptr*。

若要釋放由**operator new**所配置的儲存體，請呼叫[operator delete](../standard-library/new-operators.md#op_delete)。

如需新的擲回或非擲回行為的詳細資訊，請參閱[new 和 Delete 運算子](../cpp/new-and-delete-operators.md)。

### <a name="example"></a>範例

```cpp
// new_op_new.cpp
// compile with: /EHsc
#include<new>
#include<iostream>

using namespace std;

class MyClass
{
public:
   MyClass( )
   {
      cout << "Construction MyClass." << this << endl;
   };

   ~MyClass( )
   {
      imember = 0; cout << "Destructing MyClass." << this << endl;
   };
   int imember;
};

int main( )
{
   // The first form of new delete
   MyClass* fPtr = new MyClass;
   delete fPtr;

   // The second form of new delete
   MyClass* fPtr2 = new( nothrow ) MyClass;
   delete fPtr2;

   // The third form of new delete
   char x[sizeof( MyClass )];
   MyClass* fPtr3 = new( &x[0] ) MyClass;
   fPtr3 -> ~MyClass();
   cout << "The address of x[0] is : " << ( void* )&x[0] << endl;
}
```

## <a name="op_new_arr"></a>operator new []

new 運算式所呼叫來為物件陣列配置儲存體的配置函式。

```cpp
void* operator new[](std::size_t count) throw(std::bad_alloc);
void* operator new[](std::size_t count, const std::nothrow_t&) throw();
void* operator new[](std::size_t count, void* ptr) throw();
```

### <a name="parameters"></a>參數

*計數*\
要為陣列物件配置的儲存體位元組數。

*ptr*\
必須傳回指標。

### <a name="return-value"></a>傳回值

新配置之儲存體的最低位元組位址指標。 或*ptr*。

### <a name="remarks"></a>備註

呼叫第一個函式的是 `new[]` 運算式，用來配置已適當校準之 `count` 個位元組的儲存體，以代表等於或小於該大小的任何陣列物件。 程式可以使用此函式簽章來定義函式，以取代「C++ 標準程式庫」所定義的預設版本。 所需的行為與[operator new](../standard-library/new-operators.md#op_new)（**size_t**）相同。 預設行為是傳回 `operator new`( `count`)。

呼叫第二個函式的是位置 `new[]` 運算式，用來配置已適當校準之 `count` 個位元組的儲存體，以代表該大小的任何陣列物件。 程式可以使用此函式簽章來定義函式，以取代「C++ 標準程式庫」所定義的預設版本。 預設行為是在該函式成功時傳回**operatornew**（`count`）。 否則，會傳回 Null 指標。

呼叫第三個函式的是 `new[]`new **(** args *)* T **[** N **] 格式的位置**  運算式。 此處的 *args* 是由單一物件指標所組成。 此函式會傳回 `ptr`。

若要釋出 `operator new[]` 所配置的儲存體，請呼叫 [operator delete&#91;&#93;](../standard-library/new-operators.md#op_delete_arr)。

如需有關 new 的擲回或不擲回行為的詳細資訊，請參閱 [new 和 delete 運算子](../cpp/new-and-delete-operators.md)。

### <a name="example"></a>範例

```cpp
// new_op_alloc.cpp
// compile with: /EHsc
#include <new>
#include <iostream>

using namespace std;

class MyClass {
public:
   MyClass() {
      cout << "Construction MyClass." << this << endl;
   };

   ~MyClass() {
      imember = 0; cout << "Destructing MyClass." << this << endl;
      };
   int imember;
};

int main() {
   // The first form of new delete
   MyClass* fPtr = new MyClass[2];
   delete[ ] fPtr;

   // The second form of new delete
   char x[2 * sizeof( MyClass ) + sizeof(int)];

   MyClass* fPtr2 = new( &x[0] ) MyClass[2];
   fPtr2[1].~MyClass();
   fPtr2[0].~MyClass();
   cout << "The address of x[0] is : " << ( void* )&x[0] << endl;

   // The third form of new delete
   MyClass* fPtr3 = new( nothrow ) MyClass[2];
   delete[ ] fPtr3;
}
```
