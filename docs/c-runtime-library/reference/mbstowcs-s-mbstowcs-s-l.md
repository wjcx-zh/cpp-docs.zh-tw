---
title: mbstowcs_s、_mbstowcs_s_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _mbstowcs_s_l
- mbstowcs_s
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
- _mbstowcs_s_l
- mbstowcs_s
dev_langs:
- C++
helpviewer_keywords:
- _mbstowcs_s_l function
- mbstowcs_s function
- mbstowcs_s_l function
ms.assetid: 2fbda953-6918-498f-b440-3e7b21ed65a4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5f366e01fbaa8da5c0dbc96ff4da324611e132f1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="mbstowcss-mbstowcssl"></a>mbstowcs_s、_mbstowcs_s_l

將多位元組字元序列轉換成對應的寬字元序列。 這些是 [mbstowcs、_mbstowcs_l](mbstowcs-mbstowcs-l.md) 的版本，具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。

## <a name="syntax"></a>語法

```C
errno_t mbstowcs_s(
   size_t *pReturnValue,
   wchar_t *wcstr,
   size_t sizeInWords,
   const char *mbstr,
   size_t count
);
errno_t _mbstowcs_s_l(
   size_t *pReturnValue,
   wchar_t *wcstr,
   size_t sizeInWords,
   const char *mbstr,
   size_t count,
   _locale_t locale
);
template <size_t size>
errno_t mbstowcs_s(
   size_t *pReturnValue,
   wchar_t (&wcstr)[size],
   const char *mbstr,
   size_t count
); // C++ only
template <size_t size>
errno_t _mbstowcs_s_l(
   size_t *pReturnValue,
   wchar_t (&wcstr)[size],
   const char *mbstr,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>參數

*pReturnValue*<br/>
已轉換的字元數。

*wcstr*<br/>
所產生之已轉換寬字元字串的緩衝區位址。

*sizeInWords*<br/>
大小*wcstr*中文字的緩衝區。

*mbstr*<br/>
以 Null 結束之多位元組字元序列的位址。

*count*<br/>
將儲存在寬字元的數目上限*wcstr*緩衝區，不包括結束的 null 或[_TRUNCATE](../../c-runtime-library/truncate.md)。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

如果成功，則為零，如果失敗，則為錯誤碼。

|錯誤狀況|傳回值和**errno**|
|---------------------|------------------------------|
|*wcstr*是**NULL**和*sizeInWords* > 0|**EINVAL**|
|*mbstr*是**NULL**|**EINVAL**|
|目的地緩衝區為太小，無法包含已轉換的字串 (除非*計數*是 **_TRUNCATE**; 請參閱下面的備註)|**ERANGE**|
|*wcstr*不**NULL**和*sizeInWords* = = 0|**EINVAL**|

如果發生上述任何一種情況，則會叫用無效的參數例外狀況，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，函數會傳回錯誤碼，並設定**errno**如下表所示。

## <a name="remarks"></a>備註

**Mbstowcs_s**函式所指向的多位元組字元字串，轉換為*mbstr*成儲存在緩衝區所指向的寬字元*wcstr*。 除非遇到下列情況之一，否則會繼續為每個字元進行轉換：

- 遇到多位元組的 null 字元

- 遇到無效的多位元組字元

- 儲存在寬字元數目*wcstr*緩衝等於*計數*。

目的字串一律會以 Null 結束 (即使發生錯誤亦然)。

如果*計數*是特殊值[_TRUNCATE](../../c-runtime-library/truncate.md)，然後**mbstowcs_s**轉換的字串會盡量符合目的地緩衝區，同時仍留出空間給 null結束字元。

如果**mbstowcs_s**成功轉換來源字串中，置於已轉換的字串，包含 null 結束字元的寬字元大小 *&#42;pReturnValue* (提供*pReturnValue*不**NULL**)。 發生這種情況即使*wcstr*引數是**NULL** ，並提供一個方式來判斷所需的緩衝區大小。 請注意，如果*wcstr*是**NULL**，*計數*會被忽略，和*sizeInWords*必須是 0。

如果**mbstowcs_s**遇到無效的多位元組字元，它會將 0 放 *&#42;pReturnValue*，設定目的地緩衝區為空字串，設定**errno** 至**EILSEQ**，並傳回**EILSEQ**。

如果指向的序列*mbstr*和*wcstr*重疊，行為**mbstowcs_s**是未定義。

> [!IMPORTANT]
> 請確認*wcstr*和*mbstr*沒有重疊，而且*計數*會正確反映要轉換的多位元組字元數。

**mbstowcs_s**針對任何地區設定相關行為; 使用目前的地區設定 **_mbstowcs_s_l**是完全相同，不同之處在於它會改用傳入的地區設定。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

C++ 利用多載樣板簡化了這些函式的使用方式。多載可自動推斷緩衝區長度 (因而不須指定大小引數)，也可以將不安全的舊函式自動取代成較新且安全的對應函式。 如需詳細資訊，請參閱 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**mbstowcs_s**|\<stdlib.h>|
|**_mbstowcs_s_l**|\<stdlib.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[資料轉換](../../c-runtime-library/data-conversion.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[MultiByteToWideChar](http://msdn.microsoft.com/library/windows/desktop/dd319072)<br/>
[多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen、mblen、_mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbtowc、_mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wcstombs、_wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[wctomb、_wctomb_l](wctomb-wctomb-l.md)<br/>
