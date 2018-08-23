---
title: BoolStruct 結構 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::BoolStruct
dev_langs:
- C++
helpviewer_keywords:
- BoolStruct structure
ms.assetid: 666eae78-e81d-4fb7-a9e4-1ba617d6d4cd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c4981c7f82fe2c544bf907ac59d6e9ca22105cbd
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42592533"
---
# <a name="boolstruct-structure"></a>BoolStruct 結構

支援 WRL 結構，而且不是直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
struct BoolStruct;
```

## <a name="remarks"></a>備註

**BoolStruct**結構會定義是否`ComPtr`管理介面的物件存留期。 **BoolStruct**會在內部使用[BoolType()](../windows/comptr-operator-microsoft-wrl-details-booltype-operator.md)運算子。

## <a name="members"></a>成員

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[BoolStruct::Member 資料成員](../windows/boolstruct-member-data-member.md)|指定[ComPtr](../windows/comptr-class.md) ，或不是，管理介面的物件存留期。|

## <a name="inheritance-hierarchy"></a>繼承階層

`BoolStruct`

## <a name="requirements"></a>需求

**標頭：** internal.h

**命名空間：** Microsoft::WRL::Details

## <a name="see-also"></a>另請參閱

[Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)  
[ComPtr::operator Microsoft::WRL::Details::BoolType 運算子](../windows/comptr-operator-microsoft-wrl-details-booltype-operator.md)