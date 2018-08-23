---
title: 模組類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module
dev_langs:
- C++
helpviewer_keywords:
- Module class
ms.assetid: dd67e3b8-c2e1-4f53-8c0f-565a140ba649
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2ae36838a1375b541951122bb00b522cf320650d
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42599751"
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

*moduleType*  
一或多個組合[ModuleType](../windows/moduletype-enumeration.md)列舉值。

## <a name="members"></a>成員

### <a name="protected-classes"></a>受保護的類別

|名稱|描述|
|----------|-----------------|
|[Module::GenericReleaseNotifier 類別](../windows/module-genericreleasenotifier-class.md)|發行目前的模組中的最後一個物件時，會叫用事件處理常式。 Lambda、 函式或函式指標上所指定的事件處理常式。|
|[Module::MethodReleaseNotifier 類別](../windows/module-methodreleasenotifier-class.md)|發行目前的模組中的最後一個物件時，會叫用事件處理常式。 物件和其指標-至-a-方法成員所指定的事件處理常式。|
|[Module::ReleaseNotifier 類別](../windows/module-releasenotifier-class.md)|發行模組中的最後一個物件時，會叫用事件處理常式。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[Module::~Module 解構函式](../windows/module-tilde-module-destructor.md)|取消初始化目前的執行個體**模組**類別。|

### <a name="protected-constructors"></a>受保護的建構函式

|名稱|描述|
|----------|-----------------|
|[Module::Module 建構函式](../windows/module-module-constructor.md)|初始化的新執行個體**模組**類別。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[Module::Create 方法](../windows/module-create-method.md)|建立模組的執行個體。|
|[Module::DecrementObjectCount 方法](../windows/module-decrementobjectcount-method.md)|此模組所追蹤的物件數目的遞減。|
|[Module::GetActivationFactory 方法](../windows/module-getactivationfactory-method.md)|取得啟用 factory 模組。|
|[Module::GetClassObject 方法](../windows/module-getclassobject-method.md)|擷取快取的 class factory。|
|[Module::GetModule 方法](../windows/module-getmodule-method.md)|建立模組的執行個體。|
|[Module::GetObjectCount 方法](../windows/module-getobjectcount-method.md)|擷取由這個模組的物件數目。|
|[Module::IncrementObjectCount 方法](../windows/module-incrementobjectcount-method.md)|遞增模組所追蹤的物件數目。|
|[Module::RegisterCOMObject 方法](../windows/module-registercomobject-method.md)|讓其他應用程式可以連線到它們，請註冊一個或多個 COM 物件。|
|[Module::RegisterObjects 方法](../windows/module-registerobjects-method.md)|註冊 COM 或 Windows 執行階段物件，讓其他應用程式可以連線到它們。|
|[Module::RegisterWinRTObject 方法](../windows/module-registerwinrtobject-method.md)|讓其他應用程式可以連線到它們，請註冊一個或多個 Windows 執行階段物件。|
|[Module::Terminate 方法](../windows/module-terminate-method.md)|會導致所有關閉的模組來具現化的處理站。|
|[Module::UnregisterCOMObject 方法](../windows/module-unregistercomobject-method.md)|取消註冊一或多個 COM 物件，這是為了避免與它們連線的其他應用程式。|
|[Module::UnregisterObjects 方法](../windows/module-unregisterobjects-method.md)|取消註冊指定的模組中的物件，以便讓其他應用程式無法連線。|
|[Module::UnregisterWinRTObject 方法](../windows/module-unregisterwinrtobject-method.md)|取消註冊一或多個 Windows 執行階段物件，以便讓其他應用程式無法連線。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[Module::Create 方法](../windows/module-create-method.md)|建立模組的執行個體。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[Module::objectCount_ 資料成員](../windows/module-objectcount-data-member.md)|追蹤已建立多少個類別的[讓](../windows/make-function.md)函式。|
|[Module::releaseNotifier_ 資料成員](../windows/module-releasenotifier-data-member.md)|保留的指標`ReleaseNotifier`物件。|

### <a name="macros"></a>巨集

|||
|-|-|
|[ActivatableClass](../windows/activatableclass-macros.md)|擴展內部快取，其中包含可以建立指定類別的執行個體的處理站。 這個巨集指定預設的處理站和群組識別碼的參數。|
|[ActivatableClassWithFactory](../windows/activatableclass-macros.md)|擴展內部快取，其中包含可以建立指定類別的執行個體的處理站。 這個巨集可讓您指定特定的處理站參數。|
|[ActivatableClassWithFactoryEx](../windows/activatableclass-macros.md)|擴展內部快取，其中包含可以建立指定類別的執行個體的處理站。 這個巨集可讓您指定特定的處理站和群組 ID 參數。|

## <a name="inheritance-hierarchy"></a>繼承階層

`ModuleBase`

`Module`

`Module`

## <a name="requirements"></a>需求

**標頭：** module.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)