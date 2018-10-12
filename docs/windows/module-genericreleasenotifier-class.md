---
title: 'Module:: genericreleasenotifier 類別 |Microsoft Docs'
ms.custom: ''
ms.date: 09/17/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::GenericReleaseNotifier
- module/Microsoft::WRL::Module::GenericReleaseNotifier::callback_
- module/Microsoft::WRL::Module::GenericReleaseNotifier::GenericReleaseNotifier
- module/Microsoft::WRL::Module::GenericReleaseNotifier::Invoke
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Module::GenericReleaseNotifier class
- Microsoft::WRL::Module::GenericReleaseNotifier::callback_ data member
- Microsoft::WRL::Module::GenericReleaseNotifier::GenericReleaseNotifier, constructor
- Microsoft::WRL::Module::GenericReleaseNotifier::Invoke method
ms.assetid: 244a8fbe-f89b-409b-aa65-db3e37f9b125
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ad7081e22762409682250da0330575885378e8ab
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49161875"
---
# <a name="modulegenericreleasenotifier-class"></a>Module::GenericReleaseNotifier 類別

發行目前的模組中的最後一個物件時，會叫用事件處理常式。 Lambda、 函式或函式指標上所指定的事件處理常式。

## <a name="syntax"></a>語法

```cpp
template<typename T>
class GenericReleaseNotifier : public ReleaseNotifier;
```

### <a name="parameters"></a>參數

*T*<br/>
包含事件處理常式的位置資料成員的型別。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

名稱                                                                                                     | 描述
-------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------
[Module::GenericReleaseNotifier::GenericReleaseNotifier](#genericreleasenotifier-genericreleasenotifier) | 初始化 `Module::GenericReleaseNotifier` 類別的新執行個體。

### <a name="public-methods"></a>公用方法

名稱                                                                     | 描述
------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------
[Module:: genericreleasenotifier:: 叫用](#genericreleasenotifier-invoke) | 呼叫目前相關聯的事件處理常式`Module::GenericReleaseNotifier`物件。

### <a name="protected-data-members"></a>受保護的資料成員

名稱                                                                          | 描述
----------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------
[Module::GenericReleaseNotifier::callback_](#genericreleasenotifier-callback) | 保存 lambda、 函式或目前相關聯的函式指標事件處理常式`Module::GenericReleaseNotifier`物件。

## <a name="inheritance-hierarchy"></a>繼承階層

`ReleaseNotifier`

`GenericReleaseNotifier`

## <a name="requirements"></a>需求

**標頭：** module.h

**命名空間：** Microsoft::WRL

## <a name="genericreleasenotifier-callback"></a>Module::GenericReleaseNotifier::callback_

保存 lambda、 函式或目前相關聯的函式指標事件處理常式`Module::GenericReleaseNotifier`物件。

```cpp
T callback_;
```

## <a name="genericreleasenotifier-genericreleasenotifier"></a>Module::GenericReleaseNotifier::GenericReleaseNotifier

初始化 `Module::GenericReleaseNotifier` 類別的新執行個體。

```cpp
GenericReleaseNotifier(
   T callback,
   bool release
) throw() : ReleaseNotifier(release), callback_(callback);
```

### <a name="parameters"></a>參數

*回呼*<br/>
Lambda、 函式或可以使用括號函式運算子叫用的函式指標事件處理常式 (`()`)。

*release*<br/>
指定 **，則為 true**若要啟用呼叫基礎[模組:: ReleaseNotifier::Release()](../windows/module-releasenotifier-release.md)方法; 否則指定**false**。

## <a name="genericreleasenotifier-invoke"></a>Module:: genericreleasenotifier:: 叫用

呼叫目前相關聯的事件處理常式`Module::GenericReleaseNotifier`物件。

```cpp
void Invoke();
```
