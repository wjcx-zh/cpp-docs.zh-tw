---
title: _CIcos | Microsoft Docs
ms.custom: ''
ms.date: 04/11/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _CIcos
apilocation:
- msvcr90.dll
- msvcrt.dll
- msvcr120.dll
- msvcr100.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr110.dll
apitype: DLLExport
f1_keywords:
- CIcos
- _CIcos
dev_langs:
- C++
helpviewer_keywords:
- _CIcos intrinsic
- CIcos intrinsic
ms.assetid: 6fc203fb-66f3-4ead-9784-f85833c26f1b
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cb399a25bacd7fc288ad881625589e240009068a
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="cicos"></a>_CIcos

計算浮點堆疊頂端值的餘弦值。

## <a name="syntax"></a>語法

```C
void __cdecl _CIcos();
```

## <a name="remarks"></a>備註

這個版本的 [cos](../c-runtime-library/reference/cos-cosf-cosl.md) 函式具有編譯器了解的特定呼叫慣例。 因為它可以防止產生複本並協助暫存器配置，所以會加速執行。

產生的值會推入至浮點堆疊的頂端。

## <a name="requirements"></a>需求

**平台：**x86

## <a name="see-also"></a>另請參閱

[依字母順序排列的函式參考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[cos、cosf、cosl](../c-runtime-library/reference/cos-cosf-cosl.md)<br/>
