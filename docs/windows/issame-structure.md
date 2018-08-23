---
title: IsSame 結構 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::IsSame
dev_langs:
- C++
helpviewer_keywords:
- IsSame structure
ms.assetid: 1eddbc3f-3cc5-434f-8495-e4477e1f868e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e9e45f64d8eda3e24fb7c85120f14e981963f7f1
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42595781"
---
# <a name="issame-structure"></a>IsSame 結構

支援 WRL 結構，而且不是直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
template <
   typename T1,
   typename T2
>
struct IsSame;
template <
   typename T1
>
struct IsSame<T1, T1>;
```

### <a name="parameters"></a>參數

*T1*  
類型。

*T2*  
另一個型別。

## <a name="remarks"></a>備註

其中一個指定的型別是否相當於另一個測試指定的類型。

## <a name="members"></a>成員

### <a name="public-constants"></a>公用常數

|名稱|描述|
|----------|-----------------|
|[IsSame::value 常數](../windows/issame-value-constant.md)|表示一種型別是否與另一個相同。|

## <a name="inheritance-hierarchy"></a>繼承階層

`IsSame`

## <a name="requirements"></a>需求

**標頭：** internal.h

**命名空間：** Microsoft::WRL::Details

## <a name="see-also"></a>另請參閱

[Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)