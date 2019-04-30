---
title: ComPtr 類別
ms.date: 10/01/2018
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
ms.openlocfilehash: 9e5b2419f070ead17e72b1642f510f74bad8260e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398676"
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
介面，`ComPtr`表示。

*U*<br/>
類別目前`ComPtr`為 friend。 (使用這個參數的範本會受到保護)。

## <a name="remarks"></a>備註

`ComPtr<>` 宣告代表基礎介面指標的類型。 使用 `ComPtr<>`來宣告變數，然後使用 箭號成員存取運算子 (`->`) 來存取介面成員函式。

如需智慧型指標的詳細資訊，請參閱的 < COM 智慧型指標 > 一節[COM Coding Practices](/windows/desktop/LearnWin32/com-coding-practices) MSDN Library 中的主題。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

名稱            | 描述
--------------- | ---------------------------------------------------------------
`InterfaceType` | 所指定之類型的同義字*T*樣板參數。

### <a name="public-constructors"></a>公用建構函式

名稱                             | 描述
-------------------------------- | --------------------------------------------------------------------------------------------------------------------
[ComPtr::ComPtr](#comptr)        | 初始化 `ComPtr` 類別的新執行個體。 多載提供預設、複製、移動和轉換建構函式。
[ComPtr::~ComPtr](#tilde-comptr) | 取消初始化的執行個體`ComPtr`。

### <a name="public-methods"></a>公用方法

名稱                                                      | 描述
--------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[ComPtr::As](#as)                                         | 傳回`ComPtr`物件，表示指定的範本參數所識別的介面。
[ComPtr::AsIID](#asiid)                                   | 傳回`ComPtr`物件，表示指定的介面識別碼所識別的介面
[ComPtr::AsWeak](#asweak)                                 | 擷取目前物件的弱式參考。
[ComPtr::Attach](#attach)                                 | 將這`ComPtr`與目前的範本類型參數所指定的介面類型。
[ComPtr::CopyTo](#copyto)                                 | 複製目前或指定相關聯的介面與這個`ComPtr`到指定的輸出指標。
[ComPtr::Detach](#detach)                                 | 解除這`ComPtr`從它所代表的介面。
[ComPtr::Get](#get)                                       | 擷取與此相關聯的介面的指標`ComPtr`。
[ComPtr::GetAddressOf](#getaddressof)                     | 擷取位址[ptr_](#ptr)資料成員，其中包含這所代表之介面的指標`ComPtr`。
[ComPtr::ReleaseAndGetAddressOf](#releaseandgetaddressof) | 釋放與這個相關聯的介面`ComPtr`，然後擷取的地址[ptr_](#ptr)資料成員，其中包含已釋放之介面的指標。
[ComPtr::Reset](#reset)                                   | 釋放與此相關聯的介面指標的所有參考`ComPtr`。
[ComPtr::Swap](#swap)                                     | 交換目前所管理之介面`ComPtr`所指定的管理介面與`ComPtr`。

### <a name="protected-methods"></a>保護方法

名稱                                        | 描述
------------------------------------------- | --------------------------------------------------------------------------------
[ComPtr::InternalAddRef](#internaladdref)   | 與此相關聯的介面的參考計數遞增`ComPtr`。
[ComPtr::InternalRelease](#internalrelease) | 執行與此相關聯的介面上的 COM 釋放作業`ComPtr`。

### <a name="public-operators"></a>公用運算子

名稱                                                                                           | 描述
---------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------
[ComPtr::operator&](#operator-ampersand)                                                       | 擷取目前的地址`ComPtr`。
[ComPtr::operator->](#operator-arrow)                                                          | 擷取目前範本參數所指定之類型的指標。
[ComPtr::operator=](#operator-assign)                                                          | 將值指派給目前`ComPtr`。
[ComPtr::operator==](#operator-equality)                                                       | 表示兩個 `ComPtr` 物件是否相等。
[ComPtr::operator!=](#operator-inequality)                                                     | 表示兩個 `ComPtr` 物件是否不相等。
[Comptr:: booltype](#operator-microsoft-wrl-details-booltype) | 指出是否`ComPtr`管理介面的物件存留期。

### <a name="protected-data-members"></a>受保護的資料成員

名稱                 | 描述
-------------------- | ------------------------------------------------------------------------------------------
[ComPtr::ptr_](#ptr) | 包含相關聯，並管理由這個介面的指標`ComPtr`。

## <a name="inheritance-hierarchy"></a>繼承階層

`ComPtr`

## <a name="requirements"></a>需求

**標頭：** client.h

**命名空間：** Microsoft:: wrl

## <a name="tilde-comptr"></a>ComPtr::~ComPtr

取消初始化的執行個體`ComPtr`。

```cpp
WRL_NOTHROW ~ComPtr();
```

## <a name="as"></a>Comptr:: As

傳回`ComPtr`物件，表示指定的範本參數所識別的介面。

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
參數所表示的介面*p*。

*p*<br/>
A`ComPtr`物件，表示參數所指定的介面*U*。參數*p*必須是指目前`ComPtr`物件。

### <a name="remarks"></a>備註

第一個範本是程式碼中應該使用的表單。 第二個範本是內部的，支援 C++ 語言功能的協助程式特製化，例如 [auto](../../cpp/auto-cpp.md) 類型推斷關鍵字。

### <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

## <a name="asiid"></a>ComPtr::AsIID

傳回`ComPtr`物件，表示指定的介面識別碼所識別的介面

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
如果物件具有其識別碼等於的介面*riid*，所指定之介面的雙向間接指標*riid*參數，否則指標`IUnknown`。

### <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

## <a name="asweak"></a>Comptr:: Asweak

擷取目前物件的弱式參考。

```cpp
HRESULT AsWeak(
   _Out_ WeakRef* pWeakRef
);
```

### <a name="parameters"></a>參數

*pWeakRef*<br/>
這項作業完成時，弱式參考物件的指標。

### <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

## <a name="attach"></a>ComPtr::Attach

將這`ComPtr`與目前的範本類型參數所指定的介面類型。

```cpp
void Attach(
   _In_opt_ InterfaceType* other
);
```

### <a name="parameters"></a>參數

*other*<br/>
介面型別。

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
   typename ENABLE_IF<__is_convertible_to(U*,
   T*),
   void *>;
WRL_NOTHROW ComPtr(
   _Inout_ ComPtr &&other
);
template<class U>
WRL_NOTHROW ComPtr(
   _Inout_ ComPtr<U>&& other,
   typename ENABLE_IF<__is_convertible_to(U*,
   T*),
   void *>;
```

### <a name="parameters"></a>參數

*U*<br/>
型別*其他*參數。

*other*<br/>
型別的物件*U*。

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

第一個建構函式是預設建構函式，哪一個隱含建立空的物件。 第二個建構函式指定[__nullptr](../../extensions/nullptr-cpp-component-extensions.md)，明確建立空的物件。

第三個建構函式會從指標所指定的物件建立的物件。

第四個和第五個建構函式是複製建構函式。 第五個建構函式將物件複製時轉換成目前的類型。

第六個和第七個建構函式會移動建構函式。 第七個建構函式會移動物件，如果它是可以轉換成目前的類型。

## <a name="copyto"></a>ComPtr::CopyTo

複製目前或指定相關聯的介面與這個`ComPtr`至指定的指標。

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
這項作業完成時，所要求介面的指標。

*riid*<br/>
介面識別碼。

### <a name="return-value"></a>傳回值

如果成功則為 S_OK否則，HRESULT，指出為什麼隱含`QueryInterface`作業失敗。

### <a name="remarks"></a>備註

第一次的函式會傳回與此相關聯的介面指標的複本`ComPtr`。 此函式一律會傳回 S_OK。

第二個函式會執行`QueryInterface`與此相關聯的介面上的作業`ComPtr`所指定的介面*riid*參數。

第三個函式會執行`QueryInterface`與此相關聯的介面上的作業`ComPtr`為基礎的介面*U*參數。

## <a name="detach"></a>ComPtr::Detach

解除這`ComPtr`從它所代表之介面的物件。

```cpp
T* Detach();
```

### <a name="return-value"></a>傳回值

這由介面的指標`ComPtr`物件。

## <a name="get"></a>ComPtr::Get

擷取與此相關聯的介面的指標`ComPtr`。

```cpp
T* Get() const;
```

### <a name="return-value"></a>傳回值

與此相關聯之介面指標`ComPtr`。

## <a name="getaddressof"></a>ComPtr::GetAddressOf

擷取位址[ptr_](#ptr)資料成員，其中包含這所代表之介面的指標`ComPtr`。

```cpp
T* const* GetAddressOf() const;
T** GetAddressOf();
```

### <a name="return-value"></a>傳回值

變數的位址。

## <a name="internaladdref"></a>ComPtr::InternalAddRef

與此相關聯的介面的參考計數遞增`ComPtr`。

```cpp
void InternalAddRef() const;
```

### <a name="remarks"></a>備註

這個方法受到保護。

## <a name="internalrelease"></a>ComPtr::InternalRelease

執行與此相關聯的介面上的 COM 釋放作業`ComPtr`。

```cpp
void InternalRelease();
```

### <a name="remarks"></a>備註

這個方法受到保護。

## <a name="operator-ampersand"></a>ComPtr::operator&amp;

釋放與這個相關聯的介面`ComPtr`物件，並接著會擷取的位址`ComPtr`物件。

```cpp
Details::ComPtrRef<WeakRef> operator&()

const Details::ComPtrRef<const WeakRef> operator&() const
```

### <a name="return-value"></a>傳回值

目前的弱式參考`ComPtr`。

### <a name="remarks"></a>備註

這個方法不同於[comptr:: Getaddressof](#getaddressof) ，這個方法會釋放介面指標的參考。 使用`ComPtr::GetAddressOf`當您需要的介面指標的位址，但不是想要釋放該介面。

## <a name="operator-arrow"></a>ComPtr::operator-&gt;

擷取目前範本參數所指定之類型的指標。

```cpp
WRL_NOTHROW Microsoft::WRL::Details::RemoveIUnknown<InterfaceType>* operator->() const;
```

### <a name="return-value"></a>傳回值

目前的範本型別名稱所指定之類型的指標。

### <a name="remarks"></a>備註

此協助程式函式會移除不必要使用 STDMETHOD 巨集所造成的額外負荷。 這個功能可讓`IUnknown`型別`private`而不是`virtual`。

## <a name="operator-assign"></a>ComPtr::operator=

將值指派給目前`ComPtr`。

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
類別中。

*other*<br/>
指標、 參考或右值參考類型或另一個`ComPtr`。

### <a name="return-value"></a>傳回值

目前的參考`ComPtr`。

### <a name="remarks"></a>備註

這個運算子的第一個版本會將空值指派給目前`ComPtr`。

在第二個版本中，如果指派的介面指標不是目前的相同`ComPtr`介面指標，第二個介面指標指派給目前`ComPtr`。

在第三個版本中，指派的介面指標指派給目前`ComPtr`。

在第四個版本中，如果指派值的介面指標不是目前的相同`ComPtr`介面指標，第二個介面指標指派給目前`ComPtr`。

第五個版本是複製運算子;參考`ComPtr`指派給目前`ComPtr`。

第六個版本是複製運算子使用移動語意;右值參考`ComPtr`如果任何型別是靜態的轉換，然後指派給目前`ComPtr`。

第七個版本是複製運算子使用移動語意;右值參考`ComPtr`型別的*U*會靜態然後轉換並指派給目前`ComPtr`。

## <a name="operator-equality"></a>Comptr:: Operator = =

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
另一個的參考`ComPtr`物件。

### <a name="return-value"></a>傳回值

第一個運算子會產生`true`如果物件是否等於物件*b*; 否則`false`。

第二個和第三個運算子會產生`true`如果物件等於`nullptr`; 否則`false`。

## <a name="operator-inequality"></a>Comptr:: Operator ！ =

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
另一個的參考`ComPtr`物件。

### <a name="return-value"></a>傳回值

第一個運算子會產生`true`如果物件是否不等於物件*b*; 否則`false`。

第二個和第三個運算子會產生`true`如果物件是否不等於`nullptr`; 否則`false`。

## <a name="operator-microsoft-wrl-details-booltype"></a>Comptr:: booltype

指出是否`ComPtr`管理介面的物件存留期。

```cpp
WRL_NOTHROW operator Microsoft::WRL::Details::BoolType() const;
```

### <a name="return-value"></a>傳回值

如果介面是與此相關聯`ComPtr`的地址[boolstruct:: Member](boolstruct-structure.md#member)資料成員，否則`nullptr`。

## <a name="ptr"></a>ComPtr::ptr_

包含相關聯，並管理由這個介面的指標`ComPtr`。

```cpp
InterfaceType *ptr_;
```

### <a name="remarks"></a>備註

`ptr_` 是內部、 受保護的資料成員。

## <a name="releaseandgetaddressof"></a>ComPtr::ReleaseAndGetAddressOf

釋放與這個相關聯的介面`ComPtr`，然後擷取的地址[ptr_](#ptr)資料成員，其中包含已釋放之介面的指標。

```cpp
T** ReleaseAndGetAddressOf();
```

### <a name="return-value"></a>傳回值

地址[ptr_](#ptr)資料成員`ComPtr`。

## <a name="reset"></a>ComPtr::Reset

釋放與此相關聯的介面指標的所有參考`ComPtr`。

```cpp
unsigned long Reset();
```

### <a name="return-value"></a>傳回值

釋放的參考數目 (若有的話)。

## <a name="swap"></a>ComPtr::Swap

交換目前所管理之介面`ComPtr`所指定的管理介面與`ComPtr`。

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

