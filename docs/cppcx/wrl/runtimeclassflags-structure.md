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
ms.openlocfilehash: 9fed5bb31b077288495a78aefcbd8401b3520bb6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367218"
---
# <a name="runtimeclassflags-structure"></a>RuntimeClassFlags 結構

包含[運行時類](runtimeclass-class.md)實例的類型。

## <a name="syntax"></a>語法

```cpp
template <unsigned int flags>
struct RuntimeClassFlags;
```

### <a name="parameters"></a>參數

*標誌*<br/>
[運行時類類型枚舉](runtimeclasstype-enumeration.md)值。

## <a name="members"></a>成員

### <a name="public-constants"></a>公用常數

|名稱|描述|
|----------|-----------------|
|[RuntimeClassFlags::value 常數](#value-constant)|包含[執行時類類型枚舉](runtimeclasstype-enumeration.md)值。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

`RuntimeClassFlags`

## <a name="requirements"></a>需求

**標題:** 實現.h

**命名空間：** Microsoft::WRL

## <a name="runtimeclassflagsvalue-constant"></a><a name="value-constant"></a>執行時類別標誌::值常量

包含[運行時類類型枚舉值的](runtimeclasstype-enumeration.md)欄位。

```cpp
static const unsigned int value = flags;
```
