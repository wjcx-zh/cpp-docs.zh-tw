---
title: RuntimeClassFlags 結構 |Microsoft Docs
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClassFlags
- implements/Microsoft::WRL::RuntimeClassFlags::value
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::RuntimeClassFlags structure
- Microsoft::WRL::RuntimeClassFlags::value constant
ms.assetid: 7098d605-bd14-4d51-82f4-3def8296a938
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 90b590637935b7dbeaa0bb6a07ed84faeb0d0a1d
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50076174"
---
# <a name="runtimeclassflags-structure"></a>RuntimeClassFlags 結構

包含的執行個體的型別[RuntimeClass](../windows/runtimeclass-class.md)。

## <a name="syntax"></a>語法

```cpp
template <unsigned int flags>
struct RuntimeClassFlags;
```

### <a name="parameters"></a>參數

*flags*<br/>
A [RuntimeClassType 列舉](../windows/runtimeclasstype-enumeration.md)值。

## <a name="members"></a>成員

### <a name="public-constants"></a>公用常數

|名稱|描述|
|----------|-----------------|
|[RuntimeClassFlags::value 常數](#value-constant)|包含[RuntimeClassType 列舉](../windows/runtimeclasstype-enumeration.md)值。|

## <a name="inheritance-hierarchy"></a>繼承階層

`RuntimeClassFlags`

## <a name="requirements"></a>需求

**標頭：** implements.h

**命名空間：** Microsoft::WRL

## <a name="value-constant"></a>Runtimeclassflags:: Value 常數

包含的欄位[RuntimeClassType 列舉](../windows/runtimeclasstype-enumeration.md)值。

```cpp
static const unsigned int value = flags;
```
