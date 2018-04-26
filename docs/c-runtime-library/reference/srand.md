---
title: srand | Microsoft Docs
ms.custom: ''
ms.date: 1/02/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- srand
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- srand
dev_langs:
- C++
helpviewer_keywords:
- random starting point
- random starting point, setting
- random numbers, generating
- srand function
- numbers, pseudorandom
- numbers, random
- pseudorandom numbers
- starting points, setting random
- starting points
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a01e56159bf4f04f2c8a53f39e3fcd1e7dd450b5
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="srand"></a>srand

設定虛擬隨機號碼產生器所使用的起始的種子值**rand**函式。

## <a name="syntax"></a>語法

```C
void srand(
   unsigned int seed
);
```

### <a name="parameters"></a>參數

*種子*虛擬隨機產生的種子

## <a name="remarks"></a>備註

**Srand**函式會將目前的執行緒中產生虛擬隨機整數的一系列的起點。 若要重新初始化來建立結果的相同順序產生器，呼叫**srand**函式，並使用相同*種子*一次的引數。 任何其他值作為*種子*設定產生器中的虛擬隨機序列不同的起始點。 **rand**擷取所產生的虛擬隨機數字。 呼叫**rand**之前的任何呼叫**srand**會產生相同的順序與呼叫**srand**與*種子*傳遞為 1。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**srand**|\<stdlib.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱 [rand](rand.md) 的範例。

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[rand](rand.md)<br/>
