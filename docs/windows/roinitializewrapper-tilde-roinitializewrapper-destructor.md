---
title: 'RoInitializeWrapper:: ~ RoInitializeWrapper 解構函式 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper::~RoInitializeWrapper
dev_langs:
- C++
ms.assetid: afef4c1f-ffde-4cd2-8654-8de4182eb5f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5548eb413f0d5cd4c72983e00bdf65f61bb98f6d
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42597919"
---
# <a name="roinitializewrapperroinitializewrapper-destructor"></a>RoInitializeWrapper::~RoInitializeWrapper 解構函式

取消初始化 Windows 執行階段。

## <a name="syntax"></a>語法

```cpp
~RoInitializeWrapper()  
```

## <a name="remarks"></a>備註

**RoInitializeWrapper**類別叫用`Windows::Foundation::Uninitialize()`。

## <a name="requirements"></a>需求

**標頭：** corewrappers.h

**命名空間：** Microsoft::WRL::Wrappers

## <a name="see-also"></a>另請參閱

[HandleT 類別](../windows/handlet-class.md)