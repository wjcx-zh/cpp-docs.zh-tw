---
title: _fcvt_s
ms.date: 4/2/2020
api_name:
- _fcvt_s
- _o__fcvt_s
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
- fcvt_s
- _fcvt_s
helpviewer_keywords:
- fcvt_s function
- converting floating point, to strings
- floating-point functions, converting number to string
- _fcvt_s function
ms.assetid: 48671197-1d29-4c2b-a5d8-d2368f5f68a1
ms.openlocfilehash: 557a1d359c389f0eb7477aab4bf9cbb51558703a
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920197"
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

*緩衝區*<br/>
保留轉換結果之提供的緩衝區。

*sizeInBytes*<br/>
以位元組為單位的緩衝區大小。

*值*<br/>
要轉換的數字。

*計數*<br/>
小數點後的小數位數。

*十進位*<br/>
預存小數點位置的指標。

*簽訂*<br/>
預存正負號指標的指標。

## <a name="return-value"></a>傳回值

如果成功，則為零。 如果失敗，傳回的值會是錯誤碼。 錯誤碼於 Errno.h 中定義。 如需這些錯誤的清單，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

如果是下表所列的無效參數，則此函式會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，此函式會將**errno**設定為**EINVAL** ，並傳回**EINVAL**。

### <a name="error-conditions"></a>錯誤狀況

|*緩衝區*|*sizeInBytes*|value|count|dec|簽署|傳回|*Buffer*中的值|
|--------------|-------------------|-----------|-----------|---------|----------|------------|-----------------------|
|**Null**|任意|任意|任意|任意|任意|**EINVAL**|未修改。|
|Not **Null** （指向有效的記憶體）|<=0|任意|任意|任意|任意|**EINVAL**|未修改。|
|任意|任意|任意|任意|**Null**|任意|**EINVAL**|未修改。|
|任意|任意|任意|任意|任意|**Null**|**EINVAL**|未修改。|

## <a name="security-issues"></a>安全性問題

如果*緩衝區*未指向有效的記憶體，而且不是**Null**， **_fcvt_s**可能會產生存取違規。

## <a name="remarks"></a>備註

**_Fcvt_s**函式會將浮點數轉換成以 null 結束的字元字串。 *Value*參數是要轉換的浮點數。 **_fcvt_s**將*值*的數位儲存為字串，並附加 null 字元（' \ 0 '）。 *Count*參數指定小數點之後要儲存的位數。 多餘的數位會四捨五入以*計算*位置。 如果精確度的位數少於*計數*，字串會以零填補。

字串中只能儲存數字。 在呼叫之後，可以從*dec*和*sign*取得小數點和*值*正負號的位置。 *Dec*參數指向整數值;這個整數值會提供相對於字串開頭的小數點位置。 零或負整數值表示小數點位於第一位數字的左邊。 參數*正負號*指向表示*值*正負號的整數。 如果*值*為正數，則整數設定為0，如果*值*為負數，則設定為非零的數位。

長度 **_CVTBUFSIZE**的緩衝區足以滿足任何浮點值。

**_Ecvt_s**和 **_fcvt_s**之間的差異在於*count*參數的轉譯。 **_ecvt_s**會將*count*轉譯為輸出字串中的總位數， **_fcvt_s**會將*count*解讀為小數點後面的位數。

在 C++ 中，使用這個函式已為範本多載簡化；多載可自動推斷緩衝區長度，因而不需要指定大小引數。 如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。

此函式的 debug 版本會先使用0xFE 填滿緩衝區。 若要停用此行為，請使用 [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md)。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|函式|必要的標頭|選擇性標頭|
|--------------|---------------------|---------------------|
|**_fcvt_s**|\<stdlib.h>|\<errno.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

**程式庫︰** 所有版本的 [CRT 程式庫功能](../../c-runtime-library/crt-library-features.md)。

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
