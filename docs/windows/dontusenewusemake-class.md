---
title: DontUseNewUseMake 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::DontUseNewUseMake
dev_langs:
- C++
helpviewer_keywords:
- DontUseNewUseMake class
ms.assetid: 8b38d07b-fc14-4cea-afb9-4c1a7dde0093
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: dc2b2f03cfbd488de8358b2e4b123716efcbfe15
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46431303"
---
# <a name="dontusenewusemake-class"></a>DontUseNewUseMake 類別

支援 WRL 結構，而且不是直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
class DontUseNewUseMake;
```

## <a name="remarks"></a>備註

防止使用運算子**新**在`RuntimeClass`。 因此，您必須使用[讓函式](../windows/make-function.md)改。

## <a name="members"></a>成員

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[DontUseNewUseMake::operator new 運算子](../windows/dontusenewusemake-operator-new-operator.md)|多載運算子**新**並且讓它無法使用於`RuntimeClass`。|

## <a name="inheritance-hierarchy"></a>繼承階層

`DontUseNewUseMake`

## <a name="requirements"></a>需求

**標頭：** implements.h

**命名空間：** Microsoft::WRL::Details

## <a name="see-also"></a>另請參閱

[Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)<br/>
[Make 函式](../windows/make-function.md)