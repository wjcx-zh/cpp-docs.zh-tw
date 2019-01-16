---
title: WeakRef 類別
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef
- client/Microsoft::WRL::WeakRef::~WeakRef
- client/Microsoft::WRL::WeakRef::As
- client/Microsoft::WRL::WeakRef::AsIID
- client/Microsoft::WRL::WeakRef::CopyTo
- client/Microsoft::WRL::WeakRef::operator&
- client/Microsoft::WRL::WeakRef::WeakRef
helpviewer_keywords:
- Microsoft::WRL::WeakRef class
- Microsoft::WRL::WeakRef::~WeakRef, destructor
- Microsoft::WRL::WeakRef::As method
- Microsoft::WRL::WeakRef::AsIID method
- Microsoft::WRL::WeakRef::CopyTo method
- Microsoft::WRL::WeakRef::operator& operator
- Microsoft::WRL::WeakRef::WeakRef, constructor
ms.assetid: 572be703-c641-496c-8af5-ad6164670ba1
ms.openlocfilehash: 9616fcffac0b92d5ac6d96cfe5f4119f3a3b180f
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54336409"
---
# <a name="weakref-class"></a>WeakRef 類別

代表 *弱式參考* 僅供 Windows 執行階段使用，而不供傳統 COM 使用。 弱式參考代表不一定可存取的物件。

## <a name="syntax"></a>語法

```cpp
class WeakRef : public ComPtr<IWeakReference>;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[WeakRef::WeakRef 建構函式](#weakref)|初始化 `WeakRef` 類別的新執行個體。|
|[WeakRef::~WeakRef 解構函式](#tilde-weakref)|取消初始化目前的執行個體`WeakRef`類別。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[WeakRef::As 方法](#as)|設定指定`ComPtr`指標參數代表指定的介面。|
|[WeakRef::AsIID 方法](#asiid)|設定指定`ComPtr`指標參數代表指定的介面識別碼。|
|[WeakRef::CopyTo 方法](#copyto)|指派介面指標 (如有提供) 給指定的指標變數。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[WeakRef::operator& 運算子](#operator-ampersand-operator)|傳回`ComPtrRef`物件，表示目前`WeakRef`物件。|

## <a name="remarks"></a>備註

A`WeakRef`物件會維護*強式參考*，這與物件相關聯，而且可以是有效或無效。 呼叫`As()`或`AsIID()`方法，以取得強式參考。 當強式參考為有效時，它可以存取相關聯的物件。 強式參考無效時 (`nullptr`)，就無法存取相關聯的物件。

A`WeakRef`物件一般用來代表其存在由外部執行緒或應用程式所控制的物件。 例如，建構`WeakRef`檔案物件的參考物件。 在檔案開啟時，強式參考是有效的。 但若檔案關閉，強式參考就變成無效的。

請注意，在 Windows 10 SDK 的 [As](#as)、 [AsIID](#asiid) 和 [CopyTo](#copyto) 方法中有行為變更。 先前，在呼叫之後任何一種方法，您可以檢查`WeakRef`針對`nullptr`來判斷是否強式參考已成功取得，如下列程式碼所示：

```cpp
WeakRef wr;
strongComptrRef.AsWeak(&wr);

// Now suppose that the object strongComPtrRef points to no longer exists
// and the following code tries to get a strong ref from the weak ref:
ComPtr<ISomeInterface> strongRef;
HRESULT hr = wr.As(&strongRef);

// This check won't work with the Windows 10 SDK version of the library.
// Check the input pointer instead.
if(wr == nullptr)
{
    wprintf(L"Couldn’t get strong ref!");
}
```

使用 Windows 10 SDK (或更新版本) 時，上述程式碼不作用。 相反地，請檢查傳入的指標`nullptr`。

```cpp
if (strongRef == nullptr)
{
    wprintf(L"Couldn't get strong ref!");
}
```

## <a name="inheritance-hierarchy"></a>繼承階層

`ComPtr`

`WeakRef`

## <a name="requirements"></a>需求

**標頭：** client.h

**命名空間：** Microsoft:: wrl

## <a name="tilde-weakref"></a>WeakRef:: ~ WeakRef 解構函式

取消初始化目前的執行個體`WeakRef`類別。

```cpp
~WeakRef();
```

## <a name="as"></a>Weakref:: As 方法

設定指定`ComPtr`指標參數代表指定的介面。

```cpp
template<typename U>
HRESULT As(
   _Out_ ComPtr<U>* ptr
);

template<typename U>
HRESULT As(
   _Out_ Details::ComPtrRef<ComPtr<U>> ptr
);
```

### <a name="parameters"></a>參數

*U*<br/>
介面識別碼。

*ptr*<br/>
這項作業完成時，表示參數的物件*U*。

### <a name="return-value"></a>傳回值

- 如果這項作業成功，則為 S_OK否則，指出原因的 HRESULT 作業失敗，並*ptr*設定為`nullptr`。

- 如果這項作業成功，但目前為 S_OK`WeakRef`物件已被釋放。 參數*ptr*設定為`nullptr`。

- 如果這項作業成功，但目前為 S_OK`WeakRef`物件不衍生自參數*U*。參數*ptr*設定為`nullptr`。

### <a name="remarks"></a>備註

如果，就會發出錯誤參數*U*是`IWeakReference`，或不衍生自`IInspectable`。

第一個範本是程式碼中應該使用的表單。 第二個範本是內部的，支援 C++ 語言功能的協助程式特製化，例如 [auto](../../cpp/auto-cpp.md) 類型推斷關鍵字。

從 Windows 10 SDK 開始，這個方法不會設定`WeakRef`執行個體`nullptr`如果無法取得弱式參考，因此您應該避免檢查錯誤的程式碼，檢查`WeakRef`如`nullptr`。 相反地，檢查*ptr*如`nullptr`。

## <a name="asiid"></a>Weakref:: Asiid 方法

設定指定`ComPtr`指標參數代表指定的介面識別碼。

```cpp
HRESULT AsIID(
   REFIID riid,
   _Out_ ComPtr<IInspectable>* ptr
);
```

### <a name="parameters"></a>參數

*riid*<br/>
介面識別碼。

*ptr*<br/>
這項作業完成時，表示參數的物件*riid*。

### <a name="return-value"></a>傳回值

- 如果這項作業成功，則為 S_OK否則，指出原因的 HRESULT 作業失敗，並*ptr*設定為`nullptr`。

- 如果這項作業成功，但目前為 S_OK`WeakRef`物件已被釋放。 參數*ptr*設定為`nullptr`。

- 如果這項作業成功，但目前為 S_OK`WeakRef`物件不衍生自參數*riid*。 參數*ptr*設定為`nullptr`。 (如需詳細資訊，請參閱＜備註＞)。

### <a name="remarks"></a>備註

如果，就會發出錯誤參數*riid*不衍生自`IInspectable`。 這個錯誤會取代傳回值。

第一個範本是程式碼中應該使用的表單。 第二個範本 (此處未顯示但會在標頭檔中宣告) 是支援 C++ 語言功能的內部協助程式特製化，例如 [auto](../../cpp/auto-cpp.md) 類型推斷關鍵字。

從 Windows 10 SDK 開始，這個方法不會設定`WeakRef`執行個體`nullptr`如果無法取得弱式參考，因此您應該避免檢查錯誤的程式碼，檢查`WeakRef`如`nullptr`。 相反地，檢查*ptr*如`nullptr`。

## <a name="copyto"></a>Weakref:: Copyto 方法

指派介面指標 (如有提供) 給指定的指標變數。

```cpp
HRESULT CopyTo(
   REFIID riid,
   _Deref_out_ IInspectable** ptr
);

template<typename U>
HRESULT CopyTo(
   _Deref_out_ U** ptr
);

HRESULT CopyTo(
   _Deref_out_ IWeakReference** ptr
);
```

### <a name="parameters"></a>參數

*U*<br/>
指標`IInspectable`介面。 如果，就會發出錯誤*U*不衍生自`IInspectable`。

*riid*<br/>
介面識別碼。 如果，就會發出錯誤*riid*不衍生自`IWeakReference`。

*ptr*<br/>
雙向間接指標`IInspectable`或`IWeakReference`。

### <a name="return-value"></a>傳回值

若成功，則為 S_OK，否則會是 HRESULT 指出失敗。 如需詳細資訊，請參閱**備註**。

### <a name="remarks"></a>備註

傳回值 S_OK 只表示此作業已成功，而不會指出是否已將弱式參考解析為強式參考。 如果傳回 S_OK，測試參數*p*為強式參考，也就是參數*p*不等於`nullptr`。

從 Windows 10 SDK 開始，這個方法不會設定`WeakRef`執行個體`nullptr`如果無法取得弱式參考，因此您應該避免錯誤檢查程式碼，檢查`WeakRef`如`nullptr`。 相反地，檢查*ptr*如`nullptr`。

## <a name="operator-ampersand-operator"></a>Weakref::&amp;運算子

傳回`ComPtrRef`物件，表示目前`WeakRef`物件。

```cpp
Details::ComPtrRef<WeakRef> operator&() throw()
```

### <a name="return-value"></a>傳回值

A`ComPtrRef`物件，表示目前`WeakRef`物件。

### <a name="remarks"></a>備註

這是不適合用於您的程式碼中的內部 helper 運算子。

## <a name="weakref"></a>Weakref:: Weakref 建構函式

初始化 `WeakRef` 類別的新執行個體。

```cpp
WeakRef();
WeakRef(
   decltype(__nullptr)
);

WeakRef(
   _In_opt_ IWeakReference* ptr
);

WeakRef(
   const ComPtr<IWeakReference>& ptr
);

WeakRef(
   const WeakRef& ptr
);

WeakRef(
   _Inout_ WeakRef&& ptr
);
```

### <a name="parameters"></a>參數

*ptr*<br/>
指標、 參考或右值參考至現有的物件，初始化目前`WeakRef`物件。

### <a name="remarks"></a>備註

第一個建構函式會初始化空`WeakRef`物件。 第二個建構函式初始化`WeakRef`物件的指標`IWeakReference`介面。 第三個建構函式初始化`WeakRef`物件的參考從`ComPtr<IWeakReference>`物件。 第四個和第五個建構函式初始化`WeakRef`物件從另一個`WeakRef`物件。
