---
title: _get_printf_count_output
ms.date: 11/04/2016
api_name:
- _get_printf_count_output
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
- get_printf_count_output
- _get_printf_count_output
helpviewer_keywords:
- '%n format'
- get_printf_count_output function
- _get_printf_count_output function
ms.assetid: 850f9f33-8319-433e-98d8-6a694200d994
ms.openlocfilehash: 15b37ac759821ad56cc5c03c9b98719d8f0cc19a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70955714"
---
# <a name="_get_printf_count_output"></a>_get_printf_count_output

指出[printf、_printf_l、wprintf、_wprintf_l](printf-printf-l-wprintf-wprintf-l.md)系列函數是否支援 **% n**格式。

## <a name="syntax"></a>語法

```C
int _get_printf_count_output();
```

## <a name="return-value"></a>傳回值

如果支援 **% n** ，則為非零，如果不支援 **% n**則為0。

## <a name="remarks"></a>備註

如果不支援 **% n** （預設值），則在任何**printf**函式的格式字串中遇到 **% n** ，將會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果已啟用 **% n**支援（請參閱[_set_printf_count_output](set-printf-count-output.md)），則 **% n**的行為會如[格式規格語法： printf 和 wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)函式中所述。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_get_printf_count_output**|\<stdio.h>|

如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱[_set_printf_count_output](set-printf-count-output.md)的範例。

## <a name="see-also"></a>另請參閱

[_set_printf_count_output](set-printf-count-output.md)<br/>
