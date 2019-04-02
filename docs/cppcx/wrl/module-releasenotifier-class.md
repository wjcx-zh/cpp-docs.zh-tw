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
ms.openlocfilehash: 5fc1b8965bf8bf2f86dd30f2195fa825f85f6d7e
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58783973"
---
# <a name="modulereleasenotifier-class"></a>Module::ReleaseNotifier 類別

發行模組中的最後一個物件時，會叫用事件處理常式。

## <a name="syntax"></a>語法

```cpp
class ReleaseNotifier;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

名稱                                                                                | 描述
----------------------------------------------------------------------------------- | --------------------------------------------------------------------------
[Module::ReleaseNotifier::~ReleaseNotifier](#releasenotifier-tilde-releasenotifier) | 取消初始化目前的執行個體`Module::ReleaseNotifier`類別。
[Module::ReleaseNotifier::ReleaseNotifier](#releasenotifier-releasenotifier)        | 初始化 `Module::ReleaseNotifier` 類別的新執行個體。

### <a name="public-methods"></a>公用方法

名稱                                                         | 描述
------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------
[Module::ReleaseNotifier::Invoke](#releasenotifier-invoke)   | 實作時，請在發行模組中的最後一個物件時呼叫的事件處理常式。
[Module::ReleaseNotifier::Release](#releasenotifier-release) | 刪除目前`Module::ReleaseNotifier`物件如果物件建構搭配參數 **，則為 true**。

## <a name="inheritance-hierarchy"></a>繼承階層

`ReleaseNotifier`

## <a name="requirements"></a>需求

**標頭：** module.h

**命名空間：** Microsoft:: wrl

## <a name="releasenotifier-tilde-releasenotifier"></a>Module:: releasenotifier:: ~ ReleaseNotifier

取消初始化目前的執行個體`Module::ReleaseNotifier`類別。

```cpp
WRL_NOTHROW virtual ~ReleaseNotifier();
```

## <a name="releasenotifier-invoke"></a>Module::ReleaseNotifier::Invoke

實作時，請在發行模組中的最後一個物件時呼叫的事件處理常式。

```cpp
virtual void Invoke() = 0;
```

## <a name="releasenotifier-release"></a>Module::ReleaseNotifier::Release

刪除目前`Module::ReleaseNotifier`物件如果物件建構搭配參數 **，則為 true**。

```cpp
void Release() throw();
```

## <a name="releasenotifier-releasenotifier"></a>Module::ReleaseNotifier::ReleaseNotifier

初始化 `Module::ReleaseNotifier` 類別的新執行個體。

```cpp
ReleaseNotifier(bool release) throw();
```

### <a name="parameters"></a>參數

*release*<br/>
`true` 若要刪除這個執行個體時`Release`方法稱為;`false`未刪除此執行個體。
