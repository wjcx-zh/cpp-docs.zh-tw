---
title: Module::ReleaseNotifier 類別
ms.date: 09/17/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::ReleaseNotifier
- module/Microsoft::WRL::Module::ReleaseNotifier::~ReleaseNotifier
- module/Microsoft::WRL::Module::ReleaseNotifier::Invoke
- module/Microsoft::WRL::Module::ReleaseNotifier::Release
- module/Microsoft::WRL::Module::ReleaseNotifier::ReleaseNotifier
helpviewer_keywords:
- Microsoft::WRL::Module::ReleaseNotifier class
- Microsoft::WRL::Module::ReleaseNotifier::~ReleaseNotifier, destructor
- Microsoft::WRL::Module::ReleaseNotifier::Invoke method
- Microsoft::WRL::Module::ReleaseNotifier::Release method
- Microsoft::WRL::Module::ReleaseNotifier::ReleaseNotifier, constructor
ms.assetid: 17249cd1-4d88-42e3-8146-da9e942d12bd
ms.openlocfilehash: 25fbb23ee7ecb7e55377aed74effe8bfa43a1597
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218360"
---
# <a name="modulereleasenotifier-class"></a>Module::ReleaseNotifier 類別

釋放模組中的最後一個物件時，叫用事件處理常式。

## <a name="syntax"></a>語法

```cpp
class ReleaseNotifier;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

名稱                                                                                | 說明
----------------------------------------------------------------------------------- | --------------------------------------------------------------------------
[Module：： ReleaseNotifier：： ~ ReleaseNotifier](#releasenotifier-tilde-releasenotifier) | 將類別的目前實例 `Module::ReleaseNotifier` 。
[Module：： ReleaseNotifier：： ReleaseNotifier](#releasenotifier-releasenotifier)        | 初始化 `Module::ReleaseNotifier` 類別的新執行個體。

### <a name="public-methods"></a>公用方法

名稱                                                         | 說明
------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------
[Module：： ReleaseNotifier：： Invoke](#releasenotifier-invoke)   | 當執行時，會在釋放模組中的最後一個物件時呼叫事件處理常式。
[Module::ReleaseNotifier::Release](#releasenotifier-release) | 如果物件是使用的參數所建立，則刪除目前的 `Module::ReleaseNotifier` 物件 **`true`** 。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`ReleaseNotifier`

## <a name="requirements"></a>需求

**標頭：** module. h

**命名空間：** Microsoft::WRL

## <a name="modulereleasenotifierreleasenotifier"></a><a name="releasenotifier-tilde-releasenotifier"></a>Module：： ReleaseNotifier：： ~ ReleaseNotifier

將類別的目前實例 `Module::ReleaseNotifier` 。

```cpp
WRL_NOTHROW virtual ~ReleaseNotifier();
```

## <a name="modulereleasenotifierinvoke"></a><a name="releasenotifier-invoke"></a>Module：： ReleaseNotifier：： Invoke

當執行時，會在釋放模組中的最後一個物件時呼叫事件處理常式。

```cpp
virtual void Invoke() = 0;
```

## <a name="modulereleasenotifierrelease"></a><a name="releasenotifier-release"></a>Module：： ReleaseNotifier：： Release

如果物件是使用的參數所建立，則刪除目前的 `Module::ReleaseNotifier` 物件 **`true`** 。

```cpp
void Release() throw();
```

## <a name="modulereleasenotifierreleasenotifier"></a><a name="releasenotifier-releasenotifier"></a>Module：： ReleaseNotifier：： ReleaseNotifier

初始化 `Module::ReleaseNotifier` 類別的新執行個體。

```cpp
ReleaseNotifier(bool release) throw();
```

### <a name="parameters"></a>參數

*版本*<br/>
**`true`** 表示在呼叫方法時刪除這個實例， `Release` 則 **`false`** 不會刪除這個實例。
