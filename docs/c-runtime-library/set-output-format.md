---
title: _set_output_format | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- _set_output_format
apilocation:
- msvcrt.dll
- msvcr120.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr110.dll
- msvcr80.dll
apitype: DLLExport
f1_keywords:
- set_output_format
- _set_output_format
dev_langs:
- C++
helpviewer_keywords:
- _TWO_DIGIT_EXPONENT constant
- output formatting
- TWO_DIGIT_EXPONENT constant
- _set_output_format function
- set_output_format function
ms.assetid: 1cb48df8-44b4-4400-bd27-287831d6b3ff
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d9d41ae92a829452edebe390723997a67b5cd812
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46112066"
---
# <a name="setoutputformat"></a>_set_output_format

自訂格式化 I/O 函式所使用的輸出格式。

> [!IMPORTANT]
>  此函式已被取代。 自 Visual Studio 2015 起，此函式即無法在 CRT 中使用。

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

`_set_output_format` 可用於設定格式化 I/O 函式的輸出，例如 [printf_s](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)。 目前此函式唯一能變更的格式化慣例，是在浮點數字輸出指數中顯示的位數。

即使三不需要三位數代表指數值，函式 (例如 `printf_s`、 `wprintf_s`及 Visual C++ 標準 C 程式庫中的相關函式) 的預設浮點數字輸出仍會列印三位數的指數。 零會用來將值填補到三位數。 `_set_output_format` 可用於變更此行為。除非指數大小需要第三位數，否則將會列印只有兩位數的指數。

若要啟用兩位數指數，請呼叫此函式並使用參數 `_TWO_DIGIT_EXPONENT`，如範例中所示。 若要停用兩位數指數，請呼叫此函式並使用引數 0。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|`_set_output_format`|\<stdio.h>|

如需相容性詳細資訊，請參閱簡介中的 [相容性](../c-runtime-library/compatibility.md) 。

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

## <a name="see-also"></a>請參閱

[printf_s、_printf_s_l、wprintf_s、_wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)<br/>
[_get_output_format](../c-runtime-library/get-output-format.md)