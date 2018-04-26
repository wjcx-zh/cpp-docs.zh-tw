---
title: _mbsnbcoll、_mbsnbcoll_l、_mbsnbicoll、_mbsnbicoll_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _mbsnbicoll_l
- _mbsnbcoll_l
- _mbsnbcoll
- _mbsnbicoll
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
- mbsnbicoll
- mbsnbcoll
- mbsnbicoll_l
- _mbsnbcoll
- _mbsnbicoll
- _ftcsnicoll
- _ftcsncoll
- mbsnbcoll_l
dev_langs:
- C++
helpviewer_keywords:
- _mbsnbcoll_l function
- mbsnbcoll_l function
- _mbsnbcoll function
- _tcsnicoll function
- mbsnbcoll function
- mbsnbicoll_l function
- mbsnbicoll function
- _tcsncoll function
- _mbsnbicoll function
- _mbsnbicoll_l function
- tcsncoll function
- tcsnicoll function
ms.assetid: d139ed63-ccba-4458-baa2-61cbcef03e94
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5be9c6cb3421b5ba1b191977f70a35d7ffc38625
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="mbsnbcoll-mbsnbcolll-mbsnbicoll-mbsnbicolll"></a>_mbsnbcoll、_mbsnbcoll_l、_mbsnbicoll、_mbsnbicoll_l

比較*n*位元組的兩個多位元組字元字串，使用多位元組字碼頁資訊。

> [!IMPORTANT]
> 這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
int _mbsnbcoll(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
int _mbsnbcoll_l(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count,
   _locale_t locale
);
int _mbsnbicoll(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
int _mbsnbicoll_l(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>參數

*string1*， *string2*<br/>
要比較的字串。

*count*<br/>
要比較的位元組數目。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

傳回值會指出子字串的關聯性*string1*和*string2*。

|傳回值|描述|
|------------------|-----------------|
|< 0|*string1*子字串小於*string2*子字串。|
|0|*string1*子字串等於*string2*子字串。|
|> 0|*string1*子字串大於*string2*子字串。|

如果*string1*或*string2*是**NULL**或*計數*大於**INT_MAX**，無效參數叫用處理常式，如中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，這些函數會傳回 **_NLSCMPERROR**並設定**errno**至**EINVAL**。 若要使用 **_NLSCMPERROR**，包括 String.h 或 Mbstring.h。

## <a name="remarks"></a>備註

所有這些函式自動分頁，最多第一個*計數*位元組*string1*和*string2*和傳回值，指出產生之間的關聯性子字串的*string1*和*string2*。 如果中的子字串的最後一個位元組*string1*或*string2*是前導位元組，它將不會包含在比較中，這些函式比較之子字串只有完整的字元。 **_mbsnbicoll**是不區分大小寫版本的 **_mbsnbcoll**。 像[_mbsnbcmp](mbsnbcmp-mbsnbcmp-l.md)和[_mbsnbicmp](mbsnbicmp-mbsnbicmp-l.md)， **_mbsnbcoll**和 **_mbsnbicoll** collate 根據兩個的多位元組字元字串多位元組所指定的字典編撰順序[字碼頁](../../c-runtime-library/code-pages.md)目前使用中。

針對某些字碼頁和對應的字元集，字元集中的字元順序可能與詞典編纂的字元順序不同。 在 "C" 地區設定中則不然：ASCII 字元集中的字元順序會與詞典編纂的字元順序相同。 不過，某些歐洲字碼頁中的字元順序卻不同，例如，字元 'a' (值 0x61) 在字元集中排在字元 'ä' (值 0xE4) 之前，但在詞典編纂上，字元 'a' 卻排在字元 'ä' 之後。 若要執行這類執行個體中的位元組字串的詞典編纂比較，請使用 **_mbsnbcoll**而 **_mbsnbcmp**; 若要只會檢查字串是否相等，請使用 **_mbsnbcmp**.

因為**coll**函式自動分頁字串以辭典編纂順序進行比較，而**cmp**函式只會測試字串是否相等， **coll**函式對應比慢很多**cmp**版本。 因此， **coll**沒有目前的字碼頁字元集順序與詞典編纂字元順序之間的差異，且比較感興趣的這項差異時，才應該使用函式。

輸出值會影響的設定**LC_CTYPE**之地區設定分類設定，請參閱 < [setlocale](setlocale-wsetlocale.md)如需詳細資訊。 這些沒有 **_l** 尾碼的函式版本，會針對此與地區設定相關的行為使用目前的地區設定；具有 **_l** 尾碼的版本也一樣，只不過它們會改用傳遞的地區設定參數。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsncoll**|[_strncoll](strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|**_mbsnbcoll**|[_wcsncoll](strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|
|**_tcsncoll_l**|[_strncoll、_wcsncoll、_mbsncoll、_strncoll_l、_wcsncoll_l、_mbsncoll_l](strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|**_mbsnbcoll_l**|[_wcsncoll_l](strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|
|**_tcsnicoll**|[_strnicoll](strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|**_mbsnbicoll**|[_wcsnicoll](strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|
|**_tcsnicoll_l**|[_strnicoll_l](strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|**_mbsnbicoll_l**|[_wcsnicoll_l](strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_mbsnbcoll**|\<mbstring.h>|
|**_mbsnbcoll_l**|\<mbstring.h>|
|**_mbsnbicoll**|\<mbstring.h>|
|**_mbsnbicoll_l**|\<mbstring.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[字串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat、_mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_mbsnbcmp、_mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_mbsnbicmp、_mbsnbicmp_l](mbsnbicmp-mbsnbicmp-l.md)<br/>
[strcoll 函式](../../c-runtime-library/strcoll-functions.md)<br/>
[strncmp、wcsncmp、_mbsncmp、_mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp、_wcsnicmp、_mbsnicmp、_strnicmp_l、_wcsnicmp_l、_mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
