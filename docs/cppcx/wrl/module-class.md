---
title: Module 類別
ms.date: 10/18/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module
- module/Microsoft::WRL::Module::Create
- module/Microsoft::WRL::Module::DecrementObjectCount
- module/Microsoft::WRL::Module::GetActivationFactory
- module/Microsoft::WRL::Module::GetClassObject
- module/Microsoft::WRL::Module::GetModule
- module/Microsoft::WRL::Module::GetObjectCount
- module/Microsoft::WRL::Module::IncrementObjectCount
- module/Microsoft::WRL::Module::Module
- module/Microsoft::WRL::Module::objectCount_Data
- module/Microsoft::WRL::Module::RegisterCOMObject
- module/Microsoft::WRL::Module::RegisterObjects
- module/Microsoft::WRL::Module::RegisterWinRTObject
- module/Microsoft::WRL::Module::releaseNotifier_
- module/Microsoft::WRL::Module::Terminate
- module/Microsoft::WRL::Module::~Module
- module/Microsoft::WRL::Module::UnregisterCOMObject
- module/Microsoft::WRL::Module::UnregisterObjects
- module/Microsoft::WRL::Module::UnregisterWinRTObject
helpviewer_keywords:
- Microsoft::WRL::Module class
- Microsoft::WRL::Module::Create method
- Microsoft::WRL::Module::DecrementObjectCount method
- Microsoft::WRL::Module::GetActivationFactory method
- Microsoft::WRL::Module::GetClassObject method
- Microsoft::WRL::Module::GetModule method
- Microsoft::WRL::Module::GetObjectCount method
- Microsoft::WRL::Module::IncrementObjectCount method
- Microsoft::WRL::Module::Module, constructor
- Microsoft::WRL::Module::objectCount_ data member
- Microsoft::WRL::Module::RegisterCOMObject method
- Microsoft::WRL::Module::RegisterObjects method
- Microsoft::WRL::Module::RegisterWinRTObject method
- Microsoft::WRL::Module::releaseNotifier_ data member
- Microsoft::WRL::Module::Terminate method
- Microsoft::WRL::Module::~Module, destructor
- Microsoft::WRL::Module::UnregisterCOMObject method
- Microsoft::WRL::Module::UnregisterObjects method
- Microsoft::WRL::Module::UnregisterWinRTObject method
ms.assetid: dd67e3b8-c2e1-4f53-8c0f-565a140ba649
ms.openlocfilehash: f7930247c979c111a7f4798e35ebe7aa95209f37
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225744"
---
# <a name="module-class"></a>Module 類別

表示相關物件的集合。

## <a name="syntax"></a>語法

```cpp
template<ModuleType moduleType>
class Module;

template<>
class Module<InProc> : public Details::ModuleBase;

template<>
class Module<OutOfProc> : public Module<InProc>;
```

### <a name="parameters"></a>參數

*moduleType*<br/>
一或多個[ModuleType](moduletype-enumeration.md)列舉值的組合。

## <a name="members"></a>成員

### <a name="protected-classes"></a>受保護的類別

名稱                                                                                | 說明
----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------
[Module：： GenericReleaseNotifier](module-genericreleasenotifier-class.md) | 當目前模組中的最後一個物件釋放時，叫用事件處理常式。 事件處理常式是由 lambda、仿函數或指標對函式所指定。
[Module：： MethodReleaseNotifier](module-methodreleasenotifier-class.md)   | 當目前模組中的最後一個物件釋放時，叫用事件處理常式。 事件處理常式是由物件和其指標對方法成員所指定。
[Module：： ReleaseNotifier](module-releasenotifier-class.md)               | 釋放模組中的最後一個物件時，叫用事件處理常式。

### <a name="public-constructors"></a>公用建構函式

名稱                             | 說明
-------------------------------- | -----------------------------------------------------------
[Module：： ~ 模組](#tilde-module) | 將類別的目前實例 `Module` 。

### <a name="protected-constructors"></a>受保護的建構函式

名稱                      | 說明
------------------------- | ---------------------------------------------------
[Module：： Module](#module) | 初始化 `Module` 類別的新執行個體。

### <a name="public-methods"></a>公用方法

名稱                                                    | 說明
------------------------------------------------------- | --------------------------------------------------------------------------------------------------
[Module：： Create](#create)                               | 建立模組的實例。
[模組：:D ecrementObjectCount](#decrementobjectcount)   | 遞減模組所追蹤的物件數目。
[Module：： GetActivationFactory](#getactivationfactory)   | 取得模組的啟用 factory。
[Module：： GetClassObject](#getclassobject)               | 抓取 class factory 的快取。
[Module：： GetModule](#getmodule)                         | 建立模組的實例。
[Module：： GetObjectCount](#getobjectcount)               | 抓取此模組所管理的物件數目。
[Module：： IncrementObjectCount](#incrementobjectcount)   | 遞增模組所追蹤的物件數目。
[Module：： RegisterCOMObject](#registercomobject)         | 註冊一個或多個 COM 物件，讓其他應用程式可以連接到它們。
[Module：： RegisterObjects](#registerobjects)             | 註冊 COM 或 Windows 執行階段物件，讓其他應用程式可以連接到它們。
[Module：： RegisterWinRTObject](#registerwinrtobject)     | 註冊一個或多個 Windows 執行階段物件，讓其他應用程式可以連接到它們。
[Module：： Terminate](#terminate)                         | 導致模組具現化的所有 factory 都已關閉。
[Module：： UnregisterCOMObject](#unregistercomobject)     | 取消註冊一或多個 COM 物件，以防止其他應用程式連接到這些物件。
[Module：： UnregisterObjects](#unregisterobjects)         | 取消註冊指定模組中的物件，讓其他應用程式無法與其連線。
[Module：： UnregisterWinRTObject](#unregisterwinrtobject) | 取消註冊一或多個 Windows 執行階段物件，讓其他應用程式無法與其連線。

### <a name="protected-methods"></a>保護方法

名稱                      | 說明
------------------------- | --------------------------------
[Module：： Create](#create) | 建立模組的實例。

### <a name="protected-data-members"></a>受保護的資料成員

名稱                                         | 說明
-------------------------------------------- | --------------------------------------------------------------------------------------------------------
[Module：： objectCount_](#objectcount)         | 使用[Make](make-function.md)函式來追蹤已建立的類別數目。
[Module：： releaseNotifier_](#releasenotifier) | 保存物件的指標 `ReleaseNotifier` 。

### <a name="macros"></a>巨集

名稱                                                                   | 說明
---------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[ActivatableClass](activatableclass-macros.md)              | 填入內部快取，其中包含可建立指定類別之實例的 factory。 此宏會指定預設 factory 和群組識別碼參數。
[ActivatableClassWithFactory](activatableclass-macros.md)   | 填入內部快取，其中包含可建立指定類別之實例的 factory。 這個宏可讓您指定特定的 factory 參數。
[ActivatableClassWithFactoryEx](activatableclass-macros.md) | 填入內部快取，其中包含可建立指定類別之實例的 factory。 此宏可讓您指定特定的 factory 和群組識別碼參數。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`ModuleBase`

`Module`

`Module`

## <a name="requirements"></a>需求

**標頭：** module. h

**命名空間：** Microsoft::WRL

## <a name="modulemodule"></a><a name="tilde-module"></a>Module：： ~ 模組

將類別的目前實例 `Module` 。

```cpp
virtual ~Module();
```

## <a name="modulecreate"></a><a name="create"></a>Module：： Create

建立模組的實例。

```cpp
WRL_NOTHROW static Module& Create();
template<typename T>
WRL_NOTHROW static Module& Create(
   T callback
);
template<typename T>
WRL_NOTHROW static Module& Create(
   _In_ T* object,
   _In_ void (T::* method)()
);
```

### <a name="parameters"></a>參數

*T*<br/>
模組類型。

*回撥*<br/>
在釋放模組的最後一個實例物件時呼叫。

*object*<br/>
*物件*和*方法*參數會搭配使用。 當釋放模組中的最後一個實例物件時，指向最後一個實例物件。

*方法*<br/>
*物件*和*方法*參數會搭配使用。 當釋放模組中的最後一個實例物件時，指向最後一個實例物件的方法。

### <a name="return-value"></a>傳回值

模組的參考。

## <a name="moduledecrementobjectcount"></a><a name="decrementobjectcount"></a>模組：:D ecrementObjectCount

遞減模組所追蹤的物件數目。

```cpp
virtual long DecrementObjectCount();
```

### <a name="return-value"></a>傳回值

遞減運算之前的計數。

## <a name="modulegetactivationfactory"></a><a name="getactivationfactory"></a>Module：： GetActivationFactory

取得模組的啟用 factory。

```cpp
WRL_NOTHROW HRESULT GetActivationFactory(
   _In_ HSTRING pActivatibleClassId,
   _Deref_out_ IActivationFactory **ppIFactory,
   wchar_t* serverName = nullptr
);
```

### <a name="parameters"></a>參數

*pActivatibleClassId*<br/>
執行時間類別的 IID。

*ppIFactory*<br/>
所指定執行時間類別的 IActivationFactory。

*serverName*<br/>
目前模組中的 class factory 子集名稱。 指定[ActivatableClassWithFactoryEx](activatableclass-macros.md)宏中使用的伺服器名稱，或指定 **`nullptr`** 以取得預設的伺服器名稱。

### <a name="return-value"></a>傳回值

如果成功，則 S_OK;否則，GetActivationFactory 會傳回 HRESULT。

## <a name="modulegetclassobject"></a><a name="getclassobject"></a>Module：： GetClassObject

擷取 class factory 的快取。

```cpp
HRESULT GetClassObject(
   REFCLSID clsid,
   REFIID riid,
   _Deref_out_ void **ppv,
   wchar_t* serverName = nullptr
);
```

### <a name="parameters"></a>參數

*clsid*<br/>
類別識別碼。

*riid*<br/>
您要求的介面識別碼。

*ppv*<br/>
傳回之物件的指標。

*serverName*<br/>
在、或宏中指定的伺服器名稱 `ActivatableClassWithFactory` ， `ActivatableClassWithFactoryEx` 或用 `ActivatableClass` **`nullptr`** 來取得預設的伺服器名稱。

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

此方法僅適用于 COM，而不是 Windows 執行階段。 這個方法只會公開 `IClassFactory` 方法。

## <a name="modulegetmodule"></a><a name="getmodule"></a>Module：： GetModule

建立模組的實例。

```cpp
static Module& GetModule();
WRL_NOTHROW static Module& GetModule();
```

### <a name="return-value"></a>傳回值

模組的參考。

## <a name="modulegetobjectcount"></a><a name="getobjectcount"></a>Module：： GetObjectCount

抓取此模組所管理的物件數目。

```cpp
virtual long GetObjectCount() const;
```

### <a name="return-value"></a>傳回值

此模組目前管理的物件數目。

## <a name="moduleincrementobjectcount"></a><a name="incrementobjectcount"></a>Module：： IncrementObjectCount

遞增模組所追蹤的物件數目。

```cpp
virtual long IncrementObjectCount();
```

### <a name="return-value"></a>傳回值

遞增作業之前的計數。

## <a name="modulemodule"></a><a name="module"></a>Module：： Module

初始化 `Module` 類別的新執行個體。

```cpp
Module();
```

### <a name="remarks"></a>備註

這個函式會受到保護，而且不能使用關鍵字來呼叫 **`new`** 。 請改為呼叫[module：： GetModule](#getmodule)或[Module：： Create](#create)。

## <a name="moduleobjectcount_"></a><a name="objectcount"></a>Module：： objectCount_

使用[Make](make-function.md)函式來追蹤已建立的類別數目。

```cpp
volatile long objectCount_;
```

## <a name="moduleregistercomobject"></a><a name="registercomobject"></a>Module：： RegisterCOMObject

註冊一個或多個 COM 物件，讓其他應用程式可以連接到它們。

```cpp
WRL_NOTHROW virtual HRESULT RegisterCOMObject(
   const wchar_t* serverName,
   IID* clsids,
   IClassFactory** factories,
   DWORD* cookies,
   unsigned int count);
```

### <a name="parameters"></a>參數

*serverName*<br/>
伺服器的完整名稱。

*clsid*<br/>
要註冊的 Clsid 陣列。

*factories*<br/>
要發行其可用性之類別物件的 IUnknown 介面陣列。

*cookie*<br/>
當作業完成時，就是值的指標陣列，用以識別已註冊的類別物件。 稍後會使用這些值撤銷註冊。

*計數*<br/>
要註冊的 Clsid 數目。

### <a name="return-value"></a>傳回值

S_OK 成功;否則，就是 CO_E_OBJISREG 的 HRESULT，表示作業失敗的原因。

### <a name="remarks"></a>備註

COM 物件會使用 CLSCTX 列舉的 CLSCTX_LOCAL_SERVER 列舉值進行註冊。

已註冊物件的連線類型是由目前*comflag*樣板參數的組合和 REGCLS 列舉的 REGCLS_SUSPENDED 列舉值所指定。

## <a name="moduleregisterobjects"></a><a name="registerobjects"></a>Module：： RegisterObjects

註冊 COM 或 Windows 執行階段物件，讓其他應用程式可以連接到它們。

```cpp
HRESULT RegisterObjects(
   ModuleBase* module,
   const wchar_t* serverName);
```

### <a name="parameters"></a>參數

*module*<br/>
COM 或 Windows 執行階段物件的陣列。

*serverName*<br/>
建立物件的伺服器名稱。

### <a name="return-value"></a>傳回值

如果成功，則 S_OK;否則，即為 HRESULT，表示作業失敗的原因。

## <a name="moduleregisterwinrtobject"></a><a name="registerwinrtobject"></a>Module：： RegisterWinRTObject

註冊一個或多個 Windows 執行階段物件，讓其他應用程式可以連接到它們。

```cpp
HRESULT RegisterWinRTObject(const wchar_t* serverName,
   wchar_t** activatableClassIds,
   WINRT_REGISTRATION_COOKIE* cookie,
   unsigned int count)
```

### <a name="parameters"></a>參數

*serverName*<br/>
指定受此作業影響之物件子集的名稱。

*activatableClassIds*<br/>
要註冊的可啟動 Clsid 陣列。

*去*<br/>
值，識別已註冊的類別物件。 稍後會使用此值來撤銷註冊。

*計數*<br/>
要註冊的物件數目。

### <a name="return-value"></a>傳回值

如果成功，則 S_OK;否則，就會出現錯誤 HRESULT，例如 CO_E_OBJISREG，指出作業失敗的原因。

## <a name="modulereleasenotifier_"></a><a name="releasenotifier"></a>Module：： releaseNotifier_

保存物件的指標 `ReleaseNotifier` 。

```cpp
ReleaseNotifier *releaseNotifier_;
```

## <a name="moduleterminate"></a><a name="terminate"></a>Module：： Terminate

導致模組具現化的所有 factory 都已關閉。

```cpp
void Terminate();
```

### <a name="remarks"></a>備註

釋放快取中的處理站。

## <a name="moduleunregistercomobject"></a><a name="unregistercomobject"></a>Module：： UnregisterCOMObject

取消註冊一或多個 COM 物件，以防止其他應用程式連接到這些物件。

```cpp
virtual HRESULT UnregisterCOMObject(
   const wchar_t* serverName,
   DWORD* cookies,
   unsigned int count
```

### <a name="parameters"></a>參數

*serverName*<br/>
未使用

*cookie*<br/>
值的指標陣列，識別要取消註冊的類別物件。 陣列是由[RegisterCOMObject](#registercomobject)方法所建立。

*計數*<br/>
要取消註冊的類別數目。

### <a name="return-value"></a>傳回值

如果此作業成功，則 S_OK;否則，就會出現錯誤 HRESULT，指出作業失敗的原因。

## <a name="moduleunregisterobjects"></a><a name="unregisterobjects"></a>Module：： UnregisterObjects

取消註冊指定模組中的物件，讓其他應用程式無法與其連線。

```cpp
HRESULT UnregisterObjects(
   ModuleBase* module,
   const wchar_t* serverName);
```

### <a name="parameters"></a>參數

*module*<br/>
模組的指標。

*serverName*<br/>
限定名稱，指定受此作業影響之物件的子集。

### <a name="return-value"></a>傳回值

如果此作業成功，則 S_OK;否則，就會出現錯誤 HRESULT，指出此作業失敗的原因。

## <a name="moduleunregisterwinrtobject"></a><a name="unregisterwinrtobject"></a>Module：： UnregisterWinRTObject

取消註冊一或多個 Windows 執行階段物件，讓其他應用程式無法與其連線。

```cpp
virtual HRESULT UnregisterWinRTObject(
   unsigned int,
   _Inout_ WINRT_REGISTRATION_COOKIE* cookie
);
```

### <a name="parameters"></a>參數

*去*<br/>
值的指標，識別要撤銷其註冊的類別物件。
