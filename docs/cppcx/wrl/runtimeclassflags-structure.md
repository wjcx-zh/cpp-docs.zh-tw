---
title: RuntimeClassFlags 結構
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClassFlags
- implements/Microsoft::WRL::RuntimeClassFlags::value
helpviewer_keywords:
- Microsoft::WRL::RuntimeClassFlags structure
- Microsoft::WRL::RuntimeClassFlags::value constant
ms.assetid: 7098d605-bd14-4d51-82f4-3def8296a938
ms.openlocfilehash: 4cbd3f367bc57c2eedf672422a458b67b1908fc0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403148"
---
# <a name="runtimeclassflags-structure"></a>RuntimeClassFlags 結構

包含的執行個體的型別[RuntimeClass](runtimeclass-class.md)。

## <a name="syntax"></a>語法

```cpp
template <unsigned int flags>
struct RuntimeClassFlags;
```

### <a name="parameters"></a>參數

*flags*<br/>
A [RuntimeClassType 列舉](runtimeclasstype-enumeration.md)值。

## <a name="members"></a>成員

### <a name="public-constants"></a>公用常數

|名稱|描述|
|----------|-----------------|
|[RuntimeClassFlags::value 常數](#value-constant)|包含[RuntimeClassType 列舉](runtimeclasstype-enumeration.md)值。|

## <a name="inheritance-hierarchy"></a>繼承階層

`RuntimeClassFlags`

## <a name="requirements"></a>需求

**標頭：** implements.h

**命名空間：** Microsoft:: wrl

## <a name="value-constant"></a>Runtimeclassflags:: Value 常數

包含的欄位[RuntimeClassType 列舉](runtimeclasstype-enumeration.md)值。

```cpp
static const unsigned int value = flags;
```
