---
title: 'Asyncbase:: Checkvalidstatefordelegatecall 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::CheckValidStateForDelegateCall
dev_langs:
- C++
helpviewer_keywords:
- CheckValidStateForDelegateCall method
ms.assetid: d997ebe7-2378-4e74-a379-f0f85e6922f0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cd3629fcaf8507abd2baf6cded3c6a63bc6fd64f
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42611496"
---
# <a name="asyncbasecheckvalidstatefordelegatecall-method"></a>AsyncBase::CheckValidStateForDelegateCall 方法

測試是否可以修改委派屬性，在目前的非同步狀態。

## <a name="syntax"></a>語法

```cpp
inline HRESULT CheckValidStateForDelegateCall();
```

## <a name="return-value"></a>傳回值

如果可以修改委派屬性，為 S_OK否則，E_ILLEGAL_METHOD_CALL。

## <a name="requirements"></a>需求

**標頭：** async.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[AsyncBase 類別](../windows/asyncbase-class.md)