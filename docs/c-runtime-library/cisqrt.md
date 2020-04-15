---
title: _CIsqrt
ms.date: 4/2/2020
api_name:
- _CIsqrt
- _o__CIsqrt
api_location:
- msvcr90.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcrt.dll
- msvcr110.dll
- msvcr100.dll
- api-ms-win-crt-math-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _CIsqrt
- CIsqrt
helpviewer_keywords:
- CIsqrt intrinsic
- _CIsqrt intrinsic
ms.assetid: 663548ea-398c-48ee-8397-a787c6ebb937
ms.openlocfilehash: eb67474ce5ecd1e6769f8d5fb676fd1753ef6d72
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81349521"
---
# <a name="_cisqrt"></a>_CIsqrt

計算堆疊頂端值的平方根。

## <a name="syntax"></a>語法

```
void __cdecl _CIsqrt();
```

## <a name="remarks"></a>備註

這個版本的 `sqrt` 函式具有編譯器了解的特定呼叫慣例。 因為它可以防止產生複本並協助暫存器配置，所以會加速執行。

產生的值會推入至堆疊的頂端。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](global-state.md)。

## <a name="requirements"></a>需求

**平台:** x86

## <a name="see-also"></a>另請參閱

[依字母順序排列的函式參考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[sqrt、sqrtf、sqrtl](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)
