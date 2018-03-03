---
title: "Simpleclassfactory:: Createinstance 方法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::SimpleClassFactory::CreateInstance
dev_langs:
- C++
helpviewer_keywords:
- CreateInstance method
ms.assetid: 17b7947a-2608-49d9-b730-fef76501c9bc
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 68778eb1b5421cfcf22261d8b1c1efd99bc32c50
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="simpleclassfactorycreateinstance-method"></a>SimpleClassFactory::CreateInstance 方法

建立指定之介面的執行個體。

## <a name="syntax"></a>語法

```cpp
STDMETHOD( CreateInstance )(
   _Inout_opt_ IUnknown* pUnkOuter,
   REFIID riid,
   _Deref_out_ void** ppvObject
);
```

### <a name="parameters"></a>參數

*pUnkOuter*  
必須是`nullptr`; 否則傳回的值是 CLASS_E_NOAGGREGATION。

SimpleClassFactory 不支援彙總。 如果支援彙總，而且所建立的物件已是在彙總的一部分`pUnkOuter`會彙總控制 IUnknown 介面指標。

*riid*  
介面來建立物件的識別碼。

*ppvObject*  
這項作業完成時，所指定的物件執行個體的指標`riid`參數。

## <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

## <a name="remarks"></a>備註

如果 &#95; &#95;WRL_STRICT #95; &#95;已定義，判斷提示會發出錯誤如果類別樣板參數中指定的基底類別不衍生自[RuntimeClass](../windows/runtimeclass-class.md)，或未設定為使用 ClassicCom 或 WinRtClassicComMix [RuntimeClassType](../windows/runtimeclasstype-enumeration.md)列舉值。

## <a name="requirements"></a>需求

**標頭：** module.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>請參閱

[SimpleClassFactory 類別](../windows/simpleclassfactory-class.md)