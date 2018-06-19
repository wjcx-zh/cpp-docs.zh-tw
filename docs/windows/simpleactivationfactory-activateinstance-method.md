---
title: 'Simpleactivationfactory:: Activateinstance 方法 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::SimpleActivationFactory::ActivateInstance
dev_langs:
- C++
helpviewer_keywords:
- ActivateInstance method
ms.assetid: 4f836e51-5a6c-4bad-b871-9f25199298b4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5af4bfd22302b7694b9bafbc1452d636b19cb3c7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33889417"
---
# <a name="simpleactivationfactoryactivateinstance-method"></a>SimpleActivationFactory::ActivateInstance 方法

建立指定之介面的執行個體。

## <a name="syntax"></a>語法

```cpp
STDMETHOD( ActivateInstance )(
    _Deref_out_ IInspectable **ppvObject
);
```

### <a name="parameters"></a>參數

*ppvObject*  
這項作業完成時，所指定的物件執行個體的指標`Base`類別樣板參數。

## <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

## <a name="remarks"></a>備註

如果&#95; &#95;WRL_STRICT&#95; &#95;是定義，判斷提示會發出錯誤如果類別樣板參數中指定的基底類別不衍生自[RuntimeClass](../windows/runtimeclass-class.md)，或未設定與 WinRt 或WinRtClassicComMix [RuntimeClassType](../windows/runtimeclasstype-enumeration.md)列舉值。

## <a name="requirements"></a>需求

**標頭：** module.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[SimpleActivationFactory 類別](../windows/simpleactivationfactory-class.md)