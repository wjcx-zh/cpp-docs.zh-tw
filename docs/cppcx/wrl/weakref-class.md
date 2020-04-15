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
ms.openlocfilehash: 681f5a64c3e2902c66facbd4f0ac3a3663a7e79d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374260"
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
|[WeakRef::WeakRef 建構函式](#weakref)|將 `WeakRef` 類別的新執行個體初始化。|
|[WeakRef::~WeakRef 解構函式](#tilde-weakref)|取消初始化類的`WeakRef`當前實例。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[WeakRef::As 方法](#as)|設置指定的`ComPtr`指標參數以表示指定的介面。|
|[WeakRef::AsIID 方法](#asiid)|設置指定的`ComPtr`指標參數以表示指定的介面 ID。|
|[WeakRef::CopyTo 方法](#copyto)|指派介面指標 (如有提供) 給指定的指標變數。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[WeakRef::operator& 運算子](#operator-ampersand-operator)|返回表示`ComPtrRef``WeakRef`當前物件的物件。|

## <a name="remarks"></a>備註

對`WeakRef`象 維護與對象關聯的*強引用*,並且可以有效或無效。 調用`As()``AsIID()`或 方法以獲取強引用。 當強式參考為有效時，它可以存取相關聯的物件。 強式參考無效時 (`nullptr`)，就無法存取相關聯的物件。

物件`WeakRef`通常用於表示其存在由外部線程或應用程式控制的物件。 例如,從對檔`WeakRef`物件的引用構造物件。 在檔案開啟時，強式參考是有效的。 但若檔案關閉，強式參考就變成無效的。

請注意，在 Windows 10 SDK 的 [As](#as)、 [AsIID](#asiid) 和 [CopyTo](#copyto) 方法中有行為變更。 以前,在調用這些方法中的任何一個后,可以檢查`WeakRef``nullptr`for 以確定是否成功獲取了強引用,如以下代碼中:

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

使用 Windows 10 SDK (或更新版本) 時，上述程式碼不作用。 相反,請檢查傳入的`nullptr`指標。

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

## <a name="weakrefweakref-destructor"></a><a name="tilde-weakref"></a>弱參考::*弱參考析構函數

取消初始化類的`WeakRef`當前實例。

```cpp
~WeakRef();
```

## <a name="weakrefas-method"></a><a name="as"></a>弱引用:作為方法

設置指定的`ComPtr`指標參數以表示指定的介面。

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

*美國*<br/>
介面識別碼。

*Ptr*<br/>
此操作完成後,表示參數*U*的物件。

### <a name="return-value"></a>傳回值

- 如果此操作成功,S_OK;否則,指示操作失敗原因的 HRESULT,並將*ptr*設定為`nullptr`。

- S_OK此操作是否成功,但當前`WeakRef`物件已釋放。 參數*ptr*`nullptr`設定為 。

- 如果此操作成功,S_OK,但當前`WeakRef`物件不是從參數*U*派生的。參數*ptr*`nullptr`設定為 。

### <a name="remarks"></a>備註

如果參數*U*U`IWeakReference`是 ,或者不是`IInspectable`派生自 ,則發出錯誤。

第一個範本是程式碼中應該使用的表單。 第二個範本是內部的，支援 C++ 語言功能的協助程式特製化，例如 [auto](../../cpp/auto-cpp.md) 類型推斷關鍵字。

從 Windows 10 SDK 開始`WeakRef`,如果`nullptr`無法獲取 弱引用 ,此方法不會將實例設置為`WeakRef``nullptr`,因此應避免檢查 for 的代碼錯誤檢查。 相反,檢查*ptr*的`nullptr`。

## <a name="weakrefasiid-method"></a><a name="asiid"></a>弱引用:asIID 方法

設置指定的`ComPtr`指標參數以表示指定的介面 ID。

```cpp
HRESULT AsIID(
   REFIID riid,
   _Out_ ComPtr<IInspectable>* ptr
);
```

### <a name="parameters"></a>參數

*riid*<br/>
介面識別碼。

*Ptr*<br/>
此操作完成後,表示參數*riid*的物件。

### <a name="return-value"></a>傳回值

- 如果此操作成功,S_OK;否則,指示操作失敗原因的 HRESULT,並將*ptr*設定為`nullptr`。

- S_OK此操作是否成功,但當前`WeakRef`物件已釋放。 參數*ptr*`nullptr`設定為 。

- 如果此操作成功,但當前`WeakRef`物件不是從參數*riid*派生的,S_OK。 參數*ptr*`nullptr`設定為 。 (如需詳細資訊，請參閱＜備註＞)。

### <a name="remarks"></a>備註

如果參數*riid*不是派生自`IInspectable`,則將發出錯誤。 這個錯誤會取代傳回值。

第一個範本是程式碼中應該使用的表單。 第二個範本 (此處未顯示但會在標頭檔中宣告) 是支援 C++ 語言功能的內部協助程式特製化，例如 [auto](../../cpp/auto-cpp.md) 類型推斷關鍵字。

從 Windows 10 SDK 開始`WeakRef`,如果`nullptr`無法獲取 弱引用 ,此方法不會將實例設置為`WeakRef``nullptr`,因此應避免檢查 for 的代碼錯誤檢查。 相反,檢查*ptr*的`nullptr`。

## <a name="weakrefcopyto-method"></a><a name="copyto"></a>弱引用::複製到方法

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

*美國*<br/>
指標介面`IInspectable`。 如果*U*不是派生自`IInspectable`,則將發出錯誤。

*riid*<br/>
介面識別碼。 如果*riid*不是派`IWeakReference`生自 ,則將發出錯誤。

*Ptr*<br/>
指向`IInspectable``IWeakReference`或的雙間接指標。

### <a name="return-value"></a>傳回值

若成功，則為 S_OK，否則會是 HRESULT 指出失敗。 有關詳細資訊,請參閱**備註**。

### <a name="remarks"></a>備註

傳回值 S_OK 只表示此作業已成功，而不會指出是否已將弱式參考解析為強式參考。 如果返回S_OK,則測試參數*p*是強引用;也就是說,參數*p*不`nullptr`等於 。

從 Windows 10 SDK 開始`WeakRef`,如果`nullptr`無法獲取 弱引用 ,此方法不會將實例設置為`WeakRef`,`nullptr`因此應避免錯誤檢查檢查 for 的代碼。 相反,檢查*ptr*的`nullptr`。

## <a name="weakrefoperatoramp-operator"></a><a name="operator-ampersand-operator"></a>WeakRef::運算元&amp;運算子

返回表示`ComPtrRef``WeakRef`當前物件的物件。

```cpp
Details::ComPtrRef<WeakRef> operator&() throw()
```

### <a name="return-value"></a>傳回值

表示`ComPtrRef``WeakRef`當前物件的物件。

### <a name="remarks"></a>備註

這是一個內部幫助運算符,不用於代碼。

## <a name="weakrefweakref-constructor"></a><a name="weakref"></a>弱參考::弱參考構造函數

將 `WeakRef` 類別的新執行個體初始化。

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

*Ptr*<br/>
對初始化當前`WeakRef`物件的現有物件的指標、引用或rvalue引用。

### <a name="remarks"></a>備註

第一個構造函數初始化一個`WeakRef`空物件。 第二個`WeakRef`建構函數從`IWeakReference`指向介面的指標初始化物件。 第三個`WeakRef`構造函數從對`ComPtr<IWeakReference>`物件的引用初始化物件。 第四個和第五個構造函數從另一`WeakRef``WeakRef`個 物件初始化物件。
