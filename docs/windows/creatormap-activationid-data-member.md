---
title: 'Creatormap:: Activationid 資料成員 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreatorMap::activationId
dev_langs:
- C++
helpviewer_keywords:
- activationId data member
ms.assetid: 77518b76-6e6a-4b48-8e2e-a4c7c67769e0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: eeaaedeb4c3806af888f36e62c8fa8e54c47eb46
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42595690"
---
# <a name="creatormapactivationid-data-member"></a>CreatorMap::activationId 資料成員

支援 WRL 結構，而且不是直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
union {
   const IID* clsid;
   const wchar_t* (*getRuntimeName)();
} activationId;
```

### <a name="parameters"></a>參數

*clsid*  
介面識別碼。

*getRuntimeName*  
擷取函式的 Windows 執行階段物件的名稱。

## <a name="remarks"></a>備註

表示透過傳統的 COM 類別識別碼或 Windows 執行階段名稱識別的物件識別碼。

## <a name="requirements"></a>需求

**標頭：** module.h

**命名空間：** Microsoft::WRL::Details

## <a name="see-also"></a>另請參閱

[CreatorMap 結構](../windows/creatormap-structure.md)  
[Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)