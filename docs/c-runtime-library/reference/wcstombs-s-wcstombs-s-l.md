---
title: wcstombs_s、_wcstombs_s_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _wcstombs_s_l
- wcstombs_s
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
- wcstombs_s
- _wcstombs_s_l
dev_langs:
- C++
helpviewer_keywords:
- wcstombs_s function
- string conversion, wide characters
- wide characters, converting
- _wcstombs_s_l function
- wcstombs_s_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 105f2d33-221a-4f6d-864c-23c1865c42af
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1fec8a41a1c9d1a9d01952a0a72829d2122e0e40
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43216973"
---
# <a name="wcstombss-wcstombssl"></a>wcstombs_s、_wcstombs_s_l

將一連串的寬字元轉換為對應的一連串多位元組字元。 具有 [CRT 的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述之安全性增強功能的 [wcstombs、_wcstombs_l](wcstombs-wcstombs-l.md) 版本。

## <a name="syntax"></a>語法

```C
errno_t wcstombs_s(
   size_t *pReturnValue,
   char *mbstr,
   size_t sizeInBytes,
   const wchar_t *wcstr,
   size_t count
);

errno_t _wcstombs_s_l(
   size_t *pReturnValue,
   char *mbstr,
   size_t sizeInBytes,
   const wchar_t *wcstr,
   size_t count,
   _locale_t locale
);

template <size_t size>
errno_t wcstombs_s(
   size_t *pReturnValue,
   char (&mbstr)[size],
   const wchar_t *wcstr,
   size_t count
); // C++ only

template <size_t size>
errno_t _wcstombs_s_l(
   size_t *pReturnValue,
   char (&mbstr)[size],
   const wchar_t *wcstr,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>參數

*pReturnValue*<br/>
已轉換的字元數。

*mbstr*<br/>
所產生之已轉換的多位元組字串的緩衝區位址。

*sizeInBytes*<br/>
以位元組為單位的大小*mbstr*緩衝區。

*wcstr*<br/>
指向要轉換的寬字元字串。

*count*<br/>
要儲存的位元組數目上限*mbstr*緩衝區，不包括結束的 null 字元，或[_TRUNCATE](../../c-runtime-library/truncate.md)。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

如果成功，則為零，如果失敗，則為錯誤碼。

|錯誤狀況|傳回值和**errno**|
|---------------------|------------------------------|
|*mbstr*已**NULL**並*sizeInBytes* > 0|**EINVAL**|
|*wcstr*是**NULL**|**EINVAL**|
|目的緩衝區太小而無法包含已轉換的字串 (除非*計數*是 **_TRUNCATE**; 請參閱下面的 < 備註 >)|**ERANGE**|

如果發生上述任何一種情況，則會叫用無效的參數例外狀況，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，函式會傳回錯誤碼，並設定**errno**資料表中所示。

## <a name="remarks"></a>備註

**Wcstombs_s**函式會將所指向的寬字元字串轉換*wcstr*到儲存在緩衝區所指向的多位元組字元*mbstr*。 除非遇到下列情況之一，否則會繼續為每個字元進行轉換：

- 遇到 Null 寬字元

- 遇到無法轉換的寬字元

- 儲存在位元組的數目*mbstr*緩衝 equals*計數*。

目的字串一律會以 Null 結束 (即使發生錯誤亦然)。

如果*計數*是特殊值[_TRUNCATE](../../c-runtime-library/truncate.md)，然後**wcstombs_s**的字串會轉換符合目的緩衝區，同時仍留出空間給 null 值結束字元。 如果字串被截斷時，傳回的值是**STRUNCATE**，而且轉換會視為成功。

如果**wcstombs_s**成功轉換來源字串中，它會在將大小以位元組為單位的已轉換的字串，包括 null 結束字元，將放置 *&#42;pReturnValue* (提供*pReturnValue*不是**NULL**)。 發生這種情況即使*mbstr*引數是**NULL** ，並提供一個方式來判斷所需的緩衝區大小。 請注意，如果*mbstr*是**NULL**，*計數*會被忽略。

如果**wcstombs_s**遇到寬字元，它無法轉換成多位元組字元，它會將 0 放 *&#42;pReturnValue*，將目的緩衝區設為空字串，設定**errno**要**EILSEQ**，並傳回**EILSEQ**。

如果指向的序列所*wcstr*並*mbstr*重疊，就會有的行為**wcstombs_s**是未定義。

> [!IMPORTANT]
> 請確認*wcstr*並*mbstr*未重疊時，且*計數*正確反映要轉換的寬字元數目。

**wcstombs_s**針對任何地區設定相關行為; 會使用目前的地區設定 **_wcstombs_s_l**等同於**wcstombs**不同之處在於它會改用傳入的地區設定。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

C++ 利用多載樣板簡化了這些函式的使用方式。多載可自動推斷緩衝區長度 (因而不須指定大小引數)，也可以將不安全的舊函式自動取代成較新且安全的對應函式。 如需詳細資訊，請參閱 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**wcstombs_s**|\<stdlib.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

此程式說明的行為**wcstombs_s**函式。

```C
// crt_wcstombs_s.c
// This example converts a wide character
// string to a multibyte character string.
#include <stdio.h>
#include <stdlib.h>
#include <assert.h>

#define BUFFER_SIZE 100

int main( void )
{
    size_t   i;
    char      *pMBBuffer = (char *)malloc( BUFFER_SIZE );
    wchar_t*pWCBuffer = L"Hello, world.";

    printf( "Convert wide-character string:\n" );

    // Conversion
    wcstombs_s(&i, pMBBuffer, (size_t)BUFFER_SIZE,
               pWCBuffer, (size_t)BUFFER_SIZE );

    // Output
    printf("   Characters converted: %u\n", i);
    printf("    Multibyte character: %s\n\n",
     pMBBuffer );

    // Free multibyte character buffer
    if (pMBBuffer)
    {
    free(pMBBuffer);
    }
}
```

```Output
Convert wide-character string:
   Characters converted: 14
    Multibyte character: Hello, world.
```

## <a name="see-also"></a>另請參閱

[資料轉換](../../c-runtime-library/data-conversion.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[_mbclen、mblen、_mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs、_mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc、_mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wctomb_s、_wctomb_s_l](wctomb-s-wctomb-s-l.md)<br/>
[WideCharToMultiByte](/windows/desktop/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
