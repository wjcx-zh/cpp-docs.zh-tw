---
title: srand
ms.date: 4/2/2020
api_name:
- srand
- _o_srand
api_location:
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 3f6f97ad9a3bd0d7e4e88ad1797d369f012bbe5e
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82913600"
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

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

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
