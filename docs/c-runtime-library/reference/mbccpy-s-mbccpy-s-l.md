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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 85db4e478b070823bb14028018d918e0f3cabbd7
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920313"
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

*buffSizeInBytes*<br/>
目的緩衝區大小。

*pCopied*<br/>
填入所複製的位元組數目 (若成功，即為 1 或 2)。 如果您不在意數位，請傳遞**Null** 。

*src*<br/>
要複製的多位元組字元。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

如果成功，就是零，如果失敗，則為錯誤碼。 如果*src*或*dest*是**Null**，或如果超過**buffSizeinBytes**個位元組會複製到*目的地*，則會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，則函式會傳回**EINVAL** ，而**errno**會設定為**EINVAL**。

## <a name="remarks"></a>備註

**_Mbccpy_s**函數會將一個多位元組字元從*src*複製到*dest*。 如果*src*未指向[_ismbblead](ismbblead-ismbblead-l.md)的隱含呼叫所決定之多位元組字元的前導位元組，則會複製*src*指向的單一位元組。 如果*src*指向前導位元組，但下列位元組為0，因此無效，則0會複製到*dest*， **errno**會設為**EILSEQ**，而函數會傳回**EILSEQ**。

**_mbccpy_s**不會附加 null 結束字元;不過，如果*src*指向 null 字元，則會將該 null 複製到*目的地*（這只是一般的單一位元組複本）。

*PCopied*中的值會填入已複製的位元組數目。 如果作業成功，可能的值為 1 和 2。 如果傳入**Null** ，則會忽略這個參數。

|*src*|已複製到*目的地*|*pCopied*|傳回值|
|-----------|----------------------|---------------|------------------|
|非前導位元組|非前導位元組|1|0|
|0|0|1|0|
|後面接著非 0 的前導位元組|後面接著非 0 的前導位元組|2|0|
|後面接著 0 的前導位元組|0|1|**EILSEQ**|

請注意，第二個資料列只不過是第一個資料列的特殊案例。 另請注意，資料表會假設*buffSizeInBytes* >= *pCopied*。

**_mbccpy_s**會針對任何與地區設定相關的行為使用目前的地區設定。 **_mbccpy_s_l**與 **_mbccpy_s**相同，不同之處在于 **_mbccpy_s_l**會使用傳入的地區設定來進行任何與地區設定相關的行為。

在 C++ 中，使用這些函式已為範本多載簡化；多載可自動推斷緩衝區長度，因而不需要指定大小引數。 如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

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

[語言](../../c-runtime-library/locale.md)<br/>
[多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen、mblen、_mblen_l](mbclen-mblen-mblen-l.md)<br/>
