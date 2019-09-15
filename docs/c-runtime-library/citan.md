---
title: _CItan
ms.date: 04/11/2018
api_name:
- _CItan
api_location:
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr80.dll
- msvcrt.dll
- msvcr110.dll
- msvcr90.dll
- msvcr120.dll
- api-ms-win-crt-math-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _CItan
- CItan
helpviewer_keywords:
- CItan intrinsic
- _CItan intrinsic
ms.assetid: d1ea3113-50a2-45a6-b6bc-680fcdcc0928
ms.openlocfilehash: e509d785648148e51004950076147b69c2db18ec
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70940457"
---
# <a name="_citan"></a>_CItan

計算浮點堆疊頂端值的正切值。

## <a name="syntax"></a>語法

```C
void __cdecl _CItan();
```

## <a name="remarks"></a>備註

這個版本的 [tan](../c-runtime-library/reference/tan-tanf-tanl.md) 函式具有編譯器了解的特定呼叫慣例。 因為函式可以防止產生複本並協助暫存器配置，所以會加速執行。

產生的值會推入至浮點堆疊的頂端。

## <a name="requirements"></a>需求

**平台：** x86

## <a name="see-also"></a>另請參閱

[依字母順序排列的函式參考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[tan、tanf、tanl](../c-runtime-library/reference/tan-tanf-tanl.md)<br/>
