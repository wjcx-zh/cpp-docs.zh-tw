---
title: InterfaceList 結構 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceList
dev_langs:
- C++
helpviewer_keywords:
- InterfaceList structure
ms.assetid: 6ec3228d-eb3e-4b7e-aef1-7dcf17bdf61a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 61a8e7b36448a485705b914fbb37892271d7d9fc
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42597162"
---
# <a name="interfacelist-structure"></a>InterfaceList 結構

支援 WRL 結構，而且不是直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
template <
   typename T,
   typename U
>
struct InterfaceList;
```

### <a name="parameters"></a>參數

*T*  
介面名稱;[遞迴] 清單中的第一個介面。

*U*  
介面名稱;在 [遞迴] 清單中其餘的介面。

## <a name="remarks"></a>備註

用來建立介面的遞迴清單。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|`FirstT`|範本參數同義*T*。|
|`RestT`|範本參數同義*U*。|

## <a name="inheritance-hierarchy"></a>繼承階層

`InterfaceList`

## <a name="requirements"></a>需求

**標頭：** implements.h

**命名空間：** Microsoft::WRL::Details

## <a name="see-also"></a>另請參閱

[Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)