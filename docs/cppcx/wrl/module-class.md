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
ms.openlocfilehash: afd2edacefdf5d62b50a03c0a8c37f13ee5d9c9f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371322"
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

*模組類型*<br/>
一個或多個[模組類型](moduletype-enumeration.md)枚舉值的組合。

## <a name="members"></a>成員

### <a name="protected-classes"></a>受保護類

名稱                                                                                | 描述
----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------
[模組::通用釋放程式](module-genericreleasenotifier-class.md) | 釋放當前模組中的最後一個物件時調用事件處理程式。 事件處理程式由 lambda、functor 或指標到函數指定。
[模組::方法釋放器](module-methodreleasenotifier-class.md)   | 釋放當前模組中的最後一個物件時調用事件處理程式。 事件處理程式由物件及其指向方法的成員指定。
[模組::釋放器](module-releasenotifier-class.md)               | 釋放模組中的最後一個物件時調用事件處理程式。

### <a name="public-constructors"></a>公用建構函式

名稱                             | 描述
-------------------------------- | -----------------------------------------------------------
[模組::*模組](#tilde-module) | 取消初始化類的`Module`當前實例。

### <a name="protected-constructors"></a>受保護的建構函式

名稱                      | 描述
------------------------- | ---------------------------------------------------
[模組::模組](#module) | 將 `Module` 類別的新執行個體初始化。

### <a name="public-methods"></a>公用方法

名稱                                                    | 描述
------------------------------------------------------- | --------------------------------------------------------------------------------------------------
[模組::建立](#create)                               | 創建模組的實例。
[模組::D物件計數](#decrementobjectcount)   | 減少模組跟蹤的物件數。
[模組::取得啟動工廠](#getactivationfactory)   | 獲取模組的激活工廠。
[模組::取得類物件](#getclassobject)               | 檢索類工廠的緩存。
[模組::取得模組](#getmodule)                         | 創建模組的實例。
[模組::取得物件計數](#getobjectcount)               | 檢索此模組管理的物件數。
[模組::增量物件計數](#incrementobjectcount)   | 增加模組跟蹤的物件數。
[模組::註冊COM物件](#registercomobject)         | 註冊一個或多個 COM 物件,以便其他應用程式可以連接到它們。
[模組::註冊物件](#registerobjects)             | 註冊 COM 或 Windows 執行時物件,以便其他應用程式可以連接到它們。
[模組::註冊WinRT物件](#registerwinrtobject)     | 註冊一個或多個 Windows 運行時物件,以便其他應用程式可以連接到它們。
[模組::終止](#terminate)                         | 導致模組實例化的所有工廠關閉。
[模組::未註冊COM物件](#unregistercomobject)     | 取消註冊一個或多個 COM 物件,這阻止其他應用程式連接到它們。
[模組::取消註冊物件](#unregisterobjects)         | 取消註冊指定模組中的物件,以便其他應用程式無法連接到它們。
[模組::未註冊WinRT物件](#unregisterwinrtobject) | 取消註冊一個或多個 Windows 運行時物件,以便其他應用程式無法連接到它們。

### <a name="protected-methods"></a>保護方法

名稱                      | 描述
------------------------- | --------------------------------
[模組::建立](#create) | 創建模組的實例。

### <a name="protected-data-members"></a>受保護的資料成員

名稱                                         | 描述
-------------------------------------------- | --------------------------------------------------------------------------------------------------------
[模組::objectCount_](#objectcount)         | 追蹤使用[Make](make-function.md)函數建立的類數。
[模組::releaseNotifier_](#releasenotifier) | 保存指向`ReleaseNotifier`物件的指標。

### <a name="macros"></a>巨集

名稱                                                                   | 描述
---------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[ActivatableClass](activatableclass-macros.md)              | 填充包含可以創建指定類實例的工廠的內部緩存。 此宏指定預設工廠和組 ID 參數。
[ActivatableClassWithFactory](activatableclass-macros.md)   | 填充包含可以創建指定類實例的工廠的內部緩存。 此宏使您能夠指定特定的工廠參數。
[ActivatableClassWithFactoryEx](activatableclass-macros.md) | 填充包含可以創建指定類實例的工廠的內部緩存。 此宏使您能夠指定特定的工廠和組 ID 參數。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`ModuleBase`

`Module`

`Module`

## <a name="requirements"></a>需求

**標題:** 模組.h

**命名空間：** Microsoft::WRL

## <a name="modulemodule"></a><a name="tilde-module"></a>模組::*模組

取消初始化類的`Module`當前實例。

```cpp
virtual ~Module();
```

## <a name="modulecreate"></a><a name="create"></a>模組::建立

創建模組的實例。

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
釋放模組的最後一個實例物件時調用。

*物件*<br/>
*物件**和方法*參數是組合使用的。 釋放模組中的最後一個實例物件時,指向最後一個實例物件。

*方法*<br/>
*物件**和方法*參數是組合使用的。 在釋放模組中的最後一個實例物件時,指向最後一個實例物件的方法。

### <a name="return-value"></a>傳回值

參考模組。

## <a name="moduledecrementobjectcount"></a><a name="decrementobjectcount"></a>模組::D物件計數

減少模組跟蹤的物件數。

```cpp
virtual long DecrementObjectCount();
```

### <a name="return-value"></a>傳回值

遞減操作前的計數。

## <a name="modulegetactivationfactory"></a><a name="getactivationfactory"></a>模組::取得啟動工廠

獲取模組的激活工廠。

```cpp
WRL_NOTHROW HRESULT GetActivationFactory(
   _In_ HSTRING pActivatibleClassId,
   _Deref_out_ IActivationFactory **ppIFactory,
   wchar_t* serverName = nullptr
);
```

### <a name="parameters"></a>參數

*p 可啟動類別 Id*<br/>
運行時類的 IID。

*ppIFactory*<br/>
指定運行時類的 IactivationFactory。

*伺服器名稱*<br/>
當前模組中類工廠子集的名稱。 指定[可啟動類與FactoryEx](activatableclass-macros.md)宏中使用的伺服器名稱,`nullptr`或指定 獲取預設伺服器名稱。

### <a name="return-value"></a>傳回值

S_OK如果成功;否則,獲取啟動工廠返回的 HRESULT。

## <a name="modulegetclassobject"></a><a name="getclassobject"></a>模組::取得類物件

保留一個類工廠的緩存。

```cpp
HRESULT GetClassObject(
   REFCLSID clsid,
   REFIID riid,
   _Deref_out_ void **ppv,
   wchar_t* serverName = nullptr
);
```

### <a name="parameters"></a>參數

*Clsid*<br/>
類識別碼。

*riid*<br/>
您請求的介面 ID。

*Ppv*<br/>
指向返回物件的指標。

*伺服器名稱*<br/>
在`ActivatableClassWithFactory``ActivatableClassWithFactoryEx``ActivatableClass`、 或巨集中指定的伺服器名稱;或`nullptr`獲取預設伺服器名稱。

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

此方法僅適用於 COM,而不是 Windows 執行時。 此方法僅`IClassFactory`公開方法。

## <a name="modulegetmodule"></a><a name="getmodule"></a>模組::取得模組

創建模組的實例。

```cpp
static Module& GetModule();
WRL_NOTHROW static Module& GetModule();
```

### <a name="return-value"></a>傳回值

對模組的引用。

## <a name="modulegetobjectcount"></a><a name="getobjectcount"></a>模組::取得物件計數

檢索此模組管理的物件數。

```cpp
virtual long GetObjectCount() const;
```

### <a name="return-value"></a>傳回值

此模組管理的物件的當前數量。

## <a name="moduleincrementobjectcount"></a><a name="incrementobjectcount"></a>模組::增量物件計數

增加模組跟蹤的物件數。

```cpp
virtual long IncrementObjectCount();
```

### <a name="return-value"></a>傳回值

增量操作之前的計數。

## <a name="modulemodule"></a><a name="module"></a>模組::模組

將 `Module` 類別的新執行個體初始化。

```cpp
Module();
```

### <a name="remarks"></a>備註

此構造函數受到保護,不能使用 關鍵`new`字調用。 相反,呼叫[模組:取得模組](#getmodule)或[模組::建立](#create)。

## <a name="moduleobjectcount_"></a><a name="objectcount"></a>模組::objectCount_

追蹤使用[Make](make-function.md)函數建立的類數。

```cpp
volatile long objectCount_;
```

## <a name="moduleregistercomobject"></a><a name="registercomobject"></a>模組::註冊COM物件

註冊一個或多個 COM 物件,以便其他應用程式可以連接到它們。

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
伺服器的完全限定名稱。

*克拉西德斯*<br/>
要註冊的 CLSID 陣列。

*factories*<br/>
正在發佈其可用性的類物件的I未知介面的陣列。

*餅乾*<br/>
操作完成後,指向標識已註冊的類物件的值的指標陣列。 這些值稍後使用,撤銷註冊。

*count*<br/>
要註冊的 CLSID 的數量。

### <a name="return-value"></a>傳回值

S_OK成功者;否則,指示操作失敗原因的 hRESULT,如CO_E_OBJISREG。

### <a name="remarks"></a>備註

COM 物件註冊到 CLSCTX 枚舉的CLSCTX_LOCAL_SERVER枚舉器。

與已註冊物件的連接類型由當前*標誌*範本參數和 REGCLS 枚舉的REGCLS_SUSPENDED枚舉器的組合指定。

## <a name="moduleregisterobjects"></a><a name="registerobjects"></a>模組::註冊物件

註冊 COM 或 Windows 執行時物件,以便其他應用程式可以連接到它們。

```cpp
HRESULT RegisterObjects(
   ModuleBase* module,
   const wchar_t* serverName);
```

### <a name="parameters"></a>參數

*模組*<br/>
COM 或 Windows 運行時物件的陣列。

*伺服器名稱*<br/>
建立物件的伺服器的名稱。

### <a name="return-value"></a>傳回值

S_OK如果成功;否則,指示操作失敗原因的 HRESULT。

## <a name="moduleregisterwinrtobject"></a><a name="registerwinrtobject"></a>模組::註冊WinRT物件

註冊一個或多個 Windows 運行時物件,以便其他應用程式可以連接到它們。

```cpp
HRESULT RegisterWinRTObject(const wchar_t* serverName,
   wchar_t** activatableClassIds,
   WINRT_REGISTRATION_COOKIE* cookie,
   unsigned int count)
```

### <a name="parameters"></a>參數

*伺服器名稱*<br/>
指定受此操作影響的物件子集的名稱。

*可啟動類別識別*<br/>
要註冊的可啟動 CLSID 陣列。

*餅乾*<br/>
標識已註冊的類物件的值。 此值稍後用於撤銷註冊。

*count*<br/>
要註冊的物件數。

### <a name="return-value"></a>傳回值

S_OK如果成功;否則,錯誤 HRESULT,如CO_E_OBJISREG指示操作失敗的原因。

## <a name="modulereleasenotifier_"></a><a name="releasenotifier"></a>模組::releaseNotifier_

保存指向`ReleaseNotifier`物件的指標。

```cpp
ReleaseNotifier *releaseNotifier_;
```

## <a name="moduleterminate"></a><a name="terminate"></a>模組::終止

導致模組實例化的所有工廠關閉。

```cpp
void Terminate();
```

### <a name="remarks"></a>備註

釋放緩存中的工廠。

## <a name="moduleunregistercomobject"></a><a name="unregistercomobject"></a>模組::未註冊COM物件

取消註冊一個或多個 COM 物件,這阻止其他應用程式連接到它們。

```cpp
virtual HRESULT UnregisterCOMObject(
   const wchar_t* serverName,
   DWORD* cookies,
   unsigned int count
```

### <a name="parameters"></a>參數

*伺服器名稱*<br/>
( 未使用 )

*餅乾*<br/>
指向標識要取消註冊的類物件的值的指標陣列。 陣列由[註冊COMObject](#registercomobject)方法創建。

*count*<br/>
要取消註冊的類數。

### <a name="return-value"></a>傳回值

如果此操作成功,S_OK;否則,指示操作失敗原因的錯誤 HRESULT。

## <a name="moduleunregisterobjects"></a><a name="unregisterobjects"></a>模組::取消註冊物件

取消註冊指定模組中的物件,以便其他應用程式無法連接到它們。

```cpp
HRESULT UnregisterObjects(
   ModuleBase* module,
   const wchar_t* serverName);
```

### <a name="parameters"></a>參數

*模組*<br/>
指向模組的指標。

*伺服器名稱*<br/>
指定受此操作影響的物件子集的限定名稱。

### <a name="return-value"></a>傳回值

如果此操作成功,S_OK;否則,指示此操作失敗原因的錯誤 HRESULT。

## <a name="moduleunregisterwinrtobject"></a><a name="unregisterwinrtobject"></a>模組::未註冊WinRT物件

取消註冊一個或多個 Windows 運行時物件,以便其他應用程式無法連接到它們。

```cpp
virtual HRESULT UnregisterWinRTObject(
   unsigned int,
   _Inout_ WINRT_REGISTRATION_COOKIE* cookie
);
```

### <a name="parameters"></a>參數

*餅乾*<br/>
指向要吊銷其註冊的類對象的值的指標。
