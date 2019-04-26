---
title: _mbccpy_s、_mbccpy_s_l
ms.date: 11/04/2016
apiname:
- _mbccpy_s
- _mbccpy_s_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: f9a7554630bd3b46196358c01c21b99978c53e53
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62156846"
---
# <a name="mbccpys-mbccpysl"></a>_mbccpy_s、_mbccpy_s_l

將一個多位元組字元從某個字串複製到另一個字串。 這些是 [_mbccpy、_mbccpy_l](mbccpy-mbccpy-l.md) 的版本，具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。

> [!IMPORTANT]
> 這個應用程式開發介面不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

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

*buffSizeInBytes*<br/>
目的緩衝區大小。

*pCopied*<br/>
填入所複製的位元組數目 (若成功，即為 1 或 2)。 傳遞**NULL**如果您不在意的數字。

*src*<br/>
要複製的多位元組字元。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

如果成功，就是零，如果失敗，則為錯誤碼。 如果*src*或是*dest*是**NULL**，或如果多個**buffSizeinBytes**位元組將會複製到*dest*，則無效參數處理常式會叫用，如中所述[Parameter Validation](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，則函式會傳回**EINVAL**並**errno**設定為**EINVAL**。

## <a name="remarks"></a>備註

**_Mbccpy_s**函式會複製一個多位元組字元從*src*來*dest*。 如果*src*未指向隱含呼叫所決定之多位元組字元的前導位元組[_ismbblead](ismbblead-ismbblead-l.md)，然後的單一位元組， *src*指向會複製。 如果*src*指向前導位元組，但下一個位元組 0 而無效，則 0 複製到*dest*， **errno**設定為**EILSEQ**，和函式會傳回**EILSEQ**。

**_mbccpy_s**不會附加 null 結束字元; 不過，如果*src*指向 null 字元，則該 null 值複製到*dest* （這是只是一般的單一位元組複本）。

中的值*pCopied*填滿複製的位元組數。 如果作業成功，可能的值為 1 和 2。 如果**NULL**傳遞中，會忽略這個參數。

|*src*|複製到*dest*|*pCopied*|傳回值|
|-----------|----------------------|---------------|------------------|
|非前導位元組|非前導位元組|1|0|
|0|0|1|0|
|後面接著非 0 的前導位元組|後面接著非 0 的前導位元組|2|0|
|後面接著 0 的前導位元組|0|1|**EILSEQ**|

請注意，第二個資料列只不過是第一個資料列的特殊案例。 另外請注意，此表格假設*buffSizeInBytes* >= *pCopied*。

**_mbccpy_s**針對任何地區設定相關行為使用目前的地區設定。 **_mbccpy_s_l**等同於 **_mbccpy_s**不同之處在於 **_mbccpy_s_l**會針對任何地區設定相關行為傳入的地區設定。

在 C++ 中，使用這些函式已透過範本多載簡化；多載可自動推斷緩衝區長度，因而不需要指定大小引數。 如需詳細資訊，請參閱 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tccpy_s**|巨集或內嵌函式的對應。|**_mbccpy_s**|巨集或內嵌函式的對應。|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_mbccpy_s**|\<mbstring.h>|
|**_mbccpy_s_l**|\<mbstring.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[地區設定](../../c-runtime-library/locale.md)<br/>
[多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen、mblen、_mblen_l](mbclen-mblen-mblen-l.md)<br/>
