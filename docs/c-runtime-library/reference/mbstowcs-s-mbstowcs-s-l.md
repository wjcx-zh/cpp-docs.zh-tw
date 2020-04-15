---
title: mbstowcs_s、_mbstowcs_s_l
ms.date: 4/2/2020
api_name:
- _mbstowcs_s_l
- mbstowcs_s
- _o__mbstowcs_s_l
- _o_mbstowcs_s
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-convert-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mbstowcs_s_l
- mbstowcs_s
helpviewer_keywords:
- _mbstowcs_s_l function
- mbstowcs_s function
- mbstowcs_s_l function
ms.assetid: 2fbda953-6918-498f-b440-3e7b21ed65a4
ms.openlocfilehash: 07d694a7430f23e2f9600a5d2b147bcee2ef0e09
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338815"
---
# <a name="mbstowcs_s-_mbstowcs_s_l"></a>mbstowcs_s、_mbstowcs_s_l

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

*p 傳回值*<br/>
已轉換的字元數。

*wc斯特*<br/>
所產生之已轉換寬字元字串的緩衝區位址。

*大小字內*<br/>
單詞中*wcstr*緩衝區的大小。

*姆布斯特*<br/>
以 Null 結束之多位元組字元序列的位址。

*count*<br/>
要儲存在*wcstr*緩衝區中的最大寬字元數,不包括終止 null 或[_TRUNCATE](../../c-runtime-library/truncate.md)。

*現場*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

如果成功，則為零，如果失敗，則為錯誤碼。

|錯誤狀況|傳回值與**差錯**|
|---------------------|------------------------------|
|*wcstr*為**NULL,***大小 >* 0|**埃因瓦爾**|
|*mbstr*為**NULL**|**埃因瓦爾**|
|目標緩衝區太小,無法包含轉換後的字串(除非*計數***_TRUNCATE;** 請參閱下面的備註 )|**ERANGE**|
|*wcstr*不是**NULL,***大小 InWords* = 0|**埃因瓦爾**|

如果發生上述任何一種情況，則會叫用無效參數例外狀況，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行,則函數將返回錯誤代碼並設置表中指示的**errno。**

## <a name="remarks"></a>備註

**mbstowcs_s**函數將*mbstr*指向的多位元組字串轉換為存儲在*wcstr*指向的緩衝區中的寬字元。 除非遇到下列情況之一，否則會繼續為每個字元進行轉換：

- 遇到多位元組的 null 字元

- 遇到無效的多位元組字元

- 儲存在*wcstr*緩衝區的寬字元數等於*計數*。

目的字串一律會以 Null 結束 (即使發生錯誤亦然)。

如果*count*是[特殊值_TRUNCATE,](../../c-runtime-library/truncate.md)則**mbstowcs_s**轉換盡可能多的字串,以適應目標緩衝區,同時仍然留有空終止符的空間。

如果**mbstowcs_s**成功轉換源字串,它將轉換後的字串(包括空終止符)的大小放入 *&#42;pReturnValue(* 前提是*pReturnValue*不是**NULL)。** 即使*wcstr*參數為**NULL,** 並提供一種確定所需緩衝區大小的方法,也會發生這種情況。 請注意,如果*wcstr*為**NULL,** 則忽略*計數*,*大小 InWords*必須為 0。

如果**mbstowcs_s**遇到無效的多位元位元,它將在*pReturnValue&#42;* 中放入 0,將目標緩衝區設定為空字串,將**errno**設定到**EILSEQ,** 並傳回**EILSEQ**。

如果*mbstr*和*wcstr*指向的序列重疊,則**mbstowcs_s**的行為未定義。

> [!IMPORTANT]
> 確保*wcstr*和*mbstr*不重疊,並且*該計數*正確反映要轉換的多位元組位元元數。

**mbstowcs_s**將當前區域設置用於任何與區域設置相關的行為;**_mbstowcs_s_l**是相同的,只是它使用傳入區域設置。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

C++ 利用多載樣板簡化了這些函式的使用方式。多載可自動推斷緩衝區長度 (因而不須指定大小引數)，也可以將不安全的舊函式自動取代成較新且安全的對應函式。 如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**mbstowcs_s**|\<stdlib.h>|
|**_mbstowcs_s_l**|\<stdlib.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[資料轉換](../../c-runtime-library/data-conversion.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar)<br/>
[多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen、mblen、_mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbtowc、_mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wcstombs、_wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[wctomb、_wctomb_l](wctomb-wctomb-l.md)<br/>
