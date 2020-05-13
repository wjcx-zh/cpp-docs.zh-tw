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
ms.openlocfilehash: f314d09c443d0d284e3a821b5c879bfb74baf812
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371280"
---
# <a name="modulereleasenotifier-class"></a>Module::ReleaseNotifier 類別

釋放模組中的最後一個物件時調用事件處理程式。

## <a name="syntax"></a>語法

```cpp
class ReleaseNotifier;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

名稱                                                                                | 描述
----------------------------------------------------------------------------------- | --------------------------------------------------------------------------
[模組::釋放器::*釋放器](#releasenotifier-tilde-releasenotifier) | 取消初始化類的`Module::ReleaseNotifier`當前實例。
[模組::釋放程式::釋放器](#releasenotifier-releasenotifier)        | 將 `Module::ReleaseNotifier` 類別的新執行個體初始化。

### <a name="public-methods"></a>公用方法

名稱                                                         | 描述
------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------
[模組::釋放程式::調用](#releasenotifier-invoke)   | 實現後,在釋放模組中的最後一個物件時調用事件處理程式。
[Module::ReleaseNotifier::Release](#releasenotifier-release) | 如果物件建構的`Module::ReleaseNotifier`參數為**true**,則刪除當前物件。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`ReleaseNotifier`

## <a name="requirements"></a>需求

**標題:** 模組.h

**命名空間：** Microsoft::WRL

## <a name="modulereleasenotifierreleasenotifier"></a><a name="releasenotifier-tilde-releasenotifier"></a>模組::釋放器::*釋放器

取消初始化類的`Module::ReleaseNotifier`當前實例。

```cpp
WRL_NOTHROW virtual ~ReleaseNotifier();
```

## <a name="modulereleasenotifierinvoke"></a><a name="releasenotifier-invoke"></a>模組::釋放程式::調用

實現後,在釋放模組中的最後一個物件時調用事件處理程式。

```cpp
virtual void Invoke() = 0;
```

## <a name="modulereleasenotifierrelease"></a><a name="releasenotifier-release"></a>模組::發佈程式::發佈

如果物件建構的`Module::ReleaseNotifier`參數為**true**,則刪除當前物件。

```cpp
void Release() throw();
```

## <a name="modulereleasenotifierreleasenotifier"></a><a name="releasenotifier-releasenotifier"></a>模組::釋放程式::釋放器

將 `Module::ReleaseNotifier` 類別的新執行個體初始化。

```cpp
ReleaseNotifier(bool release) throw();
```

### <a name="parameters"></a>參數

*釋放*<br/>
`true`在調用`Release`方法時刪除此實例;`false`不刪除此實例。
