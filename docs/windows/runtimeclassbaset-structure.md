---
title: RuntimeClassBaseT 結構 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::RuntimeClassBaseT
dev_langs:
- C++
ms.assetid: a62775fb-3359-4f45-9ff1-c07fa8da464b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4b0bae186a0c4d4e9a6c7eec8553c296428b3a59
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42597187"
---
# <a name="runtimeclassbaset-structure"></a>RuntimeClassBaseT 結構

支援 WRL 結構，而且不是直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
template <
   unsigned int RuntimeClassTypeT
>
friend struct Details::RuntimeClassBaseT;
```

### <a name="parameters"></a>參數

*RuntimeClassTypeT*  
指定一或多個旗標欄位[RuntimeClassType](../windows/runtimeclasstype-enumeration.md)列舉值。

## <a name="remarks"></a>備註

提供 helper 方法來`QueryInterface`作業和取得的介面識別碼。

## <a name="members"></a>成員

## <a name="inheritance-hierarchy"></a>繼承階層

`RuntimeClassBaseT`

## <a name="requirements"></a>需求

**標頭：** implements.h

**命名空間：** Microsoft::WRL::Details

## <a name="see-also"></a>另請參閱

[參考 （Windows 執行階段程式庫）](http://msdn.microsoft.com/00000000-0000-0000-0000-000000000000)  
[Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)