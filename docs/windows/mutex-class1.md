---
title: Mutex 類別 1 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Mutex
dev_langs:
- C++
helpviewer_keywords:
- Mutex class
ms.assetid: 682a0963-721c-46a2-8871-000e9997505b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b20c270f7848a346d717357f474d89e37ea117a4
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42600024"
---
# <a name="mutex-class1"></a>Mutex 類別 1

表示以獨佔方式控制共用的資源的同步處理物件。

## <a name="syntax"></a>語法

```cpp
class Mutex : public HandleT<HandleTraits::MutexTraits>
```

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|`SyncLock`|支援同步鎖定的類型同義。|

### <a name="public-constructor"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[Mutex::Mutex 建構函式](../windows/mutex-mutex-constructor.md)|初始化的新執行個體**Mutex**類別。|

### <a name="public-members"></a>Public 成員

|名稱|描述|
|----------|-----------------|
|[Mutex::Lock 方法](../windows/mutex-lock-method.md)|等到目前的物件，或**Mutex**與指定的控制代碼、 mutex 或指定的逾時間隔經過的版本相關聯的物件。|

### <a name="public-operator"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[Mutex::operator= 運算子](../windows/mutex-operator-assign-operator.md)|指派 （移動） 指定**Mutex**物件與目前**Mutex**物件。|

## <a name="inheritance-hierarchy"></a>繼承階層

`Mutex`

## <a name="requirements"></a>需求

**標頭：** corewrappers.h

**命名空間：** Microsoft::WRL::Wrappers

## <a name="see-also"></a>另請參閱

[Microsoft::WRL::Wrappers 命名空間](../windows/microsoft-wrl-wrappers-namespace.md)