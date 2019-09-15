---
title: _set_printf_count_output
ms.date: 11/04/2016
api_name:
- _set_printf_count_output
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
- api-ms-win-crt-stdio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- set_printf_count_output
- _set_printf_count_output
helpviewer_keywords:
- '%n format'
- set_printf_count_output function
- _set_printf_count_output function
ms.assetid: d8259ec5-764e-42d0-9169-72172e95163b
ms.openlocfilehash: 0d53b4e4c56a69582a4eb517fa1a5c9e10cd7d2f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948425"
---
# <a name="_set_printf_count_output"></a>_set_printf_count_output

啟用或停用[printf、_printf_l、wprintf、_wprintf_l](printf-printf-l-wprintf-wprintf-l.md)系列函式中的 **% n**格式支援。

## <a name="syntax"></a>語法

```C
int _set_printf_count_output(
   int enable
);
```

### <a name="parameters"></a>參數

*enable*<br/>
若要啟用 **% n**支援，則為非零值，0表示停用 **% n**支援。

## <a name="property-valuereturn-value"></a>屬性值/傳回值

在呼叫此函式之前， **% n**支援的狀態：非零，如果已啟用 **% n**支援，則為0（如果已停用）。

## <a name="remarks"></a>備註

基於安全性的理由，對 **% n**格式規範的支援預設會在**printf**及其所有變數中停用。 如果在**printf**格式規格中遇到 **% n** ，預設行為是叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 使用非零引數呼叫 **_set_printf_count_output**將會導致**printf**系列函式解讀 **% n** ，如[格式規格語法： printf 和 wprintf 函數](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)中所述。

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
