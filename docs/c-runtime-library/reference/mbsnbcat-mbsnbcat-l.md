---
title: _mbsnbcat、_mbsnbcat_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _mbsnbcat_l
- _mbsnbcat
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
- mbsnbcat
- mbsnbcat_l
- _mbsnbcat
- _mbsnbcat_l
dev_langs:
- C++
helpviewer_keywords:
- tcsncat_l function
- _tcsncat function
- mbsnbcat_l function
- mbsnbcat function
- _mbsnbcat_l function
- _tcsncat_l function
- _mbsnbcat function
- tcsncat function
ms.assetid: aa0f1d30-0ddd-48d1-88eb-c6884b20fd91
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ff7dc09e4305c16ebe710cb99c9e1bdd24490761
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32405050"
---
# <a name="mbsnbcat-mbsnbcatl"></a>_mbsnbcat、_mbsnbcat_l

最多會附加第一個**n**到另一個多位元組字元字串位元組。 這些函式已有更安全的版本可用，請參閱 [_mbsnbcat_s、_mbsnbcat_s_l](mbsnbcat-s-mbsnbcat-s-l.md)。

> [!IMPORTANT]
> 這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
unsigned char *_mbsnbcat(
   unsigned char *dest,
   const unsigned char *src,
   size_t count
);
unsigned char *_mbsnbcat_l(
   unsigned char *dest,
   const unsigned char *src,
   size_t count,
   _locale_t locale
);
template <size_t size>
unsigned char *_mbsnbcat(
   unsigned char (&dest)[size],
   const unsigned char *src,
   size_t count
); // C++ only
template <size_t size>
unsigned char *_mbsnbcat_l(
   unsigned char (&dest)[size],
   const unsigned char *src,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>參數

*dest*<br/>
以 null 終止的多位元組字元目的字串。

*src*<br/>
以 null 終止的多位元組字元來源字串。

*count*<br/>
從位元組數目*src*要附加至*目的地*。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

**_mbsnbcat**傳回目的地字串的指標。 未保留表示錯誤的傳回值。

## <a name="remarks"></a>備註

**_Mbsnbcat**函式會將附加，最多第一個*計數*位元組*src*至*目的地*。 如果前置節點中的 null 字元的位元組*目的地*前導位元組的初始位元組*src*會覆寫此前導位元組。 否則的初始位元組*src*結束的 null 字元會覆寫*目的地*。 如果中出現 null 位元組*src*之前*計數*會附加位元組， **_mbsnbcat**附加所有位元組*src*，直到 null 字元。 如果*計數*大於的長度*src*，長度*src*用來取代*計數*。 此產生的字串會以 Null 字元結束。 如果在重疊的字串之間執行複製，則行為是未定義的。

輸出值會受到地區設定的 **LC_CTYPE** 分類設定影響；如需詳細資訊，請參閱 [setlocale](setlocale-wsetlocale.md)。 **_Mbsnbcat**函式版本會使用目前的地區設定針對此與地區設定相關行為; **_mbsnbcat_l**版本也一樣，只不過它們改用傳入的地區設定參數。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

**安全性提示**：使用以 Null 結束的字串。 以 Null 結束的字串不得超過目的緩衝區的大小。 如需詳細資訊，請參閱 [Avoiding Buffer Overruns (避免緩衝區滿溢)](http://msdn.microsoft.com/library/windows/desktop/ms717795)。

如果*目的地*或*src*是**NULL**，函式中所述，將會產生無效的參數錯誤，[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果處理此錯誤，則此函數會傳回**EINVAL**並設定**errno**至**EINVAL**。

在 C++ 中，這些函式具有樣板多載，可以叫用這些函式的更新且安全的對應版本。 如需詳細資訊，請參閱 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsncat**|[strncat](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)|**_mbsnbcat**|[wcsncat](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)|
|**_tcsncat_l**|**_strncat_l**|**_mbsnbcat_l**|**_wcsncat_l**|

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_mbsnbcat**|\<mbstring.h>|
|**_mbsnbcat_l**|\<mbstring.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[字串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcmp、_mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_strncnt、_wcsncnt、_mbsnbcnt、_mbsnbcnt_l、_mbsnccnt、_mbsnccnt_l](strncnt-wcsncnt-mbsnbcnt-mbsnbcnt-l-mbsnccnt-mbsnccnt-l.md)<br/>
[_mbsnbcpy、_mbsnbcpy_l](mbsnbcpy-mbsnbcpy-l.md)<br/>
[_mbsnbicmp、_mbsnbicmp_l](mbsnbicmp-mbsnbicmp-l.md)<br/>
[_mbsnbset、_mbsnbset_l](mbsnbset-mbsnbset-l.md)<br/>
[strncat、_strncat_l、wcsncat、_wcsncat_l、_mbsncat、_mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[_mbsnbcat_s、_mbsnbcat_s_l](mbsnbcat-s-mbsnbcat-s-l.md)<br/>
