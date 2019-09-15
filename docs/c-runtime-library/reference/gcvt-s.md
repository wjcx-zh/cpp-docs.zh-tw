---
title: _gcvt_s
ms.date: 04/05/2018
api_name:
- _gcvt_s
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
- _gcvt_s
- gcvt_s
helpviewer_keywords:
- _gcvt_s function
- _CVTBUFSIZE
- floating-point functions, converting number to string
- gcvt_s function
- numbers, converting to strings
- conversions, floating point to strings
- strings [C++], converting from floating point
- CVTBUFSIZE
ms.assetid: 0a8d8a26-5940-4ae3-835e-0aa6ec1b0744
ms.openlocfilehash: 7ecb6fe105d8a976979f91d38c9e536b10989310
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956114"
---
# <a name="_gcvt_s"></a>_gcvt_s

將浮點值轉換為字串。 這是具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述之安全性增強功能的 [_gcvt](gcvt.md) 版本。

## <a name="syntax"></a>語法

```C
errno_t _gcvt_s(
   char *buffer,
   size_t sizeInBytes,
   double value,
   int digits
);
template <size_t cchStr>
errno_t _gcvt_s(
   char (&buffer)[cchStr],
   double value,
   int digits
); // C++ only
```

### <a name="parameters"></a>參數

*buffer*<br/>
儲存轉換結果的緩衝區。

*sizeInBytes*<br/>
緩衝區的大小。

*值*<br/>
要轉換的值。

*digits*<br/>
儲存的重要數字的數目。

## <a name="return-value"></a>傳回值

如果成功，則為零。 如果因為不正確的參數而發生失敗 (請參閱下表中無效的值)，會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，則會傳回錯誤碼。 錯誤碼於 Errno.h 中定義。 如需這些錯誤的清單，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

### <a name="error-conditions"></a>錯誤狀況

|*buffer*|*sizeInBytes*|*值*|*digits*|Return|*Buffer*中的值|
|--------------|-------------------|-------------|--------------|------------|-----------------------|
|**NULL**|any|any|any|**EINVAL**|未修改。|
|Not **Null** （指向有效的記憶體）|零|any|any|**EINVAL**|未修改。|
|Not **Null** （指向有效的記憶體）|any|any|>= *sizeInBytes*|**EINVAL**|未修改。|

**安全性問題**

如果*緩衝區*未指向有效的記憶體，而且不是**Null**，則 **_gcvt_s**可能會產生存取違規。

## <a name="remarks"></a>備註

**_Gcvt_s**函式會將浮點*值*轉換為字元字串（其中包括小數點和可能的正負號位元組），並將字串儲存在*buffer*中。 *緩衝區*應該夠大，足以容納轉換的值加上會自動附加的終止 null 字元。 長度 **_CVTBUFSIZE**的緩衝區足以滿足任何浮點值。 如果使用的緩衝區大小為*數位*+ 1，則函式不會覆寫緩衝區結尾，因此請務必提供足夠的緩衝區來進行這項作業。 **_gcvt_s**會嘗試以十進位格式來產生*位數*數位。 如果無法這麼做，則會產生指數格式的*數位*。 可於轉換中隱藏尾端零。

在 C++ 中，這個函式的使用已由範本多載簡化；多載可自動推斷緩衝區長度，因而不需要指定大小引數。 如需詳細資訊，請參閱 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

此函式的偵錯版本會先用 0xFD 填滿緩衝區。 若要停用此行為，請使用 [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|選擇性標頭|
|-------------|---------------------|---------------------|
|**_gcvt_s**|\<stdlib.h>|\<error.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_gcvt_s.c
#include <stdio.h>
#include <stdlib.h>
#include <errno.h>

int main()
{
    char buf[_CVTBUFSIZE];
    int decimal;
    int sign;
    int err;

    err = _gcvt_s(buf, _CVTBUFSIZE, 1.2, 5);

    if (err != 0)
    {
        printf("_gcvt_s failed with error code %d\n", err);
        exit(1);
    }

    printf("Converted value: %s\n", buf);
}
```

```Output
Converted value: 1.2
```

## <a name="see-also"></a>另請參閱

[資料轉換](../../c-runtime-library/data-conversion.md)<br/>
[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[atof、_atof_l、_wtof、_wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt_s](ecvt-s.md)<br/>
[_fcvt_s](fcvt-s.md)<br/>
[_gcvt](gcvt.md)<br/>
