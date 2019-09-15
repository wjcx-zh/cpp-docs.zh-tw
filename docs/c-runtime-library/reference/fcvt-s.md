---
title: _fcvt_s
ms.date: 04/05/2018
api_name:
- _fcvt_s
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
- fcvt_s
- _fcvt_s
helpviewer_keywords:
- fcvt_s function
- converting floating point, to strings
- floating-point functions, converting number to string
- _fcvt_s function
ms.assetid: 48671197-1d29-4c2b-a5d8-d2368f5f68a1
ms.openlocfilehash: a63b542333717a57097da455fb514eeef80344b4
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941362"
---
# <a name="_fcvt_s"></a>_fcvt_s

將浮點數轉換為字串。 這是如 [CRT 的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述之增強安全性的 [_lfind](fcvt.md) 版本。

## <a name="syntax"></a>語法

```C
errno_t _fcvt_s(
   char* buffer,
   size_t sizeInBytes,
   double value,
   int count,
   int *dec,
   int *sign
);
template <size_t size>
errno_t _fcvt_s(
   char (&buffer)[size],
   double value,
   int count,
   int *dec,
   int *sign
); // C++ only
```

### <a name="parameters"></a>參數

*buffer*<br/>
保留轉換結果之提供的緩衝區。

*sizeInBytes*<br/>
以位元組為單位的緩衝區大小。

*值*<br/>
要轉換的數字。

*計數*<br/>
小數點後的小數位數。

*dec*<br/>
預存小數點位置的指標。

*簽署*<br/>
預存正負號指標的指標。

## <a name="return-value"></a>傳回值

如果成功，則為零。 如果失敗，傳回的值會是錯誤碼。 錯誤碼於 Errno.h 中定義。 如需這些錯誤的清單，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

如果是下表所列的無效參數，則此函式會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，此函式會將**errno**設定為**EINVAL** ，並傳回**EINVAL**。

### <a name="error-conditions"></a>錯誤狀況

|*buffer*|*sizeInBytes*|value|計數|dec|Sign|Return|*Buffer*中的值|
|--------------|-------------------|-----------|-----------|---------|----------|------------|-----------------------|
|**NULL**|any|any|any|any|any|**EINVAL**|未修改。|
|Not **Null** （指向有效的記憶體）|<=0|any|any|any|any|**EINVAL**|未修改。|
|any|any|any|any|**NULL**|any|**EINVAL**|未修改。|
|any|any|any|any|any|**NULL**|**EINVAL**|未修改。|

## <a name="security-issues"></a>安全性問題

如果*緩衝區*未指向有效的記憶體，而且不是**Null**，則 **_fcvt_s**可能會產生存取違規。

## <a name="remarks"></a>備註

**_Fcvt_s**函數會將浮點數轉換成以 null 結束的字元字串。 *Value*參數是要轉換的浮點數。 **_fcvt_s**會將*值*的數位儲存為字串，並附加 null 字元（' \ 0 '）。 *Count*參數指定小數點之後要儲存的位數。 多餘的數位會四捨五入以*計算*位置。 如果精確度的位數少於*計數*，字串會以零填補。

字串中只能儲存數字。 在呼叫之後，可以從*dec*和*sign*取得小數點和*值*正負號的位置。 *Dec*參數指向整數值;這個整數值會提供相對於字串開頭的小數點位置。 零或負整數值表示小數點位於第一位數字的左邊。 參數*正負號*指向表示*值*正負號的整數。 如果*值*為正數，則整數設定為0，如果*值*為負數，則設定為非零的數位。

長度 **_CVTBUFSIZE**的緩衝區足以滿足任何浮點值。

**_Ecvt_s**和 **_fcvt_s**之間的差異在於*count*參數的轉譯。 **_ecvt_s**會將*count*解讀為輸出字串中的總位數，而 **_fcvt_s**會將*count*解讀為小數點後的位數。

在 C++ 中，這個函式的使用已由範本多載簡化；多載可自動推斷緩衝區長度，因而不需要指定大小引數。 如需詳細資訊，請參閱 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

此函式的偵錯版本會先用 0xFD 填滿緩衝區。 若要停用此行為，請使用 [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md)。

## <a name="requirements"></a>需求

|函數|必要的標頭|選擇性標頭|
|--------------|---------------------|---------------------|
|**_fcvt_s**|\<stdlib.h>|\<errno.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

**磁帶**[CRT 程式庫功能](../../c-runtime-library/crt-library-features.md)的所有版本。

## <a name="example"></a>範例

```C
// fcvt_s.c
#include <stdio.h>
#include <stdlib.h>
#include <errno.h>

int main()
{
    char * buf = 0;
    int decimal;
    int sign;
    int err;

    buf = (char*) malloc(_CVTBUFSIZE);
    err = _fcvt_s(buf, _CVTBUFSIZE, 1.2, 5, &decimal, &sign);

    if (err != 0)
    {
        printf("_fcvt_s failed with error code %d\n", err);
        exit(1);
    }

    printf("Converted value: %s\n", buf);
}
```

```Output
Converted value: 120000
```

## <a name="see-also"></a>另請參閱

[資料轉換](../../c-runtime-library/data-conversion.md)<br/>
[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[atof、_atof_l、_wtof、_wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt_s](ecvt-s.md)<br/>
[_gcvt_s](gcvt-s.md)<br/>
[_fcvt](fcvt.md)<br/>
