---
title: "Runtimeclass:: Gettrustlevel 方法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::RuntimeClass::GetTrustLevel
dev_langs: C++
helpviewer_keywords: GetTrustLevel method
ms.assetid: bd90407e-6dd7-41c3-9ea0-c402c276014a
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: bf5125f7f0fdfe6309d668404dd1077e629a4fac
ms.sourcegitcommit: ca2f94dfd015e0098a6eaf5c793ec532f1c97de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="runtimeclassgettrustlevel-method"></a>RuntimeClass::GetTrustLevel 方法

取得目前 RuntimeClass 物件的信任層級。

## <a name="syntax"></a>語法

```cpp
STDMETHOD(GetTrustLevel)(
    _Out_ TrustLevel* trustLvl
);
```

### <a name="parameters"></a>參數

*trustLvl*  
這項作業完成時，目前 RuntimeClass 物件的信任層級。

## <a name="return-value"></a>傳回值

一律為 S_OK。

## <a name="remarks"></a>備註

判斷提示錯誤是發出的如果 #95; &#95;WRL_STRICT #95; &#95;或 &#95; &#95;WRL_FORCE_INSPECTABLE_CLASS_MACRO #95; &#95;未定義。

## <a name="requirements"></a>需求

**標頭：** implements.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[RuntimeClass 類別](../windows/runtimeclass-class.md)