---
title: "Simpleactivationfactory:: Activateinstance 方法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::SimpleActivationFactory::ActivateInstance
dev_langs: C++
helpviewer_keywords: ActivateInstance method
ms.assetid: 4f836e51-5a6c-4bad-b871-9f25199298b4
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f1e28afad17f4fdc593e6dea4bebddf27f1548f7
ms.sourcegitcommit: ca2f94dfd015e0098a6eaf5c793ec532f1c97de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
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

如果 &#95; &#95;WRL_STRICT #95; &#95;已定義，判斷提示會發出錯誤如果類別樣板參數中指定的基底類別不衍生自[RuntimeClass](../windows/runtimeclass-class.md)，或未設定為使用 WinRt 或 WinRtClassicComMix [RuntimeClassType](../windows/runtimeclasstype-enumeration.md)列舉值。

## <a name="requirements"></a>需求

**標頭：** module.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[SimpleActivationFactory 類別](../windows/simpleactivationfactory-class.md)