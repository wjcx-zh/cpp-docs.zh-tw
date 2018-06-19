---
title: _CItan | Microsoft Docs
ms.custom: ''
ms.date: 04/11/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _CItan
apilocation:
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr80.dll
- msvcrt.dll
- msvcr110.dll
- msvcr90.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- _CItan
- CItan
dev_langs:
- C++
helpviewer_keywords:
- CItan intrinsic
- _CItan intrinsic
ms.assetid: d1ea3113-50a2-45a6-b6bc-680fcdcc0928
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fcbd7f4258447df6f60f464b4c0a24080155fa9c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32387973"
---
# <a name="citan"></a>_CItan

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
