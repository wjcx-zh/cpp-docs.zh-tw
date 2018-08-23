---
title: 'Activationfactory:: Release 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ActivationFactory::Release
dev_langs:
- C++
helpviewer_keywords:
- Release method
ms.assetid: 5bc25ff0-ee3c-4a2d-a9b6-2d8f158033ad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2d21210455a19a45b5dfde3b5bb31920f33cb777
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42605290"
---
# <a name="activationfactoryrelease-method"></a>ActivationFactory::Release 方法

遞減參考計數的目前**ActivationFactory**物件。

## <a name="syntax"></a>語法

```cpp
STDMETHOD_(
   ULONG,
   Release
)();
```

## <a name="return-value"></a>傳回值

若成功，則為 S_OK，否則會是 HRESULT 指出失敗。

## <a name="requirements"></a>需求

**標頭：** module.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[ActivationFactory 類別](../windows/activationfactory-class.md)