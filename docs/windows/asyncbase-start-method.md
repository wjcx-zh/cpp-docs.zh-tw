---
title: 'Asyncbase:: Start 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::Start
dev_langs:
- C++
helpviewer_keywords:
- Start method
ms.assetid: 67405c9d-0d1a-4c1e-8ea4-6ba01c1f90d9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d81a3f29e99f49b03eb76f44af60c42d433e0bdc
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42611228"
---
# <a name="asyncbasestart-method"></a>AsyncBase::Start 方法

啟動非同步作業。

## <a name="syntax"></a>語法

```cpp
STDMETHOD(
   Start
)(void);
```

## <a name="return-value"></a>傳回值

S_OK 如果作業啟動或已啟動;否則，E_ILLEGAL_STATE_CHANGE。

## <a name="remarks"></a>備註

**Start （)** 的預設實作`IAsyncInfo::Start`，並不執行任何實際工作。 若要實際啟動非同步作業，覆寫`OnStart()`純虛擬方法。

## <a name="requirements"></a>需求

**標頭：** async.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[AsyncBase 類別](../windows/asyncbase-class.md)