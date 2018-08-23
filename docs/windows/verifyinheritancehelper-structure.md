---
title: VerifyInheritanceHelper 結構 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::VerifyInheritanceHelper
dev_langs:
- C++
helpviewer_keywords:
- VerifyInheritanceHelper structure
ms.assetid: 8a48a702-0f71-4807-935b-8311f0a7a8b6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6a7b101091cefcdca65518c2a62bd274f7af4607
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42610251"
---
# <a name="verifyinheritancehelper-structure"></a>VerifyInheritanceHelper 結構

支援 WRL 結構，而且不是直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
template <
   typename I,
   typename Base
>
struct VerifyInheritanceHelper;
template <
   typename I
>
struct VerifyInheritanceHelper<I, Nil>;
```

### <a name="parameters"></a>參數

*I*  
類型。

*基底*  
另一個型別。

## <a name="remarks"></a>備註

測試是否有一個介面衍生自另一個介面。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[VerifyInheritanceHelper::Verify 方法](../windows/verifyinheritancehelper-verify-method.md)|測試目前的範本參數所指定的兩個介面，並決定是否要將一個介面衍生自其他。|

## <a name="inheritance-hierarchy"></a>繼承階層

`VerifyInheritanceHelper`

## <a name="requirements"></a>需求

**標頭：** implements.h

**命名空間：** Microsoft::WRL::Details

## <a name="see-also"></a>另請參閱

[Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)