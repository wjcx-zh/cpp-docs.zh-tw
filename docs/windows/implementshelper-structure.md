---
title: ImplementsHelper 結構 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::ImplementsHelper
dev_langs:
- C++
helpviewer_keywords:
- ImplementsHelper structure
ms.assetid: b857ba80-81bd-4e53-92b6-210991954243
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5a3a31125d8489551f1eec143013661bf385f29a
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43212441"
---
# <a name="implementshelper-structure"></a>ImplementsHelper 結構

支援 WRL 結構，而且不是直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
template <
   typename RuntimeClassFlagsT,
   typename ILst,
   bool IsDelegateToClass
>
friend struct Details::ImplementsHelper;
```

### <a name="parameters"></a>參數

*RuntimeClassFlagsT*  
指定一或多個旗標欄位[RuntimeClassType](../windows/runtimeclasstype-enumeration.md)列舉值。

*ILst*  
介面識別碼的清單。

*IsDelegateToClass*  
指定 **，則為 true**如果目前的執行個體`Implements`的基底類別中的第一個介面識別碼*ILst*; 否則**false**。

## <a name="remarks"></a>備註

可協助實作[實作](../windows/implements-structure.md)結構。

此範本會周遊之介面的清單，並將它們加入做為基底類別，以及啟用所需的資訊`QueryInterface`。

## <a name="members"></a>成員

## <a name="inheritance-hierarchy"></a>繼承階層

`ImplementsHelper`

## <a name="requirements"></a>需求

**標頭：** implements.h

**命名空間：** Microsoft::WRL::Details

## <a name="see-also"></a>另請參閱

[參考 （Windows 執行階段程式庫）](https://msdn.microsoft.com/00000000-0000-0000-0000-000000000000)  
[Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)