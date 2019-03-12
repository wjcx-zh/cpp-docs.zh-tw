---
title: _CIsqrt
ms.date: 11/04/2016
apiname:
- _CIsqrt
apilocation:
- msvcr90.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcrt.dll
- msvcr110.dll
- msvcr100.dll
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _CIsqrt
- CIsqrt
helpviewer_keywords:
- CIsqrt intrinsic
- _CIsqrt intrinsic
ms.assetid: 663548ea-398c-48ee-8397-a787c6ebb937
ms.openlocfilehash: 5042be822df7789d30d2b4ea2d5be6cf8a081ef9
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2019
ms.locfileid: "57749382"
---
# <a name="cisqrt"></a>_CIsqrt

計算堆疊頂端值的平方根。

## <a name="syntax"></a>語法

```
void __cdecl _CIsqrt();
```

## <a name="remarks"></a>備註

這個版本的 `sqrt` 函式具有編譯器了解的特定呼叫慣例。 因為它可以防止產生複本並協助暫存器配置，所以會加速執行。

產生的值會推入至堆疊的頂端。

## <a name="requirements"></a>需求

**平台：** x86

## <a name="see-also"></a>另請參閱

[依字母順序排列的函式參考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[sqrt、sqrtf、sqrtl](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)
