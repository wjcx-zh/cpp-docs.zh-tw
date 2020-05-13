---
title: _gcvt_s
ms.date: 4/2/2020
api_name:
- _gcvt_s
- _o__gcvt_s
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 83e34bffbe62bf07d2d3f9f649d12607b0e08be7
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919419"
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

*緩衝區*<br/>
儲存轉換結果的緩衝區。

*sizeInBytes*<br/>
緩衝區的大小。

*值*<br/>
要轉換的值。

*數字*<br/>
儲存的重要數字的數目。

## <a name="return-value"></a>傳回值

如果成功，則為零。 如果因為不正確的參數而發生失敗 (請參閱下表中無效的值)，會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，則會傳回錯誤碼。 錯誤碼於 Errno.h 中定義。 如需這些錯誤的清單，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

### <a name="error-conditions"></a>錯誤狀況

|*緩衝區*|*sizeInBytes*|*值*|*數字*|傳回|*Buffer*中的值|
|--------------|-------------------|-------------|--------------|------------|-----------------------|
|**Null**|任意|任意|任意|**EINVAL**|未修改。|
|Not **Null** （指向有效的記憶體）|零|任意|任意|**EINVAL**|未修改。|
|Not **Null** （指向有效的記憶體）|任意|任意|>= *sizeInBytes*|**EINVAL**|未修改。|

**安全性問題**

如果*緩衝區*未指向有效的記憶體，而且不是**Null**， **_gcvt_s**可能會產生存取違規。

## <a name="remarks"></a>備註

**_Gcvt_s**函式會將浮點*值*轉換為字元字串（其中包括小數點和可能的正負號位元組），並將字串儲存在*buffer*中。 *緩衝區*應該夠大，足以容納轉換的值加上會自動附加的終止 null 字元。 長度 **_CVTBUFSIZE**的緩衝區足以滿足任何浮點值。 如果使用的緩衝區大小為*數位*+ 1，則函式不會覆寫緩衝區結尾，因此請務必提供足夠的緩衝區來進行這項作業。 **_gcvt_s**嘗試以十進位格式產生*位數*數位。 如果無法這麼做，則會產生指數格式的*數位*。 可於轉換中隱藏尾端零。

在 C++ 中，使用這個函式已為範本多載簡化；多載可自動推斷緩衝區長度，因而不需要指定大小引數。 如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。

此函式的 debug 版本會先使用0xFE 填滿緩衝區。 若要停用此行為，請使用 [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md)。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|選擇性標頭|
|-------------|---------------------|---------------------|
|**_gcvt_s**|\<stdlib.h>|\<error.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

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
