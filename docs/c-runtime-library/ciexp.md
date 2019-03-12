---
title: _CIexp
ms.date: 11/04/2016
apiname:
- _CIexp
apilocation:
- msvcr120.dll
- msvcr80.dll
- msvcr110.dll
- msvcr100.dll
- msvcrt.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- CIexp
- _CIexp
helpviewer_keywords:
- CIexp intrinsic
- _CIexp intrinsic
ms.assetid: f8a3e3b7-fa57-41a3-9983-6c81914cbb55
ms.openlocfilehash: 5d51e8e542ffb14a77001d045903dccb1a091d53
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2019
ms.locfileid: "57751323"
---
# <a name="ciexp"></a>_CIexp

計算堆疊頂端值的指數。

## <a name="syntax"></a>語法

```
void __cdecl _CIexp();
```

## <a name="remarks"></a>備註

這個版本的 `exp` 函式具有編譯器了解的特定呼叫慣例。 因為它可以防止產生複本並協助暫存器配置，所以會加速執行。

產生的值會推入至堆疊的頂端。

## <a name="requirements"></a>需求

**平台：** x86

## <a name="see-also"></a>另請參閱

[依字母順序排列的函式參考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[exp、expf、expl](../c-runtime-library/reference/exp-expf.md)
