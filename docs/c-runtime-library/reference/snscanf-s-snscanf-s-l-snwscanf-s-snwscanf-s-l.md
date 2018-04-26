---
title: _snscanf_s、_snscanf_s_l、_snwscanf_s、_snwscanf_s_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _snwscanf_s_l
- _snwscanf_s
- _snscanf_s
- _snscanf_s_l
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
apitype: DLLExport
f1_keywords:
- _sntscanf_s
- snscanf_s
- _snwscanf_s_l
- sntscanf_s_l
- snwscanf_s_l
- snwscanf_s
- _snscanf_s
- _snwscanf_s
- snscanf_s_l
- _sntscanf_s_l
- _snscanf_s_l
- sntscanf_s
dev_langs:
- C++
helpviewer_keywords:
- _snscanf_s_l function
- snwscanf_s function
- _snwscanf_s function
- sntscanf_s_l function
- sntscanf_s function
- _snwscanf_s_l function
- _snscanf_s function
- snscanf_s_l function
- strings [C++], reading data from
- _sntscanf_s_l function
- reading data, strings
- snscanf_s function
- strings [C++], reading
- _sntscanf_s function
- snwscanf_s_l function
ms.assetid: 72356653-7362-461a-af73-597b9c0a8094
caps.latest.revision: 24
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0253b8c103d3125810aab48606d7a20099827e6f
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="snscanfs-snscanfsl-snwscanfs-snwscanfsl"></a>_snscanf_s、_snscanf_s_l、_snwscanf_s、_snwscanf_s_l

從字串讀取所指定長度的格式化資料。 這些是具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述之安全性增強功能的 [_snscanf、_snscanf_l、_snwscanf、_snwscanf_l](snscanf-snscanf-l-snwscanf-snwscanf-l.md) 版本。

## <a name="syntax"></a>語法

```C
int __cdecl _snscanf_s(
   const char * input,
   size_t length,
   const char * format [, argument_list]
);
int __cdecl _snscanf_s_l(
   const char * input,
   size_t length,
   const char * format,
   locale_t locale [, argument_list]
);
int __cdecl _snwscanf_s(
   const wchar_t * input,
   size_t length,
   const wchar_t * format [, argument_list]
);
int __cdecl _snwscanf_s_l(
   const wchar_t * input,
   size_t length,
   const wchar_t * format,
   locale_t locale [, argument_list]
);
```

### <a name="parameters"></a>參數

*input*<br/>
要檢查的輸入字串。

*length*<br/>
要檢查中的字元數*輸入*。

*格式*<br/>
一或多個格式指定名稱。

*locale*<br/>
要使用的地區設定。

*argument_list*<br/>
要指派根據格式字串的選擇性引數。

## <a name="return-value"></a>傳回值

這兩個函式都會傳回成功轉換和指派的欄位數；傳回值不包含已讀取但未指派的欄位。 傳回值 0 表示未指派任何欄位。 傳回值是**EOF**錯誤或如果字串的結尾已到達第一個轉換之前。 如需詳細資訊，請參閱 [sscanf_s、_sscanf_s_l、swscanf_s、_swscanf_s_l](sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)。

如果*輸入*或*格式*是**NULL**指標、 無效參數處理常式會叫用，如中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，這些函數會傳回**EOF**並設定**errno**至**EINVAL**。

如需這些錯誤碼和其他錯誤碼的資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

此函式就像**sscanf_s**不同之處在於它會提供指定固定的檢查從輸入字串的字元數的能力。 如需詳細資訊，請參閱 [sscanf_s、_sscanf_s_l、swscanf_s、_swscanf_s_l](sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)。

緩衝區大小參數是必要項目類型欄位字元**c**， **C**， **s**， **S**，和 **[**. 如需詳細資訊，請參閱 [scanf 類型欄位字元](../../c-runtime-library/scanf-type-field-characters.md)。

> [!NOTE]
> 大小參數的類型是**不帶正負號**，而非**size_t**。

這些函式版本 **_l**尾碼是一樣的不同之處在於會使用傳遞而不是目前的執行緒地區設定的地區設定參數。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_sntscanf_s**|**_snscanf_s**|**_snscanf_s**|**_snwscanf_s**|
|**_sntscanf_s_l**|**_snscanf_s_l**|**_snscanf_s_l**|**_snwscanf_s_l**|

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_snscanf_s**， **_snscanf_s_l**|\<stdio.h>|
|**_snwscanf_s**， **_snwscanf_s_l**|\<stdio.h> 或 \<wchar.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_snscanf_s.c
// This example scans a string of
// numbers, using both the character
// and wide character secure versions
// of the snscanf function.

#include <stdio.h>

int main( )
{
    char        str1[] = "15 12 14...";
    wchar_t     str2[] = L"15 12 14...";
    char        s1[3];
    wchar_t     s2[3];
    int         i;
    float       fp;

    i = _snscanf_s( str1, 6,  "%s %f", s1, 3, &fp);
    printf_s("_snscanf_s converted %d fields: ", i);
    printf_s("%s and %f\n", s1, fp);

    i = _snwscanf_s( str2, 6,  L"%s %f", s2, 3, &fp);
    wprintf_s(L"_snwscanf_s converted %d fields: ", i);
    wprintf_s(L"%s and %f\n", s2, fp);
}
```

```Output
_snscanf_s converted 2 fields: 15 and 12.000000
_snwscanf_s converted 2 fields: 15 and 12.000000
```

## <a name="see-also"></a>另請參閱

[scanf 寬度規格](../../c-runtime-library/scanf-width-specification.md)<br/>
