---
title: _ecvt_s
ms.date: 4/2/2020
api_name:
- _ecvt_s
- _o__ecvt_s
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: e33840e772de770e0f05ae45d2c2d4bec7e09939
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348051"
---
# <a name="_ecvt_s"></a>_ecvt_s

將**雙**數轉換為字串。 這是具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述之安全性增強功能的 [_ecvt](ecvt.md) 版本。

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

如果是下表所列的無效參數，則此函式會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許執行繼續,此函數將**errno**設定到**EINVAL**並傳回**EINVAL**。

### <a name="error-conditions"></a>錯誤狀況

|*_Buffer*|*_SizeInBytes*|_Value|_Count|_Dec|_Sign|傳回值|*緩衝區*中的值|
|---------------|--------------------|-------------|-------------|-----------|------------|------------------|-----------------------|
|**空**|任意|任意|任意|任意|任意|**埃因瓦爾**|未修改。|
|**非 NULL(** 指向有效記憶體 )|<=0|任意|任意|任意|任意|**埃因瓦爾**|未修改。|
|任意|任意|任意|任意|**空**|任意|**埃因瓦爾**|未修改。|
|任意|任意|任意|任意|任意|**空**|**埃因瓦爾**|未修改。|

## <a name="security-issues"></a>安全性問題

如果*緩衝區*不指向有效記憶體且不是**NULL,_ecvt_s**可能會生成**NULL**訪問衝突。

## <a name="remarks"></a>備註

**_ecvt_s**函數將浮點數轉換為字串。 *_Value*參數是要轉換的浮點數。 此函數最多存儲 *_Value**的數字作為字串*,並追加一個空字元 (『\0』)。 如果 *_Value*的數字數超過 *_Count,* 則低階數位為四捨五入。 如果*數位少於計數*數位,則字串將用零填充。

字串中只能儲存數字。 小數點的位置和 *_Value*標誌可以從*調用后_Dec**和_Sign*獲得。 *_Dec*參數指向一個整數值,該值給出相對於字串開頭的小數點的位置。 0 或負整數值表示小數點位於第一位數字的左邊。 *_Sign*參數指向指示轉換數字符號的整數。 如果整數值為 0，則數字為正數。 否則，數字為負數。

長度 **_CVTBUFSIZE**緩衝區對於任何浮點值都足夠。

**_ecvt_s**和 **_fcvt_s**的區別在於 *_Count參數的解釋*。 **_ecvt_s**將 *_Count*解釋為輸出字串中的總位數,而 **_fcvt_s**將 *_Count*解釋為小數點之後的位數。

在 C++ 中，使用這個函式已為範本多載簡化；多載可自動推斷緩衝區長度，因而不需要指定大小引數。 如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。

此函數的調試版本首先用 0xFE 填充緩衝區。 若要停用此行為，請使用 [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md)。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|函式|必要的標頭|選擇性標頭|
|--------------|---------------------|---------------------|
|**_ecvt_s**|\<stdlib.h>|\<errno.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

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
