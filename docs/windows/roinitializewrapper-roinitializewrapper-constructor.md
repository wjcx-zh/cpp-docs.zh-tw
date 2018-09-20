---
title: 'Roinitializewrapper:: Roinitializewrapper 建構函式 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper::RoInitializeWrapper
dev_langs:
- C++
ms.assetid: c6f7fb07-14af-4574-9135-cea164607f30
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8b5cf858ae3fb3974898428b8437784ac3ce324e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46416275"
---
# <a name="roinitializewrapperroinitializewrapper-constructor"></a>RoInitializeWrapper::RoInitializeWrapper 建構函式

初始化的新執行個體**RoInitializeWrapper**類別。

## <a name="syntax"></a>語法

```cpp
RoInitializeWrapper(   RO_INIT_TYPE flags)  
```

### <a name="parameters"></a>參數

*flags*<br/>
其中一個的 RO_INIT_TYPE 列舉型別，指定 Windows 執行階段所提供的支援。

## <a name="remarks"></a>備註

**RoInitializeWrapper**類別叫用`Windows::Foundation::Initialize(flags)`。

## <a name="requirements"></a>需求

**標頭：** corewrappers.h

**命名空間：** Microsoft::WRL::Wrappers

## <a name="see-also"></a>另請參閱

[HandleT 類別](../windows/handlet-class.md)