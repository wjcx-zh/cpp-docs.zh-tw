---
title: 'Asyncbase:: Cancel 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::Cancel
dev_langs:
- C++
helpviewer_keywords:
- Cancel method
ms.assetid: 8bfebc63-3848-4629-bc89-aa538ed7e7ad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: dbf216d672dd22e453f8c213f7a9f34f08a47273
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42593133"
---
# <a name="asyncbasecancel-method"></a>AsyncBase::Cancel 方法

取消非同步作業。

## <a name="syntax"></a>語法

```cpp
STDMETHOD(
   Cancel
)(void);
```

## <a name="return-value"></a>傳回值

根據預設，一律會傳回 S_OK。

## <a name="remarks"></a>備註

**Cancel**的預設實作`IAsyncInfo::Cancel`，並不執行任何實際工作。 若要實際取消非同步作業，請覆寫`OnCancel()`純虛擬方法。

## <a name="requirements"></a>需求

**標頭：** async.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[AsyncBase 類別](../windows/asyncbase-class.md)