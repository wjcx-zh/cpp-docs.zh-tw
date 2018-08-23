---
title: 'Runtimeclass:: Queryinterface 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClass::QueryInterface
dev_langs:
- C++
helpviewer_keywords:
- QueryInterface method
ms.assetid: 8f01f4a1-3fa2-4a8e-88c6-03629236cb9f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f3c50857a683c806d57b5e754bc98ba5a5340fd8
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42597804"
---
# <a name="runtimeclassqueryinterface-method"></a>RuntimeClass::QueryInterface 方法

擷取指定的介面 ID 的指標

## <a name="syntax"></a>語法

```cpp
STDMETHOD(
   QueryInterface
)  
   (REFIID riid,
   _Deref_out_ void **ppvObject);
```

### <a name="parameters"></a>參數

*riid*  
介面識別碼。

*ppvObject*  
此 opereation 完成時，所指定之介面的指標*riid*參數。

## <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

## <a name="requirements"></a>需求

**標頭：** implements.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[RuntimeClass 類別](../windows/runtimeclass-class.md)