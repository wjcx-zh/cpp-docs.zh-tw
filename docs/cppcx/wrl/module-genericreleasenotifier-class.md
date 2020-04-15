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
ms.openlocfilehash: e3cc8e33d596fb1d3ecc4a94fee7971a50ffe596
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371299"
---
# <a name="modulegenericreleasenotifier-class"></a>Module::GenericReleaseNotifier 類別

釋放當前模組中的最後一個物件時調用事件處理程式。 事件處理程式由 lambda、functor 或指標到函數指定。

## <a name="syntax"></a>語法

```cpp
template<typename T>
class GenericReleaseNotifier : public ReleaseNotifier;
```

### <a name="parameters"></a>參數

*T*<br/>
包含事件處理程式位置的數據成員的類型。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

名稱                                                                                                     | 描述
-------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------
[模組::通用釋放程式::通用釋放程式](#genericreleasenotifier-genericreleasenotifier) | 將 `Module::GenericReleaseNotifier` 類別的新執行個體初始化。

### <a name="public-methods"></a>公用方法

名稱                                                                     | 描述
------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------
[模組::通用釋放程式::呼叫](#genericreleasenotifier-invoke) | 調用與當前`Module::GenericReleaseNotifier`物件關聯的事件處理程式。

### <a name="protected-data-members"></a>受保護的資料成員

名稱                                                                          | 描述
----------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------
[模組::通用釋放程式::callback_](#genericreleasenotifier-callback) | 保存與當前`Module::GenericReleaseNotifier`物件關聯的 lambda、functor 或指向函數的指標事件處理程式。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`ReleaseNotifier`

`GenericReleaseNotifier`

## <a name="requirements"></a>需求

**標題:** 模組.h

**命名空間：** Microsoft::WRL

## <a name="modulegenericreleasenotifiercallback_"></a><a name="genericreleasenotifier-callback"></a>模組::通用釋放程式::callback_

保存與當前`Module::GenericReleaseNotifier`物件關聯的 lambda、functor 或指向函數的指標事件處理程式。

```cpp
T callback_;
```

## <a name="modulegenericreleasenotifiergenericreleasenotifier"></a><a name="genericreleasenotifier-genericreleasenotifier"></a>模組::通用釋放程式::通用釋放程式

將 `Module::GenericReleaseNotifier` 類別的新執行個體初始化。

```cpp
GenericReleaseNotifier(
   T callback,
   bool release
) throw() : ReleaseNotifier(release), callback_(callback);
```

### <a name="parameters"></a>參數

*回撥*<br/>
可以使用括弧函數運算符 ()`()`呼叫的 lambda、functor 或指標到函數事件處理程式。

*釋放*<br/>
指定`true`以啟用調用基礎[模組::釋放說明器:::釋放()](module-releasenotifier-class.md#releasenotifier-release)方法;否則,指定`false`。

## <a name="modulegenericreleasenotifierinvoke"></a><a name="genericreleasenotifier-invoke"></a>模組::通用釋放程式::呼叫

調用與當前`Module::GenericReleaseNotifier`物件關聯的事件處理程式。

```cpp
void Invoke();
```
