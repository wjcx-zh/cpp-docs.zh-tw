---
title: 號誌類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Semaphore
dev_langs:
- C++
helpviewer_keywords:
- Semaphore class
ms.assetid: ded53526-17b4-4381-9c60-ea5e77363db6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bb0b3d5dff91bcb1fb1688c7b1a9314fe7ebf00c
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42598411"
---
# <a name="semaphore-class"></a>Semaphore 類別

表示控制項可以支援有限的數目的使用者共用的資源的同步處理物件。

## <a name="syntax"></a>語法

```cpp
class Semaphore : public HandleT<HandleTraits::SemaphoreTraits>
```

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|`SyncLock`|支援同步鎖定的類型同義。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[Semaphore::Semaphore 建構函式](../windows/semaphore-semaphore-constructor.md)|初始化的新執行個體**號誌**類別。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[InvokeHelper::Invoke 方法](../windows/invokehelper-invoke-method.md)|會呼叫其簽章包含指定的引數的事件處理常式。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[Semaphore::Lock 方法](../windows/semaphore-lock-method.md)|等待目前的物件或指定的控制代碼相關聯的物件處於收到信號的狀態，或經過指定的逾時間隔。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[Semaphore::operator= 運算子](../windows/semaphore-operator-assign-operator.md)|將指定的控制代碼，從**號誌**物件與目前**號誌**物件。|

## <a name="inheritance-hierarchy"></a>繼承階層

`Semaphore`

## <a name="requirements"></a>需求

**標頭：** corewrappers.h

**命名空間：** Microsoft::WRL::Wrappers

## <a name="see-also"></a>另請參閱

[Microsoft::WRL::Wrappers 命名空間](../windows/microsoft-wrl-wrappers-namespace.md)