---
title: 'Module:: releasenotifier 類別 |Microsoft Docs'
ms.custom: ''
ms.date: 09/17/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::ReleaseNotifier
- module/Microsoft::WRL::Module::ReleaseNotifier::~ReleaseNotifier
- module/Microsoft::WRL::Module::ReleaseNotifier::Invoke
- module/Microsoft::WRL::Module::ReleaseNotifier::Release
- module/Microsoft::WRL::Module::ReleaseNotifier::ReleaseNotifier
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Module::ReleaseNotifier class
- Microsoft::WRL::Module::ReleaseNotifier::~ReleaseNotifier, destructor
- Microsoft::WRL::Module::ReleaseNotifier::Invoke method
- Microsoft::WRL::Module::ReleaseNotifier::Release method
- Microsoft::WRL::Module::ReleaseNotifier::ReleaseNotifier, constructor
ms.assetid: 17249cd1-4d88-42e3-8146-da9e942d12bd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5c9af03549eec7b62cc34aec2840764c54d2a21e
ms.sourcegitcommit: 338e1ddc2f3869d92ba4b73599d35374cf1d5b69
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2018
ms.locfileid: "46494357"
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
[Module:: releasenotifier:: ~ ReleaseNotifier](#releasenotifier-tilde-releasenotifier) | 取消初始化目前的執行個體`Module::ReleaseNotifier`類別。
[Module::ReleaseNotifier::ReleaseNotifier](#releasenotifier-releasenotifier)        | 初始化 `Module::ReleaseNotifier` 類別的新執行個體。

### <a name="public-methods"></a>公用方法

名稱                                                         | 描述
------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------
[Module:: releasenotifier:: 叫用](#releasenotifier-invoke)   | 實作時，請在發行模組中的最後一個物件時呼叫的事件處理常式。
[Module::ReleaseNotifier::Release](#releasenotifier-release) | 刪除目前`Module::ReleaseNotifier`物件如果物件以參數的建構`true`。

## <a name="inheritance-hierarchy"></a>繼承階層

`ReleaseNotifier`

## <a name="requirements"></a>需求

**標頭：** module.h

**命名空間：** Microsoft::WRL

## <a name="releasenotifier-tilde-releasenotifier"></a>Module:: releasenotifier:: ~ ReleaseNotifier

取消初始化目前的執行個體`Module::ReleaseNotifier`類別。

```cpp
WRL_NOTHROW virtual ~ReleaseNotifier();
```

## <a name="releasenotifier-invoke"></a>Module:: releasenotifier:: 叫用

實作時，請在發行模組中的最後一個物件時呼叫的事件處理常式。

```cpp
virtual void Invoke() = 0;
```

## <a name="releasenotifier-release"></a>Module::ReleaseNotifier::Release

刪除目前`Module::ReleaseNotifier`物件如果物件以參數的建構`true`。

```cpp
void Release() throw();
```

## <a name="releasenotifier-releasenotifier"></a>Module::ReleaseNotifier::ReleaseNotifier

初始化 `Module::ReleaseNotifier` 類別的新執行個體。

```cpp
ReleaseNotifier(bool release) throw();
```

### <a name="parameters"></a>參數

*release*  
`true` 若要刪除這個執行個體時`Release`方法稱為;`false`未刪除此執行個體。
