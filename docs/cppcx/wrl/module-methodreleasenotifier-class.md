---
title: Module::MethodReleaseNotifier 類別
ms.date: 09/17/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::MethodReleaseNotifier
- module/Microsoft::WRL::Module::MethodReleaseNotifier::Invoke
- module/Microsoft::WRL::Module::MethodReleaseNotifier::method_
- module/Microsoft::WRL::Module::MethodReleaseNotifier::MethodReleaseNotifier
- module/Microsoft::WRL::Module::MethodReleaseNotifier::object_
helpviewer_keywords:
- Microsoft::WRL::Module::MethodReleaseNotifier class
- Microsoft::WRL::Module::MethodReleaseNotifier::Invoke method
- Microsoft::WRL::Module::MethodReleaseNotifier::method_ data member
- Microsoft::WRL::Module::MethodReleaseNotifier::MethodReleaseNotifier, constructor
- Microsoft::WRL::Module::MethodReleaseNotifier::object_ data member
ms.assetid: 5c2902be-964b-488f-9f1c-adf504995cbc
ms.openlocfilehash: 5b0e5766fda878acb1fdc54a79ce162444eb06de
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225718"
---
# <a name="modulemethodreleasenotifier-class"></a>Module::MethodReleaseNotifier 類別

當目前模組中的最後一個物件釋放時，叫用事件處理常式。 事件處理常式是由物件和其指標對方法成員所指定。

## <a name="syntax"></a>語法

```cpp
template<typename T>
class MethodReleaseNotifier : public ReleaseNotifier;
```

### <a name="parameters"></a>參數

*T*<br/>
物件的類型，其成員函式為事件處理常式。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

名稱                                                                                                 | 說明
---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------
[Module：： MethodReleaseNotifier：： MethodReleaseNotifier](#methodreleasenotifier-methodreleasenotifier) | 初始化 `Module::MethodReleaseNotifier` 類別的新執行個體。

### <a name="public-methods"></a>公用方法

名稱                                                                   | 說明
---------------------------------------------------------------------- | -------------------------------------------------------------------------------------------
[Module：： MethodReleaseNotifier：： Invoke](#methodreleasenotifier-invoke) | 呼叫與目前物件相關聯的事件處理常式 `Module::MethodReleaseNotifier` 。

### <a name="protected-data-members"></a>受保護的資料成員

名稱                                                                    | 說明
----------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------
[Module：： MethodReleaseNotifier：： method_](#methodreleasenotifier-method) | 保留目前物件之事件處理常式的指標 `Module::MethodReleaseNotifier` 。
[Module：： MethodReleaseNotifier：： object_](#methodreleasenotifier-object) | 保存物件的指標，其成員函式是目前物件的事件處理常式 `Module::MethodReleaseNotifier` 。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`ReleaseNotifier`

`MethodReleaseNotifier`

## <a name="requirements"></a>需求

**標頭：** module. h

**命名空間：** Microsoft::WRL

## <a name="modulemethodreleasenotifierinvoke"></a><a name="methodreleasenotifier-invoke"></a>Module：： MethodReleaseNotifier：： Invoke

呼叫與目前物件相關聯的事件處理常式 `Module::MethodReleaseNotifier` 。

```cpp
void Invoke();
```

## <a name="modulemethodreleasenotifiermethod_"></a><a name="methodreleasenotifier-method"></a>Module：： MethodReleaseNotifier：： method_

保留目前物件之事件處理常式的指標 `Module::MethodReleaseNotifier` 。

```cpp
void (T::* method_)();
```

## <a name="modulemethodreleasenotifiermethodreleasenotifier"></a><a name="methodreleasenotifier-methodreleasenotifier"></a>Module：： MethodReleaseNotifier：： MethodReleaseNotifier

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
其成員函式為事件處理常式的物件。

*方法*<br/>
參數*物件*的成員函式，此為事件處理常式。

*版本*<br/>
指定 **`true`** 以啟用呼叫基礎[Module：： ReleaseNotifier：： Release （）](module-releasenotifier-class.md#releasenotifier-release)方法，否則請指定 **`false`** 。

## <a name="modulemethodreleasenotifierobject_"></a><a name="methodreleasenotifier-object"></a>Module：： MethodReleaseNotifier：： object_

保存物件的指標，其成員函式是目前物件的事件處理常式 `Module::MethodReleaseNotifier` 。

```cpp
T* object_;
```
