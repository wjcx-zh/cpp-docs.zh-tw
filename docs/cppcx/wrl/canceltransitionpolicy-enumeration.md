---
title: CancelTransitionPolicy 列舉
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::CancelTransitionPolicy::TransitionFromCanceled
- module/Microsoft::WRL::CancelTransitionPolicy::RemainCanceled
- module/Microsoft::WRL::CancelTransitionPolicy
helpviewer_keywords:
- CancelTransitionPolicy Enumeration
ms.assetid: 5de49f7d-e5e3-43e9-bbca-666caf226cef
ms.openlocfilehash: e820b3fffb4a00e95a1210a5c0beb3229c6d1657
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214119"
---
# <a name="canceltransitionpolicy-enumeration"></a>CancelTransitionPolicy 列舉

指出非同步作業如何嘗試轉換成已完成或錯誤的終止狀態，其行為應該與用戶端要求的已取消狀態有關。

## <a name="syntax"></a>語法

```cpp
enum CancelTransitionPolicy;
```

## <a name="members"></a>成員

### <a name="values"></a>值

|名稱|描述|
|----------|-----------------|
|`RemainCanceled`|如果非同步作業目前是以用戶端要求的已取消狀態，這表示它會維持在已取消狀態，而不是轉換成終端機已完成或錯誤狀態。|
|`TransitionFromCanceled`|如果非同步作業目前處於用戶端要求的已取消狀態，這表示狀態應從該已取消狀態轉換為已完成的終止狀態，或由使用此旗標的呼叫所判斷的錯誤。|

## <a name="requirements"></a>需求

**標頭：** async。h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[Microsoft::WRL 命名空間](microsoft-wrl-namespace.md)
