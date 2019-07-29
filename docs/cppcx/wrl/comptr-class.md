---
title: ComPtr 類別
ms.date: 07/26/2019
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
ms.openlocfilehash: 889b722c91fd56613c5902eb4ce6439763a49bd9
ms.sourcegitcommit: 720b74dddb1cdf4e570d55103158304ee1df81f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2019
ms.locfileid: "68606495"
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
`ComPtr`表示的介面。

*U*<br/>
目前`ComPtr`為 friend 的類別。 (使用這個參數的範本會受到保護)。

## <a name="remarks"></a>備註

`ComPtr<>`宣告代表基礎介面指標的類型。 使用`ComPtr<>`來宣告變數, 然後使用箭號成員存取運算子 (`->`) 來存取介面成員函式。

如需智慧型指標的詳細資訊, 請參閱 MSDN Library 中[Com 編碼實務](/windows/desktop/LearnWin32/com-coding-practices)主題的「Com 智慧型指標」子節。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

名稱            | 描述
--------------- | ---------------------------------------------------------------
`InterfaceType` | *T*範本參數所指定之類型的同義字。

### <a name="public-constructors"></a>公用建構函式

名稱                             | 描述
-------------------------------- | --------------------------------------------------------------------------------------------------------------------
[ComPtr::ComPtr](#comptr)        | 初始化 `ComPtr` 類別的新執行個體。 多載提供預設、複製、移動和轉換建構函式。
[ComPtr::~ComPtr](#tilde-comptr) | 將的實例`ComPtr`。

### <a name="public-methods"></a>公用方法

名稱                                                      | 描述
--------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[ComPtr:: As](#as)                                         | `ComPtr`傳回物件, 表示指定之範本參數所識別的介面。
[ComPtr::AsIID](#asiid)                                   | `ComPtr`傳回物件, 表示指定之介面識別碼所識別的介面。
[ComPtr::AsWeak](#asweak)                                 | 擷取目前物件的弱式參考。
[ComPtr::Attach](#attach)                                 | 將這個`ComPtr`與目前範本類型參數所指定的介面類別型產生關聯。
[ComPtr::CopyTo](#copyto)                                 | 將與這個`ComPtr`相關聯的目前或指定的介面複製到指定的輸出指標。
[ComPtr::Detach](#detach)                                 | 將這個`ComPtr`與它所代表的介面解除。
[ComPtr::Get](#get)                                       | 抓取與這個`ComPtr`相關聯之介面的指標。
[ComPtr::GetAddressOf](#getaddressof)                     | 抓取[ptr_](#ptr)資料成員的位址, 其中包含這個`ComPtr`所表示之介面的指標。
[ComPtr::ReleaseAndGetAddressOf](#releaseandgetaddressof) | 釋放與這個`ComPtr`相關聯的介面, 然後抓取[ptr_](#ptr)資料成員的位址, 其中包含已釋放之介面的指標。
[ComPtr::Reset](#reset)                                   | 釋放與這個`ComPtr`相關聯之介面指標的所有參考。
[ComPtr::Swap](#swap)                                     | 使用由指定`ComPtr`之管理的介面`ComPtr` , 交換目前所管理的介面。

### <a name="protected-methods"></a>保護方法

名稱                                        | 描述
------------------------------------------- | --------------------------------------------------------------------------------
[ComPtr::InternalAddRef](#internaladdref)   | 遞增與這個`ComPtr`相關聯之介面的參考計數。
[ComPtr::InternalRelease](#internalrelease) | 在與此`ComPtr`相關聯的介面上執行 COM 發行作業。

### <a name="public-operators"></a>公用運算子

名稱                                                                                           | 描述
---------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------
[ComPtr::operator&](#operator-ampersand)                                                       | 抓取目前`ComPtr`的位址。
[ComPtr::operator->](#operator-arrow)                                                          | 擷取目前範本參數所指定之類型的指標。
[ComPtr::operator=](#operator-assign)                                                          | 將值指派給目前`ComPtr`的。
[ComPtr::operator==](#operator-equality)                                                       | 表示兩個 `ComPtr` 物件是否相等。
[ComPtr::operator!=](#operator-inequality)                                                     | 表示兩個 `ComPtr` 物件是否不相等。
[ComPtr:: operator Microsoft:: WRL::D etails:: BoolType](#operator-microsoft-wrl-details-booltype) | 指出是否`ComPtr`正在管理介面的物件存留期。

### <a name="protected-data-members"></a>受保護的資料成員

名稱                 | 描述
-------------------- | ------------------------------------------------------------------------------------------
[ComPtr::ptr_](#ptr) | 包含與這個相關聯之介面的指標, 並由這個`ComPtr`所管理。

## <a name="inheritance-hierarchy"></a>繼承階層

`ComPtr`

## <a name="requirements"></a>需求

**標頭：** client.h

**命名空間：** Microsoft:: WRL

## <a name="tilde-comptr"></a>ComPtr:: ~ ComPtr

將的實例`ComPtr`。

```cpp
WRL_NOTHROW ~ComPtr();
```

## <a name="as"></a>ComPtr:: As

`ComPtr`傳回物件, 表示指定之範本參數所識別的介面。

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

*p*<br/>
物件, 表示參數 U 所指定的介面。  `ComPtr`參數*p*不能參考目前`ComPtr`的物件。

### <a name="remarks"></a>備註

第一個範本是程式碼中應該使用的表單。 第二個範本是內部的，支援 C++ 語言功能的協助程式特製化，例如 [auto](../../cpp/auto-cpp.md) 類型推斷關鍵字。

### <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

## <a name="asiid"></a>ComPtr:: AsIID

`ComPtr`傳回物件, 表示指定之介面識別碼所識別的介面。

```cpp
WRL_NOTHROW HRESULT AsIID(
   REFIID riid,
   _Out_ ComPtr<IUnknown>* p
) const;
```

### <a name="parameters"></a>參數

*riid*<br/>
介面識別碼。

*p*<br/>
如果物件的識別碼等於*riid*的介面, 則為*riid*參數所指定之介面的雙向間接指標;否則為的指標`IUnknown`。

### <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

## <a name="asweak"></a>ComPtr:: AsWeak

擷取目前物件的弱式參考。

```cpp
HRESULT AsWeak(
   _Out_ WeakRef* pWeakRef
);
```

### <a name="parameters"></a>參數

*pWeakRef*<br/>
當此作業完成時, 即為弱式參考物件的指標。

### <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

## <a name="attach"></a>ComPtr:: Attach

將這個`ComPtr`與目前範本類型參數所指定的介面類別型產生關聯。

```cpp
void Attach(
   _In_opt_ InterfaceType* other
);
```

### <a name="parameters"></a>參數

*other*<br/>
介面類別型。

## <a name="comptr"></a>ComPtr::ComPtr

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

*other*<br/>
類型為*U*的物件。

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

第一個函式是預設的函式, 隱含會建立空的物件。 第二個函式會指定[__nullptr](../../extensions/nullptr-cpp-component-extensions.md), 以明確建立空的物件。

第三個函式會從指標所指定的物件建立物件。 ComPtr 現在擁有指向的記憶體, 並維護它的參考計數。

第四個和第五個是複製的函式。 第五個函式會複製物件 (如果它可轉換成目前的類型)。

第六和第七個函式是移動的函式。 第七個函式會移動物件 (如果它可轉換成目前的類型)。

## <a name="copyto"></a>ComPtr:: CopyTo

將與這個`ComPtr`相關聯的目前或指定的介面複製到指定的指標。

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
當此作業完成時, 為要求之介面的指標。

*riid*<br/>
介面識別碼。

### <a name="return-value"></a>傳回值

如果成功, 則為 S_OK;否則, 就是指出隱含`QueryInterface`作業失敗原因的 HRESULT。

### <a name="remarks"></a>備註

第一個函式會傳回與這個`ComPtr`相關聯之介面的指標複本。 這個函數一律會傳回 S_OK。

第二個函式`QueryInterface`會在與這個`ComPtr`相關聯的介面上執行作業, 以用於*riid*參數所指定的介面。

第三個函式`QueryInterface`會針對*U*參數的基礎介面`ComPtr` , 在與此相關聯的介面上執行運算。

## <a name="detach"></a>ComPtr::Detach

解除這個`ComPtr`物件與它所代表之介面的交互。

```cpp
T* Detach();
```

### <a name="return-value"></a>傳回值

這個`ComPtr`物件所表示之介面的指標。

## <a name="get"></a>ComPtr:: Get

抓取與這個`ComPtr`相關聯之介面的指標。

```cpp
T* Get() const;
```

### <a name="return-value"></a>傳回值

與這個`ComPtr`相關聯之介面的指標。

## <a name="getaddressof"></a>ComPtr::GetAddressOf

抓取[ptr_](#ptr)資料成員的位址, 其中包含這個`ComPtr`所表示之介面的指標。

```cpp
T* const* GetAddressOf() const;
T** GetAddressOf();
```

### <a name="return-value"></a>傳回值

變數的位址。

## <a name="internaladdref"></a>ComPtr::InternalAddRef

遞增與這個`ComPtr`相關聯之介面的參考計數。

```cpp
void InternalAddRef() const;
```

### <a name="remarks"></a>備註

這個方法受到保護。

## <a name="internalrelease"></a>ComPtr::InternalRelease

在與此`ComPtr`相關聯的介面上執行 COM 發行作業。

```cpp
void InternalRelease();
```

### <a name="remarks"></a>備註

這個方法受到保護。

## <a name="operator-ampersand"></a>ComPtr::operator&amp;

釋放與這個`ComPtr`物件相關聯的介面, 然後抓取`ComPtr`物件的位址。

```cpp
Details::ComPtrRef<WeakRef> operator&()

const Details::ComPtrRef<const WeakRef> operator&() const
```

### <a name="return-value"></a>傳回值

對目前`ComPtr`的弱式參考。

### <a name="remarks"></a>備註

這個方法與[ComPtr:: GetAddressOf](#getaddressof)不同之處在于, 這個方法會釋放介面指標的參考。 當`ComPtr::GetAddressOf`您需要介面指標的位址, 但不想釋放該介面時, 請使用。

## <a name="operator-arrow"></a>ComPtr:: operator-&gt;

擷取目前範本參數所指定之類型的指標。

```cpp
WRL_NOTHROW Microsoft::WRL::Details::RemoveIUnknown<InterfaceType>* operator->() const;
```

### <a name="return-value"></a>傳回值

目前範本類型名稱所指定之類型的指標。

### <a name="remarks"></a>備註

此 helper 函式會移除使用 STDMETHOD 宏所造成的不必要額外負荷。 此函式`IUnknown`會`private`建立類型`virtual`, 而不是。

## <a name="operator-assign"></a>ComPtr:: operator =

將值指派給目前`ComPtr`的。

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

*other*<br/>
類型或另`ComPtr`一個的指標、參考或右值參考。

### <a name="return-value"></a>傳回值

目前`ComPtr`的參考。

### <a name="remarks"></a>備註

這個運算子的第一個版本會將空值指派給目前`ComPtr`的。

在第二個版本中, 如果指派的介面指標與目前`ComPtr`的介面指標不同, 則會將第二個介面指標指派給目前`ComPtr`的。

在第三個版本中, 指派介面指標會指派給目前`ComPtr`的。

在第四個版本中, 如果指派值的介面指標與目前`ComPtr`的介面指標不同, 則會將第二個介面指標指派給目前`ComPtr`的。

第五個版本是複製運算子;的參考`ComPtr`會指派給目前`ComPtr`的。

第六個版本是使用 move 語義的複製運算子;如果有任何類型是`ComPtr`靜態轉換, 然後指派給目前`ComPtr`的, 則為的右值參考。

第七個版本是使用 move 語義的複製運算子;類型`ComPtr` *U*的右值參考是靜態轉換, 然後指派給目前`ComPtr`的。

## <a name="operator-equality"></a>ComPtr:: operator = =

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

*a*<br/>
對 `ComPtr` 物件的參考。

*b*<br/>
另`ComPtr`一個物件的參考。

### <a name="return-value"></a>傳回值

如果物件*a*等於`true`物件*b*, 第一個運算子會產生, `false`否則為。

第二個和第三`true`個運算子會產生, 如果`nullptr`物件*a*等於`false`, 則為, 否則為。

## <a name="operator-inequality"></a>ComPtr:: operator! =

表示兩個 `ComPtr` 物件是否不相等。

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

*a*<br/>
對 `ComPtr` 物件的參考。

*b*<br/>
另`ComPtr`一個物件的參考。

### <a name="return-value"></a>傳回值

如果物件*a*不`true`等於物件*b*, 第一個運算子會產生, `false`否則為。

第二個和第三`true`個運算子 `nullptr`會產生, 如果物件 a 不等於`false`, 則為, 否則為。

## <a name="operator-microsoft-wrl-details-booltype"></a>ComPtr:: operator Microsoft:: WRL::D etails:: BoolType

指出是否`ComPtr`正在管理介面的物件存留期。

```cpp
WRL_NOTHROW operator Microsoft::WRL::Details::BoolType() const;
```

### <a name="return-value"></a>傳回值

如果介面與此`ComPtr`相關聯, 則為[BoolStruct:: Member](boolstruct-structure.md#member)資料`nullptr`成員的位址, 否則為。

## <a name="ptr"></a>ComPtr::p tr_

包含與這個相關聯之介面的指標, 並由這個`ComPtr`所管理。

```cpp
InterfaceType *ptr_;
```

### <a name="remarks"></a>備註

`ptr_`是內部受保護的資料成員。

## <a name="releaseandgetaddressof"></a>ComPtr::ReleaseAndGetAddressOf

釋放與這個`ComPtr`相關聯的介面, 然後抓取[ptr_](#ptr)資料成員的位址, 其中包含已釋放之介面的指標。

```cpp
T** ReleaseAndGetAddressOf();
```

### <a name="return-value"></a>傳回值

這個`ComPtr`的[ptr_](#ptr)資料成員的位址。

## <a name="reset"></a>ComPtr:: Reset

釋放與這個`ComPtr`相關聯之介面指標的所有參考。

```cpp
unsigned long Reset();
```

### <a name="return-value"></a>傳回值

釋放的參考數目 (若有的話)。

## <a name="swap"></a>ComPtr:: Swap

使用由指定`ComPtr`之管理的介面`ComPtr` , 交換目前所管理的介面。

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

