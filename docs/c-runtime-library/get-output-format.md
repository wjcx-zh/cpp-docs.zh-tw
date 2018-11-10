---
title: _get_output_format
ms.date: 11/04/2016
apiname:
- _get_output_format
apilocation:
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcr80.dll
- msvcrt.dll
- msvcr90.dll
- msvcr120.dll
- msvcr110.dll
apitype: DLLExport
f1_keywords:
- get_output_format
- _get_output_format
helpviewer_keywords:
- output formatting
- get_output_format function
- _get_output_format function
ms.assetid: 0ce42f3b-3479-41c4-bcbf-1d21f7ee37e7
ms.openlocfilehash: a78ffb1c7fd32db3092bcf1d2297a0be6fa9f47b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50518790"
---
# <a name="getoutputformat"></a>_get_output_format

取得輸出格式旗標目前的值。

> [!IMPORTANT]
>  此函式已被取代。 自 Visual Studio 2015 起，此函式即無法在 CRT 中使用。

## <a name="syntax"></a>語法

```
unsigned int _get_output_format();
```

## <a name="return-value"></a>傳回值

輸出格式旗標目前的值。

## <a name="remarks"></a>備註

格式化 I/O 的輸出格式旗標控制 功能。 此旗標目前有兩個可能值：0 及 `_TWO_DIGIT_EXPONENT`。 若設定 `_TWO_DIGIT_EXPONENT` ，除非指數大小需要第三位數，否則將會列印只有兩位數浮點數字的指數。 若此旗標為零，浮點輸出會顯示三位數指數，並在必要使用零將值填補到三位數。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|`_get_output_format`|\<stdio.h>|

如需相容性詳細資訊，請參閱簡介中的 [相容性](../c-runtime-library/compatibility.md) 。

## <a name="see-also"></a>請參閱

[格式規格語法：printf 和 wprintf 函式](../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)<br/>
[printf、_printf_l、wprintf、_wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)<br/>
[printf_s、_printf_s_l、wprintf_s、_wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)<br/>
[_set_output_format](../c-runtime-library/set-output-format.md)
