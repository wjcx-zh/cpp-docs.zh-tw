---
title: InvokeHelper 結構 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::InvokeHelper
dev_langs:
- C++
helpviewer_keywords:
- InvokeHelper structure
ms.assetid: 555ad2bc-4dd6-4e65-a2e2-1242c395f0e5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0586b5073e8d97c882f33bb118d62b0c1bb04c07
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42611547"
---
# <a name="invokehelper-structure"></a>InvokeHelper 結構

支援 WRL 結構，而且不是直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
template<
   typename TDelegateInterface,
   typename TCallback,
   unsigned int argCount
>
struct InvokeHelper;
template<
   typename TDelegateInterface,
   typename TCallback
>
struct InvokeHelper<TDelegateInterface, TCallback, 0> : public Microsoft::WRL::RuntimeClass<RuntimeClassFlags<Delegate>, TDelegateInterface>;
template<
   typename TDelegateInterface,
   typename TCallback
>
struct InvokeHelper<TDelegateInterface, TCallback, 1> : public Microsoft::WRL::RuntimeClass<RuntimeClassFlags<Delegate>, TDelegateInterface>;
template<
   typename TDelegateInterface,
   typename TCallback
>
struct InvokeHelper<TDelegateInterface, TCallback, 2> : public Microsoft::WRL::RuntimeClass<RuntimeClassFlags<Delegate>, TDelegateInterface>;
template<
   typename TDelegateInterface,
   typename TCallback
>
struct InvokeHelper<TDelegateInterface, TCallback, 3> : public Microsoft::WRL::RuntimeClass<RuntimeClassFlags<Delegate>, TDelegateInterface>;
template<
   typename TDelegateInterface,
   typename TCallback
>
struct InvokeHelper<TDelegateInterface, TCallback, 4> : Microsoft::WRL::RuntimeClass<RuntimeClassFlags<Delegate>, TDelegateInterface>;
template<
   typename TDelegateInterface,
   typename TCallback
>
struct InvokeHelper<TDelegateInterface, TCallback, 5> : Microsoft::WRL::RuntimeClass<RuntimeClassFlags<Delegate>, TDelegateInterface>;
template<
   typename TDelegateInterface,
   typename TCallback
>
struct InvokeHelper<TDelegateInterface, TCallback, 6> : Microsoft::WRL::RuntimeClass<RuntimeClassFlags<Delegate>, TDelegateInterface>;
template<
   typename TDelegateInterface,
   typename TCallback
>
struct InvokeHelper<TDelegateInterface, TCallback, 7> : Microsoft::WRL::RuntimeClass<RuntimeClassFlags<Delegate>, TDelegateInterface>;
template<
   typename TDelegateInterface,
   typename TCallback
>
struct InvokeHelper<TDelegateInterface, TCallback, 8> : Microsoft::WRL::RuntimeClass<RuntimeClassFlags<Delegate>, TDelegateInterface>;
template<
   typename TDelegateInterface,
   typename TCallback
>
struct InvokeHelper<TDelegateInterface, TCallback, 9> : Microsoft::WRL::RuntimeClass<RuntimeClassFlags<Delegate>, TDelegateInterface>;
```

### <a name="parameters"></a>參數

*TDelegateInterface*  
*TCallback*  
事件處理常式函式的類型。

*argCount*  
中的引數的數目**InvokeHelper**特製化。

## <a name="remarks"></a>備註

提供實作`Invoke()`方法根據指定的數目和類型的引數。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|`Traits`|類別定義的每個事件處理常式的引數類型同義。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[InvokeHelper::InvokeHelper 建構函式](../windows/invokehelper-invokehelper-constructor.md)|初始化的新執行個體**InvokeHelper**類別。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[InvokeHelper::Invoke 方法](../windows/invokehelper-invoke-method.md)|會呼叫其簽章包含指定的引數的事件處理常式。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[InvokeHelper::callback_ 資料成員](../windows/invokehelper-callback-data-member.md)|表示事件發生時要呼叫的事件處理常式。|

## <a name="inheritance-hierarchy"></a>繼承階層

`InvokeHelper`

## <a name="requirements"></a>需求

**標頭：** event.h

**命名空間：** Microsoft::WRL::Details

## <a name="see-also"></a>另請參閱

[Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)