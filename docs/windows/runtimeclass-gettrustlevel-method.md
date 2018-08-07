---
title: 'Runtimeclass:: Gettrustlevel 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClass::GetTrustLevel
dev_langs:
- C++
helpviewer_keywords:
- GetTrustLevel method
ms.assetid: bd90407e-6dd7-41c3-9ea0-c402c276014a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 98bd73d2c067e6d5bbb4425782de594bbaa47bc1
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/07/2018
ms.locfileid: "39606620"
---
# <a name="runtimeclassgettrustlevel-method"></a>RuntimeClass::GetTrustLevel 方法

取得目前的信任層級**RuntimeClass**物件。

## <a name="syntax"></a>語法

```cpp
STDMETHOD(GetTrustLevel)(
    _Out_ TrustLevel* trustLvl
);
```

### <a name="parameters"></a>參數

*trustLvl*  
這項作業完成時，目前的信任層級**RuntimeClass**物件。

## <a name="return-value"></a>傳回值

一律傳回 S_OK。

## <a name="remarks"></a>備註

如果，就會發出判斷提示 」 錯誤&#95; &#95;WRL_STRICT&#95; &#95;或&#95; &#95;WRL_FORCE_INSPECTABLE_CLASS_MACRO&#95; &#95;未定義。

## <a name="requirements"></a>需求

**標頭：** implements.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱
 [RuntimeClass 類別](../windows/runtimeclass-class.md)