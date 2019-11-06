---
title: _ecvt_s
ms.date: 04/05/2018
api_name:
- _ecvt_s
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
- ecvt_s
- _ecvt_s
helpviewer_keywords:
- _ecvt_s function
- ecvt_s function
- numbers, converting
- converting double numbers
ms.assetid: d52fb0a6-cb91-423f-80b3-952a8955d914
ms.openlocfilehash: a37508c293ee72934a8580f822878f27031b864b
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2019
ms.locfileid: "73624376"
---
# <a name="_ecvt_s"></a>_ecvt_s

將**雙精度浮**點數轉換為字串。 這是具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述之安全性增強功能的 [_ecvt](ecvt.md) 版本。

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

如果是下表所列的無效參數，則此函式會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，此函式會將**errno**設定為**EINVAL** ，並傳回**EINVAL**。

### <a name="error-conditions"></a>錯誤狀況

|*_Buffer*|*_SizeInBytes*|_Value|_Count|_Dec|_Sign|傳回值|*Buffer*中的值|
|---------------|--------------------|-------------|-------------|-----------|------------|------------------|-----------------------|
|**NULL**|任何|任何|任何|任何|任何|**EINVAL**|未修改。|
|Not **Null** （指向有效的記憶體）|<=0|任何|任何|任何|任何|**EINVAL**|未修改。|
|任何|任何|任何|任何|**NULL**|任何|**EINVAL**|未修改。|
|任何|任何|任何|任何|任何|**NULL**|**EINVAL**|未修改。|

## <a name="security-issues"></a>安全性問題

如果*緩衝區*未指向有效的記憶體，而且不是**Null**， **_ecvt_s**可能會產生存取違規。

## <a name="remarks"></a>備註

**_Ecvt_s**函式會將浮點數轉換成字元字串。 *_Value*參數是要轉換的浮點數。 此函式會將 *_Value*的*計數*數位儲存為字串，並附加 null 字元（' \ 0 '）。 如果 *_Value*中的位數超過 *_Count*，則會將低序位數位四捨五入。 如果數位少於*計數*，字串會以零填補。

字串中只能儲存數字。 小數點的位置和 *_Value*的正負號可以從 *_Dec*取得，並在呼叫之後 *_Sign* 。 *_Dec*參數會指向整數值，以提供相對於字串開頭的小數點位置。 0 或負整數值表示小數點位於第一位數字的左邊。 *_Sign*參數指向整數，表示已轉換數位的正負號。 如果整數值為 0，則數字為正數。 否則，數字為負數。

長度 **_CVTBUFSIZE**的緩衝區足以滿足任何浮點值。

**_Ecvt_s**和 **_fcvt_s**之間的差異在於 *_Count*參數的轉譯。 **_ecvt_s**會將 *_Count*轉譯為輸出字串中的總位數，而 **_fcvt_s**會將 *_Count*轉譯為小數點後面的位數。

在 C++ 中，使用這個函式已為範本多載簡化；多載可自動推斷緩衝區長度，因而不需要指定大小引數。 如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。

此函式的 debug 版本會先使用0xFE 填滿緩衝區。 若要停用此行為，請使用 [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md)。

## <a name="requirements"></a>需求

|功能|必要的標頭|選擇性標頭|
|--------------|---------------------|---------------------|
|**_ecvt_s**|\<stdlib.h>|\<errno.h>|

如需相容性的詳細資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

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

## <a name="see-also"></a>請參閱

[資料轉換](../../c-runtime-library/data-conversion.md)<br/>
[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[atof、_atof_l、_wtof、_wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt](ecvt.md)<br/>
[_fcvt_s](fcvt-s.md)<br/>
[_gcvt_s](gcvt-s.md)<br/>
