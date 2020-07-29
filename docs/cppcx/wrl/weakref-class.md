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
ms.openlocfilehash: 715a823784aaa75f9abe349ef0a7ddc9e5d607d1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218347"
---
# <a name="weakref-class"></a>WeakRef 類別

代表 *弱式參考* 僅供 Windows 執行階段使用，而不供傳統 COM 使用。 弱式參考代表不一定可存取的物件。

## <a name="syntax"></a>語法

```cpp
class WeakRef : public ComPtr<IWeakReference>;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[WeakRef::WeakRef 建構函式](#weakref)|初始化 `WeakRef` 類別的新執行個體。|
|[WeakRef::~WeakRef 解構函式](#tilde-weakref)|將類別的目前實例 `WeakRef` 。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[WeakRef::As 方法](#as)|設定指定的 `ComPtr` 指標參數來表示指定的介面。|
|[WeakRef::AsIID 方法](#asiid)|設定指定的 `ComPtr` 指標參數，以代表指定的介面識別碼。|
|[WeakRef::CopyTo 方法](#copyto)|指派介面指標 (如有提供) 給指定的指標變數。|

### <a name="public-operators"></a>公用運算子

|名稱|說明|
|----------|-----------------|
|[WeakRef::operator& 運算子](#operator-ampersand-operator)|傳回 `ComPtrRef` 表示目前物件的物件 `WeakRef` 。|

## <a name="remarks"></a>備註

`WeakRef`物件會維護*強式參考*，它與物件相關聯，而且可以是有效的或不正確。 呼叫 `As()` 或 `AsIID()` 方法，以取得強式參考。 當強式參考為有效時，它可以存取相關聯的物件。 當強式參考無效（ **`nullptr`** ）時，無法存取相關聯的物件。

`WeakRef`物件通常用來表示物件，其存在是由外部執行緒或應用程式所控制。 例如， `WeakRef` 從檔案物件的參考來建立物件。 在檔案開啟時，強式參考是有效的。 但若檔案關閉，強式參考就變成無效的。

請注意，在 Windows 10 SDK 的 [As](#as)、 [AsIID](#asiid) 和 [CopyTo](#copyto) 方法中有行為變更。 先前在呼叫這些方法的任何一個之後，您可以檢查的， `WeakRef` **`nullptr`** 以判斷是否已成功取得強式參考，如下列程式碼所示：

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

使用 Windows 10 SDK (或更新版本) 時，上述程式碼不作用。 請改為檢查傳入的指標 **`nullptr`** 。

```cpp
if (strongRef == nullptr)
{
    wprintf(L"Couldn't get strong ref!");
}
```

## <a name="inheritance-hierarchy"></a>繼承階層架構

`ComPtr`

`WeakRef`

## <a name="requirements"></a>需求

**標頭：** client.h

**命名空間：** Microsoft::WRL

## <a name="weakrefweakref-destructor"></a><a name="tilde-weakref"></a>WeakRef：： ~ WeakRef 析構函式

將類別的目前實例 `WeakRef` 。

```cpp
~WeakRef();
```

## <a name="weakrefas-method"></a><a name="as"></a>WeakRef：： As 方法

設定指定的 `ComPtr` 指標參數來表示指定的介面。

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
當此作業完成時，表示參數*U*的物件。

### <a name="return-value"></a>傳回值

- 如果此作業成功，則 S_OK;否則，即為 HRESULT，表示作業失敗的原因，且*ptr*設定為 **`nullptr`** 。

- 如果此作業成功，則 S_OK，但目前的 `WeakRef` 物件已經釋放。 參數*ptr*設定為 **`nullptr`** 。

- S_OK，如果此作業成功，但目前的 `WeakRef` 物件不是衍生自參數*U*。參數*ptr*設定為 **`nullptr`** 。

### <a name="remarks"></a>備註

如果參數*U*為 `IWeakReference` ，或並非衍生自，則會發出錯誤 `IInspectable` 。

第一個範本是程式碼中應該使用的表單。 第二個範本是內部的，支援 C++ 語言功能的協助程式特製化，例如 [auto](../../cpp/auto-cpp.md) 類型推斷關鍵字。

從 Windows 10 SDK 開始， `WeakRef` 如果無法取得弱式參考，這個方法就不會將實例設定為 **`nullptr`** ，因此您應該避免檢查的錯誤檢查程式碼 `WeakRef` **`nullptr`** 。 相反地，請檢查的*ptr* **`nullptr`** 。

## <a name="weakrefasiid-method"></a><a name="asiid"></a>WeakRef：： AsIID 方法

設定指定的 `ComPtr` 指標參數，以代表指定的介面識別碼。

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
當此作業完成時，表示參數*riid*的物件。

### <a name="return-value"></a>傳回值

- 如果此作業成功，則 S_OK;否則，即為 HRESULT，表示作業失敗的原因，且*ptr*設定為 **`nullptr`** 。

- 如果此作業成功，則 S_OK，但目前的 `WeakRef` 物件已經釋放。 參數*ptr*設定為 **`nullptr`** 。

- S_OK，如果此作業成功，但目前的 `WeakRef` 物件不是衍生自參數*riid*。 參數*ptr*設定為 **`nullptr`** 。 (如需詳細資訊，請參閱＜備註＞)。

### <a name="remarks"></a>備註

如果參數*riid*並非衍生自，則會發出錯誤 `IInspectable` 。 這個錯誤會取代傳回值。

第一個範本是程式碼中應該使用的表單。 第二個範本 (此處未顯示但會在標頭檔中宣告) 是支援 C++ 語言功能的內部協助程式特製化，例如 [auto](../../cpp/auto-cpp.md) 類型推斷關鍵字。

從 Windows 10 SDK 開始， `WeakRef` 如果無法取得弱式參考，這個方法就不會將實例設定為 **`nullptr`** ，因此您應該避免檢查的錯誤檢查程式碼 `WeakRef` **`nullptr`** 。 相反地，請檢查的*ptr* **`nullptr`** 。

## <a name="weakrefcopyto-method"></a><a name="copyto"></a>WeakRef：： CopyTo 方法

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
指標 `IInspectable` 介面。 如果*U*不是衍生自，就會發出錯誤 `IInspectable` 。

*riid*<br/>
介面識別碼。 如果*riid*並非衍生自，則會發出錯誤 `IWeakReference` 。

*ptr*<br/>
或的雙向間接指標 `IInspectable` `IWeakReference` 。

### <a name="return-value"></a>傳回值

若成功，則為 S_OK，否則會是 HRESULT 指出失敗。 如需詳細資訊，請參閱**備註**。

### <a name="remarks"></a>備註

傳回值 S_OK 只表示此作業已成功，而不會指出是否已將弱式參考解析為強式參考。 如果傳回 S_OK，請測試參數*p*是否為強式參考。也就是，參數*p*不等於 **`nullptr`** 。

從 Windows 10 SDK 開始， `WeakRef` 如果無法取得弱式參考，這個方法就不會將實例設定為 **`nullptr`** ，因此您應該避免錯誤檢查檢查的程式碼 `WeakRef` **`nullptr`** 。 相反地，請檢查的*ptr* **`nullptr`** 。

## <a name="weakrefoperatoramp-operator"></a><a name="operator-ampersand-operator"></a>WeakRef：： operator &amp; 運算子

傳回 `ComPtrRef` 表示目前物件的物件 `WeakRef` 。

```cpp
Details::ComPtrRef<WeakRef> operator&() throw()
```

### <a name="return-value"></a>傳回值

`ComPtrRef`物件，表示目前的 `WeakRef` 物件。

### <a name="remarks"></a>備註

這是內部 helper 運算子，不適合用于您的程式碼。

## <a name="weakrefweakref-constructor"></a><a name="weakref"></a>WeakRef：： WeakRef 函式

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
初始化目前物件之現有物件的指標、參考或右值參考 `WeakRef` 。

### <a name="remarks"></a>備註

第一個函式會初始化空的 `WeakRef` 物件。 第二個函式會 `WeakRef` 從介面的指標初始化物件 `IWeakReference` 。 第三個函式會 `WeakRef` 從物件的參考初始化物件 `ComPtr<IWeakReference>` 。 第四個和第五個函式會 `WeakRef` 從另一個物件初始化物件 `WeakRef` 。
