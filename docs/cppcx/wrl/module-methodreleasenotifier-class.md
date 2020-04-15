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
ms.openlocfilehash: c641f150b6f029facffa62f7b47c7da32138735e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371293"
---
# <a name="modulemethodreleasenotifier-class"></a>Module::MethodReleaseNotifier 類別

釋放當前模組中的最後一個物件時調用事件處理程式。 事件處理程式由物件及其指向方法的成員指定。

## <a name="syntax"></a>語法

```cpp
template<typename T>
class MethodReleaseNotifier : public ReleaseNotifier;
```

### <a name="parameters"></a>參數

*T*<br/>
其成員函數為事件處理程序的物件的類型。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

名稱                                                                                                 | 描述
---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------
[模組::方法釋放程式::方法釋放器](#methodreleasenotifier-methodreleasenotifier) | 將 `Module::MethodReleaseNotifier` 類別的新執行個體初始化。

### <a name="public-methods"></a>公用方法

名稱                                                                   | 描述
---------------------------------------------------------------------- | -------------------------------------------------------------------------------------------
[模組::方法釋放程式::調用](#methodreleasenotifier-invoke) | 調用與當前`Module::MethodReleaseNotifier`物件關聯的事件處理程式。

### <a name="protected-data-members"></a>受保護的資料成員

名稱                                                                    | 描述
----------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------
[模組::方法釋放程式::method_](#methodreleasenotifier-method) | 為當前`Module::MethodReleaseNotifier`物件保留指向事件處理程序的指標。
[模組::方法釋放程式::object_](#methodreleasenotifier-object) | 保存指向其成員函數是當前`Module::MethodReleaseNotifier`物件的事件處理程序的物件的指標。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`ReleaseNotifier`

`MethodReleaseNotifier`

## <a name="requirements"></a>需求

**標題:** 模組.h

**命名空間：** Microsoft::WRL

## <a name="modulemethodreleasenotifierinvoke"></a><a name="methodreleasenotifier-invoke"></a>模組::方法釋放程式::調用

調用與當前`Module::MethodReleaseNotifier`物件關聯的事件處理程式。

```cpp
void Invoke();
```

## <a name="modulemethodreleasenotifiermethod_"></a><a name="methodreleasenotifier-method"></a>模組::方法釋放程式::method_

為當前`Module::MethodReleaseNotifier`物件保留指向事件處理程序的指標。

```cpp
void (T::* method_)();
```

## <a name="modulemethodreleasenotifiermethodreleasenotifier"></a><a name="methodreleasenotifier-methodreleasenotifier"></a>模組::方法釋放程式::方法釋放器

將 `Module::MethodReleaseNotifier` 類別的新執行個體初始化。

```cpp
MethodReleaseNotifier(
   _In_ T* object,
   _In_ void (T::* method)(),
   bool release) throw() :
            ReleaseNotifier(release), object_(object),
            method_(method);
```

### <a name="parameters"></a>參數

*物件*<br/>
其成員函數為事件處理程序的物件。

*方法*<br/>
參數*物件*的成員函數,即事件處理程式。

*釋放*<br/>
指定`true`以啟用調用基礎[模組::釋放說明器:::釋放()](module-releasenotifier-class.md#releasenotifier-release)方法;否則,指定`false`。

## <a name="modulemethodreleasenotifierobject_"></a><a name="methodreleasenotifier-object"></a>模組::方法釋放程式::object_

保存指向其成員函數是當前`Module::MethodReleaseNotifier`物件的事件處理程序的物件的指標。

```cpp
T* object_;
```
