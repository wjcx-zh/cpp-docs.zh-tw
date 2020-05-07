---
title: _CItan
ms.date: 4/2/2020
api_name:
- _CItan
- _o__CItan
api_location:
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr80.dll
- msvcrt.dll
- msvcr110.dll
- msvcr90.dll
- msvcr120.dll
- api-ms-win-crt-math-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 65cce8b094a1508566e2de7162b9e8e76712742a
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82918325"
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

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](global-state.md)。

## <a name="requirements"></a>需求

**平臺：** x86

## <a name="see-also"></a>另請參閱

[依字母順序排列的函式參考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[tan、tanf、tanl](../c-runtime-library/reference/tan-tanf-tanl.md)<br/>
