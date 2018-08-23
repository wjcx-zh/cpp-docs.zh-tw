---
title: 'Interfacetraits:: Casttobase 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceTraits::CastToBase
dev_langs:
- C++
helpviewer_keywords:
- CastToBase method
ms.assetid: 0591a017-0adf-4358-b946-eb0a307ce7f2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 55a4d7487be5b3565ba3945630cab4388f287a68
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42611820"
---
# <a name="interfacetraitscasttobase-method"></a>InterfaceTraits::CastToBase 方法

支援 WRL 結構，而且不是直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
template<typename T>
static __forceinline Base* CastToBase(
   _In_ T* ptr
);
```

### <a name="parameters"></a>參數

*T*  
參數的型別*ptr*。

*ptr*  
類型指標*T*。

## <a name="return-value"></a>傳回值

指標`Base`。

## <a name="remarks"></a>備註

轉換指標的指定的指標`Base`。

如需詳細資訊`Base`，請參閱公用 Typedefs 一節[InterfaceTraits 結構](../windows/interfacetraits-structure.md)。

## <a name="requirements"></a>需求

**標頭：** implements.h

**命名空間：** Microsoft::WRL::Details

## <a name="see-also"></a>另請參閱

[InterfaceTraits 結構](../windows/interfacetraits-structure.md)  
[Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)