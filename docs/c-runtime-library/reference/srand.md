---
title: srand | Microsoft Docs
ms.custom: ''
ms.date: 1/02/2018
ms.technology:
- cpp-standard-libraries
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
ms.workload:
- cplusplus
ms.openlocfilehash: 7972ddfe6ae9c1d591bdbd4cc5e208d78e826037
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44107521"
---
# <a name="srand"></a>srand

設定使用的虛擬隨機數字產生器的起始種子值**rand**函式。

## <a name="syntax"></a>語法

```C
void srand(
   unsigned int seed
);
```

### <a name="parameters"></a>參數

*seed*<br/>
虛擬亂數產生的種子

## <a name="remarks"></a>備註

**Srand**函式會設定為目前的執行緒中產生一系列的虛擬隨機整數的起點。 若要重新初始化產生器以建立相同結果的順序，請呼叫**srand**函式，並使用相同*種子*一次的引數。 任何其他值*種子*設定產生器中的虛擬隨機序列不同的起始點。 **rand**擷取所產生的虛擬隨機數字。 呼叫**rand**任何呼叫之前**srand**會產生與呼叫的相同順序**srand**具有*種子*傳遞為 1。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**srand**|\<stdlib.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱 [rand](rand.md) 的範例。

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[rand](rand.md)<br/>
