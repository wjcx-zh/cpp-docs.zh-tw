---
title: 'Module:: methodreleasenotifier 類別 |Microsoft Docs'
ms.custom: ''
ms.date: 09/17/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::MethodReleaseNotifier
- module/Microsoft::WRL::Module::MethodReleaseNotifier::Invoke
- module/Microsoft::WRL::Module::MethodReleaseNotifier::method_
- module/Microsoft::WRL::Module::MethodReleaseNotifier::MethodReleaseNotifier
- module/Microsoft::WRL::Module::MethodReleaseNotifier::object_
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Module::MethodReleaseNotifier class
- Microsoft::WRL::Module::MethodReleaseNotifier::Invoke method
- Microsoft::WRL::Module::MethodReleaseNotifier::method_ data member
- Microsoft::WRL::Module::MethodReleaseNotifier::MethodReleaseNotifier, constructor
- Microsoft::WRL::Module::MethodReleaseNotifier::object_ data member
ms.assetid: 5c2902be-964b-488f-9f1c-adf504995cbc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 68f85794c8d70d642295f9125ac45311df29f16e
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49163513"
---
# <a name="modulemethodreleasenotifier-class"></a>Module::MethodReleaseNotifier 類別

發行目前的模組中的最後一個物件時，會叫用事件處理常式。 物件和其指標-至-a-方法成員所指定的事件處理常式。

## <a name="syntax"></a>語法

```cpp
template<typename T>
class MethodReleaseNotifier : public ReleaseNotifier;
```

### <a name="parameters"></a>參數

*T*<br/>
成員函式是事件處理常式的物件類型。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

名稱                                                                                                 | 描述
---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------
[Module::MethodReleaseNotifier::MethodReleaseNotifier](#methodreleasenotifier-methodreleasenotifier) | 初始化 `Module::MethodReleaseNotifier` 類別的新執行個體。

### <a name="public-methods"></a>公用方法

名稱                                                                   | 描述
---------------------------------------------------------------------- | -------------------------------------------------------------------------------------------
[Module:: methodreleasenotifier:: 叫用](#methodreleasenotifier-invoke) | 呼叫目前相關聯的事件處理常式`Module::MethodReleaseNotifier`物件。

### <a name="protected-data-members"></a>受保護的資料成員

名稱                                                                    | 描述
----------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------
[Module::MethodReleaseNotifier::method_](#methodreleasenotifier-method) | 目前的事件處理常式會保留指標`Module::MethodReleaseNotifier`物件。
[Module::MethodReleaseNotifier::object_](#methodreleasenotifier-object) | 成員函式是目前的事件處理常式的物件會保留指標`Module::MethodReleaseNotifier`物件。

## <a name="inheritance-hierarchy"></a>繼承階層

`ReleaseNotifier`

`MethodReleaseNotifier`

## <a name="requirements"></a>需求

**標頭：** module.h

**命名空間：** Microsoft::WRL

## <a name="methodreleasenotifier-invoke"></a>Module:: methodreleasenotifier:: 叫用

呼叫目前相關聯的事件處理常式`Module::MethodReleaseNotifier`物件。

```cpp
void Invoke();
```

## <a name="methodreleasenotifier-method"></a>Module::MethodReleaseNotifier::method_

目前的事件處理常式會保留指標`Module::MethodReleaseNotifier`物件。

```cpp
void (T::* method_)();
```

## <a name="methodreleasenotifier-methodreleasenotifier"></a>Module::MethodReleaseNotifier::MethodReleaseNotifier

初始化 `Module::MethodReleaseNotifier` 類別的新執行個體。

```cpp
MethodReleaseNotifier(
   _In_ T* object,
   _In_ void (T::* method)(),
   bool release) throw() :
            ReleaseNotifier(release), object_(object),
            method_(method);
```

### <a name="parameters"></a>參數

*object*<br/>
物件，其成員函式為事件處理常式。

*方法*<br/>
成員函式的參數*物件*也就是事件處理常式。

*release*<br/>
指定 **，則為 true**若要啟用呼叫基礎[模組:: ReleaseNotifier::Release()](../windows/module-releasenotifier-class.md#releasenotifier-release)方法; 否則指定**false**。

## <a name="methodreleasenotifier-object"></a>Module::MethodReleaseNotifier::object_

成員函式是目前的事件處理常式的物件會保留指標`Module::MethodReleaseNotifier`物件。

```cpp
T* object_;
```
