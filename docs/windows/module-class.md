---
title: 模組類別 |Microsoft Docs
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-windows
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5df7ae90a347d82b303d7db251e533733c8e4a86
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808626"
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
一或多個組合[ModuleType](../windows/moduletype-enumeration.md)列舉值。

## <a name="members"></a>成員

### <a name="protected-classes"></a>受保護的類別

名稱                                                                                | 描述
----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------
[Module:: genericreleasenotifier](../windows/module-genericreleasenotifier-class.md) | 發行目前的模組中的最後一個物件時，會叫用事件處理常式。 Lambda、 函式或函式指標上所指定的事件處理常式。
[Module:: methodreleasenotifier](../windows/module-methodreleasenotifier-class.md)   | 發行目前的模組中的最後一個物件時，會叫用事件處理常式。 物件和其指標-至-a-方法成員所指定的事件處理常式。
[Module:: releasenotifier](../windows/module-releasenotifier-class.md)               | 發行模組中的最後一個物件時，會叫用事件處理常式。

### <a name="public-constructors"></a>公用建構函式

名稱                             | 描述
-------------------------------- | -----------------------------------------------------------
[模組:: ~ 模組](#tilde-module) | 取消初始化目前的執行個體`Module`類別。

### <a name="protected-constructors"></a>受保護的建構函式

名稱                      | 描述
------------------------- | ---------------------------------------------------
[Module:: module](#module) | 初始化 `Module` 類別的新執行個體。

### <a name="public-methods"></a>公用方法

名稱                                                    | 描述
------------------------------------------------------- | --------------------------------------------------------------------------------------------------
[Module:: create](#create)                               | 建立模組的執行個體。
[Module:: decrementobjectcount](#decrementobjectcount)   | 此模組所追蹤的物件數目的遞減。
[Module:: getactivationfactory](#getactivationfactory)   | 取得啟用 factory 模組。
[Module:: getclassobject](#getclassobject)               | 擷取快取的 class factory。
[Module:: getmodule](#getmodule)                         | 建立模組的執行個體。
[Module:: getobjectcount](#getobjectcount)               | 擷取由這個模組的物件數目。
[Module:: incrementobjectcount](#incrementobjectcount)   | 遞增模組所追蹤的物件數目。
[Module:: registercomobject](#registercomobject)         | 讓其他應用程式可以連線到它們，請註冊一個或多個 COM 物件。
[Module:: registerobjects](#registerobjects)             | 註冊 COM 或 Windows 執行階段物件，讓其他應用程式可以連線到它們。
[Module:: registerwinrtobject](#registerwinrtobject)     | 讓其他應用程式可以連線到它們，請註冊一個或多個 Windows 執行階段物件。
[Module:: terminate](#terminate)                         | 會導致所有關閉的模組來具現化的處理站。
[Module:: unregistercomobject](#unregistercomobject)     | 取消註冊一或多個 COM 物件，這是為了避免與它們連線的其他應用程式。
[Module:: unregisterobjects](#unregisterobjects)         | 取消註冊指定的模組中的物件，以便讓其他應用程式無法連線。
[Module:: unregisterwinrtobject](#unregisterwinrtobject) | 取消註冊一或多個 Windows 執行階段物件，以便讓其他應用程式無法連線。

### <a name="protected-methods"></a>保護方法

名稱                      | 描述
------------------------- | --------------------------------
[Module:: create](#create) | 建立模組的執行個體。

### <a name="protected-data-members"></a>受保護的資料成員

名稱                                         | 描述
-------------------------------------------- | --------------------------------------------------------------------------------------------------------
[Module:: objectcount_](#objectcount)         | 追蹤已建立多少個類別的[讓](../windows/make-function.md)函式。
[Module:: releasenotifier_](#releasenotifier) | 保留的指標`ReleaseNotifier`物件。

### <a name="macros"></a>巨集

名稱 |描述-----|---美元[ActivatableClass](../windows/activatableclass-macros.md) | 擴展內部快取，其中包含可以建立指定類別的執行個體的處理站。 這個巨集指定預設的處理站和群組識別碼的參數。
[ActivatableClassWithFactory](../windows/activatableclass-macros.md) |擴展內部快取，其中包含可以建立指定類別的執行個體的處理站。 這個巨集可讓您指定特定的處理站參數。
[ActivatableClassWithFactoryEx](../windows/activatableclass-macros.md) |擴展內部快取，其中包含可以建立指定類別的執行個體的處理站。 這個巨集可讓您指定特定的處理站和群組 ID 參數。

## <a name="inheritance-hierarchy"></a>繼承階層

`ModuleBase`

`Module`

`Module`

## <a name="requirements"></a>需求

**標頭：** module.h

**命名空間：** Microsoft::WRL

## <a name="tilde-module"></a>模組:: ~ 模組

取消初始化目前的執行個體`Module`類別。

```cpp
virtual ~Module();
```

## <a name="create"></a>Module:: create

建立模組的執行個體。

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

*回呼*<br/>
當您釋放最後一個執行個體物件的模組時呼叫。

*object*<br/>
*物件*並*方法*參數搭配使用的。 點的最後一個執行個體物件，當使用者放開模組中的最後一個執行個體物件。

*方法*<br/>
*物件*並*方法*參數搭配使用的。 方法的最後一個執行個體物件時釋放最後一個執行個體物件模組中的點。

### <a name="return-value"></a>傳回值

模組參考。

## <a name="decrementobjectcount"></a>Module:: decrementobjectcount

此模組所追蹤的物件數目的遞減。

```cpp
virtual long DecrementObjectCount();
```

### <a name="return-value"></a>傳回值

遞減作業之前計數。

## <a name="getactivationfactory"></a>Module:: getactivationfactory

取得啟用 factory 模組。

```cpp
WRL_NOTHROW HRESULT GetActivationFactory(
   _In_ HSTRING pActivatibleClassId,
   _Deref_out_ IActivationFactory **ppIFactory,
   wchar_t* serverName = nullptr
);
```

### <a name="parameters"></a>參數

*pActivatibleClassId*<br/>
執行階段類別的 IID。

*ppIFactory*<br/>
指定的執行階段類別 IActivationFactory。

*伺服器名稱*<br/>
在目前模組的 class factory 子集的名稱。 指定用於的伺服器名稱[ActivatableClassWithFactoryEx](../windows/activatableclass-macros.md)巨集，或指定`nullptr`取得預設的伺服器名稱。

### <a name="return-value"></a>傳回值

如果成功則為 S_OK否則，GetActivationFactory 所傳回的 HRESULT。

## <a name="getclassobject"></a>Module:: getclassobject

擷取快取的 class factory。

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
傳回的物件指標。

*伺服器名稱*<br/>
中指定的伺服器名稱`ActivatableClassWithFactory`， `ActivatableClassWithFactoryEx`，或`ActivatableClass`巨集; 或`nullptr`取得預設的伺服器名稱。

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

這個方法僅適用於 COM，而不是 Windows 執行階段。 這個方法只會公開`IClassFactory`方法。

## <a name="getmodule"></a>Module:: getmodule

建立模組的執行個體。

```cpp
static Module& GetModule();
WRL_NOTHROW static Module& GetModule();
```

### <a name="return-value"></a>傳回值

模組的參考。

## <a name="getobjectcount"></a>Module:: getobjectcount

擷取由這個模組的物件數目。

```cpp
virtual long GetObjectCount() const;
```

### <a name="return-value"></a>傳回值

目前受此模組的物件數目。

## <a name="incrementobjectcount"></a>Module:: incrementobjectcount

遞增模組所追蹤的物件數目。

```cpp
virtual long IncrementObjectCount();
```

### <a name="return-value"></a>傳回值

之前的遞增作業計數。

## <a name="module"></a>Module:: module

初始化 `Module` 類別的新執行個體。

```cpp
Module();
```

### <a name="remarks"></a>備註

這個建構函式受到保護，而且無法使用呼叫`new`關鍵字。 相反地，呼叫[module:: getmodule](#getmodule)或是[module:: create](#create)。

## <a name="objectcount"></a>Module:: objectcount_

追蹤已建立多少個類別的[讓](../windows/make-function.md)函式。

```cpp
volatile long objectCount_;
```

## <a name="registercomobject"></a>Module:: registercomobject

讓其他應用程式可以連線到它們，請註冊一個或多個 COM 物件。

```cpp
WRL_NOTHROW virtual HRESULT RegisterCOMObject(
   const wchar_t* serverName,
   IID* clsids,
   IClassFactory** factories,
   DWORD* cookies,
   unsigned int count);

```

### <a name="parameters"></a>參數

*伺服器名稱*<br/>
完整伺服器名稱。

*clsid*<br/>
若要註冊的 Clsid 的陣列。

*處理站*<br/>
正在發行其可用性的類別物件的 IUnknown 介面的陣列。

*Cookie*<br/>
作業完成後，物件的陣列的指標識別類別的值，已註冊。 稍後會使用這些值，撤銷。

*count*<br/>
若要註冊的 Clsid 數目。

### <a name="return-value"></a>傳回值

S_OK 如果成功;否則，例如指出原因的 CO_E_OBJISREG HRESULT 作業失敗。

### <a name="remarks"></a>備註

COM 物件會向 CLSCTX 列舉型別的 CLSCTX_LOCAL_SERVER 列舉值。

連線到已註冊的物件的型別由目前的組合*comflag*樣板參數和 REGCLS 列舉型別的 REGCLS_SUSPENDED 列舉值。

## <a name="registerobjects"></a>Module:: registerobjects

註冊 COM 或 Windows 執行階段物件，讓其他應用程式可以連線到它們。

```cpp
HRESULT RegisterObjects(
   ModuleBase* module,
   const wchar_t* serverName);
```

### <a name="parameters"></a>參數

*module*<br/>
COM 或 Windows 執行階段物件的陣列。

*伺服器名稱*<br/>
建立物件的伺服器名稱。

### <a name="return-value"></a>傳回值

如果成功則為 S_OK否則，HRESULT，指出的原因，作業失敗。

## <a name="registerwinrtobject"></a>Module:: registerwinrtobject

讓其他應用程式可以連線到它們，請註冊一個或多個 Windows 執行階段物件。

```cpp
HRESULT RegisterWinRTObject(const wchar_t* serverName,
   wchar_t** activatableClassIds,
   WINRT_REGISTRATION_COOKIE* cookie,
   unsigned int count)
```

### <a name="parameters"></a>參數

*伺服器名稱*<br/>
指定此作業所影響的物件子集的名稱。

*activatableClassIds*<br/>
若要註冊的可啟動 Clsid 的陣列。

*Cookie*<br/>
識別已註冊的類別物件的值。 此值稍後用來撤銷註冊。

*count*<br/>
若要註冊的物件數目。

### <a name="return-value"></a>傳回值

如果成功則為 S_OK否則，錯誤 HRESULT CO_E_OBJISREG 指出的原因，例如作業失敗。

## <a name="releasenotifier"></a>Module:: releasenotifier_

保留的指標`ReleaseNotifier`物件。

```cpp
ReleaseNotifier *releaseNotifier_;
```

## <a name="terminate"></a>Module:: terminate

會導致所有關閉的模組來具現化的處理站。

```cpp
void Terminate();
```

### <a name="remarks"></a>備註

釋放快取中的處理站。

## <a name="unregistercomobject"></a>Module:: unregistercomobject

取消註冊一或多個 COM 物件，這是為了避免與它們連線的其他應用程式。

```cpp
virtual HRESULT UnregisterCOMObject(
   const wchar_t* serverName,
   DWORD* cookies,
   unsigned int count
```

### <a name="parameters"></a>參數

*伺服器名稱*<br/>
（未使用）

*Cookie*<br/>
識別要取消註冊的類別物件的值的指標陣列。 建立陣列[RegisterCOMObject](#registercomobject)方法。

*count*<br/>
若要取消註冊的類別數目。

### <a name="return-value"></a>傳回值

如果這項作業是成功則為 S_OK否則，錯誤的 HRESULT，指出的原因，作業失敗。

## <a name="unregisterobjects"></a>Module:: unregisterobjects

取消註冊指定的模組中的物件，以便讓其他應用程式無法連線。

```cpp
HRESULT UnregisterObjects(
   ModuleBase* module,
   const wchar_t* serverName);
```

### <a name="parameters"></a>參數

*module*<br/>
模組的指標。

*伺服器名稱*<br/>
合格的名稱，指定此作業所影響的物件子集。

### <a name="return-value"></a>傳回值

如果這項作業是成功則為 S_OK否則為錯誤的 HRESULT 指出的原因，這項作業失敗。

## <a name="unregisterwinrtobject"></a>Module:: unregisterwinrtobject

取消註冊一或多個 Windows 執行階段物件，以便讓其他應用程式無法連線。

```cpp
virtual HRESULT UnregisterWinRTObject(
   unsigned int,
   _Inout_ WINRT_REGISTRATION_COOKIE* cookie
);
```

### <a name="parameters"></a>參數

*Cookie*<br/>
值，識別要撤銷其註冊的類別物件指標。
