---
title: _set_output_format
ms.date: 11/04/2016
api_name:
- _set_output_format
api_location:
- msvcrt.dll
- msvcr120.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr110.dll
- msvcr80.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- set_output_format
- _set_output_format
helpviewer_keywords:
- _TWO_DIGIT_EXPONENT constant
- output formatting
- TWO_DIGIT_EXPONENT constant
- _set_output_format function
- set_output_format function
ms.assetid: 1cb48df8-44b4-4400-bd27-287831d6b3ff
ms.openlocfilehash: c855df4c29a53fd898b920f6446afe4e568ba5bb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360912"
---
# <a name="_set_output_format"></a>_set_output_format

自訂格式化 I/O 函式所使用的輸出格式。

> [!IMPORTANT]
> 此函式已過時。 自 Visual Studio 2015 起，此函式即無法在 CRT 中使用。

## <a name="syntax"></a>語法

```
unsigned int _set_output_format(
   unsigned int format
);
```

#### <a name="parameters"></a>參數

*格式*<br/>
[in] 值，代表要使用的格式。

## <a name="return-value"></a>傳回值

舊的輸出格式。

## <a name="remarks"></a>備註

`_set_output_format`用於配置格式化的 I/O 函數(如[printf_s](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md))的輸出。 目前此函式唯一能變更的格式化慣例，是在浮點數字輸出指數中顯示的位數。

即使三不需要三位數代表指數值，函式 (例如 `printf_s`、 `wprintf_s`及 Visual C++ 標準 C 程式庫中的相關函式) 的預設浮點數字輸出仍會列印三位數的指數。 零會用來將值填補到三位數。 `_set_output_format` 可用於變更此行為。除非指數大小需要第三位數，否則將會列印只有兩位數的指數。

若要啟用兩位數指數，請呼叫此函式並使用參數 `_TWO_DIGIT_EXPONENT`，如範例中所示。 若要停用兩位數指數，請呼叫此函式並使用引數 0。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|`_set_output_format`|\<stdio.h>|

如需詳細的相容性資訊，請參閱簡介中的 [Compatibility](../c-runtime-library/compatibility.md) 。

## <a name="example"></a>範例

```C
// crt_set_output_format.c
#include <stdio.h>

void printvalues(double x, double y)
{
   printf_s("%11.4e %11.4e\n", x, y);
   printf_s("%11.4E %11.4E\n", x, y);
   printf_s("%11.4g %11.4g\n", x, y);
   printf_s("%11.4G %11.4G\n", x, y);
}

int main()
{
   double x = 1.211E-5;
   double y = 2.3056E-112;
   unsigned int old_exponent_format;

   // Use the default format
   printvalues(x, y);

   // Enable two-digit exponent format
   old_exponent_format = _set_output_format(_TWO_DIGIT_EXPONENT);

   printvalues(x, y);

   // Disable two-digit exponent format
   _set_output_format( old_exponent_format );

   printvalues(x, y);
}
```

```Output
1.2110e-005 2.3056e-112
1.2110E-005 2.3056E-112
1.211e-005  2.306e-112
1.211E-005  2.306E-112
1.2110e-05 2.3056e-112
1.2110E-05 2.3056E-112
  1.211e-05  2.306e-112
  1.211E-05  2.306E-112
1.2110e-005 2.3056e-112
1.2110E-005 2.3056E-112
1.211e-005  2.306e-112
1.211E-005  2.306E-112
```

## <a name="see-also"></a>另請參閱

[printf_s、_printf_s_l、wprintf_s、_wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)<br/>
[_get_output_format](../c-runtime-library/get-output-format.md)
