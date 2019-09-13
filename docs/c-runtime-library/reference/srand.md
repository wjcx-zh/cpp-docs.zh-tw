---
title: srand
ms.date: 01/02/2018
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
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- srand
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
ms.openlocfilehash: d74ae4cbec5a76df48bb2b56acab7329e6cf8aa5
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70927410"
---
# <a name="srand"></a>srand

設定**rand**函數所使用之亂數產生器的起始種子值。

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

**Srand**函式會設定起點，以便在目前的執行緒中產生一連串的隨機整數。 若要重新初始化產生器以建立相同的結果序列，請呼叫**srand**函數，然後再次使用相同的*種子*引數。 *種子*的任何其他值會將產生器設為隨機序列中的不同起點。 **rand**會抓取所產生的亂數。 在呼叫**srand**之前呼叫**rand** ，會產生與呼叫**srand**的順序相同的序列，其*種子*會傳遞為1。

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
