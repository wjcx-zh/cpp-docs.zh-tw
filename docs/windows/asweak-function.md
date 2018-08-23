---
title: AsWeak 函式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::AsWeak
dev_langs:
- C++
helpviewer_keywords:
- AsWeak function
ms.assetid: a6f10cfc-c1d6-4761-adb9-1a119cc99913
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: dea10165e920c6b0bbd3856fc04e9ec9661e60c4
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42571330"
---
# <a name="asweak-function"></a>AsWeak 函式

擷取指定執行個體的弱式參考。

## <a name="syntax"></a>語法

```cpp
template<typename T>
HRESULT AsWeak(
   _In_ T* p,
   _Out_ WeakRef* pWeak
);
```

### <a name="parameters"></a>參數

*T*  
參數的類型指標*p*。

*p*  
型別的執行個體。

*pWeak*  
這項作業完成時，參數的弱式參考的指標*p*。

## <a name="return-value"></a>傳回值

S_ok 時，如果這項作業成功，否則，發生錯誤的 HRESULT，表示失敗的原因。

## <a name="requirements"></a>需求

**標頭：** client.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)