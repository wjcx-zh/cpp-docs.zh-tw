---
title: 'Simpleclassfactory:: Createinstance 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::SimpleClassFactory::CreateInstance
dev_langs:
- C++
helpviewer_keywords:
- CreateInstance method
ms.assetid: 17b7947a-2608-49d9-b730-fef76501c9bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d9dfb783a8e002f249d5f6b4cc0a45193669efb3
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42603109"
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
必須是**nullptr**; 否則傳回的值是 CLASS_E_NOAGGREGATION。

SimpleClassFactory 不支援彙總。 如果已支援彙總，但所建立的物件已是在彙總的一部分*pUnkOuter*會是指標，以控制`IUnknown`彙總的介面。

*riid*  
介面若要建立之物件的識別碼。

*ppvObject*  
這項作業完成時，所指定的物件執行個體的指標*riid*參數。

## <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

## <a name="remarks"></a>備註

如果`__WRL_STRICT__`是定義，判斷提示會發出錯誤如果類別範本參數中指定的基底類別不衍生自[RuntimeClass](../windows/runtimeclass-class.md)，或因未設定 ClassicCom 或 WinRtClassicComMix [RuntimeClassType](../windows/runtimeclasstype-enumeration.md)列舉值。

## <a name="requirements"></a>需求

**標頭：** module.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[SimpleClassFactory 類別](../windows/simpleclassfactory-class.md)