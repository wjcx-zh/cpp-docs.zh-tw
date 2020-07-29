---
title: ComPtr 類別
ms.date: 06/02/2020
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr
- client/Microsoft::WRL::ComPtr::As
- client/Microsoft::WRL::ComPtr::AsIID
- client/Microsoft::WRL::ComPtr::AsWeak
- client/Microsoft::WRL::ComPtr::Attach
- client/Microsoft::WRL::ComPtr::ComPtr
- client/Microsoft::WRL::ComPtr::CopyTo
- client/Microsoft::WRL::ComPtr::Detach
- client/Microsoft::WRL::ComPtr::Get
- client/Microsoft::WRL::ComPtr::GetAddressOf
- client/Microsoft::WRL::ComPtr::InternalAddRef
- client/Microsoft::WRL::ComPtr::InternalRelease
- client/Microsoft::WRL::ComPtr::operator&
- client/Microsoft::WRL::ComPtr::operator->
- client/Microsoft::WRL::ComPtr::operator=
- client/Microsoft::WRL::ComPtr::operator==
- client/Microsoft::WRL::ComPtr::operator!=
- client/Microsoft::WRL::ComPtr::operator Microsoft::WRL::Details::BoolType
- client/Microsoft::WRL::ComPtr::ptr_
- client/Microsoft::WRL::ComPtr::ReleaseAndGetAddressOf
- client/Microsoft::WRL::ComPtr::Reset
- client/Microsoft::WRL::ComPtr::Swap
- client/Microsoft::WRL::ComPtr::~ComPtr
helpviewer_keywords:
- Microsoft::WRL::ComPtr class
- Microsoft::WRL::ComPtr::As method
- Microsoft::WRL::ComPtr::AsIID method
- Microsoft::WRL::ComPtr::AsWeak method
- Microsoft::WRL::ComPtr::Attach method
- Microsoft::WRL::ComPtr::ComPtr, constructor
- Microsoft::WRL::ComPtr::CopyTo method
- Microsoft::WRL::ComPtr::Detach method
- Microsoft::WRL::ComPtr::Get method
- Microsoft::WRL::ComPtr::GetAddressOf method
- Microsoft::WRL::ComPtr::InternalAddRef method
- Microsoft::WRL::ComPtr::InternalRelease method
- Microsoft::WRL::ComPtr::operator& operator
- Microsoft::WRL::ComPtr::operator-> operator
- Microsoft::WRL::ComPtr::operator= operator
- Microsoft::WRL::ComPtr::operator== operator
- Microsoft::WRL::ComPtr::operator!= operator
- Microsoft::WRL::ComPtr::operator Microsoft::WRL::Details::BoolType operator
- Microsoft::WRL::ComPtr::ptr_ data member
- Microsoft::WRL::ComPtr::ReleaseAndGetAddressOf method
- Microsoft::WRL::ComPtr::Reset method
- Microsoft::WRL::ComPtr::Swap method
- Microsoft::WRL::ComPtr::~ComPtr, destructor
ms.assetid: a6551902-6819-478a-8df7-b6f312ab1fb0
ms.openlocfilehash: 4f9462ca15f5db5c3f8c0de88ce5a76b142065b4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220544"
---
# <a name="comptr-class"></a>ComPtr 類別

建立代表範本參數所指定之介面的 *「智慧型指標」* (Smart Pointer) 類型。 `ComPtr` 自動維護基礎介面指標的參考計數，並在參考計數歸零時釋放介面。

## <a name="syntax"></a>語法

```cpp
template <typename T>
class ComPtr;

template<class T>
friend class ComPtr;
```

### <a name="parameters"></a>參數

*T*<br/>
表示的介面 `ComPtr` 。

*U*<br/>
目前 `ComPtr` 為 friend 的類別。 (使用這個參數的範本會受到保護)。

## <a name="remarks"></a>備註

`ComPtr<>`宣告代表基礎介面指標的類型。 使用 `ComPtr<>` 來宣告變數，然後使用箭號成員存取運算子（ `->` ）來存取介面成員函式。

如需智慧型指標的詳細資訊，請參閱[Com 編碼實務](/windows/win32/LearnWin32/com-coding-practices)文章的「Com 智慧型指標」子節。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

名稱            | 說明
--------------- | ---------------------------------------------------------------
`InterfaceType` | *T*範本參數所指定之類型的同義字。

### <a name="public-constructors"></a>公用建構函式

名稱                             | 說明
-------------------------------- | --------------------------------------------------------------------------------------------------------------------
[ComPtr：： ComPtr](#comptr)        | 初始化 `ComPtr` 類別的新執行個體。 多載提供預設、複製、移動和轉換建構函式。
[ComPtr：： ~ ComPtr](#tilde-comptr) | 將的實例 `ComPtr` 。

### <a name="public-methods"></a>公用方法

名稱                                                      | 說明
--------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[ComPtr：： As](#as)                                         | 傳回 `ComPtr` 物件，表示指定之範本參數所識別的介面。
[ComPtr：： AsIID](#asiid)                                   | 傳回 `ComPtr` 物件，表示指定之介面識別碼所識別的介面。
[ComPtr：： AsWeak](#asweak)                                 | 擷取目前物件的弱式參考。
[ComPtr：： Attach](#attach)                                 | 將這個 `ComPtr` 與目前範本類型參數所指定的介面類別型產生關聯。
[ComPtr：： CopyTo](#copyto)                                 | 將與這個相關聯的目前或指定的介面複製 `ComPtr` 到指定的輸出指標。
[ComPtr：:D etach](#detach)                                 | 將這個 `ComPtr` 與它所代表的介面解除。
[ComPtr：： Get](#get)                                       | 抓取與這個相關聯之介面的指標 `ComPtr` 。
[ComPtr：： GetAddressOf](#getaddressof)                     | 抓取[ptr_](#ptr)資料成員的位址，其中包含這個所表示之介面的指標 `ComPtr` 。
[ComPtr：： ReleaseAndGetAddressOf](#releaseandgetaddressof) | 釋放與這個相關聯的介面， `ComPtr` 然後抓取[ptr_](#ptr)資料成員的位址，其中包含已釋放之介面的指標。
[ComPtr::Reset](#reset)                                   | 釋放與這個相關聯的介面 `ComPtr` ，並傳回新的參考計數。
[ComPtr：： Swap](#swap)                                     | `ComPtr`使用由指定之管理的介面，交換目前所管理的介面 `ComPtr` 。

### <a name="protected-methods"></a>保護方法

名稱                                        | 說明
------------------------------------------- | --------------------------------------------------------------------------------
[ComPtr：： InternalAddRef](#internaladdref)   | 遞增與這個相關聯之介面的參考計數 `ComPtr` 。
[ComPtr：： InternalRelease](#internalrelease) | 在與此相關聯的介面上執行 COM 發行作業 `ComPtr` 。

### <a name="public-operators"></a>公用運算子

名稱                                                                                           | 說明
---------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------
[ComPtr：： operator&](#operator-ampersand)                                                       | 抓取目前的位址 `ComPtr` 。
[ComPtr：： operator->](#operator-arrow)                                                          | 擷取目前範本參數所指定之類型的指標。
[ComPtr：： operator =](#operator-assign)                                                          | 將值指派給目前的 `ComPtr` 。
[ComPtr：： operator = =](#operator-equality)                                                       | 表示兩個 `ComPtr` 物件是否相等。
[ComPtr：： operator！ =](#operator-inequality)                                                     | 指出兩個 `ComPtr` 物件是否不相等。
[ComPtr：： operator Microsoft：： WRL：:D etails：： BoolType](#operator-microsoft-wrl-details-booltype) | 指出是否 `ComPtr` 正在管理介面的物件存留期。

### <a name="protected-data-members"></a>受保護的資料成員

名稱                 | 說明
-------------------- | ------------------------------------------------------------------------------------------
[ComPtr：:p tr_](#ptr) | 包含與這個相關聯之介面的指標，並由這個所管理 `ComPtr` 。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`ComPtr`

## <a name="requirements"></a>需求

**標頭：** client.h

**命名空間：** Microsoft::WRL

## <a name="comptrcomptr"></a><a name="tilde-comptr"></a>ComPtr：： ~ ComPtr

將的實例 `ComPtr` 。

```cpp
WRL_NOTHROW ~ComPtr();
```

## <a name="comptras"></a><a name="as"></a>ComPtr：： As

傳回 `ComPtr` 物件，表示指定之範本參數所識別的介面。

```cpp
template<typename U>
HRESULT As(
   _Out_ ComPtr<U>* p
) const;

template<typename U>
HRESULT As(
   _Out_ Details::ComPtrRef<ComPtr<U>> p
) const;
```

### <a name="parameters"></a>參數

*U*<br/>
要由參數*p*表示的介面。

*p&id*<br/>
`ComPtr`物件，表示參數*U*所指定的介面。參數*p*不能參考目前的 `ComPtr` 物件。

### <a name="remarks"></a>備註

第一個範本是程式碼中應該使用的表單。 第二個範本是內部的協助程式特製化。 它支援 c + + 語言功能，例如[auto](../../cpp/auto-cpp.md)類型推斷關鍵字。

### <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

## <a name="comptrasiid"></a><a name="asiid"></a>ComPtr：： AsIID

傳回 `ComPtr` 物件，表示指定之介面識別碼所識別的介面。

```cpp
WRL_NOTHROW HRESULT AsIID(
   REFIID riid,
   _Out_ ComPtr<IUnknown>* p
) const;
```

### <a name="parameters"></a>參數

*riid*<br/>
介面識別碼。

*p&id*<br/>
如果物件的識別碼等於*riid*的介面，則為*riid*參數所指定之介面的雙向間接指標。 否則為的指標 `IUnknown` 。

### <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

## <a name="comptrasweak"></a><a name="asweak"></a>ComPtr：： AsWeak

擷取目前物件的弱式參考。

```cpp
HRESULT AsWeak(
   _Out_ WeakRef* pWeakRef
);
```

### <a name="parameters"></a>參數

*pWeakRef*<br/>
當此作業完成時，即為弱式參考物件的指標。

### <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

## <a name="comptrattach"></a><a name="attach"></a>ComPtr：： Attach

將這個 `ComPtr` 與目前範本類型參數所指定的介面類別型產生關聯。

```cpp
void Attach(
   _In_opt_ InterfaceType* other
);
```

### <a name="parameters"></a>參數

*另一方面*<br/>
介面類別型。

## <a name="comptrcomptr"></a><a name="comptr"></a>ComPtr：： ComPtr

初始化 `ComPtr` 類別的新執行個體。 多載提供預設、複製、移動和轉換建構函式。

```cpp
WRL_NOTHROW ComPtr();

WRL_NOTHROW ComPtr(
   decltype(__nullptr)
);

template<class U>
WRL_NOTHROW ComPtr(
   _In_opt_ U *other
);

WRL_NOTHROW ComPtr(
   const ComPtr& other
);

template<class U>
WRL_NOTHROW ComPtr(
   const ComPtr<U> &other,
   typename ENABLE_IF<__is_convertible_to(U*, T*), void *>
);

WRL_NOTHROW ComPtr(
   _Inout_ ComPtr &&other
);

template<class U>
WRL_NOTHROW ComPtr(
   _Inout_ ComPtr<U>&& other, typename ENABLE_IF<__is_convertible_to(U*, T*), void *>
);
```

### <a name="parameters"></a>參數

*U*<br/>
*另*一個參數的類型。

*另一方面*<br/>
類型為*U*的物件。

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

第一個函式是預設的函數，它會隱含建立空的物件。 第二個函式會指定[__nullptr](../../extensions/nullptr-cpp-component-extensions.md)，以明確建立空的物件。

第三個函式會從指標所指定的物件建立物件。 ComPtr 現在擁有指向的記憶體，並維護它的參考計數。

第四個和第五個是複製的函式。 第五個函式會複製物件（如果它可轉換成目前的類型）。

第六和第七個函式是移動的函式。 第七個函式會移動物件（如果它可轉換成目前的類型）。

## <a name="comptrcopyto"></a><a name="copyto"></a>ComPtr：： CopyTo

將與這個相關聯的目前或指定的介面複製 `ComPtr` 到指定的指標。

```cpp
HRESULT CopyTo(
   _Deref_out_ InterfaceType** ptr
);

HRESULT CopyTo(
   REFIID riid,
   _Deref_out_ void** ptr
) const;

template<typename U>
HRESULT CopyTo(
   _Deref_out_ U** ptr
) const;
```

### <a name="parameters"></a>參數

*U*<br/>
類型名稱。

*ptr*<br/>
當此作業完成時，為要求之介面的指標。

*riid*<br/>
介面識別碼。

### <a name="return-value"></a>傳回值

如果成功，則 S_OK;否則，就是指出隱含作業失敗原因的 HRESULT `QueryInterface` 。

### <a name="remarks"></a>備註

第一個函式會傳回與這個相關聯之介面的指標複本 `ComPtr` 。 此函式一律會傳回 S_OK。

第二個函式會 `QueryInterface` 在與這個相關聯的介面上執行作業， `ComPtr` 以用於*riid*參數所指定的介面。

第三個函式會 `QueryInterface` `ComPtr` 針對*U*參數的基礎介面，在與此相關聯的介面上執行運算。

## <a name="comptrdetach"></a><a name="detach"></a>ComPtr：:D etach

解除這個 `ComPtr` 物件與它所代表之介面的交互。

```cpp
T* Detach();
```

### <a name="return-value"></a>傳回值

這個物件所表示之介面的指標 `ComPtr` 。

## <a name="comptrget"></a><a name="get"></a>ComPtr：： Get

抓取與這個相關聯之介面的指標 `ComPtr` 。

```cpp
T* Get() const;
```

### <a name="return-value"></a>傳回值

與這個相關聯之介面的指標 `ComPtr` 。

## <a name="comptrgetaddressof"></a><a name="getaddressof"></a>ComPtr：： GetAddressOf

抓取[ptr_](#ptr)資料成員的位址，其中包含這個所表示之介面的指標 `ComPtr` 。

```cpp
T* const* GetAddressOf() const;
T** GetAddressOf();
```

### <a name="return-value"></a>傳回值

變數的位址。

## <a name="comptrinternaladdref"></a><a name="internaladdref"></a>ComPtr：： InternalAddRef

遞增與這個相關聯之介面的參考計數 `ComPtr` 。

```cpp
void InternalAddRef() const;
```

### <a name="remarks"></a>備註

這個方法受到保護。

## <a name="comptrinternalrelease"></a><a name="internalrelease"></a>ComPtr：： InternalRelease

在與此相關聯的介面上執行 COM 發行作業 `ComPtr` 。

```cpp
unsigned long InternalRelease();
```

### <a name="remarks"></a>備註

這個方法受到保護。

## <a name="comptroperatoramp"></a><a name="operator-ampersand"></a>ComPtr：： operator&amp;

釋放與這個物件相關聯的介面 `ComPtr` ，然後抓取物件的位址 `ComPtr` 。

```cpp
Details::ComPtrRef<WeakRef> operator&()

const Details::ComPtrRef<const WeakRef> operator&() const
```

### <a name="return-value"></a>傳回值

對目前的弱式參考 `ComPtr` 。

### <a name="remarks"></a>備註

這個方法與[ComPtr：： GetAddressOf](#getaddressof)不同之處在于，這個方法會釋放介面指標的參考。 `ComPtr::GetAddressOf`當您需要介面指標的位址，但不想釋放該介面時，請使用。

## <a name="comptroperator-gt"></a><a name="operator-arrow"></a>ComPtr：： operator-&gt;

擷取目前範本參數所指定之類型的指標。

```cpp
WRL_NOTHROW Microsoft::WRL::Details::RemoveIUnknown<InterfaceType>* operator->() const;
```

### <a name="return-value"></a>傳回值

目前範本類型名稱所指定之類型的指標。

### <a name="remarks"></a>備註

此 helper 函式會移除使用 STDMETHOD 宏所造成的不必要額外負荷。 此函式會建立 `IUnknown` 類型 **`private`** ，而不是 **`virtual`** 。

## <a name="comptroperator"></a><a name="operator-assign"></a>ComPtr：： operator =

將值指派給目前的 `ComPtr` 。

```cpp
WRL_NOTHROW ComPtr& operator=(
   decltype(__nullptr)
);
WRL_NOTHROW ComPtr& operator=(
   _In_opt_ T *other
);
template <typename U>
WRL_NOTHROW ComPtr& operator=(
   _In_opt_ U *other
);
WRL_NOTHROW ComPtr& operator=(
   const ComPtr &other
);
template<class U>
WRL_NOTHROW ComPtr& operator=(
   const ComPtr<U>& other
);
WRL_NOTHROW ComPtr& operator=(
   _Inout_ ComPtr &&other
);
template<class U>
WRL_NOTHROW ComPtr& operator=(
   _Inout_ ComPtr<U>&& other
);
```

### <a name="parameters"></a>參數

*U*<br/>
類別。

*另一方面*<br/>
類型或另一個的指標、參考或右值參考 `ComPtr` 。

### <a name="return-value"></a>傳回值

目前的參考 `ComPtr` 。

### <a name="remarks"></a>備註

這個運算子的第一個版本會將空值指派給目前的 `ComPtr` 。

在第二個版本中，如果指派的介面指標與目前的 `ComPtr` 介面指標不同，則會將第二個介面指標指派給目前的 `ComPtr` 。

在第三個版本中，指派介面指標會指派給目前的 `ComPtr` 。

在第四個版本中，如果指派值的介面指標與目前的 `ComPtr` 介面指標不相同，則會將第二個介面指標指派給目前的 `ComPtr` 。

第五個版本是複製運算子;的參考 `ComPtr` 會指派給目前的 `ComPtr` 。

第六個版本是使用 move 語義的複製運算子;`ComPtr`如果有任何類型是靜態轉換，然後指派給目前的，則為的右值參考 `ComPtr` 。

第七個版本是使用 move 語義的複製運算子;`ComPtr`類型*U*的右值參考是靜態轉換，然後指派給目前的 `ComPtr` 。

## <a name="comptroperator"></a><a name="operator-equality"></a>ComPtr：： operator = =

表示兩個 `ComPtr` 物件是否相等。

```cpp
bool operator==(
   const ComPtr<T>& a,
   const ComPtr<U>& b
);

bool operator==(
   const ComPtr<T>& a,
   decltype(__nullptr)
);

bool operator==(
   decltype(__nullptr),
   const ComPtr<T>& a
);
```

### <a name="parameters"></a>參數

*為*<br/>
`ComPtr` 物件的參考。

*位元組*<br/>
另一個物件的參考 `ComPtr` 。

### <a name="return-value"></a>傳回值

**`true`** 如果物件*a*等於物件*b*，第一個運算子會產生，否則為 **`false`** 。

第二個和第三個運算子會產生， **`true`** 如果物件*a*等於 **`nullptr`** ，則為，否則為 **`false`** 。

## <a name="comptroperator"></a><a name="operator-inequality"></a>ComPtr：： operator！ =

指出兩個 `ComPtr` 物件是否不相等。

```cpp
bool operator!=(
   const ComPtr<T>& a,
   const ComPtr<U>& b
);

bool operator!=(
   const ComPtr<T>& a,
   decltype(__nullptr)
);

bool operator!=(
   decltype(__nullptr),
   const ComPtr<T>& a
);
```

### <a name="parameters"></a>參數

*為*<br/>
`ComPtr` 物件的參考。

*位元組*<br/>
另一個物件的參考 `ComPtr` 。

### <a name="return-value"></a>傳回值

**`true`** 如果物件*a*不等於物件*b*，第一個運算子會產生，否則為 **`false`** 。

第二個和第三個運算子 **`true`** 會產生，如果物件*a*不等於，則為 **`nullptr`** ，否則為 **`false`** 。

## <a name="comptroperator-microsoftwrldetailsbooltype"></a><a name="operator-microsoft-wrl-details-booltype"></a>ComPtr：： operator Microsoft：： WRL：:D etails：： BoolType

指出是否 `ComPtr` 正在管理介面的物件存留期。

```cpp
WRL_NOTHROW operator Microsoft::WRL::Details::BoolType() const;
```

### <a name="return-value"></a>傳回值

如果介面與此相關聯，則為 `ComPtr` [BoolStruct：： Member](boolstruct-structure.md#member)資料成員的位址，否則為 **`nullptr`** 。

## <a name="comptrptr_"></a><a name="ptr"></a>ComPtr：:p tr_

包含與這個相關聯之介面的指標，並由這個所管理 `ComPtr` 。

```cpp
InterfaceType *ptr_;
```

### <a name="remarks"></a>備註

`ptr_`是內部受保護的資料成員。

## <a name="comptrreleaseandgetaddressof"></a><a name="releaseandgetaddressof"></a>ComPtr：： ReleaseAndGetAddressOf

釋放與這個相關聯的介面， `ComPtr` 然後抓取[ptr_](#ptr)資料成員的位址，其中包含已釋放之介面的指標。

```cpp
T** ReleaseAndGetAddressOf();
```

### <a name="return-value"></a>傳回值

這個的[ptr_](#ptr)資料成員的位址 `ComPtr` 。

## <a name="comptrreset"></a><a name="reset"></a>ComPtr：： Reset

釋放與這個相關聯的介面 `ComPtr` ，並傳回新的參考計數。

```cpp
unsigned long Reset();
```

### <a name="return-value"></a>傳回值

基礎介面剩餘的參考數目（如果有的話）。

## <a name="comptrswap"></a><a name="swap"></a>ComPtr：： Swap

`ComPtr`使用由指定之管理的介面，交換目前所管理的介面 `ComPtr` 。

```cpp
void Swap(
   _Inout_ ComPtr&& r
);

void Swap(
   _Inout_ ComPtr& r
);
```

### <a name="parameters"></a>參數

*r*<br/>
`ComPtr`。
