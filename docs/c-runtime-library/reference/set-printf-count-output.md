---
title: _set_printf_count_output
ms.date: 11/04/2016
apiname:
- _set_printf_count_output
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- set_printf_count_output
- _set_printf_count_output
helpviewer_keywords:
- '%n format'
- set_printf_count_output function
- _set_printf_count_output function
ms.assetid: d8259ec5-764e-42d0-9169-72172e95163b
ms.openlocfilehash: 0d4847d850b39c7c03ea92a98499715b1e6a4913
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50595607"
---
# <a name="setprintfcountoutput"></a>_set_printf_count_output

啟用或停用的支援 **%n**格式化[printf、 _printf_l、 wprintf、 _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)-系列函式。

## <a name="syntax"></a>語法

```C
int _set_printf_count_output(
   int enable
);
```

### <a name="parameters"></a>參數

*enable*<br/>
非零值，以啟用 **%n**支援，0 以停用 **%n**支援。

## <a name="property-valuereturn-value"></a>屬性值/傳回值

狀態 **%n**之前呼叫這個函式支援： 非零 if **%n**支援已啟用，0，如果它已停用。

## <a name="remarks"></a>備註

基於安全性原因，對 **%n**格式規範中的預設會停用**printf**和其所有變體。 如果 **%n**中遇到**printf**格式規格中，預設行為是叫用無效參數處理常式，如中所述[Parameter Validation](../../c-runtime-library/parameter-validation.md)。 呼叫 **_set_printf_count_output**為非零引數會導致**printf**-系列函式解譯 **%n**中所述[格式規格語法： printf 和 wprintf 函式](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_set_printf_count_output**|\<stdio.h>|

如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_set_printf_count_output.c
#include <stdio.h>

int main()
{
   int e;
   int i;
   e = _set_printf_count_output( 1 );
   printf( "%%n support was %sabled.\n",
        e ? "en" : "dis" );
   printf( "%%n support is now %sabled.\n",
        _get_printf_count_output() ? "en" : "dis" );
   printf( "12345%n6789\n", &i ); // %n format should set i to 5
   printf( "i = %d\n", i );
}
```

```Output
%n support was disabled.
%n support is now enabled.
123456789
i = 5
```

## <a name="see-also"></a>另請參閱

[_get_printf_count_output](get-printf-count-output.md)<br/>
