---
title: SRWLock 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::SRWLock
dev_langs:
- C++
helpviewer_keywords:
- SRWLock class
ms.assetid: 4fa250e3-5f29-4b06-ac24-61b6c04ade93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fb97a29796c287cfaadddc305f25807de5dcba2e
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42604232"
---
# <a name="srwlock-class"></a>SRWLock 類別

表示輕型讀取器/寫入器鎖定。

## <a name="syntax"></a>語法

```cpp
class SRWLock;
```

## <a name="remarks"></a>備註

輕型讀取器/寫入器鎖定用來同步存取物件或資源的執行緒上。 如需詳細資訊，請參閱 <<c0> [ 同步處理函式](/windows/desktop/Sync/synchronization-functions)。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|||
|-|-|
|`SyncLockExclusive`|同義字**SRWLock**取得獨佔模式中的物件。|
|`SyncLockShared`|同義字**SRWLock**取得以共用模式的物件。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[SRWLock::SRWLock 建構函式](../windows/srwlock-srwlock-constructor.md)|初始化的新執行個體**SRWLock**類別。|
|[SRWLock::~SRWLock 解構函式](../windows/srwlock-tilde-srwlock-destructor.md)|取消初始化的執行個體**SRWLock**類別。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[SRWLock::LockExclusive 方法](../windows/srwlock-lockexclusive-method.md)|取得**SRWLock**獨佔模式中的物件。|
|[SRWLock::LockShared 方法](../windows/srwlock-lockshared-method.md)|取得**SRWLock**以共用模式的物件。|
|[SRWLock::TryLockExclusive 方法](../windows/srwlock-trylockexclusive-method.md)|嘗試取得**SRWLock**物件獨佔模式使用目前或指定**SRWLock**物件。|
|[SRWLock::TryLockShared 方法](../windows/srwlock-trylockshared-method.md)|嘗試取得**SRWLock**物件中目前或指定的共用模式**SRWLock**物件。|

### <a name="protected-data-member"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[SRWLock::SRWLock_ 資料成員](../windows/srwlock-srwlock-data-member.md)|包含目前的基礎鎖定變數**SRWLock**物件。|

## <a name="inheritance-hierarchy"></a>繼承階層

`SRWLock`

## <a name="requirements"></a>需求

**標頭：** corewrappers.h

**命名空間：** Microsoft::WRL::Wrappers

## <a name="see-also"></a>另請參閱

[Microsoft::WRL::Wrappers 命名空間](../windows/microsoft-wrl-wrappers-namespace.md)