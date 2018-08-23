---
title: 'Classfactory:: Release 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ClassFactory::Release
dev_langs:
- C++
helpviewer_keywords:
- Release method
ms.assetid: 49da2002-f9d6-4d7f-8a65-48c20b1bf99f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e1af266d769b950324a1a4a9b8023b6b8e164038
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42606031"
---
# <a name="classfactoryrelease-method"></a>ClassFactory::Release 方法

遞減參考計數目前**ClassFactory**物件。

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

[ClassFactory 類別](../windows/classfactory-class.md)