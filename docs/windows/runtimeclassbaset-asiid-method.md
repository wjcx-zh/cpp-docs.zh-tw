---
title: 'Runtimeclassbaset:: Asiid 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::RuntimeClassBaseT::AsIID
dev_langs:
- C++
helpviewer_keywords:
- AsIID method
ms.assetid: 90d7df8a-cf9e-4eef-8837-bc1a25f3fa1a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b50466fc2c357c1d57fca272ff343cd56f3689c5
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42604262"
---
# <a name="runtimeclassbasetasiid-method"></a>RuntimeClassBaseT::AsIID 方法

支援 WRL 結構，而且不是直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
template<typename T>
__forceinline static HRESULT AsIID(
   _In_ T* implements,
   REFIID riid,
   _Deref_out_ void **ppvObject
);
```

### <a name="parameters"></a>參數

*T*  
實作介面識別碼參數所指定的型別*riid*。

*實作*  
範本參數所指定類型的變數*T*。

*riid*  
要擷取的介面識別碼。

*ppvObject*  
如果這項作業成功時，參數所指定的指標-至-a-介面的指標*riid*。

## <a name="return-value"></a>傳回值

如果成功則為 S_OK否則，會描述錯誤的 HRESULT。

## <a name="remarks"></a>備註

擷取指定的介面 ID 的指標

## <a name="requirements"></a>需求

**標頭：** implements.h

**命名空間：** Microsoft::WRL::Details

## <a name="see-also"></a>另請參閱

[RuntimeClassBaseT 結構](../windows/runtimeclassbaset-structure.md)  
[Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)