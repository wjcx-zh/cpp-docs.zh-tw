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
ms.openlocfilehash: 89c09ede972f5bdd5da1dde810cad31733bdf338
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372645"
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
表示的`ComPtr`介面。

*美國*<br/>
當前`ComPtr`是朋友的類。 (使用這個參數的範本會受到保護)。

## <a name="remarks"></a>備註

`ComPtr<>`聲明表示基礎介面指標的類型。 用於`ComPtr<>`聲明變數,然後使用箭頭成員訪問運算符 ()`->`訪問介面成員函數。

有關智慧指標的詳細資訊,請參閱 MSDN 庫中 COM 編碼實踐主題的[「COM](/windows/win32/LearnWin32/com-coding-practices)智慧指標」小節。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

名稱            | 描述
--------------- | ---------------------------------------------------------------
`InterfaceType` | *T*範本參數指定的類型的同義詞。

### <a name="public-constructors"></a>公用建構函式

名稱                             | 描述
-------------------------------- | --------------------------------------------------------------------------------------------------------------------
[ComPtr:ComPtr](#comptr)        | 初始化 `ComPtr` 類別的新執行個體。 多載提供預設、複製、移動和轉換建構函式。
[ComPtr::*ComPtr](#tilde-comptr) | 取消初始化`ComPtr`的實例。

### <a name="public-methods"></a>公用方法

名稱                                                      | 描述
--------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[ComPtr:如](#as)                                         | 返回表示`ComPtr`指定範本參數標識的介面的物件。
[ComPtr::AsIID](#asiid)                                   | 返回表示`ComPtr`指定介面 ID 標識的介面的物件。
[ComPtr::作為弱](#asweak)                                 | 擷取目前物件的弱式參考。
[ComPtr::附加](#attach)                                 | 將這與`ComPtr`當前範本類型參數指定的介面類型關聯。
[Comptr::複製到](#copyto)                                 | 將與此關聯的當前或指定介面`ComPtr`複製到指定的輸出指標。
[康普特::D泰](#detach)                                 | 將其`ComPtr`與它所代表的介面分離。
[ComPtr:取得](#get)                                       | 檢索指向與此關聯的介面的指標`ComPtr`。
[Comptr:抓取位址](#getaddressof)                     | 檢索[ptr_](#ptr)資料成員的位址,其中包含`ComPtr`指向此 表示的介面的指標。
[Comptr::釋放和取得位址](#releaseandgetaddressof) | 釋放與此關聯的介面,`ComPtr`然後檢索[ptr_](#ptr)資料成員的位址,該位址包含指向釋放的介面的指標。
[ComPtr::Reset](#reset)                                   | 釋放指向與此`ComPtr`關聯的介面的指標的所有引用。
[交流::交換](#swap)                                     | 將當前`ComPtr`管理的介面與指定的`ComPtr`的接換。

### <a name="protected-methods"></a>保護方法

名稱                                        | 描述
------------------------------------------- | --------------------------------------------------------------------------------
[ComPtr::內部AddRef](#internaladdref)   | 增加此關聯的介面的引言值`ComPtr`。
[ComPtr::內部發佈](#internalrelease) | 對此關聯介面執行 COM 宣告操作`ComPtr`。

### <a name="public-operators"></a>公用運算子

名稱                                                                                           | 描述
---------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------
[ComPtr::操作員&](#operator-ampersand)                                                       | 檢索當前`ComPtr`的位址。
[ComPtr::操作員->](#operator-arrow)                                                          | 擷取目前範本參數所指定之類型的指標。
[ComPtr::管理員*](#operator-assign)                                                          | 將值配置給目前的`ComPtr`。
[通訊::操作員*](#operator-equality)                                                       | 表示兩個 `ComPtr` 物件是否相等。
[ComPtr::操作員!](#operator-inequality)                                                     | 表示兩個 `ComPtr` 物件是否不相等。
[ComPtr::操作者微軟::WRL::D尾::布爾類型](#operator-microsoft-wrl-details-booltype) | 指示是否`ComPtr`正在管理介面的物件存留期。

### <a name="protected-data-members"></a>受保護的資料成員

名稱                 | 描述
-------------------- | ------------------------------------------------------------------------------------------
[ComPtr::ptr]](#ptr) | 包含指向與此關聯的介面並由 其管理的指標`ComPtr`。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`ComPtr`

## <a name="requirements"></a>需求

**標頭：** client.h

**命名空間：** Microsoft::WRL

## <a name="comptrcomptr"></a><a name="tilde-comptr"></a>ComPtr::*ComPtr

取消初始化`ComPtr`的實例。

```cpp
WRL_NOTHROW ~ComPtr();
```

## <a name="comptras"></a><a name="as"></a>ComPtr:如

返回表示`ComPtr`指定範本參數標識的介面的物件。

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

*美國*<br/>
參數*p*表示的介面。

*P*<br/>
表示`ComPtr`參數*U*指定的介面的物件。參數*p*不能`ComPtr`參考當前 物件。

### <a name="remarks"></a>備註

第一個範本是程式碼中應該使用的表單。 第二個範本是內部的，支援 C++ 語言功能的協助程式特製化，例如 [auto](../../cpp/auto-cpp.md) 類型推斷關鍵字。

### <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

## <a name="comptrasiid"></a><a name="asiid"></a>ComPtr::AsIID

返回表示`ComPtr`指定介面 ID 標識的介面的物件。

```cpp
WRL_NOTHROW HRESULT AsIID(
   REFIID riid,
   _Out_ ComPtr<IUnknown>* p
) const;
```

### <a name="parameters"></a>參數

*riid*<br/>
介面識別碼。

*P*<br/>
如果物件具有 ID 等於*riid*的介面,則指向*riid*參數指定的介面的雙間接指標;否則,指向`IUnknown`的指標。

### <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

## <a name="comptrasweak"></a><a name="asweak"></a>ComPtr::作為弱

擷取目前物件的弱式參考。

```cpp
HRESULT AsWeak(
   _Out_ WeakRef* pWeakRef
);
```

### <a name="parameters"></a>參數

*pWeakRef*<br/>
此操作完成後,指向弱引用物件的指標。

### <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

## <a name="comptrattach"></a><a name="attach"></a>ComPtr::附加

將這與`ComPtr`當前範本類型參數指定的介面類型關聯。

```cpp
void Attach(
   _In_opt_ InterfaceType* other
);
```

### <a name="parameters"></a>參數

*其他*<br/>
介面類型。

## <a name="comptrcomptr"></a><a name="comptr"></a>ComPtr:ComPtr

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

*美國*<br/>
*其他*參數的類型。

*其他*<br/>
*U*型態的物件 。

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

第一個構造函數是預設構造函數,它突然創建一個空物件。 第二個構造函數指定[__nullptr](../../extensions/nullptr-cpp-component-extensions.md),顯式創建空物件。

第三個構造函數從指標指定的對象創建物件。 ComPtr 現在擁有指向的記憶體,並維護對它的引用計數。

第四個和第五個構造函數是複製構造函數。 如果物件可轉換為當前類型,則第五個構造函數將複製該物件。

第六和第七構造函數是移動構造函數。 如果物件可轉換為當前類型,則第七個構造函數將對象移動。

## <a name="comptrcopyto"></a><a name="copyto"></a>Comptr::複製到

將與此關聯的當前或指定介面`ComPtr`複製到指定的指標。

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

*美國*<br/>
類型名稱。

*Ptr*<br/>
此操作完成後,將指向請求的介面的指標。

*riid*<br/>
介面識別碼。

### <a name="return-value"></a>傳回值

S_OK如果成功;否則,指示隱式`QueryInterface`操作失敗原因的 HRESULT。

### <a name="remarks"></a>備註

第一個函數返回指向與此`ComPtr`關聯的介面的指標的副本。 此函數始終返回S_OK。

第二個`QueryInterface`函`ComPtr`數 對*riid*參數指定的介面執行與此關聯的介面的操作。

第三個`QueryInterface`函`ComPtr`數 對*U*參數的基礎介面執行與此關聯的介面的操作。

## <a name="comptrdetach"></a><a name="detach"></a>康普特::D泰

將此`ComPtr`物件與它所代表的介面分離。

```cpp
T* Detach();
```

### <a name="return-value"></a>傳回值

指向此`ComPtr`物件表示的介面的指標。

## <a name="comptrget"></a><a name="get"></a>ComPtr:取得

檢索指向與此關聯的介面的指標`ComPtr`。

```cpp
T* Get() const;
```

### <a name="return-value"></a>傳回值

指向與此關聯的介面`ComPtr`的指標。

## <a name="comptrgetaddressof"></a><a name="getaddressof"></a>Comptr:抓取位址

檢索[ptr_](#ptr)資料成員的位址,其中包含`ComPtr`指向此 表示的介面的指標。

```cpp
T* const* GetAddressOf() const;
T** GetAddressOf();
```

### <a name="return-value"></a>傳回值

變數的位址。

## <a name="comptrinternaladdref"></a><a name="internaladdref"></a>ComPtr::內部AddRef

增加此關聯的介面的引言值`ComPtr`。

```cpp
void InternalAddRef() const;
```

### <a name="remarks"></a>備註

此方法受到保護。

## <a name="comptrinternalrelease"></a><a name="internalrelease"></a>ComPtr::內部發佈

對此關聯介面執行 COM 宣告操作`ComPtr`。

```cpp
void InternalRelease();
```

### <a name="remarks"></a>備註

此方法受到保護。

## <a name="comptroperatoramp"></a><a name="operator-ampersand"></a>ComPtr::運算子&amp;

釋放與此`ComPtr`物件關聯的介面,然後檢`ComPtr`索 該對象的位址。

```cpp
Details::ComPtrRef<WeakRef> operator&()

const Details::ComPtrRef<const WeakRef> operator&() const
```

### <a name="return-value"></a>傳回值

對電流`ComPtr`的弱引用。

### <a name="remarks"></a>備註

此方法不同於[ComPtr::GetAddressof,](#getaddressof)因為此方法釋放對介面指標的引用。 當您`ComPtr::GetAddressOf`需要介面指標的位址,但不希望釋放該介面時使用。

## <a name="comptroperator-gt"></a><a name="operator-arrow"></a>ComPtr::操作員-&gt;

擷取目前範本參數所指定之類型的指標。

```cpp
WRL_NOTHROW Microsoft::WRL::Details::RemoveIUnknown<InterfaceType>* operator->() const;
```

### <a name="return-value"></a>傳回值

指向當前範本類型名稱指定的類型。

### <a name="remarks"></a>備註

此幫助程式函數消除了由於使用 STDMETHOD 宏而導致的不必要的開銷。 此函數使`IUnknown`型`private`態`virtual`而不是 。

## <a name="comptroperator"></a><a name="operator-assign"></a>ComPtr::管理員*

將值配置給目前的`ComPtr`。

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

*美國*<br/>
類。

*其他*<br/>
對類型或其他的指標、引用或 rvalue`ComPtr`引用 。

### <a name="return-value"></a>傳回值

對當前`ComPtr`的引用。

### <a name="remarks"></a>備註

此運算子的第一個版本將空值分配給目前的`ComPtr`。

在第二版本中,如果分配介面指標與當前`ComPtr`介面指標不同,則第二個介面指標將分配給當前`ComPtr`。

在第三個版本中,分配介面指標分配給目前的`ComPtr`。

在第四版本中,如果分配值的介面指標與當前`ComPtr`介面指標不同,則第二個介面指標將分配給當前`ComPtr`。

第五個版本是複製運算元;對的`ComPtr`參考分配給`ComPtr`目前的 。

第六個版本是使用移動語義的複製運算符;對的`ComPtr`rvalue 引用,如果任何類型都是靜態強制轉換`ComPtr`,然後配置給目前的 。

第七個版本是使用移動語義的複製運算符;對*類型 U*`ComPtr`的 rvalue 引用是靜態強制轉換`ComPtr`,然後分配給目前 。

## <a name="comptroperator"></a><a name="operator-equality"></a>通訊::操作員*

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
`ComPtr` 物件的參考。

*B*<br/>
對另一個`ComPtr`物件的引用。

### <a name="return-value"></a>傳回值

如果物件`true`*a*等於物件*b,* 則第一個運算符將生成。否則, `false`.

如果物件*a*等於 ,則`nullptr`第二個 與第三個運算`true`符屈服 。否則, `false`.

## <a name="comptroperator"></a><a name="operator-inequality"></a>ComPtr::操作員!

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
`ComPtr` 物件的參考。

*B*<br/>
對另一個`ComPtr`物件的引用。

### <a name="return-value"></a>傳回值

如果物件`true`*a*不等於物件*b,* 則第一個運算符將生成。否則, `false`.

如果物件*a*不等於 ,則`nullptr`第二個 和第三個運算`true`符屈服 。否則, `false`.

## <a name="comptroperator-microsoftwrldetailsbooltype"></a><a name="operator-microsoft-wrl-details-booltype"></a>ComPtr::操作者微軟::WRL::D尾::布爾類型

指示是否`ComPtr`正在管理介面的物件存留期。

```cpp
WRL_NOTHROW operator Microsoft::WRL::Details::BoolType() const;
```

### <a name="return-value"></a>傳回值

如果介面與此關聯`ComPtr`,則[BoolStruct 的位址::成員](boolstruct-structure.md#member)數據成員;否則, `nullptr`.

## <a name="comptrptr_"></a><a name="ptr"></a>ComPtr::ptr]

包含指向與此關聯的介面並由 其管理的指標`ComPtr`。

```cpp
InterfaceType *ptr_;
```

### <a name="remarks"></a>備註

`ptr_`是內部受保護的數據成員。

## <a name="comptrreleaseandgetaddressof"></a><a name="releaseandgetaddressof"></a>Comptr::釋放和取得位址

釋放與此關聯的介面,`ComPtr`然後檢索[ptr_](#ptr)資料成員的位址,該位址包含指向釋放的介面的指標。

```cpp
T** ReleaseAndGetAddressOf();
```

### <a name="return-value"></a>傳回值

ptr_`ComPtr`[資料成員](#ptr)的位址。

## <a name="comptrreset"></a><a name="reset"></a>ComPtr:重置

釋放指向與此`ComPtr`關聯的介面的指標的所有引用。

```cpp
unsigned long Reset();
```

### <a name="return-value"></a>傳回值

釋放的參考數目 (若有的話)。

## <a name="comptrswap"></a><a name="swap"></a>交流::交換

將當前`ComPtr`管理的介面與指定的`ComPtr`的接換。

```cpp
void Swap(
   _Inout_ ComPtr&& r
);

void Swap(
   _Inout_ ComPtr& r
);
```

### <a name="parameters"></a>參數

*R*<br/>
`ComPtr`。
