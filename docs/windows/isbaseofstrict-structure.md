---
title: IsBaseOfStrict 結構 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::IsBaseOfStrict
dev_langs:
- C++
helpviewer_keywords:
- IsBaseOfStrict structure
ms.assetid: 6fed7366-c8d4-4991-b4fb-43ed93f8e1bf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 52db5abd0487624f52f692e785007adaf9eac7ee
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46428261"
---
# <a name="isbaseofstrict-structure"></a>IsBaseOfStrict 結構

支援 WRL 結構，而且不是直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
template <
   typename Base,
   typename Derived
>

struct IsBaseOfStrict;
template <
   typename Base
>
struct IsBaseOfStrict<Base, Base>;
```

### <a name="parameters"></a>參數

*基底*<br/>
基底類型。

*衍生*<br/>
在衍生的型別。

## <a name="remarks"></a>備註

測試某個類型是否為另一個類型的基底。

第一個範本會測試是否為型別衍生自基底型別，可能會產生**真**或是**false**。 第二個範本會測試是否為型別衍生自本身，這一律會產生**false**。

## <a name="members"></a>成員

### <a name="public-constants"></a>公用常數

|名稱|描述|
|----------|-----------------|
|[IsBaseOfStrict::value 常數](../windows/isbaseofstrict-value-constant.md)|指出是否會有一個類型的另一個基底。|

## <a name="inheritance-hierarchy"></a>繼承階層

`IsBaseOfStrict`

## <a name="requirements"></a>需求

**標頭：** internal.h

**命名空間：** Microsoft::WRL::Details

## <a name="see-also"></a>另請參閱

[Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)