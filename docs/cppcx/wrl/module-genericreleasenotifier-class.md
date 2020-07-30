---
title: Module::GenericReleaseNotifier 類別
ms.date: 09/17/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::GenericReleaseNotifier
- module/Microsoft::WRL::Module::GenericReleaseNotifier::callback_
- module/Microsoft::WRL::Module::GenericReleaseNotifier::GenericReleaseNotifier
- module/Microsoft::WRL::Module::GenericReleaseNotifier::Invoke
helpviewer_keywords:
- Microsoft::WRL::Module::GenericReleaseNotifier class
- Microsoft::WRL::Module::GenericReleaseNotifier::callback_ data member
- Microsoft::WRL::Module::GenericReleaseNotifier::GenericReleaseNotifier, constructor
- Microsoft::WRL::Module::GenericReleaseNotifier::Invoke method
ms.assetid: 244a8fbe-f89b-409b-aa65-db3e37f9b125
ms.openlocfilehash: 7437f4e1f6874d4c708780a146e1761ac6d98305
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225731"
---
# <a name="modulegenericreleasenotifier-class"></a>Module::GenericReleaseNotifier 類別

當目前模組中的最後一個物件釋放時，叫用事件處理常式。 事件處理常式是由 lambda、仿函數或指標對函式所指定。

## <a name="syntax"></a>語法

```cpp
template<typename T>
class GenericReleaseNotifier : public ReleaseNotifier;
```

### <a name="parameters"></a>參數

*T*<br/>
包含事件處理常式位置之資料成員的類型。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

名稱                                                                                                     | 說明
-------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------
[Module：： GenericReleaseNotifier：： GenericReleaseNotifier](#genericreleasenotifier-genericreleasenotifier) | 初始化 `Module::GenericReleaseNotifier` 類別的新執行個體。

### <a name="public-methods"></a>公用方法

名稱                                                                     | 說明
------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------
[Module：： GenericReleaseNotifier：： Invoke](#genericreleasenotifier-invoke) | 呼叫與目前物件相關聯的事件處理常式 `Module::GenericReleaseNotifier` 。

### <a name="protected-data-members"></a>受保護的資料成員

名稱                                                                          | 說明
----------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------
[Module：： GenericReleaseNotifier：： callback_](#genericreleasenotifier-callback) | 保存與目前物件相關聯的 lambda、仿函數或指標對函式事件處理常式 `Module::GenericReleaseNotifier` 。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`ReleaseNotifier`

`GenericReleaseNotifier`

## <a name="requirements"></a>需求

**標頭：** module. h

**命名空間：** Microsoft::WRL

## <a name="modulegenericreleasenotifiercallback_"></a><a name="genericreleasenotifier-callback"></a>Module：： GenericReleaseNotifier：： callback_

保存與目前物件相關聯的 lambda、仿函數或指標對函式事件處理常式 `Module::GenericReleaseNotifier` 。

```cpp
T callback_;
```

## <a name="modulegenericreleasenotifiergenericreleasenotifier"></a><a name="genericreleasenotifier-genericreleasenotifier"></a>Module：： GenericReleaseNotifier：： GenericReleaseNotifier

初始化 `Module::GenericReleaseNotifier` 類別的新執行個體。

```cpp
GenericReleaseNotifier(
   T callback,
   bool release
) throw() : ReleaseNotifier(release), callback_(callback);
```

### <a name="parameters"></a>參數

*回撥*<br/>
可以使用括弧函式運算子（）叫用的 lambda、仿函數或指標對函式事件處理常式 `()` 。

*版本*<br/>
指定 **`true`** 以啟用呼叫基礎[Module：： ReleaseNotifier：： Release （）](module-releasenotifier-class.md#releasenotifier-release)方法，否則請指定 **`false`** 。

## <a name="modulegenericreleasenotifierinvoke"></a><a name="genericreleasenotifier-invoke"></a>Module：： GenericReleaseNotifier：： Invoke

呼叫與目前物件相關聯的事件處理常式 `Module::GenericReleaseNotifier` 。

```cpp
void Invoke();
```
