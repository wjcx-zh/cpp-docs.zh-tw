---
title: 'Runtimeclass:: Getruntimeclassname 方法 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClass::GetRuntimeClassName
dev_langs:
- C++
helpviewer_keywords:
- GetRuntimeClassName method
ms.assetid: f6388163-fe65-4948-a4bc-ae6826f480e7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3cfe3cc4a8a304bbd04fde9e6c38e2b9170e2e73
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="runtimeclassgetruntimeclassname-method"></a>RuntimeClass::GetRuntimeClassName 方法

取得目前 RuntimeClass 物件的執行階段類別名稱。

## <a name="syntax"></a>語法

```cpp
STDMETHOD( GetRuntimeClassName )(
    _Out_ HSTRING* runtimeName
);
```

### <a name="parameters"></a>參數

*runtimeName*  
這項作業完成時，執行階段類別名稱。

## <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

## <a name="remarks"></a>備註

如果，就會發出 assert 錯誤&#95; &#95;WRL_STRICT&#95; &#95;或&#95; &#95;WRL_FORCE_INSPECTABLE_CLASS_MACRO&#95; &#95;未定義。

## <a name="requirements"></a>需求

**標頭：** implements.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[RuntimeClass 類別](../windows/runtimeclass-class.md)