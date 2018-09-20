---
title: 'Invokehelper:: Invokehelper 建構函式 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::InvokeHelper::InvokeHelper
dev_langs:
- C++
helpviewer_keywords:
- InvokeHelper, constructor
ms.assetid: 0223c574-abc3-4fc0-99e6-38626ba79243
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 11f3e82f0834863c3cdfb476443a4dbd0bdf1f6f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46385075"
---
# <a name="invokehelperinvokehelper-constructor"></a>InvokeHelper::InvokeHelper 建構函式

支援 WRL 結構，而且不是直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
explicit InvokeHelper(
   TCallback callback
);
```

### <a name="parameters"></a>參數

*回呼*<br/>
事件處理常式。

## <a name="remarks"></a>備註

初始化的新執行個體**InvokeHelper**類別。

`TCallback`範本參數會指定事件處理常式的類型。

## <a name="requirements"></a>需求

**標頭：** event.h

**命名空間：** Microsoft::WRL::Details

## <a name="see-also"></a>另請參閱

[InvokeHelper 結構](../windows/invokehelper-structure.md)<br/>
[Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)