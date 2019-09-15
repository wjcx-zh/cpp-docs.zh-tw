---
title: btowc
ms.date: 11/04/2016
api_name:
- btowc
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- btowc
helpviewer_keywords:
- btowc function
ms.assetid: 99a46e02-6f86-4569-af79-5feca012add8
ms.openlocfilehash: 1f03fce8686f919af85ee3751cb9a0a3fca1ede7
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70943460"
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

*character*<br/>
待測試整數。

## <a name="return-value"></a>傳回值

如果整數代表初始移位狀態中的有效單一位元組字元，則會傳回字元的寬字元表示法。 如果整數是 EOF，或不是初始移位狀態中的有效單一位元組字元，則會傳回 WEOF。 此函式的輸出會受到目前**LC_TYPE**地區設定的影響。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**btowc**|\<stdio.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[mbtowc、_mbtowc_l](mbtowc-mbtowc-l.md)<br/>
