---
title: _mbccpy_s、_mbccpy_s_l
ms.date: 4/2/2020
api_name:
- _mbccpy_s
- _mbccpy_s_l
- _o__mbccpy_s
- _o__mbccpy_s_l
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mbccpy_s_l
- mbccpy_s_l
- mbccpy_s
- _mbccpy_s
helpviewer_keywords:
- tccpy_s_l function
- _tccpy_s function
- _mbccpy_s function
- mbccpy_s function
- tccpy_s function
- mbccpy_s_l function
- _tccpy_s_l function
- _mbccpy_s_l function
ms.assetid: b6e965fa-53c1-4ec3-85ef-a1c4b4f2b2da
ms.openlocfilehash: 08df395c6978c84b3f53ed0b07ce988afd0249f6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341239"
---
# <a name="_mbccpy_s-_mbccpy_s_l"></a>_mbccpy_s、_mbccpy_s_l

將一個多位元組字元從某個字串複製到另一個字串。 這些是 [_mbccpy、_mbccpy_l](mbccpy-mbccpy-l.md) 的版本，具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。

> [!IMPORTANT]
> 這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
errno_t _mbccpy_s(
   unsigned char *dest,
   size_t buffSizeInBytes,
   int * pCopied,
   const unsigned char *src
);
errno_t _mbccpy_s_l(
   unsigned char *dest,
   size_t buffSizeInBytes,
   int * pCopied,
   const unsigned char *src,
   locale_t locale
);
template <size_t size>
errno_t _mbccpy_s(
   unsigned char (&dest)[size],
   int * pCopied,
   const unsigned char *src
); // C++ only
template <size_t size>
errno_t _mbccpy_s_l(
   unsigned char (&dest)[size],
   int * pCopied,
   const unsigned char *src,
   locale_t locale
); // C++ only
```

### <a name="parameters"></a>參數

*dest*<br/>
複製目的地。

*福西斯位元組*<br/>
目的緩衝區大小。

*p 複製*<br/>
填入所複製的位元組數目 (若成功，即為 1 或 2)。 如果您不關心該號碼,則通過**NULL。**

*src*<br/>
要複製的多位元組字元。

*現場*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

如果成功，就是零，如果失敗，則為錯誤碼。 如果*src*或*dest*為**NULL,** 或者如果將多個**buffSizein 位元組**的位元組複製到*dest,* 則呼叫無效參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行,則函數傳回**EINVAL,errno**設定為**errno****EINVAL**。

## <a name="remarks"></a>備註

**_mbccpy_s**函數會將多位元位元為*src*複製到*dest*。 如果*src*不指向由對[_ismbblead](ismbblead-ismbblead-l.md)的隱式調用確定的多位元位元元符號的引線位元組,則複製*src*指向的單個字節。 如果*src*指向一個引線位元組,但下面的位元組是 0,因此無效,則 0 被複製到*dest* **,errno**設定為**EILSEQ**,並且函數傳回**EILSEQ**。

**_mbccpy_s**不追加空終止符;否則,_mbccpy_s將附加空終止符。但是,如果*src*指向空字元,則該空將複製到*dest(* 這只是常規的單位元組副本)。

*pCopied*中的值用複製的位元組數填充。 如果作業成功，可能的值為 1 和 2。 如果傳入**NULL,** 則忽略此參數。

|*src*|複製到*dest*|*p 複製*|傳回值|
|-----------|----------------------|---------------|------------------|
|非前導位元組|非前導位元組|1|0|
|0|0|1|0|
|後面接著非 0 的前導位元組|後面接著非 0 的前導位元組|2|0|
|後面接著 0 的前導位元組|0|1|**EILSEQ**|

請注意，第二個資料列只不過是第一個資料列的特殊案例。 另請注意,該表假定*為 buffsizeInBYpb* >= *pcopied*。

**_mbccpy_s**對任何與區域設置相關的行為使用當前區域設置。 **_mbccpy_s_l**與 **_mbccpy_s**相同,只是 **_mbccpy_s_l**使用傳入的任何區域設置相關的行為。

在 C++ 中，使用這些函式已為範本多載簡化；多載可自動推斷緩衝區長度，因而不需要指定大小引數。 如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tccpy_s**|巨集或內嵌函式的對應。|**_mbccpy_s**|巨集或內嵌函式的對應。|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_mbccpy_s**|\<mbstring.h>|
|**_mbccpy_s_l**|\<mbstring.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[地區設定](../../c-runtime-library/locale.md)<br/>
[多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen、mblen、_mblen_l](mbclen-mblen-mblen-l.md)<br/>
