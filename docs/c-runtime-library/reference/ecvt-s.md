---
title: _ecvt_s | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _ecvt_s
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- ecvt_s
- _ecvt_s
dev_langs:
- C++
helpviewer_keywords:
- _ecvt_s function
- ecvt_s function
- numbers, converting
- converting double numbers
ms.assetid: d52fb0a6-cb91-423f-80b3-952a8955d914
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 623d12bb515794a1d57b5a18e0e93e70d50a6812
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32404356"
---
# <a name="ecvts"></a>_ecvt_s

將轉換**double**數字的字串。 這是具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述之安全性增強功能的 [_ecvt](ecvt.md) 版本。

## <a name="syntax"></a>語法

```C
errno_t _ecvt_s(
   char * _Buffer,
   size_t _SizeInBytes,
   double _Value,
   int _Count,
   int *_Dec,
   int *_Sign
);
template <size_t size>
errno_t _ecvt_s(
   char (&_Buffer)[size],
   double _Value,
   int _Count,
   int *_Dec,
   int *_Sign
); // C++ only
```

### <a name="parameters"></a>參數

*_Buffer*<br/>
填入轉換結果的位數字串指標。

*_SizeInBytes*<br/>
以位元組為單位的緩衝區大小。

*_Value*<br/>
要轉換的數字。

*_Count*<br/>
儲存的位數。

*_Dec*<br/>
儲存的小數點位置。

*_Sign*<br/>
已轉換數字的正負號。

## <a name="return-value"></a>傳回值

如果成功，則為零。 如果失敗，傳回的值會是錯誤碼。 錯誤碼於 Errno.h 中定義。 如需詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

如果是下表所列的無效參數，則此函式會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，此函式會將**errno**至**EINVAL**並傳回**EINVAL**。

### <a name="error-conditions"></a>錯誤狀況

|*_Buffer*|*_SizeInBytes*|_Value|_Count|_Dec|_Sign|傳回值|中的值*緩衝區*|
|---------------|--------------------|-------------|-------------|-----------|------------|------------------|-----------------------|
|**NULL**|任何|任何|任何|任何|任何|**EINVAL**|未修改。|
|不**NULL** （指向有效的記憶體）|<=0|任何|任何|任何|任何|**EINVAL**|未修改。|
|任何|任何|任何|任何|**NULL**|任何|**EINVAL**|未修改。|
|任何|任何|任何|任何|任何|**NULL**|**EINVAL**|未修改。|

## <a name="security-issues"></a>安全性問題

**_ecvt_s**可能會產生存取違規，如果*緩衝區*並未指向有效的記憶體，而且不是**NULL**。

## <a name="remarks"></a>備註

**_Ecvt_s**函式會將浮點數轉換為字元字串。 *_Value*參數是要轉換的浮點數。 此函式會儲存最多*計數*位數 *_Value*做為字串，並將 null 字元 ('\0')。 如果數字位數中 *_Value*超過 *_Count*，低序位字會捨入。 如果有少於*計數*以零填補數字的字串。

字串中只能儲存數字。 小數點和的正負號的位置 *_Value*可以取自 *_Dec*和 *_Sign*呼叫之後。 *_Dec*參數會指向提供字串的開頭與小數點的位置的整數值。 0 或負整數值表示小數點位於第一位數字的左邊。 *_Sign*參數指向表示已轉換的數字的正負號的整數。 如果整數值為 0，則數字為正數。 否則，數字為負數。

長度的緩衝區 **_CVTBUFSIZE**就足以應付任何浮點值。

之間的差異 **_ecvt_s**和 **_fcvt_s**中的解譯 *_Count*參數。 **_ecvt_s**解譯 *_Count*做為輸出字串中的位數總數而 **_fcvt_s**解譯 *_Count*之後位數的數目小數點。

在 C++ 中，這個函式的使用已由範本多載簡化；多載可自動推斷緩衝區長度，因而不需要指定大小引數。 如需詳細資訊，請參閱 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

此函式的偵錯版本會先用 0xFD 填滿緩衝區。 若要停用此行為，請使用 [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md)。

## <a name="requirements"></a>需求

|功能|必要的標頭|選擇性標頭|
|--------------|---------------------|---------------------|
|**_ecvt_s**|\<stdlib.h>|\<errno.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// ecvt_s.c
#include <stdio.h>
#include <stdlib.h>
#include <errno.h>

int main( )
{
    char * buf = 0;
    int decimal;
    int sign;
    int err;

    buf = (char*) malloc(_CVTBUFSIZE);
    err = _ecvt_s(buf, _CVTBUFSIZE, 1.2, 5, &decimal, &sign);

    if (err != 0)
    {
        printf("_ecvt_s failed with error code %d\n", err);
        exit(1);
    }

    printf("Converted value: %s\n", buf);
}
```

```Output
Converted value: 12000
```

## <a name="see-also"></a>另請參閱

[資料轉換](../../c-runtime-library/data-conversion.md)<br/>
[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[atof、_atof_l、_wtof、_wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt](ecvt.md)<br/>
[_fcvt_s](fcvt-s.md)<br/>
[_gcvt_s](gcvt-s.md)<br/>
