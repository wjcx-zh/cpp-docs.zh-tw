---
title: InspectableClass 巨集 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::InspectableClass
dev_langs:
- C++
ms.assetid: ff390b26-58cc-424f-87ac-1fe3cc692b59
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0a19635b635b80d65e0da99b8f50606154a5b4b2
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42594764"
---
# <a name="inspectableclass-macro"></a>InspectableClass 巨集

設定執行階段類別名稱和信任層級。

## <a name="syntax"></a>語法

```cpp
InspectableClass(
   runtimeClassName,
   trustLevel)  
```

### <a name="parameters"></a>參數

*runtimeClassName*  
執行階段類別的完整文字名稱。

*trustLevel*  
其中一個[TrustLevel](http://msdn.microsoft.com/library/br224625.aspx)列舉值。

## <a name="remarks"></a>備註

**InspectableClass**巨集只能搭配 Windows 執行階段類型。

## <a name="requirements"></a>需求

**標頭：** implements.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[RuntimeClass 類別](../windows/runtimeclass-class.md)