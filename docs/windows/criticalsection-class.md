---
title: CriticalSection 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection
dev_langs:
- C++
helpviewer_keywords:
- CriticalSection class
ms.assetid: f2e0a024-71a3-4f6b-99ea-d93a4a608ac4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cab1beeaa3ce54899d1a052e4972bd7e7f52bb57
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42592445"
---
# <a name="criticalsection-class"></a>CriticalSection 類別

表示重要區段物件。

## <a name="syntax"></a>語法

```cpp
class CriticalSection;
```

## <a name="members"></a>成員

### <a name="constructor"></a>建構函式

|名稱|描述|
|----------|-----------------|
|[CriticalSection::CriticalSection 建構函式](../windows/criticalsection-criticalsection-constructor.md)|初始化同步處理物件，類似於 mutex 物件，但可由單一的程序的執行緒。|
|[CriticalSection::~CriticalSection 解構函式](../windows/criticalsection-tilde-criticalsection-destructor.md)|取消初始化並終結目前**CriticalSection**物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CriticalSection::TryLock 方法](../windows/criticalsection-trylock-method.md)|嘗試進入重要區段，而不會封鎖。 如果呼叫成功，呼叫執行緒會取得重要區段的擁有權。|
|[CriticalSection::Lock 方法](../windows/criticalsection-lock-method.md)|等候指定的重要區段物件的擁有權。 此函數會傳回呼叫的執行緒授與擁有權時。|
|[CriticalSection::IsValid 方法](../windows/criticalsection-isvalid-method.md)|指出目前的重要區段是否有效。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CriticalSection::cs_ 資料成員](../windows/criticalsection-cs-data-member.md)|宣告重要區段的資料成員。|

## <a name="inheritance-hierarchy"></a>繼承階層

`CriticalSection`

## <a name="requirements"></a>需求

**標頭：** corewrappers.h

**命名空間：** Microsoft::WRL::Wrappers

## <a name="see-also"></a>另請參閱

[Microsoft::WRL::Wrappers 命名空間](../windows/microsoft-wrl-wrappers-namespace.md)