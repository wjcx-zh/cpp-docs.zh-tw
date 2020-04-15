---
title: btowc
ms.date: 4/2/2020
api_name:
- btowc
- _o_btowc
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
- api-ms-win-crt-convert-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- btowc
helpviewer_keywords:
- btowc function
ms.assetid: 99a46e02-6f86-4569-af79-5feca012add8
ms.openlocfilehash: b4262f31c95b5272e3917f58a6c945577d401f16
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333768"
---
# <a name="btowc"></a>btowc

判斷整數是否代表初始移位狀態中的有效單一位元組字元。

## <a name="syntax"></a>語法

```C
wint_t btowc(
   int character
);
```

### <a name="parameters"></a>參數

*字元*<br/>
待測試整數。

## <a name="return-value"></a>傳回值

如果整數代表初始移位狀態中的有效單一位元組字元，則會傳回字元的寬字元表示法。 如果整數是 EOF，或不是初始移位狀態中的有效單一位元組字元，則會傳回 WEOF。 此函數的輸出受當前**LC_TYPE**區域設置的影響。

## <a name="remarks"></a>備註

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**btowc**|\<stdio.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[mbtowc、_mbtowc_l](mbtowc-mbtowc-l.md)<br/>
