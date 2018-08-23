---
title: EnableIf 結構 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::EnableIf
dev_langs:
- C++
helpviewer_keywords:
- EnableIf structure
ms.assetid: 7825b283-e6b2-4f39-a4b9-c03bcd431b8e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0e71c43ca9222b350c07dae5f299f4a6f469bf84
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42578553"
---
# <a name="enableif-structure"></a>EnableIf 結構

支援 WRL 結構，而且不是直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
template <
   bool b,
   typename T = void
>

struct EnableIf;
template <
   typename T
>
struct EnableIf<true, T>;
```

### <a name="parameters"></a>參數

*T*  
類型。

*b*  
Boolean 運算式。

## <a name="remarks"></a>備註

如果第一個範本參數評估為第二個範本參數所指定之型別的資料成員會定義 **，則為 true**。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|`type`|如果範本參數*b*評估為 **，則為 true**，部分特製化定義資料成員`type`必須是類型`T`。|

## <a name="inheritance-hierarchy"></a>繼承階層

`EnableIf`

## <a name="requirements"></a>需求

**標頭：** internal.h

**命名空間：** Microsoft::WRL::Details

## <a name="see-also"></a>另請參閱

[Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)